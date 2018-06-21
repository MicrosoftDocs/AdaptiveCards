---
title: Extensibility - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
---

# Extensibility - JavaScript

## Custom Element Rendering

For full control of the renderer, you can access the global registry to modify behavior of element rendering, or even introduce your own.

* For Actions use `AdaptiveCards.AdaptiveCard.actionTypeRegistry` 
* For Elements use `AdaptiveCards.AdaptiveCard.elementTypeRegistry`

For example, to override the rendering of a `Input.Date` element:

```javascript
AdaptiveCards.AdaptiveCard.elementTypeRegistry.registerType("Input.Date", () => { return new DateInput(); }); 
```
To override an `Action`:

```javascript
AdaptiveCards.AdaptiveCard.actionTypeRegistry.registerType("Action.OpenUrl", () => { return new OpenUrlAction(); });  
```



