---
title: Render a card - WinUI 3 SDK
description: This article walks you through the process of rendering an Adaptive Card using the WinUI 3 SDK.
author: JeanRoca
ms.author: jproca
ms.date: 05/04/2023
ms.topic: how-to
---

# Render a card - WinUI 3

Here's how to render a card using the WinUI 3 SDK.

## Create an instance of your renderer

Create an instance of the renderer library. 

```csharp
using AdaptiveCards.Rendering.WinUI3;
// ...

var renderer = new AdaptiveCardRenderer();
```

## Create a card from a JSON string

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## Create a card from a JSON object

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## Render a card

Acquire a card from a source and render it.

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## Example

Here is an example from the WinUI 3 renderer.

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```
