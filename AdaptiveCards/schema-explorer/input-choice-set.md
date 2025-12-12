---
title:  Input.ChoiceSet Action
author: luywang
description: This page provides documentation for the `Input.ChoiceSet` input in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Input.ChoiceSet

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Input.ChoiceSet

Allows a user to input a Choice.

### Input.ChoiceSet Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Input.ChoiceSet&quot;` | Yes | Must be `"Input.ChoiceSet"`. | 1.0 |
| **id** | `string` | Yes | Unique identifier for the value. Used to identify collected input when the Submit action is performed. | 1.0 |
| **choices** | `Input.Choice[]` | No | `Choice` options. | 1.0 |
| **choices.data** | `Data.Query` | No | Allows dynamic fetching of choices from the bot to be displayed as suggestions in the dropdown when the user types in the input field. | 1.6 |
| **isMultiSelect** | `boolean` | No | Allow multiple choices to be selected. | 1.0 |
| **style** | `ChoiceInputStyle` | No | | 1.0 |
| **value** | `string` | No | The initial choice (or set of choices) that should be selected. For multi-select, specify a comma-separated string of values. | 1.0 |
| **placeholder** | `string` | No | Description of the input desired. Only visible when no selection has been made, the `style` is `compact` and `isMultiSelect` is `false` | 1.0 |
| **wrap** | `boolean` | No | If `true`, allow text to wrap. Otherwise, text is clipped. | 1.2 |

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

### Example 1: Demonstrating ChoiceSet Styles and Multi-select

| JSON | Adaptive Card |
| :--- | :--- |
| ` json {	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",	"type": "AdaptiveCard",	"version": "1.3",	"body": [		{			"type": "Input.ChoiceSet",			"id": "myColor",			"style": "compact",			"label": "What color do you want? (isMultiSelect:false, style:compact)",			"isMultiSelect": false,			"value": "1",			"choices": [				{					"title": "Red",					"value": "1"				},				{					"title": "Green",					"value": "2"				},				{					"title": "Blue",					"value": "3"				}			]		},		{			"type": "Input.ChoiceSet",			"id": "myColor2",			"style": "expanded",			"label": "What color do you want? (isMultiSelect:false, style:expanded)",			"isMultiSelect": false,			"value": "1",			"choices": [				{					"title": "Red",					"value": "1"				},				{					"title": "Green",					"value": "2"				},				{					"title": "Blue",					"value": "3"				}			]		},		{			"type": "Input.ChoiceSet",			"id": "myColor3",			"isMultiSelect": true,			"value": "1,3",			"style": "compact",			"label": "What colors do you want? (isMultiSelect:true, style:compact)",			"choices": [				{					"title": "Red",					"value": "1"				},				{					"title": "Green",					"value": "2"				},				{					"title": "Blue",					"value": "3"				}			]		},		{			"type": "Input.ChoiceSet",			"id": "myColor4",			"isMultiSelect": true,			"value": "1",			"style": "expanded",			"label": "What colors do you want? (isMultiSelect:true, style:expanded)",			"choices": [				{					"title": "Red",					"value": "1"				},				{					"title": "Green",					"value": "2"				},				{					"title": "Blue",					"value": "3"				}			]		}	],	"actions": [		{			"type": "Action.Submit",			"title": "OK"		}	] }  ` |  |

## Properties

### choices (Version 1.0)

`Choice` options.

  * **Type**: `Input.Choice[]`
  * **Required**: No
  * **Allowed values**:
      * `Input.Choice`

### choices.data (Version 1.6)

Allows dynamic fetching of choices from the bot to be displayed as suggestions in the dropdown when the user types in the input field.

  * **Type**: `Data.Query`
  * **Version** : 1.6
  * **Required**: No
  * **Allowed values**:
      * `Data.Query`

### isMultiSelect (Version 1.0)

Allow multiple choices to be selected.

  * **Type**: `boolean`
  * **Required**: No

### style (Version 1.0)

  * **Type**: `ChoiceInputStyle`
  * **Required**: No
  * **Allowed values**:
      * `"compact"`
      * `"expanded"`
      * `"filtered"`: Added in version 1.5. Allows users to filter choices in a choice set.

### value (Version 1.0)

The initial choice (or set of choices) that should be selected. For multi-select, specify a comma-separated string of values.

  * **Type**: `string`
  * **Required**: No

### placeholder (Version 1.0)

Description of the input desired. Only visible when no selection has been made, the `style` is `compact` and `isMultiSelect` is `false`

  * **Type**: `string`
  * **Required**: No

| JSON | Adaptive Card |
| :--- | :--- |
| ` json {    "type": "AdaptiveCard",    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",    "version": "1.3",    "body": [        {			"type": "Input.ChoiceSet",			"id": "CompactSelectVal",			"label": "What color do you want? (compact)",			"style": "compact",			"isRequired": true,			"errorMessage": "This is a required input",			"placeholder": "Please choose",			"choices": [				{					"title": "Red",					"value": "1"				},				{					"title": "Green",					"value": "2"				},				{					"title": "Blue",					"value": "3"				}			]		}    ],	"actions": [		{			"type": "Action.Submit",			"title": "OK"		}	] }  ` |  |

### wrap (Version 1.2)

If `true`, allow text to wrap. Otherwise, text is clipped.

  * **Type**: `boolean`
  * **Version** : 1.2
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

[SUPPORTED ONLY IN JAVASCRIPT SDK] Determines the position of the label. It can take 'inline' and 'above' values. By default, the label is placed 'above' when label position is not specified.

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
