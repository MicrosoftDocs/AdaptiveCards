---
title:  Sample of Order Delivery
author: luywang
description: This page provides a sample code for Order Delivery Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Order Delivery

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Order delivery sample

The following section displays the JSON for an "Order delivery" Adaptive Card sample, shown with and without templating
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
			"text": "Your order is confirmed!",
			"size": "large",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Order #4354235456",
			"weight": "bolder",
			"spacing": "small",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Estimated delivery: {{DATE(2022-04-10T00:00:00Z, SHORT)}}",
			"color": "accent",
			"spacing": "small",
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
							"type": "TextBlock",
							"text": "4 item(s)",
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
							"text": "Total: $12.35",
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
			"title": "View order details",
			"url": "https://adaptivecards.io"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"orderID": "4354235456",
	"itemsCount": 4,
	"totalPrice": "12.35",
	"deliveryDate": "2022-04-10T00:00:00Z"
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
			"text": "Your order is confirmed!",
			"size": "large",
			"weight": "bolder",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Order #${orderID}",
			"weight": "bolder",
			"spacing": "small",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Estimated delivery: {{DATE(${string(deliveryDate)}, SHORT)}}",
			"color": "accent",
			"spacing": "small",
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
							"type": "TextBlock",
							"text": "${itemsCount} item(s)",
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
							"text": "Total: $${totalPrice}",
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
			"title": "View order details",
			"url": "https://adaptivecards.io"
		}
	]
}
```
