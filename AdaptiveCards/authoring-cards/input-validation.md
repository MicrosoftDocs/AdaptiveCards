---
title: Input Validation
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
---

# Input Validation

Versions 1.3 and later of the Adaptive Cards schema support client side input validation of Input types.

### Validation Properties

The following properties are supported for validation in AdaptiveCards:

| Input | Properties |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

An `errorMessage` property is available on all input types to specify what error a user should be shown if they enter an invalid value. 

> [!NOTE]
>
> Min and max properties (including maxLength) on some platforms may be enforced directly by the control. For example, a min property on Input.Date may be enforced by not allowing users to select a date before the minimum in a date picker. In that case, the error message may not be shown.

## Fields to be validated and submitted

Inputs will be validated when the user clicks on an Action.Submit action in the card. Those inputs which will be validated and submitted for a given Action.Submit action are:

 - Inputs on the same card as the Action.Submit
 - Inputs on any parent cards of the card containing the Action.Submit in the case of a card under an Action.ShowCard

If those inputs pass validation, the values in their fields will be passed back to the client. If they do not pass validation, the error messages for the invalid inputs will be shown, and the submit will not be sent.

> [!NOTE]
>
> Inputs will **not** be validated or submitted if they are on a card that is a child or sibling card of the card containing the Action.Submit. This includes cards from Action.ShowCards in ActionSets in the body of that card. This is a change in behavior from renderer versions prior to 2.0, and applies to cards of all schema versions, regardless of whether input validation properties are used. 

## Other Considerations and Known Issues

 - It is not recommended to create inputs with validation properties that may not always be visible due to interaction with Action.ToggleVisibility. Error messages and visual indications that the input is invalid will not be shown if the input is not currently visible, which may cause confusion for users as to why their submit is blocked.

 - Behavior of input validation for hosts using popup show cards using the 	`"actions":"showCard":"actionMode":"popup"` value in their host config is not well defined. Popup show cards may be deprecated in a future release.

