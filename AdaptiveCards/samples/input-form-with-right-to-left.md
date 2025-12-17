---
title:  Sample of Input Form with Right-to-Left (RTL)
author: luywang
description: This page provides a sample code for Input Form with rtl Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Input Form with Right-to-Left (RTL)

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Input form with rtl sample

The following section displays the JSON for an "Input form with rtl" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"rtl": true,
	"body": [
		{
			"type": "TextBlock",
			"text": "שם המוצר:",
			"wrap": true
		},
		{
			"type": "Input.Text",
			"id": "Name",
			"value": "השם המלא של המוצר",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "צבע המוצר:",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "Color",
			"value": "1",
			"choices": [
				{
					"title": "אדום",
					"value": "1"
				},
				{
					"title": "כחול",
					"value": "2"
				},
				{
					"title": "ירוק",
					"value": "3"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "תאריך יצור:",
			"wrap": true
		},
		{
			"type": "Input.Date",
			"id": "Date",
			"label": "אנא הכנס תאריך",
			"min": "2020-01-01",
			"max": "2025-01-01"
		},
		{
			"type": "TextBlock",
			"text": "הערות נוספות:",
			"wrap": true
		},
		{
			"type": "Input.Text",
			"id": "Comment",
			"isMultiline": true,
			"value": "הכנס הערות נוספות כאן"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "שלח"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"NameText": "שם המוצר:",
	"NamePlaceholder": "השם המלא של המוצר",
	"ColorText": "צבע המוצר:",
	"ColorChoice1": "אדום",
	"ColorChoice2": "כחול",
	"ColorChoice3": "ירוק",
	"DateText": "תאריך יצור:",
	"DatePlaceholder": "אנא הכנס תאריך",
	"CommentText": "הערות נוספות:",
	"CommentPlaceholder": "הכנס הערות נוספות כאן",
	"SubmitText": "שלח"
}
```

**Template JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"rtl": true,
	"body": [
		{
			"type": "TextBlock",
			"text": "${NameText}",
			"wrap": true
		},
		{
			"type": "Input.Text",
			"id": "Name",
			"value": "${NamePlaceholder}",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${ColorText}",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "Color",
			"value": "1",
			"choices": [
				{
					"title": "${ColorChoice1}",
					"value": "1"
				},
				{
					"title": "${ColorChoice2}",
					"value": "2"
				},
				{
					"title": "${ColorChoice3}",
					"value": "3"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "${DateText}",
			"wrap": true
		},
		{
			"type": "Input.Date",
			"id": "Date",
			"label": "${DatePlaceholder}",
			"min": "2020-01-01",
			"max": "2025-01-01"
		},
		{
			"type": "TextBlock",
			"text": "${CommentText}",
			"wrap": true
		},
		{
			"type": "Input.Text",
			"id": "Comment",
			"isMultiline": true,
			"value": "${CommentPlaceholder}"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "${SubmitText}"
		}
	]
}
```

