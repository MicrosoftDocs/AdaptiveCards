---
title:  Sample of Image Gallery
author: luywang
description: This page provides a sample code for Image Gallery Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Image Gallery

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Image gallery sample

The following section displays the JSON for an "Image gallery" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "TextBlock",
			"text": "The latest from Bing",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Take a look at the image of the day, plus the last two days.",
			"wrap": true
		},
		{
			"type": "ImageSet",
			"imageSize": "medium",
			"images": [
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/BingAppIcon.png",
					"altText": "Bing App Icon"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/image1.png",
					"altText": "A close up of a flower"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/image2.png",
					"altText": "Two people standing on a mountain looking at the sunset"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/image3.png",
					"altText": "Water under a wooden bridge"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "View More",
			"url": "http://bing.com"
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5"
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"images": [
		{
			"url": "https://adaptivecards.io/content/BingAppIcon.png",
			"altText": "Bing App Icon"
		},
		{
			"url": "https://adaptivecards.io/content/image1.png",
			"altText": "A close up of a flower"
		},
		{
			"url": "https://adaptivecards.io/content/image2.png",
			"altText": "Two people standing on a mountain looking at the sunset"
		},
		{
			"url": "https://adaptivecards.io/content/image3.png",
			"altText": "Water under a wooden bridge"
		}
	]
}
```

**Template JSON**

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "TextBlock",
			"text": "The latest from Bing",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Take a look at the image of the day, plus the last two days.",
			"wrap": true
		},
		{
			"type": "ImageSet",
			"imageSize": "medium",
			"images": [
				{
					"$data": "${images}",
					"type": "Image",
					"url": "${url}",
					"altText": "${altText}"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "View More",
			"url": "http://bing.com"
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5"
}
```

