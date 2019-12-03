---
title: ICardActionHandler class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

### ICardActionHandler

``` C#
public interface ICardActionHandler : IJavaObject 
```

**Namespace**
``` C#
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler
```

### Summary

| Public methods | |
| --- | ---- |
| ```abstract void``` | [```OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)```](http://something.com) |
| ```abstract void``` | [```OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)```]() |
| ```abstract void``` | [```OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)```]() |

## Public Methods
--- 
### <a href="icardactionhandler-func-onaction"></a> OnAction
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
void OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)
```

Listener called when a OpenUrlAction, SubmitAction or ShowCardAction (if not inline) are clicked.

| Parameters | |
| --- | --- |
| p0 | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElement``` |
| p1 | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard``` |

#### Sample

``` C#
public class MyCardActionHandler : ICardActionHandler
{

    public void OnAction(BaseActionElement element, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = element.ElementType;
        if (actionType == ActionType.Submit)
        {
            var inputs = renderedCard.Inputs;
            string inputValues = string.Empty;
            foreach (var inputString in inputs)
            {
                inputValues += $"{{{inputString.Key} : {inputString.Value}}}\n";
            }
            submitData(inputValues);
        }
        else if (actionType == ActionType.ShowCard)
        {
            var showcardAction = ShowCardAction.Dynamic_cast(element);
            showCard(showcardAction.Card)
        }
        else if (actionType == ActionType.OpenUrl)
        {
            var openUrlAction = OpenUrlAction.Dynamic_cast(element);
            openUrl(openUrlAction.Url);
        }
    }
}
```

---
### <a href="icardactionhandler-func-onmediaplay"></a> OnMediaPlay
<p style='text-align:right'>Added in version 0.1</p>

``` C#
void OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)
```

Listener called when the media element starts playing.

| Parameters | |
| --- | --- |
| p0 | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| p1 | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard``` |

#### Sample

``` C#
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaPlay(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```

--- 

### <a href="icardactionhandler-func-onmediastop"></a> OnMediaStop
<p style='text-align:right'>Added in version 0.1</p>

``` C#
void OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)
```

Listener called when the media element stops playing.

| Parameters | |
| --- | --- |
| p0 | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| p1 | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard``` |

#### Sample

``` C#
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaStop(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```