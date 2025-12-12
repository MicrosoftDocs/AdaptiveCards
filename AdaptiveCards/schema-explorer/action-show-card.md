---
title:  Action.ShowCard Action
author: luywang
description: This page provides documentation for the `Action.ShowCard` action in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Action.ShowCard

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Action.ShowCard** element, which defines an Adaptive Card that is displayed to the user when the action button or link is clicked.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Action.ShowCard

Defines an AdaptiveCard which is shown to the user when the button or link is clicked.

### Action.ShowCard Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Action.ShowCard&quot;` | Yes | Must be `&quot;Action.ShowCard&quot;`. | 1.0 |
| **card** | `AdaptiveCard` | No | The Adaptive Card to show. Inputs in ShowCards will not be submitted if the submit button is located on a parent card. See [/adaptive-cards/authoring-cards/input-validation](/adaptive-cards/authoring-cards/input-validation) for more details. | 1.0 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **title** | `string` | No | Label for button or link that represents this action. | 1.0 |
| **iconUrl** | `uri` | No | Optional icon to be shown on the action in conjunction with the title. Supports data URI in version 1.2+. | 1.1 |
| **id** | `string` | No | A unique identifier associated with this Action. | 1.0 |
| **style** | `ActionStyle` | No | Controls the style of an Action, which influences how the action is displayed, spoken, etc. | 1.2 |
| **fallback** | `Action`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **tooltip** | `string` | No | Defines text that should be displayed to the end user as they hover the mouse over the action, and read when using narration software. | 1.5 |
| **isEnabled** | `boolean` | No, default: `true` | Determines whether the action should be enabled. | 1.5 |
| **mode** | `ActionMode` | No, default: `&quot;primary&quot;` | Determines whether the action should be displayed as a button or in the overflow menu. | 1.5 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic Action.ShowCard Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "This card's action will show another card"
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Action.ShowCard",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "TextBlock",
						"text": "What do you think?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "Neat!",
						"data": {
							"neat": "true"
						}
					}
				]
			}
		}
	]
}
```

## Properties

### card

The Adaptive Card to show. Inputs in ShowCards will not be submitted if the submit button is located on a parent card. See [/adaptive-cards/authoring-cards/input-validation](/adaptive-cards/authoring-cards/input-validation) for more details.

  * **Type**: `AdaptiveCard`
  * **Required**: No
  * **Allowed values**:
      * `AdaptiveCard`

### title

Label for button or link that represents this action.

  * **Type**: `string`
  * **Required**: No

### iconUrl

Optional icon to be shown on the action in conjunction with the title. Supports data URI in version 1.2+.

  * **Type**: `uri`
  * **Version**: 1.1
  * **Required**: No

### id

A unique identifier associated with this Action.

  * **Type**: `string`
  * **Required**: No

### style

Controls the style of an Action, which influences how the action is displayed, spoken, etc.

  * **Type**: `ActionStyle`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `"default"`: Action is displayed as normal.
      * `"positive"`: Action is displayed with a positive style (typically the button becomes accent color).
      * `"destructive"`: Action is displayed with a destructive style (typically the button becomes red).

### fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Action`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`, `Action.OpenUrl`, `Action.ShowCard`, `Action.Submit`, `Action.ToggleVisibility`.
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

### tooltip

Defines text that should be displayed to the end user as they hover the mouse over the action, and read when using narration software.

  * **Type**: `string`
  * **Version**: 1.5
  * **Required**: No

#### Tooltip Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"label": "Please enter your name below:",
			"type": "Input.Text",
			"id": "name"
		}
	],
	"actions": [
		{
			"type": "Action.Execute",
			"title": "Submit",
			"tooltip": "Click here to add your name to the waiting list."
		}
	]
}
```

### isEnabled

Determines whether the action should be enabled.

  * **Type**: `boolean`
  * **Version**: 1.5
  * **Required**: No, default: `true`

#### isEnabled Example (JSON)

```json
{
  "type": "AdaptiveCard",
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.5",
  "body": [
    {
      "type": "TextBlock",
      "text": "Disabled Execute Button",
      "wrap": true
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Enabled"
    },
    {
      "type": "Action.Execute",
      "title": "Disabled",
      "isEnabled": false
    }
  ]
}
```

### mode

Determines whether the action should be displayed as a button or in the overflow menu.

  * **Type**: `ActionMode`
  * **Version**: 1.5
  * **Required**: No, default: `"primary"`
  * **Allowed values**:
      * `"primary"`: Action is displayed as a button.
      * `"secondary"`: Action is placed in an overflow menu (typically a popup menu under a `...` button).

#### Mode Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Please confirm your data:",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "First Name",
					"value": "John"
				},
				{
					"title": "Last Name",
					"value": "Smith"
				},
				{
					"title": "Phone number ",
					"value": "(555) 555-5555"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.Execute",
			"title": "Confirm data"
		},
		{
			"type": "Action.Execute",
			"title": "Edit data",
			"data": "edit",
			"mode": "secondary"
		},
		{
			"type": "Action.Execute",
			"title": "Delete data",
			"data": "delete",
			"mode": "secondary"
		}
	]
}
```

### requires

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary&lt;string&gt;`
  * **Version**: 1.2
  * **Required**: No

