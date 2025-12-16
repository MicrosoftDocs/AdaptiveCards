---
title:  Sample of Input Form
author: luywang
description: This page provides a sample code for Input Form Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Input Form

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Input form sample

The following section displays the JSON for an "Input form" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Tell us about yourself",
			"size": "medium",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Text",
			"id": "myName",
			"placeholder": "Name"
		},
		{
			"type": "Input.Text",
			"id": "myTel",
			"placeholder": "Phone Number",
			"style": "Tel"
		},
		{
			"type": "Input.Text",
			"id": "myEmail",
			"placeholder": "Email",
			"style": "Email"
		},
		{
			"type": "Input.Date",
			"id": "myDate",
			"label": "When is your birthday?"
		},
		{
			"type": "Input.Toggle",
			"title": "I accept the terms and conditions",
			"id": "myToggle"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Submit"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{}
```

**Template JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Tell us about yourself",
			"size": "medium",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Text",
			"id": "myName",
			"placeholder": "Name"
		},
		{
			"type": "Input.Text",
			"id": "myTel",
			"placeholder": "Phone Number",
			"style": "Tel"
		},
		{
			"type": "Input.Text",
			"id": "myEmail",
			"placeholder": "Email",
			"style": "Email"
		},
		{
			"type": "Input.Date",
			"id": "myDate",
			"label": "When is your birthday?"
		},
		{
			"type": "Input.Toggle",
			"title": "I accept the terms and conditions",
			"id": "myToggle"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Submit"
		}
	]
}
```

