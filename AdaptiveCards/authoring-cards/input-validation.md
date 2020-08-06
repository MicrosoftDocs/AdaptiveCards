---
title: Input Validation
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
---

# Input Validation

In versions 1.3 and later of the schema, AdaptiveCards supports client side input validation of Input types.

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

## Labels

Another property added in schema version 1.3 for all input elements is the `label` string property. Using the `label` property is the recommended way of tagging inputs in an Adaptive Card, vis-a-vis the `placeholder` property. It is a simple and concise way of labeling inputs for card authors and has the following benefits:
* Validation indicators: as mentioned above inputs can be now marked as required, labels for required inputs will have a visual indicator next to them. This visual indicator is defined in the `HostConfig` and by default is rendered as an asterisk `*`.
* Accessibility: by having a connection between labels and inputs, renderer libraries can set the necessary properties to allow users using assistive technologies (screen readers) to be able to interact correctly with inputs inside adaptive cards.
    * Labels vs Placeholders: as Katie Sherwin explains in the article [Placeholders in form fields are harmful](https://www.nngroup.com/articles/form-design-placeholders/) using placeholders has many negative consequences such as straining users' short term memory, making it harder for users to verify their inputs before submitting, providing difficulties for users to read them as, usually, placeholder text has poor color contrast against it's background or screen readers not reading the placeholder text at all, just to name a few.
    * TextBlock and RichTextBlock: while using other card elements as labels may seem as a good solution it presents the issue of not being able to enforce proximity between inputs and labels, on the other hand by using the `label` property, we can ensure that both visual elements are rendered next to each other which helps users who need screen magnifiers.

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

