---
title:  Action.ToggleVisibility Action
author: luywang
description: This page provides documentation for the `Action.ToggleVisibility` action in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Action.ToggleVisibility

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Action.ToggleVisibility** element, which is an action that toggles the visibility of associated card elements.

**Introduced in version 1.2**

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Action.ToggleVisibility

An action that toggles the visibility of associated card elements.

### Action.ToggleVisibility Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Action.ToggleVisibility&quot;` | Yes | Must be `&quot;Action.ToggleVisibility&quot;`. | 1.2 |
| **targetElements** | `TargetElement[]` | Yes | The array of TargetElements. It is not recommended to include Input elements with validation under Action.Toggle due to confusion that can arise from invalid inputs that are not currently visible. See [/adaptive-cards/authoring-cards/input-validation](/adaptive-cards/authoring-cards/input-validation) for more information. | 1.2 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **title** | `string` | No | Label for button or link that represents this action. | 1.2 |
| **iconUrl** | `uri` | No | Optional icon to be shown on the action in conjunction with the title. Supports data URI in version 1.2+. | 1.1 |
| **id** | `string` | No | A unique identifier associated with this Action. | 1.2 |
| **style** | `ActionStyle` | No | Controls the style of an Action, which influences how the action is displayed, spoken, etc.. | 1.2 |
| **fallback** | `Action`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **tooltip** | `string` | No | Defines text that should be displayed to the end user as they hover the mouse over the action, and read when using narration software. | 1.5 |
| **isEnabled** | `boolean` | No, default: `true` | Determines whether the action should be enabled. | 1.5 |
| **mode** | `ActionMode` | No, default: `&quot;primary&quot;` | Determines whether the action should be displayed as a button or in the overflow menu. | 1.5 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Action.ToggleVisibility Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"version": "1.2",
	"body": [
		{
			"type": "TextBlock",
			"text": "Press the buttons to toggle the images!",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Here are some images:",
			"isVisible": false,
			"id": "textToToggle"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"style": "person",
							"type": "Image",
							"url": "https://picsum.photos/100/100?image=112",
							"isVisible": false,
							"id": "imageToToggle",
							"altText": "sample image 1",
							"size": "medium"
						}
					]
				},
				{
					"type": "Column",
					"items": [

						{
							"type": "Image",
							"url": "https://picsum.photos/100/100?image=123",
							"isVisible": false,
							"id": "imageToToggle2",
							"altText": "sample image 2",
							"size": "medium"
						}
					]
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ToggleVisibility",
			"title": "Toggle!",
			"targetElements": [ "textToToggle", "imageToToggle", "imageToToggle2" ]
		},
		{
			"type": "Action.ToggleVisibility",
			"title": "Show!",
			"targetElements": [
				{
					"elementId": "textToToggle",
					"isVisible": true
				},
				{
					"elementId": "imageToToggle",
					"isVisible": true
				},
				{
					"elementId": "imageToToggle2",
					"isVisible": true
				}
			]
		},
		{
			"type": "Action.ToggleVisibility",
			"title": "Hide!",
			"targetElements": [
				{
					"elementId": "textToToggle",
					"isVisible": false
				},
				{
					"elementId": "imageToToggle",
					"isVisible": false
				},
				{
					"elementId": "imageToToggle2",
					"isVisible": false
				}
			]
		}
	]
}
```

## Properties

### targetElements

The array of TargetElements. It is not recommended to include Input elements with validation under Action.Toggle due to confusion that can arise from invalid inputs that are not currently visible. See [/adaptive-cards/authoring-cards/input-validation](/adaptive-cards/authoring-cards/input-validation) for more information.

  * **Type**: `TargetElement[]`
  * **Required**: Yes
  * **Allowed values**:
      * `TargetElement`
      * `string`

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

Controls the style of an Action, which influences how the action is displayed, spoken, etc..

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

### isEnabled

Determines whether the action should be enabled.

  * **Type**: `boolean`
  * **Version**: 1.5
  * **Required**: No, default: `true`

### mode

Determines whether the action should be displayed as a button or in the overflow menu.

  * **Type**: `ActionMode`
  * **Version**: 1.5
  * **Required**: No, default: `"primary"`
  * **Allowed values**:
      * `"primary"`: Action is displayed as a button.
      * `"secondary"`: Action is placed in an overflow menu (typically a popup menu under a `...` button).

### requires

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary&lt;string&gt;`
  * **Version**: 1.2
  * **Required**: No

