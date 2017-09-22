---
title: Implementing a Renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
---


# Renderer Status
The following functionality should be included in every Adaptive Cards renderer.

> [!IMPORTANT]
> 
> This content is not finished yet and some major pieces are missing. Check back shortly.


### Parsing
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Return validation failures | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Parse unknown properties | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

### Card Rendering
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Check for supported version | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Render full schema | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
Render actions bar | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
Ignore unknown Elements | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
Host Config support | ✅ | ❌ | ✅ | ✅ | ✅ | ❌
Native platform styling | ✅ | ✅ | ❌ | ❌ | ❌ | ❌

### Element Rendering
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Spacing and Separator | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ 
TextBlock DATE/TIME formatting | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
TextBlock Markdown support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Full Input support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌

### Extensbility
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Override Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌
Add new Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌
Remove Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌

### Actions
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Action.OpenUrl support | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
Action.ShowCard support  | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
Action.Submit support  | ✅ | ❌ | ✅ | ✅ | ✅ | ❌ 
selectAction support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

### Events
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Element visibility changed | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 


# Detailed Specification

The following guidance describes how each of the renderers is implemented and how to follow the same concepts to implement a renderer on any UI platform.

## SDK Versioning

1. The SDK major and minor version **MUST** match the `schema` version. Patch/build **CAN** be used for renderer updates that don't have schema changes.

## Parsing

1. A renderer **SHOULD** check that it's valid JSON content
1. A renderer **SHOULD** attempt to validate against the json-schema
1. Schema validation errors **MUST** be returned to the host app
1. A renderer **MUST** check if the content exceeds the `maxPayloadSize` from Host Config
1. If unknown elements are encountered they **MUST** give the host app the opportunity to access them before rendering
1. A renderer **MUST** parse `extension` properties. TODO: This may not be necessary to highlight if they are in the json schema?
1. The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified

## Parsing Host Config
1. TODO

## Versioning

1. A renderer **MUST** implement a particular version of the schema. 
1. The `AdaptiveCard` constructor **MUST** give the `Version` property a default value based on the current schema version 
1. If a renderer encounters a `minRequiredVersion` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.

## Rendering

An `AdaptiveCard` consists of a `body` and `actions`. The `body` is a collection of `CardElement`s that a renderer will enumerate and render. 

1. Each Element is a "block level" element and **MUST** stretch to the width of its container.
1. A renderer **MUST** ignore unknown elements, and continue rendering the rest of the payload.

### Spacing and Separators

1. The `spaceing` property on every element influences the amount of space between the **current** element and the one **before** it.
1. Spacing **MUST ONLY** apply when an element **IS NOT** the first in the array.
1. A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.
1. If the element has a `separator` of `true`, then a visible line **MUST** be drawn between the current element and the one before it.
1. The separator line **MUST** be drawn using the `container` `style` `defaultColor`. (TODO: confirm this property name)
1. A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.

### Columns

1. `Column` width **MUST** be interpreted by "auto", "stretch" or a weighted ratio.

### TextBlock

1. A TextBlock **MUST** take up a single line unless the `wrap` property is `true`. 
1. The text block **SHOULD** trim any excess text with an ellipsis (...)

#### Markdown

1. Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`. 

_Supported_
Text Style | Markdown
---|---
**Bold**        | `**Bold**`
_Italic_        | `_Italic_`
Bullet list     | ```- Item 1\r- Item 2\r- Item 3```
Numbered list   | ```1. Green\r2. Orange\r3. Blue```
Hyperlinks      | ```[Title](url)```

_Not supported_
* Headers
* Tables
* Images

#### Formatting functions

1. `TextBlock` allows [date/time formatting functions](../create/TextFeatures.md) that **MUST** be supported on every renderer.
1. TODO: Include regex and spec


### Images

1. A renderer **MUST** optionally allow host apps to prefetch all HTTP images and only callback to the host app when card has been fully rendererd.
1. A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images

#### Image content

1. A renderer **MUST** support .png and .jpeg
1. A renderer **SHOULD** support .gif images


### Host Config

* TODO: What should the defaults be? Should they all share it? Should we embed a common hostConfig.json file in the binaries?
* TODO: I think HostConfig needs to be versioned as well for parsing?

[`HostConfig`](HostConfig.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.  

This allows properties which are platform agnostic to be shared among renderers on different platforms and devices. It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.

1. Renderers **MUST** expose a **Host Config** parameter to host apps
1. All elements **MUST** be styled according to their respective Host Config settings

### Native platform styling

1. Each element type **SHOULD** attach a native platform style with the generated UI element. E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.


## Extensbility 

1. A renderer **MUST** allow host apps to override default element renderers. E.g., replace `TextBlock` rendering with their own logic.
1. A renderer **MUST** allow host apps to register custom element types. E.g., add support for a custom `ProgressBar` element
1. A renderer **MUST** allow host apps to remove support for a default element. E.g., remove `Action.Submit` if they don't want it supported.

## Actions

1. If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.
1. The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card. 
1. When a button is tapped it **MUST** allow the host app to handle the event. 
1. The event **MUST** pass along all associated properties with the action
1. The event **MUST** pass along the `AdaptiveCard` which was executed

Action | Behavior
--- | ---
**Action.OpenUrl** | Open an external URL for viewing
**Action.ShowCard** | Requests a sub-card to be shown to the user.
**Action.Submit** | Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.

### Action.OpenUrl
1. `Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism
1. If this is not possible it **MUST** raise an event to the host app to handle opening the URL. This event **MUST** allow the host app to override the default behavior. E.g., let them open the URL within their own app.

### Action.ShowCard

1. `Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting. There are two modes: inline, and popup. Inline cards **SHOULD** toggle the card visibility automatically. In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.

### Action.Submit

The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them. 

1. When this **MUST** raise an event the user taps the action invokved.  
1. The `data` property **MUST** be included in the callback payload.
1. For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values. This RegEx can be used to gather input values: `/\{{2}([a-z0-9_$@]+).value\}{2}/gi;`

### selectAction

1. If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.
1. `Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.

## Inputs

1. If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.
1. Inputs **SHOULD** render with the highest fidelity possible. For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.
1. A renderer **SHOULD** display the `placeholderText` if possible
1. A renderer **DOES NOT** have to implement validation of the input. Users of Adaptive Cards must plan to validate any receieved data on their end.
1. Input value binding **MUST** be properly escaped

1. The object **MUST** be returned to the host app as follows:

 We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response. E.g., a Input.Number could return "hello" and they need to be prepared for that.


## Events

1. A renderer **MUST** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.
