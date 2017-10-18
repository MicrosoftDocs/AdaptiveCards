---
title: .NET SDK for Adaptive Cards
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
---

# .NET SDK for card creation

As we described in [Getting Started](../GettingStarted,md) page, an adaptive card is a JSON-serialized card object model. To make it easy to manipulate the object model, you can use our .NET SDK to serialize to and from JSON.

> [!IMPORTANT]
> **Breaking changes from v0.5**
> 
> 1. Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`
> 1. Due to frequent name collisions with framework namespaces, all model types have been prefixed with "Adaptive". E.g., `TextBlock` is now `AdaptiveTextBlock`
> 1. There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)


## NuGet Install
The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards 
```


## Example: Create a Card

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = "http://someUrl.com/example.png"
});
```

## Example: Parse from JSON

```csharp
AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

if (result.Card != null)
{
    // Get card from result
    AdaptiveCard card = result.Card;
}
else
{
    // Failed parsing
}
```

### Example: Serialize the card to JSON

```csharp
string json = card.ToJson();
```
