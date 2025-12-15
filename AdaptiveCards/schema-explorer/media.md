---
title:  Media Element
author: luywang
description: This page documents the Media element, which displays a media player for audio or video content.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Media Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Media** element, which displays a media player for audio or video content.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Media

Displays a media player for audio or video content.

**Introduced in version 1.1**

### Media Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Media&quot;` | Yes | Must be `&quot;Media&quot;`. | 1.1 |
| **sources** | `MediaSource[]` | Yes | Array of media sources to attempt to play. | 1.1 |
| **poster** | `uri` | No | URL of an image to display before playing. Supports data URI in version 1.2+. If poster is omitted, the Media element will either use a default poster (controlled by the host application) or will attempt to automatically pull the poster from the target video service when the source URL points to a video from a Web provider such as YouTube. | 1.1 |
| **altText** | `string` | No | Alternate text describing the audio or video. | 1.1 |
| **captionSources** | `CaptionSource[]` | No | Array of captions sources for the media element to provide. | 1.6 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.1 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.1 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.1 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Media with Captions Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.6",
	"fallbackText": "This card requires CaptionSource to be viewed. Ask your platform to update to Adaptive Cards v1.6 for this and more!",
	"body": [
		{
			"type": "Media",
			"poster": "https://adaptivecards.io/content/poster-video.png",
			"sources": [
				{
					"mimeType": "video/mp4",
					"url": "https://cdn.adaptivecards.io/assets/AdaptiveCardsOverviewVideo.mp4"
				}
			],
			"captionSources": [
				{
					"mimeType": "vtt",
					"label": "English (vtt)",
					"url": "https://raw.githubusercontent.com/microsoft/AdaptiveCards/5ac07e8adb8d7dcd7480973321e57d279d1f7d2c/assets/ProductVideoSubtitles.vtt"
				},
				{
					"mimeType": "srt",
					"label": "English (srt)",
					"url": "https://raw.githubusercontent.com/microsoft/AdaptiveCards/da2eb4ad4de60d14b37decc062d3952da9dbb790/assets/ProductVideoSubtitles.srt"
				}
			]
		}
	]
}
```

## Properties

### sources

Array of media sources to attempt to play.

  * **Type**: `MediaSource[]`
  * **Required**: Yes
  * **Allowed values**:
      * `MediaSource`

#### Sources Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.6",
	"body": [
		{
			"type": "TextBlock",
			"text": "Media supports **audio** and **video** content!",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Video",
			"horizontalAlignment": "center",
			"spacing": "medium",
			"separator": true,
			"size": "large"
		},
		{
			"type": "Media",
			"poster": "https://adaptivecards.io/content/poster-video.png",
			"altText": "Adaptive Cards overview video",
			"sources": [
				{
					"mimeType": "video/mp4",
					"url": "https://cdn.adaptivecards.io/assets/AdaptiveCardsOverviewVideo.mp4"
				}
			],
			"captionSources": [
				{
					"mimeType": "vtt",
					"label": "English (vtt)",
					"url": "https://raw.githubusercontent.com/microsoft/AdaptiveCards/5ac07e8adb8d7dcd7480973321e57d279d1f7d2c/assets/ProductVideoSubtitles.vtt"
				},
				{
					"mimeType": "srt",
					"label": "English (srt)",
					"url": "https://raw.githubusercontent.com/microsoft/AdaptiveCards/da2eb4ad4de60d14b37decc062d3952da9dbb790/assets/ProductVideoSubtitles.srt"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Audio",
			"horizontalAlignment": "center",
			"separator": true,
			"size": "large"
		},
		{
			"type": "Media",
			"poster": "https://adaptivecards.io/content/poster-audio.jpg",
			"altText": "Adaptive Cards overview audio",
			"sources": [
				{
					"mimeType": "audio/mpeg",
					"url": "https://cdn.adaptivecards.io/assets/AdaptiveCardsOverviewVideo.mp3"
				}
			]
		}
	]
}
```

### poster

URL of an image to display before playing. It supports data URI in version 1.2+. If `poster` is omitted, the Media element may use a default poster (controlled by the host application) or may automatically pull the poster from the target video service if the source URL points to a video from a Web provider like YouTube.

  * **Type**: `uri`
  * **Required**: No

### altText

Alternate text describing the audio or video.

  * **Type**: `string`
  * **Required**: No

### captionSources

Array of captions sources for the media element to provide.

  * **Type**: `CaptionSource[]`
  * **Version**: 1.6
  * **Required**: No
  * **Allowed values**:
      * `CaptionSource`

### fallback

Describes what to do when an unknown element is encountered or the requirements of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

### height

Specifies the height of the element.

  * **Type**: `BlockElementHeight`
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
