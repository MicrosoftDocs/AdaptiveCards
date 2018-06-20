---
title: .NET WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
---

# Getting started - .NET WPF

As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model. This library makes it easy to render that JSON into WPF UI that you can use within your app.

## NuGet install

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf -IncludePrerelease
```

### Xceed enhanced input package

This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box. It has a dependency on `Extended.Wpf.Toolkit`

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed -IncludePrerelease
```

## WPF Visualizer Sample

![Visualizer screenshot](../../../resources/media/tools/wpfvisualizer.png)

The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.  A `Host Config` editor is built in for editing and viewing host config settings. Save these settings as a JSON to use them in rendering in your application.

## Next steps

See [Render a card](render-a-card.md) for the next steps!