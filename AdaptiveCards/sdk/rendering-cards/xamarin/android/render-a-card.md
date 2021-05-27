---
title: Render a card - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# Render a card - Xamarin.Android

Here's how to render a card using the Xamarin.Android SDK.

## Create Adaptive Card Object Instance from JSON Text

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
AdaptiveCard adaptiveCard = parseResult.AdaptiveCard;
```

or you can also use a ```ParseContext``` object to be able to deserialize custom elements that are included in your adaptive card like this:

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

or

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

## Render a card

To be able to render a card you'll need some information
* context: Obtainable from the Activity the card is hosted in
* fragmentManager: can also be retrieved from the hosting activity
* cardActionHandler: instance of [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) to manage the action behaviour

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;
// ...

var renderedCard = AdaptiveCardRenderer.Instance.Render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.View;
```
