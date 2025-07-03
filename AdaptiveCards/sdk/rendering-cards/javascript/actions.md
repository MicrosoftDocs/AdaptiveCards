---
title: Handling actions - JavaScript SDK
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: concept-article
---

# Handling actions - JavaScript

The JavaScript SDK introduces a base `Action` and a set of dedicated action classes (that all extend `Action`) that map to the various action types defined in the Adaptive Card schema:
| Schema type name | JavaScript class |
| --- | --- |
| [Action.OpenUrl](https://adaptivecards.io/explorer/Action.OpenUrl.html) | `OpenUrlAction` |
| [Action.ShowCard](https://adaptivecards.io/explorer/Action.ShowCard.html) | `ShowCardAction` |
| [Action.ToggleVisibility](https://adaptivecards.io/explorer/Action.ToggleVisibility.html) | `ToggleVisibilityAction` |
| [Action.Submit](https://adaptivecards.io/explorer/Action.Submit.html) | `SubmitAction` |

## Handling actions when users click action buttons
To handle action execution with the JavaScript SDK, an application should provide a handler for either the global `AdaptiveCard.onExecuteAction` event, or for the per-card `adaptiveCardInstance.onExecuteAction` event. The event handler will be invoked regardless of the type of action being executed, and it is the responsibility of the application to test which type of action is being executed and run the appropriate code. Typically, applications will only need to explicitly handle `SubmitAction`, as other action types are automatically handled by the SDK.

### Example

```typescript
// Create an AdaptiveCard instance
let adaptiveCard = new AdaptiveCard();

// Parse a card payload - this is just a very simple example
adaptiveCard.parse(
    {
        "type": "AdaptiveCard",
        "version": "1.0",
        "actions": [
            {
                "type": "Action.Submit",
                "id": "clickMe",
                "title": "Click me!"
            }
        ]
    }
)

// Provide an onExecuteAction handler to handle the Action.Submit
adaptiveCard.onExecuteAction = (action: Action) => {
    if (action instanceof SubmitAction) {
        // If you copy this code sample, remove the alert statement
        // and provide your own custom handling code
        alert("You clicked " + action.title);
    }
}

document.body.appendChild(adaptiveCard.render());
```

## Executing actions in code

The JavaScript SDK allows you to execute actions in code if necessary via the `Action.execute()` method.

### Example

```typescript
function triggerAction(card: AdaptiveCard, actionId: string) {
    let action = card.getActionById(actionId);

    if (action !== undefined) {
        // Executing an action in code will trigger the
        // onExecuteAction event
        action.execute();
    }
}
```
