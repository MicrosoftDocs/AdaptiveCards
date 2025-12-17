---
title:  Sample of Order Confirmation
author: luywang
description: This page provides a sample code for Order Confirmation Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Order Confirmation

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Order confirmation sample

The following section displays the JSON for an "Order confirmation" Adaptive Card sample, shown with and without templating.

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
			"text": "Please confirm your order:",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Name",
					"value": "John Smith"
				},
				{
					"title": "Phone number",
					"value": "(555) 555-5555"
				}
			]
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
		}
	],
	"actions": [
		{
			"type": "Action.Execute",
			"title": "Place Order"
		},
		{
			"type": "Action.Execute",
			"title": "Edit Order",
			"data": "edit",
			"mode": "secondary"
		},
		{
			"type": "Action.Execute",
			"title": "Save Order",
			"data": "save",
			"mode": "secondary"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"title": "Please confirm your order:",
	"customer": [
		{
			"firstName": "John",
			"lastName": "Smith",
			"phone": "(555) 555-5555"
		}
	]
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
			"text": "${title}",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Name",
					"value": "${customer[0].firstName} ${customer[0].lastName}"
				},
				{
					"title": "Phone number",
					"value": "${customer[0].phone}"
				}
			]
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
		}
	],
	"actions": [
		{
			"type": "Action.Execute",
			"title": "Place Order"
		},
		{
			"type": "Action.Execute",
			"title": "Edit Order",
			"data": "edit",
			"mode": "secondary"
		},
		{
			"type": "Action.Execute",
			"title": "Save Order",
			"data": "save",
			"mode": "secondary"
		}
	]
}
```

