---
title:  Sample of Product Video
author: luywang
description: This page provides a sample code for Product Video Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Product Video

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Product video sample

The following section displays the JSON for a "Product video" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "Media",
			"sources": [
				{
					"mimeType": "video/mp4",
					"url": "https://adaptivecards.io/content/movie.mp4"
				}
			],
			"poster": "https://adaptivecards.io/content/poster-video.png",
			"altText": "A close up of a flower"
		},
		{
			"type": "TextBlock",
			"text": "The Contoso Home Loan app provides you with the most up-to-date loan rates.",
			"wrap": true,
			"spacing": "large"
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Learn More",
			"url": "http://adaptivecards.io"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"sources": [
		{
			"mimeType": "video/mp4",
			"url": "https://adaptivecards.io/content/movie.mp4"
		}
	],
	"poster": "https://adaptivecards.io/content/poster-video.png",
	"altText": "A close up of a flower",
	"description": "The Contoso Home Loan app provides you with the most up-to-date loan rates.",
	"url": "http://adaptivecards.io"
}
```

**Template JSON**

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "Media",
			"sources": [
				{
					"$data": "${sources}",
					"mimeType": "${mimeType}",
					"url": "${url}"
				}
			],
			"poster": "${poster}",
			"altText": "${altText}"
		},
		{
			"type": "TextBlock",
			"text": "${description}",
			"wrap": true,
			"spacing": "large"
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Learn More",
			"url": "${url}"
		}
	]
}
```

