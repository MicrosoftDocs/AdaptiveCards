---
title: Implementing a Renderer
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

> [!IMPORTANT]
> 
> This content is not finished yet and some major pieces are missing. Check back shortly.

# Renderer Status
The following functionality should be included in every Adaptive Cards renderer.

## Parsing
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Validate JSON-schema | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ 
Return validation failures | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Parse extension properties | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Versioning
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Check payload version | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Return fallback text on failure | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Rendering
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Render full schema | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
TextBlock customizations | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Ignore unknown Elements | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Host Config support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Native platform styling | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Markdown support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌

## Extensbility
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Override Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Add new Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Remove Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌

## Actions
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Action.OpenUrl support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Action.ShowCard support  | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Action.Submit support  | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Events
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Element visibility changed | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 



# Detailed Specification

The following guidance describes how each of the renderers is implemented and how to follow the same concepts to implement a renderer on any UI platform.

## SDK Versioning

1. The SDK major and minor version **MUST** match the `schema` version. Patch/build **CAN** be used for renderer updates that don't have schema changes.

## Parsing

1. A renderer **SHOULD** check that it's valid JSON content
1. A renderer **MUST** attempt to validate against the json-schema
1. Schema validation errors **MUST** be returned to the host app
1. A renderer **MUST** check if the content exceeds the `maxPayloadSize` from Host Config
1. If unknown elements are encountered they **MUST** give the host app the opportunity to access them before rendering
1. A renderer **MUST** parse `extension` properties. TODO: This may not be necessary to highlight if they are in the json schema?
1. The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified

## Parsing Host Config
1. TODO MATT

## Versioning

1. A renderer **MUST** implement a particular version of the schema. 
1. If a renderer encounters a `minRequiredVersion` property in the `AdaptiveCard` that is higher than the supported version, it **SHOULD** return the `fallbackText` instead.

## Rendering

An `AdaptiveCard` consists of a `body` and `actions`. The `body` is a collection of `CardElement`s that you will enumerate and render. 

1. Each Element is a "block level" element and **MUST** take up the width of its container.
1. A renderer **MUST** ignore unknown elements, and continue rendering the rest of the payload

> MATT TODO
> * Author final v1.0 json-schema and update docs, including separation/spacing model, `extensions`, id property

### Spacing

1. A visible separator **MUST** only be drawn if the item is not the first in an array.
> MATT TODO: detail spacing spec
https://github.com/Microsoft/AdaptiveCards/issues/462

### Columns

1. `Column` width **MUST** be interpreted by "auto", "stretch" or a weighted ratio.

### TextBlock

1. A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.

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

1. A renderer **MUST** optionally allow host apps to prefetch any HTTP images and only return when the card has been fully rendererd.
1. A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images

#### Image content
1. A renderer **MUST** support .png and .jpeg
1. A renderer **SHOULD** support .gif images


### Host Config

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


## Inputs

1. If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.
1. Inputs **SHOULD** render with the highest fidelity possible. For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then you **MUST** fall back to rendering a standard text box.
1. A renderer **MUST** display the `placeholderText` in the most appropriate way possible

1. The object **MUST** be returned to the host app as follows:
* MATT TODO SPEC

## Events

1. A renderer **MUST** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.
