---
title: HTML Server SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# HTML server library
This is a .NET server side library for generating HTML markup to be sent to a client.

## Getting the SDK
This is available as a nuget packages. 
```console
// TODO: This isn't updated
nuget install Microsoft.AdaptiveCards.Html
```

## Render card

### Instantiate a renderer
The next step is to create an instance of the renderer. 

```csharp
// Create a default renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// Or use custom host config
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

// Or assign the host config with the property
renderer.HostConfig = hostConfig;

// Get the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

### Render a Card
```csharp
RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

// Validate the rendered card
if (renderedCard.HtmlTag == null)
{
    // Failed rendering
    return;
}

// Get the HTML string
string html = renderedCard.HtmlTag.ToString();

// Just for fun, get the AdaptiveCard object model back out
AdaptiveCard originatingCard = renderedCard.OriginatingCard;
```

### Wire up Action events
This library doesn't currently support the action callback.

### HostConfig 
To customize the renderer, provide an instance of the HostConfig object. See the [Host Config Schema](../HostConfig.md) for a full description. Since the HostConfig object is instantiated with defaults, you only have to set the properties you want to change from the defaults.

Passing it to the renderer sets the HostConfig to use for every card you render.

Example:
```csharp
// Construct programmatically
var hostConfig = new HostConfig() 
{
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
HostConfigParseResult result = HostConfig.FromJson(@"{
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");

if (result.HostConfig != null)
{
    HostConfig config = result.HostConfig;
}
else
{
    // Error parsing
}
```

### Native platform styling
This framework annotates all HtmlTags it outputs with the following class names so that you can use CSS to customize further.

| Element | Style names used|
|---|---|
| AdaptiveCard | ac-adaptivecard | 
| Action.Http | - |
| Action.OpenUrl  | -|
| Action.ShowCard | -|
| Action.Submit  | -  |
| ActionSet | ac-actionset |
| Column | ac-column |
| ColumnSet | ac-columnset |
| Container | ac-container|
| Input.ChoiceSet | - |
| Input.Date | - |
| Input.Number | - |
| Input.Text | - |
| Input.Time | - |
| Input.Toggle| - |
| Image  | ac-image |
| ImageSet  | ac-imageset |
| FactSet | ac-factset, ac-facttitle, ac.factvalue|
| TextBlock  | ac-textblock |


## Extensibility

### Change per-element rendering
The HtmlRenderer has a registration mechanism which allows you to set a function that is called to perform the
rendering on a per-element basis.  It exposes a method called `ElementRenderers.Set<TElement>(func);` 

To override the rendering of a `Input.Date` element:

```csharp
renderer.ElementRenderers.Set<DateInput>(MyCustomDateInputRenderer);
```

The new date renderer would look like this:

```csharp
protected static HtmlTag MyCustomDateInputRenderer(DateInput input, RenderContext context)
{
    ...
    return htmlTag;
}
```

### Remove a renderer

```csharp
renderer.ElementRenderers.Remove<DateInput>();
```

### Get a renderer

```csharp
// Get using generic type
Func<DateInput, TContext, TUIElement> renderFunc = renderer.ElementRenderers.Get<DateInput>();

// Get using runtime type
Func<TypedElement, TContext, TUIElement> renderFunc = renderer.ElementRenderers.Get(element.GetType());
```

## Example
An example from the HTML sample app.

```csharp
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(new HostConfig()
{
    SupportsInteractivity = supportsInteractivity
});

RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

if (renderedCard.HtmlTag != null)
{
    Console.WriteLine($"<div class='cardcontainer'>{renderedCard.HtmlTag.ToString()}</div>");
}
else
{
    Console.WriteLine($"<p>Rendering failed</p>");
}
```




## Next steps

* [Implement a renderer](../ImplementingRenderer.md) 


