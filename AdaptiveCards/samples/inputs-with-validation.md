---
title:  Sample of Inputs With Validation
author: luywang
description: This page provides a sample code for Inputs With Validation Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Inputs With Validation

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Inputs with validation sample

The following section displays the JSON for an "Inputs with validation" Adaptive Card sample, shown with and without templating.

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
			"size": "medium",
			"weight": "bolder",
			"text": "Input.Text elements",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Text",
			"label": "Name",
			"style": "text",
			"id": "SimpleVal",
			"isRequired": true,
			"errorMessage": "Name is required",
			"placeholder": "Enter your name"
		},
		{
			"type": "Input.Text",
			"label": "Homepage",
			"style": "url",
			"id": "UrlVal",
			"placeholder": "Enter your homepage url"
		},
		{
			"type": "Input.Text",
			"label": "Email",
			"style": "email",
			"id": "EmailVal",
			"placeholder": "Enter your email"
		},
		{
			"type": "Input.Text",
			"label": "Phone",
			"style": "tel",
			"id": "TelVal",
			"placeholder": "Enter your phone number"
		},
		{
			"type": "Input.Text",
			"label": "Comments",
			"style": "text",
			"isMultiline": true,
			"id": "MultiLineVal",
			"placeholder": "Enter any comments"
		},
		{
			"type": "TextBlock",
			"size": "medium",
			"weight": "bolder",
			"text": "Input.Text InlineAction",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Text",
			"label": "Text input with an inline action with no icon",
			"id": "textInlineActionId",
			"placeholder": "Enter text",
			"inlineAction": {
				"type": "Action.OpenUrl",
				"title": "Reply",
				"tooltip": "Reply to this message",
				"url": "https://adaptivecards.io",
				"role": "button"
			}
		},
		{
			"type": "Input.Number",
			"label": "Quantity (Minimum -5, Maximum 5)",
			"min": -5,
			"max": 5,
			"value": 1,
			"id": "NumVal",
			"errorMessage": "The quantity must be between -5 and 5"
		},
		{
			"type": "Input.Date",
			"label": "Due Date",
			"id": "DateVal",
			"value": "2017-09-20"
		},
		{
			"type": "Input.Time",
			"label": "Start time",
			"id": "TimeVal",
			"value": "16:59"
		},
		{
			"type": "TextBlock",
			"size": "medium",
			"weight": "bolder",
			"text": "Input.ChoiceSet",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.ChoiceSet",
			"id": "CompactSelectVal",
			"label": "What color do you want? (compact)",
			"style": "compact",
			"value": "1",
			"choices": [
				{
					"title": "Red",
					"value": "1"
				},
				{
					"title": "Green",
					"value": "2"
				},
				{
					"title": "Blue",
					"value": "3"
				}
			]
		},
		{
			"type": "Input.ChoiceSet",
			"id": "SingleSelectVal",
			"label": "What color do you want? (expanded)",
			"style": "expanded",
			"value": "1",
			"choices": [
				{
					"title": "Red",
					"value": "1"
				},
				{
					"title": "Green",
					"value": "2"
				},
				{
					"title": "Blue",
					"value": "3"
				}
			]
		},
		{
			"type": "Input.ChoiceSet",
			"id": "MultiSelectVal",
			"label": "What colors do you want? (multiselect)",
			"isMultiSelect": true,
			"value": "1,3",
			"choices": [
				{
					"title": "Red",
					"value": "1"
				},
				{
					"title": "Green",
					"value": "2"
				},
				{
					"title": "Blue",
					"value": "3"
				}
			]
		},
		{
			"type": "TextBlock",
			"size": "medium",
			"weight": "bolder",
			"text": "Input.Toggle",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Toggle",
			"label": "Please accept the terms and conditions:",
			"title": "I accept the terms and conditions (True/False)",
			"valueOn": "true",
			"valueOff": "false",
			"id": "AcceptsTerms",
			"isRequired": true,
			"errorMessage": "Accepting the terms and conditions is required"
		},
		{
			"type": "Input.Toggle",
			"label": "How do you feel about red cars?",
			"title": "Red cars are better than other cars",
			"valueOn": "RedCars",
			"valueOff": "NotRedCars",
			"id": "ColorPreference"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Submit",
			"data": {
				"id": "1234567890"
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "Show Card",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Text",
						"label": "Enter comment",
						"style": "text",
						"id": "CommentVal"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK"
					}
				]
			}
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"ParticipantInfoForm": {
		"title": "Input.Text elements"
	},
	"Survey": {
		"title": "Input ChoiceSet",
		"questions": [
			{
				"question": "What color do you want? (compact)",
				"items": [
					{
						"choice": "Red",
						"value": "1"
					},
					{
						"choice": "Green",
						"value": "2"
					},
					{
						"choice": "Blue",
						"value": "3"
					}
				]
			},
			{
				"question": "What color do you want? (expanded)",
				"items": [
					{
						"choice": "Red",
						"value": "1"
					},
					{
						"choice": "Green",
						"value": "2"
					},
					{
						"choice": "Blue",
						"value": "3"
					}
				]
			},
			{
				"question": "What colors do you want? (multiselect)",
				"items": [
					{
						"choice": "Red",
						"value": "1"
					},
					{
						"choice": "Green",
						"value": "2"
					},
					{
						"choice": "Blue",
						"value": "3"
					}
				]
			},
			{
				"question": "I accept the terms and conditions (True/False)"
			},
			{
				"question": "Red cars are better than other cars"
			}
		]
	}
}
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
			"size": "medium",
			"weight": "bolder",
			"text": " ${ParticipantInfoForm.title}",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Text",
			"label": "Name",
			"style": "text",
			"id": "SimpleVal",
			"isRequired": true,
			"errorMessage": "Name is required",
			"placeholder": "Enter your name"
		},
		{
			"type": "Input.Text",
			"label": "Homepage",
			"style": "url",
			"id": "UrlVal",
			"placeholder": "Enter your homepage url"
		},
		{
			"type": "Input.Text",
			"label": "Email",
			"style": "email",
			"id": "EmailVal",
			"placeholder": "Enter your email"
		},
		{
			"type": "Input.Text",
			"label": "Phone",
			"style": "tel",
			"id": "TelVal",
			"placeholder": "Enter your phone number"
		},
		{
			"type": "Input.Text",
			"label": "Comments",
			"style": "text",
			"isMultiline": true,
			"id": "MultiLineVal",
			"placeholder": "Enter any comments"
		},
		{
			"type": "Input.Number",
			"label": "Quantity (Minimum -5, Maximum 5)",
			"min": -5,
			"max": 5,
			"value": 1,
			"id": "NumVal",
			"errorMessage": "The quantity must be between -5 and 5"
		},
		{
			"type": "Input.Date",
			"label": "Due Date",
			"id": "DateVal",
			"value": "2017-09-20"
		},
		{
			"type": "Input.Time",
			"label": "Start time",
			"id": "TimeVal",
			"value": "16:59"
		},
		{
			"type": "TextBlock",
			"size": "medium",
			"weight": "bolder",
			"text": "${Survey.title} ",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.ChoiceSet",
			"id": "CompactSelectVal",
			"label": "${Survey.questions[0].question}",
			"style": "compact",
			"value": "1",
			"choices": [
				{
					"$data": "${Survey.questions[0].items}",
					"title": "${choice}",
					"value": "${value}"
				}
			]
		},
		{
			"type": "Input.ChoiceSet",
			"id": "SingleSelectVal",
			"label": "${Survey.questions[1].question}",
			"style": "expanded",
			"value": "1",
			"choices": [
				{
					"$data": "${Survey.questions[1].items}",
					"title": "${choice}",
					"value": "${value}"
				}
			]
		},
		{
			"type": "Input.ChoiceSet",
			"id": "MultiSelectVal",
			"label": "${Survey.questions[2].question}",
			"isMultiSelect": true,
			"value": "1,3",
			"choices": [
				{
					"$data": "${Survey.questions[2].items}",
					"title": "${choice}",
					"value": "${value}"
				}
			]
		},
		{
			"type": "TextBlock",
			"size": "medium",
			"weight": "bolder",
			"text": "Input.Toggle",
			"horizontalAlignment": "center",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Input.Toggle",
			"label": "Please accept the terms and conditions:",
			"title": "${Survey.questions[3].question}",
			"valueOn": "true",
			"valueOff": "false",
			"id": "AcceptsTerms",
			"isRequired": true,
			"errorMessage": "Accepting the terms and conditions is required"
		},
		{
			"type": "Input.Toggle",
			"label": "How do you feel about red cars?",
			"title": "${Survey.questions[4].question}",
			"valueOn": "RedCars",
			"valueOff": "NotRedCars",
			"id": "ColorPreference"
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Submit",
			"data": {
				"id": "1234567890"
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "Show Card",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Text",
						"label": "Enter comment",
						"style": "text",
						"id": "CommentVal"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK"
					}
				]
			}
		}
	]
}
```

