---
title: Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# Getting started - Xamarin.Android

This is a renderer library which targets native xamarin android applications and is based on the Android renderer that you can find [here](../../android/getting-started.md). 

## NuGet install

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)

You can find the published packages [here](http://nuget.org)

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## Namespace

The necessary namespaces for using this library are
```csharp
// To import the base object model classes as AdaptiveCard, TextBlock, Column, ShowCardAction, ...
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;

// To import the AdaptiveCardRenderer class
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;

// To import the ICardActionHandler interface
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// To use feature registration and register custom behaviour 
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration;
```

## Xamarin.Android Visualizer Sample

The [Xamarin.Android Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) lets you visualize cards using Xamarin.Android. If you have ever used the Android sample application you'll find the experience to be really similar.

## Next steps

For a quick start check [Render a card](render-a-card.md) for the next steps!

For a more in depth view of the classes that have been binded for the Xamarin.Android renderer library, you can check some of the binded classes by clicking on them below:
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)
