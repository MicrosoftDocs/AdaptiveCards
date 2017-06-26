---
title: JavaScript SDK for Adaptive Cards
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Javascript Libraries for creating cards
As we described in the getting started section, an adaptive card is nothing more then a serialized json object of a card object model.  To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.

You can use any tooling that you want to create the adaptive card json.

The `microsoft-adaptivecards` npm package defines a library  for working with adaptive cards in javascript

## To install
```console
npm install microsoft-adaptivecards
```

## Example creating 
There are interface definitions in schema.d.ts which describe the shape of the schema

```typescript
let card = {
    "type": "AdaptiveCard",
    "version": "0.5",
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
                    "url": "http://adaptivecards.io/api/cat"
                }
            ]
        }
    ]
};
```
