---
title:  ImageSet Element
author: luywang
description: This page provides documentation for the `ImageSet` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# ImageSet Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


This page documents the **ImageSet** element, which displays a collection of Images similar to a gallery. Acceptable formats are PNG, JPEG, and GIF.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## ImageSet

The ImageSet displays a collection of Images similar to a gallery. Acceptable formats are PNG, JPEG, and GIF.

### ImageSet Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;ImageSet&quot;` | Yes | Must be `&quot;ImageSet&quot;`. | 1.0 |
| **images** | `Image[]` | Yes | The array of `Image` elements to show. | 1.0 |
| **imageSize** | `ImageSize` | No, default: `&quot;medium&quot;` | Controls the approximate size of each image. The physical dimensions will vary per host. Auto and stretch are not supported for ImageSet. The size will default to medium if those values are set. | 1.0 |
| **style** | `ImageSetStyle` | No | Controls how the images in the `ImageSet` are displayed. | 1.6 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.0 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic ImageSet Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "ImageSet",
			"images": [
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				}
			]
		}
	]
}
```

## Properties

### images

The array of `Image` elements to show.

  * **Type**: `Image[]`
  * **Required**: Yes
  * **Allowed values**:
      * `Image`

### imageSize

Controls the approximate size of each image. The physical dimensions will vary per host. Auto and stretch are not supported for ImageSet. The size will default to medium if those values are set.

  * **Type**: `ImageSize`
  * **Required**: No, default: `"medium"`
  * **Allowed values**:
      * `"auto"`: Image will scale down to fit if needed, but will not scale up to fill the area.
      * `"stretch"`: Image with both scale down and up to fit as needed.
      * `"small"`: Image is displayed with a fixed small width, where the width is determined by the host.
      * `"medium"`: Image is displayed with a fixed medium width, where the width is determined by the host.
      * `"large"`: Image is displayed with a fixed large width, where the width is determined by the host.

#### ImageSize Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "ImageSet",
			"imageSize": "small",
			"images": [
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/2.png",
					"altText": "Cat with red bandana"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/3.png",
					"altText": "Cat with shades"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/1.png",
					"altText": "Cat"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/2.png",
					"altText": "Cat with red bandana"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/cats/3.png",
					"altText": "Cat with shades"
				}
			]
		}
	]
}
```

### style

Controls how the images in the `ImageSet` are displayed.

  * **Type**: `ImageSetStyle`
  * **Version**: 1.6
  * **Required**: No
  * **Allowed values**:
      * `"default"`: This is the default style for `ImageSet`. Images are displayed in their original aspect ratio.
      * `"stacked"`: Display images in this `ImageSet` stack on top of each other (similar to a stack of photos).
      * `"grid"`: Display images in a grid. They are all shown at the same size. Images are clipped as needed to fit in the available space.

### fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`
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

