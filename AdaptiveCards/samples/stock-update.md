---
title:  Sample of Stock Update
author: luywang
description: This page provides a sample code for Stock Update Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Stock Update

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Stock update sample

The following section displays the JSON for a "Stock update" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Stock Update",
			"weight": "bolder",
			"size": "medium",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/img/microsof-logo.png",
							"altText": "Microsoft Logo",
							"size": "small"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "MSFT",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Microsoft Corp",
							"isSubtle": true,
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Current Price",
					"value": "$77.56"
				},
				{
					"title": "Updated At",
					"value": "{{TIME(2017-02-14T06:08:39Z)}}"
				}
			]
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "24h High",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "$77.92",
							"size": "large",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "24h Low",
							"isSubtle": true,
							"horizontalAlignment": "center",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "$75.24",
							"size": "large",
							"horizontalAlignment": "center",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Change",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "($0.33)",
							"size": "large",
							"color": "attention",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "View Stock Chart",
			"url": "http://finance.yahoo.com/q?s=MSFT"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"Symbol": "MSFT",
	"CompanyName": "Microsoft Corp",
	"logo": "https://adaptivecards.io/content/img/microsof-logo.png",
	"currentPrice": "$77.56",
	"updatedAt": "2017-02-14T06:08:39Z",
	"high": "$77.92",
	"low": "$75.24",
	"change": "($0.33)",
	"changeColor": "attention",
	"chartUrl": "http://finance.yahoo.com/q?s=MSFT"
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
			"type": "TextBlock",
			"text": "Stock Update",
			"weight": "bolder",
			"size": "medium",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "Image",
							"url": "${logo}",
							"altText": "${CompanyName} Logo",
							"size": "small"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "${Symbol}",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${CompanyName}",
							"isSubtle": true,
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Current Price",
					"value": "${currentPrice}"
				},
				{
					"title": "Updated At",
					"value": "{{TIME(${string(updatedAt)}}"
				}
			]
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "24h High",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${high}",
							"size": "large",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "24h Low",
							"isSubtle": true,
							"horizontalAlignment": "center",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${low}",
							"size": "large",
							"horizontalAlignment": "center",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Change",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${change}",
							"size": "large",
							"color": "${changeColor}",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "View Stock Chart",
			"url": "${chartUrl}"
		}
	]
}
```

