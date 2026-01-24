---
title: Extensibility - .NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: concept-article
---

# Extensibility - .NET HTML

## Custom Element Rendering

For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.

The following example shows how you could define a custom `"type": "Rating"` element and render it.

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public override string Type => "Rating";

    public double Rating { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```
