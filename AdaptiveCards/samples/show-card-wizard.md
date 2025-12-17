---
title:  Sample of Show Card Wizard
author: luywang
description: This page provides a sample code for Show Card Wizard.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Show Card Wizard

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Show card wizard sample

The following section displays the JSON for a "Show card wizard" Adaptive Card sample, shown with and without templating.

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
			"text": "Wizard with Action.ShowCard",
			"size": "medium",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Question 1: What is your preferred operating system?",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "Q1",
			"style": "expanded",
			"isMultiSelect": false,
			"choices": [
				{
					"title": "Windows",
					"value": "1"
				},
				{
					"title": "macOS",
					"value": "2"
				},
				{
					"title": "Linux",
					"value": "3"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Next",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "TextBlock",
						"text": "Question 2: Which accessories are important to you?",
						"wrap": true
					},
					{
						"type": "Input.ChoiceSet",
						"id": "Q2",
						"isMultiSelect": true,
						"choices": [
							{
								"title": "External mouse",
								"value": "1"
							},
							{
								"title": "External keyboard",
								"value": "2"
							},
							{
								"title": "Webcam",
								"value": "3"
							},
							{
								"title": "Monitor",
								"value": "4"
							}
						]
					}
				],
				"actions": [
					{
						"type": "Action.ShowCard",
						"title": "Next",
						"card": {
							"type": "AdaptiveCard",
							"body": [
								{
									"type": "TextBlock",
									"text": "Question 3: Enter your full name and email",
									"wrap": true
								},
								{
									"type": "Input.Text",
									"id": "Q3Name",
									"placeholder": "Name"
								},
								{
									"type": "Input.Text",
									"id": "Q3Email",
									"placeholder": "Email",
									"style": "email"
								}
							],
							"actions": [
								{
									"type": "Action.Submit",
									"title": "Submit"
								}
							]
						}
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
	"formTitle": "Wizard with Action.ShowCard",
	"step1": {
		"question": "Question 1: What is your preferred operating system?",
		"choices": [
			{
				"title": "Windows",
				"value": "1"
			},
			{
				"title": "macOS",
				"value": "2"
			},
			{
				"title": "Linux",
				"value": "3"
			}
		]
	},
	"step2": {
		"question": "Question 2: Which accessories are important to you?",
		"choices": [
			{
				"title": "External mouse",
				"value": "1"
			},
			{
				"title": "External keyboard",
				"value": "2"
			},
			{
				"title": "Webcam",
				"value": "3"
			},
			{
				"title": "Monitor",
				"value": "4"
			}
		]
	},
	"step3": {
		"question": "Question 3: Enter your full name and email"
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
			"text": "${formTitle}",
			"size": "medium",
			"weight": "bolder",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${step1.question}",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "Q1",
			"style": "expanded",
			"isMultiSelect": false,
			"choices": [
				{
					"$data": "${step1.choices}",
					"title": "${title}",
					"value": "${value}"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Next",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "TextBlock",
						"text": "${step2.question}",
						"wrap": true
					},
					{
						"type": "Input.ChoiceSet",
						"id": "Q2",
						"isMultiSelect": true,
						"choices": [
							{
								"$data": "${step2.choices}",
								"title": "${title}",
								"value": "${value}"
							}
						]
					}
				],
				"actions": [
					{
						"type": "Action.ShowCard",
						"title": "Next",
						"card": {
							"type": "AdaptiveCard",
							"body": [
								{
									"type": "TextBlock",
									"text": "${step3.question}",
									"wrap": true
								},
								{
									"type": "Input.Text",
									"id": "Q3Name",
									"placeholder": "Name"
								},
								{
									"type": "Input.Text",
									"id": "Q3Email",
									"placeholder": "Email",
									"style": "email"
								}
							],
							"actions": [
								{
									"type": "Action.Submit",
									"title": "Submit"
								}
							],
							"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
						}
					}
				],
				"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
			}
		}
	]
}
```
