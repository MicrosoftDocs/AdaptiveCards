---
title: Actions
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: concept-article
---

# Actions

By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect. Each SDK has the equivalent of an `OnAction` event that you must handle.

* **Action.OpenUrl** - open the specified `url`.  
* **Action.Submit** - take the result of the submit and send it to the source. How you send it to the source of the card is entirely up to you.
* **Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog. Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.
* **Action.ToggleVisibility** - shows or hides one or more elements in the card.
* **Action.Execute** - gathers input fields, merges with optional data field, and sends an event to the client. Learn more about Action.Execute in our [Universal Action Model](../authoring-cards/universal-action-model.md) section.