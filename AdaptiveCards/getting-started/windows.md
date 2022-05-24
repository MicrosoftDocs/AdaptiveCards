---
title:  Adaptive Cards for Windows Developers
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Adaptive Cards for Windows Developers

## Timeline

The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803. 

![Timeline](media/windows/timeline.png)

### UserActivity API

The [`Windows.ApplicationModel.UserActivities.UserActivity`](/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.

The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### Learning Module

There is a great 45-min learn module that covers these steps end-to-end.

[Integrate adaptive cards into Windows 10 Timeline](/learn/modules/integrate-app-into-windows-10-timeline/)

### Learn more

This session at Build 2017 covers User Activities in detail.

## Other Windows Surfaces
We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.

## Dive in!

We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.

* [Browse Sample cards](https://adaptivecards.io/samples/) for inspiration
* Use the [Schema Explorer](https://adaptivecards.io/explorer) to learn the available elements
* Build a card using the [Interactive Visualizer]([https://vnext.adaptivecards.io/visualizer/](https://vnext.adaptivecards.io/visualizer/))
* [Get in touch]([[https://adaptivecards.io/connect](https://github.com/Microsoft/AdaptiveCards/issues/new)](https://github.com/Microsoft/AdaptiveCards/issues/new?title=%5BWebsite%5D%20%5BYour%20feedback%20title%20here%5D&body=%0D%0A%0D%0A%5BYour%20detailed%20feedback%20here%5D%0D%0A%0D%0A---%0D%0A*%20URL%3A%20https%3A%2F%2Fadaptivecards.io%2Fsamples%2F))
