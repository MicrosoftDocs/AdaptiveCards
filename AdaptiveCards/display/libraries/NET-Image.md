---
title: .NET Image Rendering SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
---

# .NET Image Rendering

As we described in [Getting Started](../GettingStarted.md) page, an Adaptive Card is a JSON-serialized card object model. This library makes it easy to render that JSON into into a PNG image.

This package can even be used on a server to generate images, and implements all the "magic STA thread" goo for you. 

## NuGet install

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf -IncludePrerelease
```

## Example

```csharp
try
{
    // A URL that returns an Adaptive Card JSON payload
    var cardUrl = "http://adaptivecards.io/payloads/ActivityUpdate.json";

    // Timeout after 30 seconds
    var cts = new CancellationTokenSource(TimeSpan.FromSeconds(30));

    // Get the JSON from the card URL
    var client = new HttpClient();
    var response = await client.GetAsync(cardUrl, cts.Token);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the Adaptive Card JSON
    AdaptiveCardParseResult parseResult = AdaptiveCard.FromJson(json);
    AdaptiveCard card = parseResult.Card;

    // Create a host config with no interactivity 
    // (buttons in images would be deceiving)
    AdaptiveHostConfig hostConfig = new AdaptiveHostConfig()
    {
        SupportsInteractivity = false
    };

    // Create a renderer
    AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

    // Set any XAML resource Dictionary if you have one
    //renderer.ResourcesPath = <path-to-your-resourcedictionary.xaml>;

    // Render the card to png
    // Set createStaThread to true if running from a server
    RenderedAdaptiveCardImage renderedCard =
        await renderer.RenderCardToImageAsync(card, createStaThread: true, cancellationToken: cts.Token);
}
catch (OperationCanceledException)
{
    // Timed out
}
catch (Exception ex)
{
    // Log failure
}
```

## Customization

There are 3 ways to customize the adaptive card rendering: 
1. Host Config
2. XAML styling
3. Custom element rendering

See the [WPF docs](NET-WPF.md) for a full run-down of these options.