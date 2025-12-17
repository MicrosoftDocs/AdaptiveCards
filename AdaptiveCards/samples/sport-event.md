---
title:  Sample of Sporting Event
author: luywang
description: This page provides a sample code for Sporting Event Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Sporting Event

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Sporting event sample

The following section displays the JSON for a "Sporting event" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/SportingEvent.png",
			"altText": "Scoreboard showing home team leading visitors 24 to 20.",
			"size": "stretch"
		},
		{
			"type": "TextBlock",
			"text": "Seahawks vs. Patriots",
			"weight": "bolder",
			"size": "large",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Conference Championship",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "4:00 PM EST",
			"weight": "bolder",
			"spacing": "small",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Date",
					"value": "{{DATE(2017-02-14T06:08:39Z, SHORT)}}"
				},
				{
					"title": "Location",
					"value": "Atlanta, GA"
				}
			],
			"spacing": "small"
		},
		{
			"type": "TextBlock",
			"text": "Halftime is starting now. It's anyone's game!",
			"wrap": true,
			"spacing": "medium"
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Full Matchup",
			"url": "http://contososcubademo.azurewebsites.net"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Buy tickets",
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
	"@type": "SportsEvent",
	"name": "Seahawks vs. Patriots",
	"description": "Conference Championship",
	"image": "https://adaptivecards.io/content/SportingEvent.png",
	"startDate": "2017-02-14T16:00:00Z",
	"location": {
		"@type": "Place",
		"address": {
			"@type": "PostalAddress",
			"addressLocality": "Atlanta",
			"addressRegion": "GA"
		}
	},
	"performer": [
		{
			"@type": "SportsTeam",
			"name": "Seattle Seahawks"
		},
		{
			"@type": "SportsTeam",
			"name": "New England Patriots"
		}
	],
	"gameStatus": "Halftime is starting now. It's anyone's game!"
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
			"type": "Image",
			"url": "${image}",
			"altText": "Scoreboard showing home team leading visitors 24 to 20.",
			"size": "stretch"
		},
		{
			"type": "TextBlock",
			"text": "${name}",
			"weight": "bolder",
			"size": "large",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${description}",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "{{TIME(${string(startDate)})}} EST",
			"weight": "bolder",
			"spacing": "small",
			"wrap": true
		},
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Date",
					"value": "{{DATE(${string(startDate)}, SHORT)}}"
				},
				{
					"title": "Location",
					"value": "${location.address.addressLocality}, ${location.address.addressRegion}"
				}
			],
			"spacing": "small"
		},
		{
			"type": "TextBlock",
			"text": "${gameStatus}",
			"wrap": true,
			"spacing": "medium"
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Full Matchup",
			"url": "http://contososcubademo.azurewebsites.net"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Buy tickets",
			"url": "http://contososcubademo.azurewebsites.net"
		}
	]
}
```

