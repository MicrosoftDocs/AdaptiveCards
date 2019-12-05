---
title: Actions - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# Actions - Xamarin.Android

When a cards action is executed, the class that was passed to the render call that implements the [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) interface gets invoked. Here is how to define your action handler:

```java
public class CardActionHandlerImpl : ICardActionHandler
{

    public void OnAction(BaseActionElement element, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = element.ElementType;
        if (actionType == ActionType.Submit)
        {
            var submitAction = SubmitAction.Dynamic_cast(element);
            var data = submitAction.DataJson;
            Toast.MakeText(this, data + "\n" + inputValues, ToastLength.Short).Show();
        }
        else if (actionType == ActionType.ShowCard)
        {
            var showcardAction = ShowCardAction.Dynamic_cast(element);
            var card = showcardAction.Card;
            showCard(card);
        }
        else if (actionType == ActionType.OpenUrl)
        {
            var openUrlAction = OpenUrlAction.Dynamic_cast(element);
            var url = openUrlAction.Url;
            openUrl(url);
        }
    }

    public void OnMediaPlay(BaseCardElement element, RenderedAdaptiveCard renderedCard) { }

    public void OnMediaStop(BaseCardElement element, RenderedAdaptiveCard renderedCard) { }
}
```
