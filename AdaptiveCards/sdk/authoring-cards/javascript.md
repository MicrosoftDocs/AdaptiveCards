---
title: JavaScript SDK for Adaptive Cards
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
---

# JavaScript SDK for creating cards

> [!IMPORTANT]
> The library for serializing JSON is still in development and your milage may vary.

As we described in the getting started section, an Adaptive Card is nothing more than a serialized JSON object of a card object model.  To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.

You can use any tooling that you want to create the adaptive card json.

The `adaptivecards` npm package defines a library for working with adaptive cards in javascript

## To install
```console
npm install adaptivecards
```

## Example

The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);
let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";
card.addItem(textBlock);
let json = card.toJSON();
```
