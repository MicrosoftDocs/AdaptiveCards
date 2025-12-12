---
title:  Input.Time Action
author: luywang
description: This page provides documentation for the `Input.Time` input in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Input.Time

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Input.Time

Lets a user select a time.

### Input.Time Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Input.Time&quot;` | Yes | Must be `"Input.Time"`. | 1.0 |
| **id** | `string` | Yes | Unique identifier for the value. Used to identify collected input when the Submit action is performed. | 1.0 |
| **max** | `string` | No | Hint of maximum value expressed in HH:MM (may be ignored by some clients). | 1.0 |
| **min** | `string` | No | Hint of minimum value expressed in HH:MM (may be ignored by some clients). | 1.0 |
| **placeholder** | `string` | No | Description of the input desired. Displayed when no time has been selected. | 1.0 |
| **value** | `string` | No | The initial value for this field expressed in HH:MM. | 1.0 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **errorMessage** | `string` | No | Error message to display when entered input is invalid | 1.3 |
| **isRequired** | `boolean` | No | Whether or not this input is required | 1.3 |
| **label** | `string` | No | Label for this input | 1.3 |
| **labelPosition** | `InputLabelPosition` | No | [SUPPORTED ONLY IN JAVASCRIPT SDK] Determines the position of the label. It can take ‘inline’ and ‘above’ values. By default, the label is placed ‘above’ when label position is not specified. | 1.6 |
| **labelWidth** | `string`, `number` | No | [SUPPORTED ONLY IN JAVASCRIPT SDK] Determines the width of the label in percent like 40 or a specific pixel width like ‘40px’ when label is placed inline with the input. labelWidth would be ignored when the label is displayed above the input. | 1.6 |
| **inputStyle** | `InputStyle` | No | [SUPPORTED ONLY IN JAVASCRIPT SDK] Style hint for input fields. Allows input fields to appear as read-only but when user clicks/focuses on the field, it allows them to update those fields. | 1.6 |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary<string>` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

## Example

### Example 1: Basic Time Input with Min, Max, and Value

| JSON | Adaptive Card |
| :--- | :--- |
| ` json {	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",	"type": "AdaptiveCard",	"version": "1.0",	"body": [		{			"type": "Input.Time",			"label": "What time do you want to meet?",			"id": "time",			"min": "09:00",			"max": "17:00",			"value": "15:30"		}	],	"actions": [		{			"type": "Action.Submit",			"title": "OK"		}	] }  ` | [Adaptive Card Try it Yourself \>] |

## Properties

### max (Version 1.0)

Hint of maximum value expressed in HH:MM (may be ignored by some clients).

  * **Type**: `string`
  * **Required**: No

### min (Version 1.0)

Hint of minimum value expressed in HH:MM (may be ignored by some clients).

  * **Type**: `string`
  * **Required**: No

### placeholder (Version 1.0)

Description of the input desired. Displayed when no time has been selected.

  * **Type**: `string`
  * **Required**: No

### value (Version 1.0)

The initial value for this field expressed in HH:MM.

  * **Type**: `string`
  * **Required**: No

### id (Version 1.0)

Unique identifier for the value. Used to identify collected input when the Submit action is performed.

  * **Type**: `string`
  * **Required**: Yes

### errorMessage (Version 1.3)

Error message to display when entered input is invalid

  * **Type**: `string`
  * **Version** : 1.3
  * **Required**: No

### isRequired (Version 1.3)

Whether or not this input is required

  * **Type**: `boolean`
  * **Version** : 1.3
  * **Required**: No

### label (Version 1.3)

Label for this input

  * **Type**: `string`
  * **Version** : 1.3
  * **Required**: No

### labelPosition (Version 1.6)

[SUPPORTED ONLY IN JAVASCRIPT SDK] Determines the position of the label. It can take ‘inline’ and ‘above’ values. By default, the label is placed ‘above’ when label position is not specified.

  * **Type**: `InputLabelPosition`
  * **Version** : 1.6
  * **Required**: No
  * **Allowed values**:
      * `"inline"`
      * `"above"`

### labelWidth (Version 1.6)

[SUPPORTED ONLY IN JAVASCRIPT SDK] Determines the width of the label in percent like 40 or a specific pixel width like '40px' when label is placed inline with the input. `labelWidth` would be ignored when the label is displayed above the input.

  * **Type**: `string`, `number`
  * **Version** : 1.6
  * **Required**: No

### inputStyle (Version 1.6)

[SUPPORTED ONLY IN JAVASCRIPT SDK] Style hint for input fields. Allows input fields to appear as read-only but when user clicks/focuses on the field, it allows them to update those fields.

  * **Type**: `InputStyle`
  * **Version** : 1.6
  * **Required**: No
  * **Allowed values**:
      * `"revealOnHover"`
      * `"default"`

### fallback (Version 1.2)

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
  * **Version** : 1.2
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`
      * `ColumnSet`
      * `Container`
      * `FactSet`
      * `Image`
      * `ImageSet`
      * `Input.ChoiceSet`
      * `Input.Date`
      * `Input.Number`
      * `Input.Text`
      * `Input.Time`
      * `Input.Toggle`
      * `Media`
      * `RichTextBlock`
      * `Table`
      * `TextBlock`
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

### height (Version 1.1)

Specifies the height of the element.

  * **Type**: `BlockElementHeight`
  * **Version** : 1.1
  * **Required**: No
  * **Allowed values**:
      * `"auto"`: The height of the container will be determined by the height of its contents.
      * `"stretch"`: The container will stretch its height to the available remaining height of the parent container.

### separator (Version 1.0)

When `true`, draw a separating line at the top of the element.

  * **Type**: `boolean`
  * **Required**: No

### spacing (Version 1.0)

Controls the amount of spacing between this element and the preceding element.

  * **Type**: `Spacing`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"none"`
      * `"small"`
      * `"medium"`
      * `"large"`
      * `"extraLarge"`
      * `"padding"`

### isVisible (Version 1.2)

If `false`, this item will be removed from the visual tree.

  * **Type**: `boolean`
  * **Version** : 1.2
  * **Required**: No, default: `true`

### requires (Version 1.2)

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary<string>`
  * **Version** : 1.2
  * **Required**: No

