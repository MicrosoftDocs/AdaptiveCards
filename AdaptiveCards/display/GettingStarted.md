---
title: Displaying Cards inside your application
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Displaying Cards inside your application

It's easy to render Adaptive Cards inside your application. We provide SDKs for the all common platforms, as well as provide a [detailed specification](ImplementingRenderer.md) for creating your own Adaptive Card renderer.

1. **Install a renderer SDK** - for your target platform.
2. **Create a renderer instance** - configured with your app's style, rules, and action event handlers.
3. **Render a card to native UI** - automatically styled to your app.

## Adaptive Cards SDKs

|Platform|Install|Build|Docs|
|---|---|---|---|
| HTML Client | [![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/htmlclient) |
| .NET WPF | [![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/wpf) |
| .NET HTML | [![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/htmlserver)
| Windows UWP | [![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Renderer.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Renderer.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/uwp) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android-arm.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android-arm%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/android) |
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) |[Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Docs](https://docs.microsoft.com/en-us/adaptive-cards/display/libraries/ios) |


## Create an instance of the renderer

The next step is to create an instance of an `AdaptiveCardRenderer`. 

### Hook up action events

By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect. Each SDK has the equivalent of an `OnAction` event that you must handle.

* **Action.OpenUrl** - open the specified `url`.  
* **Action.Submit** - take the result of the submit and send it to the source. How you send it to the source of the card is entirely up to you.
* **Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog. Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.

## Render a card

After you acquire a card payload, simply call the renderer and pass in the card. You will to get back a native UI object made up of the card contents. Now just put this UI somewhere in your app.

## Customization

There are several ways you can customize what is rendered. 

### HostConfig

A [HostConfig](HostConfig.md) is a shared, cross-platform configuration object that controls the basic styling and behavior of cards inside your app. It defines things like font sizes, spacing between elements, colors, number of supported actions, etc. 

### Native platform styling

Most UI frameworks allow you to style the rendered card be using the native UI framework styling. For example, in HTML you can specify CSS classes for the HTML, or in XAML you can pass in a custom ResourceDictionary for fine-grained control of the output.

### Customize per-element rendering

Each SDK allows you to override the rendering of any element, or even add support for entirely new elements that you define.  For example, you can change the `Input.Date` renderer to emit your own custom control while still retaining the rest of the output of the renderer. Or you can add support for a custom `Rating` element to you define.



