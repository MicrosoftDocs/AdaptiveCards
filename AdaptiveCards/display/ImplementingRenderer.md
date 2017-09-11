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
Return validation errors | ✅ | ❌ | ❌ | ❌ | ❌
Parse extension properties | ❌ | ❌ | ❌ | ❌ | ❌

## Versioning
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Check payload version | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Return fallback text on failure | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Rendering
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Render full schema | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Ignore unknown Elements | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Host Config support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Native platform styling | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Markdown processing | ✅ | ❌ | ❌ | ❌ | ❌ | ❌

## Extensbility
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Override Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Add new Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌
Remove Element Renderer | ✅ | ❌ | ❌ | ❌ | ❌ | ❌

## Actions
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Fire event when tapped | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Action.ShowCard inline expansion | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Inputs
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Input binding (TODO: spec ) | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

## Events
Functionality | HTML | .NET HTML | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Element visibility changed | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Inline Card Expanded? (TODO: redundant?) | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 


# Detailed Specification

The following guidance describes how each of the renderers is implemented and how to follow the same concepts to implement a renderer on any UI platform.

## SDK Versioning

1. The SDK major and minor version MUST match the `schema` version. Patch/build CAN be used for renderer updates that don't have schema changes.

## Parsing

1. A renderer SHOULD check that it's indeed JSON content
1. A renderer MUST attempt to validate against the json-schema
1. Schema validation errors MUST be returned to the calling app
1. A renderer MUST check if the content exceeds the `maxPayloadSize` from hostConfig
1. If unknown elements are encountered they MUST give the host app the opportunity to retrieve them before rendering
1. A renderer MUST parse `extension` properties. TODO: This may not be necessary to highlight if they are in the json schema?

## Versioning

Your renderer should implement a particular version of the schema. If you encounter a `minRequiredVersion` property in the `AdaptiveCard` that is higher than your supported version, you should return the `fallbackText` instead.

## Rendering

An `AdaptiveCard` consists of a `body` and `actions`. The `body` is a collection of `CardElement`s that you will enumerate and render. 

1. Each Element is a "block level" element and MUST take up the width of its container.
1. Unknown elements MUST be ignored and rendering of the rest of the payload continues

> MATT TODO
> * Author final v1.0 json-schema and update docs, including separation/spacing model, `extensions`
> * 1 BREAKING CHANGE on the table is `backgroundImage` property moves into an `images` object.

### Spacing

> TODO: detail spacing spec

### Columns

1. `Column` width MUST be interpreted by "auto", "stretch" or a weighted ratio.

### TextBlock

1. A TextBlock MUST take up a single line unless the `wrap` property is `true`.

## Images

1. TODO Any image notes?

### Host Config

[`HostConfig`](../HostConfig.md) is a **shared configuration object** that specifies how an Adaptive Card Renderer generates UI.  

This allows properties which are platform agnostic to be shared among renderers on different platforms and devices. It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.

1. Renderers MUST expose a **Host Config** parameter to host apps
1. All elements MUST be styled according to their respective host config settings

### Native platform styling

1. Each element type SHOULD attach a native platform style with the generated UI element. E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.

### Markdown
1. Markdown processing SHOULD be supported. TODO: List exactly what we support


## Extensbility 

1. A renderer MUST allow host apps to override default element renderers. E.g., replace `TextBlock` rendering with their own logic.
1. A renderer MUST allow host apps to register custom element types. E.g., add support for a custom `ProgressBar` element
1. A renderer MUST allow host apps to remove support for a default element. E.g., remove `Action.Http` if they don't want it supported.

## Actions

1. The `actions` property MUST be rendered as buttons in some kind of action bar, usually at the bottom of the card. 
1. When a button is tapped it MUST allow the host app to handle the event. You MUST pass along all associated properties with the action, along with `input`  binding (explained below).

Action | Behavior
--- | ---
| * **Action.OpenUrl** | the button opens an external URL for viewing
| **Action.ShowCard** | Requests a sub-card to be shown to the user.  
| **Action.Http** | Requests that all of the input data is gathered up and sent via an HTTP call 
| **Action.Submit** | Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.

### Action.ShowCard

1. `Action.ShowCard` MUST be supported in some way, based on the hostConfig setting. There are two modes: inline, and popup. Inline cards should toggle the card visibility automatically. In popup mode, an event should be fired to the host app to show the card in some way.

## Inputs

1. Inputs SHOULD render with the highest fidelity possible. For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then you should always fall back to rendering a standard text box.
1. For `Action.Submit`, a renderer MUST gather all inputs on the card and retrieve their values.
1. The object MUST be returned to the host app as follows:
> MATT TODO SPEC

> Regex to get input values: `/\{{2}([a-z0-9_$@]+).value\}{2}/gi;`

## Events

1. A renderer MUST fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.
