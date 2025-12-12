---
title:  ActionSet Element
author: luywang
description: This page provides documentation for the `ActionSet` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# ActionSet Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **ActionSet** element, which displays a set of actions typically within the body of a card.

**Introduced in version 1.2**

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## ActionSet

Displays a set of actions.

**Introduced in version 1.2**

### ActionSet Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;ActionSet&quot;` | Yes | Must be `&quot;ActionSet&quot;`. | 1.2 |
| **actions** | `Action[]` | Yes | The array of `Action` elements to show. | 1.2 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.2 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.2 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.2 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### ActionSet Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"wrap": true,
			"text": "Cards can have action sets in the middle of their body."
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "ShowCard",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "TextBlock",
								"text": "This is a show card"
							}
						]
					}
				},
				{
					"type": "Action.OpenUrl",
					"title": "OpenUrl",
					"url": "https://adaptivecards.io"
				}
			]
		},
		{
			"type": "TextBlock",
			"wrap": true,
			"text": "There are also still \"actions\" at the bottom of the card"
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "ShowCard",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "TextBlock",
						"text": "This is a show card"
					}
				]
			}
		},
		{
			"type": "Action.OpenUrl",
			"title": "OpenUrl",
			"url": "https://adaptivecards.io"
		}
	]
}
```

## Properties

### actions

The array of `Action` elements to show.

  * **Type**: `Action[]`
  * **Required**: Yes
  * **Allowed values**:
      * `Action.Execute`
      * `Action.OpenUrl`
      * `Action.ShowCard`
      * `Action.Submit`
      * `Action.ToggleVisibility`

### fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
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

### height

Specifies the height of the element.

  * **Type**: `BlockElementHeight`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"auto"`: The height of the container will be determined by the height of its contents.
      * `"stretch"`: The container will stretch its height to the available remaining height of the parent container.

### separator

When `true`, draw a separating line at the top of the element.

  * **Type**: `boolean`
  * **Required**: No

### spacing

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

### id

A unique identifier associated with the item.

  * **Type**: `string`
  * **Required**: No

### isVisible

If `false`, this item will be removed from the visual tree.

  * **Type**: `boolean`
  * **Required**: No, default: `true`

### requires

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary<string>`
  * **Required**: No

