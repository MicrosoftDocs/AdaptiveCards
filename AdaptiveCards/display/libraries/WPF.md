---
title: WPF SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# WPF library

This is a renderer which targets WPF XAML.  It has no dependencies outside of standard Windows components, 
which means it supports `Date` and `Time` controls as simple textbox controls.

## Getting the SDK
This is available as a nuget packages. 
```console
Install-Package AdaptiveCards.Renderer.Wpf
```

## Render card

### Instantiate a renderer
Create an instance of the renderer library. 
```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Config;
// ...

// Create a default renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// Or use custom host config
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

// Or assign the host config with the property
renderer.HostConfig = hostConfig;

// Get the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

### Render a Card WPF

```csharp
RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

// Validate the rendered card
if (renderedCard.FrameworkElement == null)
{
    // Failed rendering
    return;
}

// Get the FrameworkElement
FrameworkElement el = renderedCard.FrameworkElement;

// Just for fun, get the AdaptiveCard object model back out
AdaptiveCard originatingCard = renderedCard.OriginatingCard;
```

### Render a Card Xamarin
In Xamarin, we return a View item.

```csharp
RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

// Validate the rendered card
if (renderedCard.View == null)
{
    // Failed rendering
    return;
}

// Get the view
View view = renderedCard.View;

// Just for fun, get the AdaptiveCard object model back out
AdaptiveCard originatingCard = renderedCard.OriginatingCard;
```

### Wire up Action events
On your rendered card, use the `OnAction` event to subscribe to action invoked events.
```csharp
RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

renderedCard.OnAction += MainView_OnAction;

private void MainView_OnAction(object sender, ActionEventArgs e)
{
    // What action was tapped
    ActionBase action = e.Action;
}
```

### HostConfig

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
If you pass in a Xaml ResourceDictionary, you can customize the Xaml behavior further. This
allows you to define roll over behaviors, animations, rounded buttons, and so forth.  Here is a table of the 
style names that are used for each element.  

| Element | Style names used|
|---|---|
| AdaptiveCard | Adaptive.Card| 
| Action.Http | Adaptive.Action.Http |
| Action.OpenUrl  | Adaptive.Action.OpenUrl  |
| Action.ShowCard | Adaptive.Action.ShowCard |
| Action.Submit  | Adaptive.Action.Submit  |
| ActionSet | Adaptive.ActionSet |
| Column | Adaptive.Column, Adaptive.Action.Tap |
| ColumnSet | Adaptive.ColumnSet, Adaptive.VerticalSeparator |
| Container | Adaptive.Container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem, |
| Input.Date | Adaptive.Input.Text.Date
| Input.Number | Adaptive.Input.Text.Number |
| Input.Text | Adaptive.Input.Text |
| Input.Time | Adaptive.Input.Text.Time |
| Input.Toggle| Adaptive.Input.Toggle|
| Image  | Adaptive.Image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value|
| TextBlock  | Adaptive.TextBlock |

Here is a sample resource dictionary which adds a hover effect on elements with an Action defined on them:
```xml
<Window.Resources>
    <Style x:Key="Adaptive.Action.Tap" TargetType="Button">
        <Style.Triggers>
            <Trigger Property="IsMouseOver" Value="True">
                <Setter Property="Cursor" Value="Hand" />
            </Trigger>
            <EventTrigger RoutedEvent="UIElement.MouseEnter">
                <BeginStoryboard>
                    <Storyboard>
                        <DoubleAnimation Duration="0:0:0.2" Storyboard.TargetProperty="Opacity" To="0.7" />
                    </Storyboard>
                </BeginStoryboard>
            </EventTrigger>
            <EventTrigger RoutedEvent="UIElement.MouseLeave">
                <BeginStoryboard>
                    <Storyboard>
                        <DoubleAnimation Duration="0:0:0.2" Storyboard.TargetProperty="Opacity" To="1.0" />
                    </Storyboard>
                </BeginStoryboard>
            </EventTrigger>

        </Style.Triggers>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="Button">
                    <Border Background="Transparent">
                        <ContentPresenter/>
                    </Border>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
</Window.Resources>
```

## Extensibility

### Change per-element rendering
The renderer has a registration mechanism which allows you to set a function that is called to perform the
rendering on a per-element basis.  It exposes a method called `ElementRenderers.Set<TElement>(func); `

To override the rendering of a `Input.Date` element:
```csharp
renderer.ElementRenderers.Set<DateInput>(MyCustomDateInputRenderer);
```

The new date renderer would look like this in WPF:
```csharp
public static FrameworkElement Render(DateInput input, RenderContext context)
{
    var datePicker = new DatePicker();
    ...
    return datePicker;
}
```

In Xamarin, it would look like this:
```csharp
public static View Render(DateInput input, RenderContext context)
{
    var datePicker = new DatePicker();
    ...
    return datePicker;
}
```


## Example
Here is an example from the WPF renderer.

```csharp
var hostConfig = new HostConfig() { ... };
var renderer = new AdaptiveCardRenderer(hostConfig);

var renderedCard = renderer.RenderCard(card);
renderedCard.OnAction += _onAction;

myGrid.Children.Add(rendererdCard.FrameworkElement);
...

private void _onAction(object sender, ActionEventArgs e)
{
    if (e.Action is OpenUrlAction)
    {
        OpenUrlAction action = (OpenUrlAction)e.Action;
        Process.Start(action.Url);
    }
    else if (e.Action is ShowCardAction)
    {
        ShowCardAction action = (ShowCardAction)e.Action;
        ShowCardWindow dialog = new ShowCardWindow(action.Title, action, this.Resources);
        dialog.ShowDialog();
    }
    else if (e.Action is SubmitAction)
    {
        SubmitAction action = (SubmitAction)e.Action;
        // Send e.Data to the source...
        ...
    }
    else if (e.Action is AdaptiveCards.HttpAction)
    {
        AdaptiveCards.HttpAction action = (HttpAction)e.Action;
        ... 
        // action.Headers  has headers for HTTP operation
        // action.Body has content body
        // action.Method has method to use
        // action.Url has url to post to
    }
}
```


## Next steps

* [Implement a renderer](../ImplementingRenderer.md) 


