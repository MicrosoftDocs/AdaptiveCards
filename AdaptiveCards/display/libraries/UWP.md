---
title: UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# UWP library
This is a renderer which targets UWP native controls.

## Add a renderer

```console
Install-Package AdaptiveCards.Rendering.Uwp -IncludePrerelease
```

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

### HostConfig 

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../HostConfig.md) for the full description.)

> The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.


Example:
```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```
> Alternatively, you can load the HostConfig from a JSON string.

Example:
```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.

### Changing per element rendering
Implement a renderer class and set it in the renderer

```csharp
// My custom renderer is going to replace how textblocks should render!
public class MyCustomRenderer : IAdaptiveElementRenderer
{
    public UIElement Render(IAdaptiveCardElement element, AdaptiveRenderContext context)
    {
        var adaptiveTextBlock = element as AdaptiveTextBlock;
        TextBlock textblock = new TextBlock()
        {
            Text = adaptiveTextBlock.Text + "I want every single textblock to append this text, and it should be aligned to the right!",
            HorizontalAlignment = HorizontalAlignment.Right
        };

        return textblock;
    }
}

renderer.ElementRenderers.Set("TextBlock", new MyCustomRenderer());
```

### UI Framework styling
*Coming soon*

