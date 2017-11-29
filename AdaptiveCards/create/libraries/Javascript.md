---
title: JavaScript SDK for Adaptive Cards
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# JavaScript library for creating cards

> [!IMPORTANT]
> The library for serializing JSON is still in development and your milage may vary.

As we described in the getting started section, an adaptive card is nothing more then a serialized json object of a card object model.  To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.

You can use any tooling that you want to create the adaptive card json.

The `adaptivecards` npm package defines a library for working with adaptive cards in javascript

## To install
```console
npm install adaptivecards
```

## Example creating 
There are interface definitions in `schema.d.ts` which describe the shape of the schema

```typescript
let card = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "Container",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "Meow!"
                },
                {
                    "type": "Image",
                    "url": "http://adaptivecards.io/content/cats/1.png"
                }
            ]
        }
    ]
};
```

There is also an object model for creating cards.


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
