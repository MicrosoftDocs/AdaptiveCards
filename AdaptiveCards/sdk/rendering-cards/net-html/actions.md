---
title: .NET HTML SDK
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
---

# Actions - .NET HTML

Top-level card `actions` will render as an HTML `<button>`. Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed. Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.

Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable. If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.

Action Type | CSS class | Additional attributes
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (the `url` property from the card)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (the `data` property from the card)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (the `id` of the `<div>` containing the inner card)