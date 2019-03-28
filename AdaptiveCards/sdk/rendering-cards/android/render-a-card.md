---
title: Render a card - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
---

# Render a card - Android

Here's how to render a card using the Android SDK.

## Create Adaptive Card Object Instance from JSON Text

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> **Breaking changes for v1.2**
> 
> 1. ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionRegistration object
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## Render a card

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
