---
title:  Sample of Restaurant Order
author: luywang
description: This page provides a sample code for Restaurant Order Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Restaurant Order

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Restaurant order sample

The following section displays the JSON for a "Restaurant order" Adaptive Card sample, shown with and without templating.

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
			"size": "medium",
			"weight": "bolder",
			"text": "The Restaurant",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Your takeout order is ready for pickup!",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Order number",
					"value": "4354235456"
				},
				{
					"title": "Time placed",
					"value": "{{TIME(2017-02-14T06:08:39Z)}}"
				},
				{
					"title": "Est. pickup",
					"value": "{{TIME(2017-02-14T06:20:39Z)}}"
				}
			],
			"spacing": "small"
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "FactSet",
					"facts": [
						{
							"title": "1x",
							"value": "Steak"
						},
						{
							"title": "2x",
							"value": "Side Rice"
						},
						{
							"title": "1x",
							"value": "Soft Drink"
						}
					],
					"spacing": "small"
				}
			],
			"spacing": "small"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "Total",
							"isSubtle": true,
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
							"text": "$12.35",
							"horizontalAlignment": "right",
							"weight": "bolder",
							"wrap": true
						}
					]
				}
			],
			"spacing": "small",
			"separator": true
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Directions",
			"url": "http://contososcubademo.azurewebsites.net"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"@context": "http://schema.org",
	"@type": "Order",
	"url": "https://www.thisisarestaurant.com",
	"orderNumber": "4354235456",
	"timePlaced": "2017-02-14T06:08:39Z",
	"expectedArrival": "2017-02-14T06:20:39Z",
	"customer": [
		{
			"firstName": "John",
			"lastName": "Smith"
		}
	],
	"seller": {
		"@type": "Restaurant",
		"name": "The Restaurant"
	},
	"acceptedOffer": {
		"@type": "Offer",
		"price": "12.35",
		"priceCurrency": "USD"
	}
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
			"size": "medium",
			"weight": "bolder",
			"text": "${seller.name}",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Your takeout order is ready for pickup!",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Order number",
					"value": "${orderNumber}"
				},
				{
					"title": "Time placed",
					"value": "{{TIME(${string(timePlaced)}}"
				},
				{
					"title": "Est. pickup",
					"value": "{{TIME(${string(expectedArrival)}}"
				}
			],
			"spacing": "small"
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "FactSet",
					"facts": [
						{
							"title": "1x",
							"value": "Steak"
						},
						{
							"title": "2x",
							"value": "Side Rice"
						},
						{
							"title": "1x",
							"value": "Soft Drink"
						}
					],
					"spacing": "small"
				}
			],
			"spacing": "small"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "Total",
							"isSubtle": true,
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
							"text": "$${acceptedOffer.price}",
							"horizontalAlignment": "right",
							"weight": "bolder",
							"wrap": true
						}
					]
				}
			],
			"spacing": "small",
			"separator": true
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Directions",
			"url": "http://contososcubademo.azurewebsites.net"
		}
	]
}
```

