---
title: .NET SDK for Adaptive Cards
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
---

# .NET SDK for Authoring Cards

As we described in the [Getting Started](../GettingStarted.md) page, an Adaptive Card is a JSON object model. The .NET library makes working with that JSON much easier.

> [!IMPORTANT]
> **Breaking changes from v0.5**
> 
> 1. Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`
> 1. Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive". E.g., `TextBlock` is now `AdaptiveTextBlock`
> 1. All "uri" properties were changed from type `string` to `Uri`
> 1. There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)


## NuGet Install
The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## Example: Create an AdaptiveCard and serialize to JSON

This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.

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
    Url = "http://adaptivecards.io/content/cats/1.png"
});

// serialize the card to JSON
string json = card.ToJson();
```

## Example: Parse an AdaptiveCard from JSON

This example demonstrates how to parse a JSON payload into an Adaptive Card. This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../display/GettingStarted.md).

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var response = await client.GetAsync(cardUrl);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```
