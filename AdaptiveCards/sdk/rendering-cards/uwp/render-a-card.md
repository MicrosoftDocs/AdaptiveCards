---
title: Render a card - UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Render a card - UWP

Here's how to render a card using the UWP SDK.

## Create an instance of your renderer

Create an instance of the renderer library. 

```csharp
using AdaptiveCards.Rendering.Uwp;
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
RenderedAdaptiveCard renderResult =  renderer.RenderAdaptiveCard(card);
// check if the render was successful
if (renderResult.FrameworkElement != null)
{
    //Get the ui element
    var uiCard = renderResult.FrameworkElement;
    // add it to your ui
    myGrid.Children.Add(uiCard);
}
```

## Example
Here is an example from the UWP renderer.

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderResult = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderResult.FrameworkElement != null)
{
    myGrid.Children.Add(renderResult.FrameworkElement);
}
...
```