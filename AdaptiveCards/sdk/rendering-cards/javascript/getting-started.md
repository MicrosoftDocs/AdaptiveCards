---
title: JavaScript library
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
---

# Getting started - JavaScript

As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model. This is a JavaScript library for generating client-side HTML in the browser.

> [!IMPORTANT]
> **Breaking changes from v0.5**
> 
> 1. Package renamed from `microsoft-adaptivecards` to `adaptivecards`
> 1. The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`. E.g., `myCard.hostConfig = {}` 
> 1. `HostConfig` has gone though various renames and moves. See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/v1.0/HostConfig/sample.json) Host Config for current structure
> 1. There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. The static `renderCard()` function was removed as it was redundant with the class methods. Use `adaptiveCard.render()` as described below. 


## Install

### Node

```console
npm install adaptivecards --save
```

### CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## Usage

### Import the module

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## Next steps

See [Render a card](render-a-card.md) for the next steps!