---
title: Extensibility - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: concept-article
---

# Extensibility - JavaScript

## Extensibility with the JS SDK version 2.0 and greater

### Before you start

> **IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html). Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered. For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).


### Custom elements
The steps for creating a custom Adaptive Card element type are:
- Create a new class deriving from `CardElement`
- Create its schema by declaring static property definitions
- Implement its `getJsonTypeName`, and `internalRender` methods
- Register it in the global element registry, or use a custom registry on a per-card basis


Let's take an example and implement a simple Progress Bar element:
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
That's it. The ProgressBar element now needs to be registered in order to be recognized by the SDK. You can register it globally:

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Or you can use a per-card registry, which allows the use of different registries for different cards in your application:

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### Custom inputs
An input is a special type of element dedicated to collecting data entered by the end user that can subsequently be passed as parameter to actions.

Versions 2.x of the Adaptive Cards JS SDK introduces two notable changes when it comes to inputs:
- **Input validation:** there is now a built-in input validation mechanism that automatically handles validation errors including visual cues
- **Accessibility improvements:** built-in inputs have better support for accessibility features

Because of this, implementing custom inputs requires a little more logic than implementing simple elements. The table below lists all the methods a custom input implementation should to implement in order to partiocipate in the input validation mechanism and be accessible:

| Method | Description |
| --------- | ------------- |
| `protected updateInputControlAriaLabelledBy()` | This method  is called during the input validation sequence. When an input fails validation, its associated error message is displayed and the underlying input control's `aria-labelledby` attribute needs to be updated in order for the input to comply with accessibility requirements. Custom inputs SHOULD override `updateInputControlAriaLabelledBy` to apply the appropriate `aria-labelledby` attribute to the underlying input control. The `getAllLabelIds(): string[]` method can be used to retrieve the Ids of all the labels that should be specified in the `aria-labelledby` attribute.  |
| `protected internalRender(): HTMLElement` | Just like for any other Adaptive Card custom element, `internalRender` MUST be overridden to render your input as desired. This is where you'll want to create the actual underlying input control. |
| `protected get isNullable(): boolean` | Indicates whether the input supports undefined values (for instance, Input.Text does, whereas Input.Toggle doesn't.) Custom inputs SHOULD override this property getter to indicate if they support undefined values. The base implementation returns `true`. |
| `public focus()` | When validation errors are encountered, the focus is automatically placed on the first input that failed validation. The base implementation of `focus` will in some cases just work for custom inputs. When that isn't the case, custom input controls MUST override `focus` to explicitly put the focus on the underlying input control.  |
| `public abstract isSet(): boolean` | Indicates whether the input's value has been set by the user. This method is called during the input validation sequence to determine if the input passes or fails validation. Custom inputs MUST override `isSet` in order to participate in the input validation mechanism. |
| `public isValid(): boolean` | Indicates whether the value of the input is valid. This method is called during the input validation sequence to determine if the input passes or fails validation. Custom inputs SHOULD override `isValid` in order to participate in the input validation mechanism. The base implementation returns `true`. |
| `public abstract get value(): any` | Returns the value of the input. Custom inputs MUST override this so that the value of the input is retrieved from the underlying input control. |


### Custom actions
The steps to implementing a custom action are the same as those for elements. The only difference is that actions are registered in action registries, and not in element registries.

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

Register the new action globally:
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Or use a per-card registry:
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## Extensibility with the JavaScript SDK prior to version 2.0

### Custom elements

### Before you start

> **IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html). Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered. For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).


### Custom elements
The steps for creating a custom Adaptive Card element type are:
- Create a new class deriving from `CardElement`
- Create its schema by declaring static property definitions
- Implement its `getJsonTypeName`, and `internalRender` methods
- Register it in the global element registry, or use a custom registry on a per-card basis


Let's take an example and implement a simple Progress Bar element:
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
That's it. The ProgressBar element now needs to be registered in order to be recognized by the SDK. You can register it globally:

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Or you can use a per-card registry, which allows the use of different registries for different cards in your application:

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### Custom actions
The steps to implementing a custom action are the same as those for elements. The only difference is that actions are registered in action registries, and not in element registries.

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

Register the new action globally:
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Or use a per-card registry:
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## Extensibility with the JS SDK prior to version 2.0

### Custom elements

The steps for creating a custom Adaptive Card element type are:
- Create a new class deriving from `CardElement`
- Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods
- Register it by adding it to the renderer's element registry

Let's take an example and implement a simple Progress Bar element:

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

That's it. Now just register the Progress Bar class with the renderer:

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## Custom actions

The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements. Here is a simple example of an Alert Action that simply displays a message box with configurable text:

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

Now register the new action:

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## Example

Here is a sample card that uses both the ProgressBar element and AlertAction action:
```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

And here is how it renders:
![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)
