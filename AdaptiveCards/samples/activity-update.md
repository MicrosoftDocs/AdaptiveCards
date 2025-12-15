---
title:  Sample - Activity Update
author: luywang
description: This page provides a sample code for Adaptive Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Activity Update

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

## Samples and Templates

These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

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
			"text": "Publish Adaptive Card schema",
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
							"url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
							"altText": "Matt Hidinger",
							"size": "small",
							"style": "person"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Matt Hidinger",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"spacing": "none",
							"text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
							"isSubtle": true,
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Board:",
					"value": "Adaptive Card"
				},
				{
					"title": "List:",
					"value": "Backlog"
				},
				{
					"title": "Assigned to:",
					"value": "Matt Hidinger"
				},
				{
					"title": "Due date:",
					"value": "Not set"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Set due date",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Date",
						"label": "Enter the due date",
						"id": "dueDate"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "Send"
					}
				]
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "Comment",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Text",
						"id": "comment",
						"isMultiline": true,
						"label": "Add a comment"
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
	"title": "Publish Adaptive Card Schema",
	"description": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
	"creator": {
		"name": "Matt Hidinger",
		"profileImage": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg"
	},
	"createdUtc": "2017-02-14T06:08:39Z",
	"viewUrl": "https://adaptivecards.io",
	"properties": [
		{ "key": "Board", "value": "Adaptive Cards" },
		{ "key": "List", "value": "Backlog" },
		{ "key": "Assigned to", "value": "Matt Hidinger" },
		{ "key": "Due date", "value": "Not set" }
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
			"size": "medium",
			"weight": "bolder",
			"text": "${title}",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Image",
							"style": "person",
							"url": "${creator.profileImage}",
							"altText": "${creator.name}",
							"size": "small"
						}
					],
					"width": "auto"
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"weight": "bolder",
							"text": "${creator.name}",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"spacing": "none",
							"text": "Created {{DATE(${string(createdUtc)}, SHORT)}}",
							"isSubtle": true,
							"wrap": true
						}
					],
					"width": "stretch"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "${description}",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"$data": "${properties}",
					"title": "${key}:",
					"value": "${value}"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Set due date",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Date",
						"label": "Enter the due date",
						"id": "dueDate"
					},
					{
						"type": "Input.Text",
						"id": "comment",
						"isMultiline": true,
						"label": "Add a comment"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK"
					}
				],
				"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
			}
		},
		{
			"type": "Action.OpenUrl",
			"title": "View",
			"url": "${viewUrl}",
			"role": "button"
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5"
}
```
