---
title:  TextBlock Element
author: luywang
description: This page documents the Image element, a card element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Image Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Image** element, a card element in the Adaptive Cards schema.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](https://docs.microsoft.com/en-us/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](https://docs.microsoft.com/en-us/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Image

Displays an image. Acceptable formats are PNG, JPEG, and GIF.

### Image Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Image&quot;` | Yes | Must be `&quot;Image&quot;`. | 1.0 |
| **url** | `uri` | Yes | The URL to the image. Supports data URI in version 1.2+. | 1.0 |
| **altText** | `string` | No | Alternate text describing the image. | 1.0 |
| **backgroundColor** | `string` | No | Applies a background to a transparent image. This property will respect the image style. | 1.1 |
| **height** | `string`, `BlockElementHeight` | No, default: `&quot;auto&quot;` | The desired height of the image. If specified as a pixel value, ending in ‘px’, E.g., 50px, the image will distort to fit that exact height. This overrides the `size` property. | 1.1 |
| **horizontalAlignment** | `HorizontalAlignment?` | No | Controls how this element is horizontally positioned within its parent. When not specified, the value of horizontalAlignment is inherited from the parent container. If no parent container has horizontalAlignment set, it defaults to Left. | 1.0 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the `Image` is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **size** | `ImageSize` | No | Controls the approximate size of the image. The physical dimensions will vary per host. | 1.0 |
| **style** | `ImageStyle` | No | Controls how this `Image` is displayed. | 1.0 |
| **width** | `string` | No | The desired on-screen width of the image, ending in ‘px’. E.g., 50px. This overrides the `size` property. | 1.1 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.0 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic Image Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat"
		}
	]
}
```

## Properties

### url

The URL to the image. Supports data URI in version 1.2+.

  * **Type**: `uri`
  * **Required**: Yes

### altText

Alternate text describing the image.

  * **Type**: `string`
  * **Required**: No

### backgroundColor

Applies a background to a transparent image. This property will respect the image style.

  * **Type**: `string`
  * **Version**: 1.1
  * **Required**: No

#### BackgroundColor Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [{
		"type": "ColumnSet",
		"columns": [{
				"type": "Column",
				"width": "stretch",
				"items": [{
					"type": "Image",
					"style": "person",
					"backgroundColor": "#982374",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				}]
			},
			{
				"type": "Column",
				"width": "stretch",
				"items": [{
					"type": "Image",
					"backgroundColor": "#128192",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				}]
			},
			{
				"type": "Column",
				"width": "stretch",
				"items": [{
					"type": "Image",
					"backgroundColor": "#183774",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				}]
			}
		]
	}]
}
```

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/2.png",
			"altText": "Cat",
			"size": "small",
			"backgroundColor": "#FF0000FF"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat",
			"style": "person",
			"backgroundColor": "#FFFF0000"
		}
	]
}
```

### height

The desired height of the image. If specified as a pixel value, ending in 'px', E.g., 50px, the image will distort to fit that exact height. This overrides the `size` property.

  * **Type**: `string`, `BlockElementHeight`
  * **Version**: 1.1
  * **Required**: No, default: `"auto"`
  * **Allowed values**:
      * `string`
      * `"auto"`: The height of the container will be determined by the height of its contents.
      * `"stretch"`: The container will stretch its height to the available remaining height of the parent container.

#### Height Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
	  {
		"type": "Image",
		"url": "https://adaptivecards.io/content/cats/1.png",
		"altText": "Cat",
		"height": "50px"
	  }
	]
  }
```

### horizontalAlignment

Controls how this element is horizontally positioned within its parent. When not specified, the value of horizontalAlignment is inherited from the parent container. If no parent container has horizontalAlignment set, it defaults to Left.

  * **Type**: `HorizontalAlignment?`
  * **Required**: No
  * **Allowed values**:
      * `"left"`
      * `"center"`
      * `"right"`

#### HorizontalAlignment Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "horizontalAlignment:left",
			"weight": "bolder"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat",
			"size": "medium",
			"horizontalAlignment": "left"
		},
		{
			"type": "TextBlock",
			"text": "horizontalAlignment:center",
			"weight": "bolder",
			"horizontalAlignment": "center"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat",
			"size": "medium",
			"horizontalAlignment": "center"
		},
		{
			"type": "TextBlock",
			"text": "horizontalAlignment:right",
			"weight": "bolder",
			"horizontalAlignment": "right"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat",
			"size": "medium",
			"horizontalAlignment": "right"
		}
	]
}
```

### selectAction

An Action that will be invoked when the `Image` is tapped or selected. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`
      * `Action.OpenUrl`
      * `Action.Submit`
      * `Action.ToggleVisibility`

#### SelectAction Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Click the cat!",
			"weight": "bolder"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Cat",
			"selectAction": {
				"type": "Action.OpenUrl",
				"tooltip": "cool link",
				"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
			}
		}
	]
}
```

### size

Controls the approximate size of the image. The physical dimensions will vary per host.

  * **Type**: `ImageSize`
  * **Required**: No
  * **Allowed values**:
      * `"auto"`: Image will scale down to fit if needed, but will not scale up to fill the area.
      * `"stretch"`: Image with both scale down and up to fit as needed.
      * `"small"`: Image is displayed with a fixed small width, where the width is determined by the host.
      * `"medium"`: Image is displayed with a fixed medium width, where the width is determined by the host.
      * `"large"`: Image is displayed with a fixed large width, where the width is determined by the host.

#### Size Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "size:small",
			"weight": "bolder",
			"size": "large"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Small cat",
			"size": "small"
		},
		{
			"type": "TextBlock",
			"text": "size:medium",
			"weight": "bolder",
			"size": "large"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Medium cat",
			"size": "medium"
		},
		{
			"type": "TextBlock",
			"text": "size:large",
			"weight": "bolder",
			"size": "large"
		},
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/cats/1.png",
			"altText": "Large cat",
			"size": "large"
		}
	]
}
```

### style

Controls how this `Image` is displayed.

  * **Type**: `ImageStyle`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"person"`

#### Style Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "style: default",
							"weight": "bolder"
						},
						{
							"type": "Image",
							"url": "https://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg",
							"altText": "Person",
							"style": "default"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "style: person",
							"weight": "bolder"
						},
						{
							"type": "Image",
							"url": "https://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg",
							"altText": "Person",
							"style": "person"
						}
					]
				}
			]
		}
	]
}
```

### width

The desired on-screen width of the image, ending in 'px'. E.g., 50px. This overrides the `size` property.

  * **Type**: `string`
  * **Version**: 1.1
  * **Required**: No

#### Width Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
	  {
		"type": "Image",
		"url": "https://adaptivecards.io/content/cats/1.png",
		"altText": "Cat",
		"width": "50px"
	  }
	]
  }
```

### fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

### separator

When `true`, draw a separating line at the top of the element.

  * **Type**: `boolean`
  * **Required**: No

### spacing

Controls the amount of spacing between this element and the preceding element.

  * **Type**: `Spacing`
  * **Required**: No
  * **Allowed values**:
      * `"default"`, `"none"`, `"small"`, `"medium"`, `"large"`, `"extraLarge"`, `"padding"`

### id

A unique identifier associated with the item.

  * **Type**: `string`
  * **Required**: No

### isVisible

If `false`, this item will be removed from the visual tree.

  * **Type**: `boolean`
  * **Version**: 1.2
  * **Required**: No, default: `true`

### requires

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary<string>`
  * **Version**: 1.2

  * **Required**: No
