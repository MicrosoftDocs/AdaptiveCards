---
title:  Sample of Calendar Reminder
author: luywang
description: This page provides a sample code for Calendar Reminder Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Calendar Reminder

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.



## Calendar reminder sample

The following section displays the JSON for a "Calendar reminder" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"speak": "<s>Your  meeting about \"Adaptive Card design session\"<break strength='weak'/> is starting at 12:30pm</s><s>Do you want to snooze <break strength='weak'/> or do you want to send a late notification to the attendees?</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "Adaptive Card design session",
			"size": "large",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Conf Room 112/3377 (10)",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "12:30 PM - 1:30 PM",
			"isSubtle": true,
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "snooze",
			"label": "Snooze for",
			"style": "compact",
			"value": "5",
			"choices": [
				{
					"title": "5 minutes",
					"value": "5"
				},
				{
					"title": "15 minutes",
					"value": "15"
				},
				{
					"title": "30 minutes",
					"value": "30"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Snooze",
			"data": {
				"x": "snooze"
			}
		},
		{
			"type": "Action.Submit",
			"title": "I'll be late",
			"data": {
				"x": "late"
			}
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"kind": "calendar#event",
	"etag": "\"3007572097704000\"",
	"id": "_6sp3gdjcksmab9kc4rgq1aldjelm8chhcgp66phocg_20191105T150000Z",
	"status": "confirmed",
	"htmlLink": "https://www.google.com/calendar/event?eid=XzZzcDNnZGoxNjBxamdiYjRja3NtYWI5a2M0cmplYjlwNjhyM2diOXA2Z3FtOGNoaGNncDY2cGhvY2dfMjA2xO1UwMDAuZ0Bt",
	"created": "2016-12-29T06:35:05.000Z",
	"updated": "2018-04-24T14:04:50.184Z",
	"summary": "Adaptive Card design session",
	"location": "Conf Room 112/3377 (10)",
	"creator": {
		"email": "sundance@outlook.com",
		"displayName": "John Doe",
		"self": true
	},
	"organizer": {
		"email": "sundance@outlook.com",
		"displayName": "John Doe",
		"self": true
	},
	"start": {
		"dateTime": "2019-11-05T12:30:00-08:00",
		"timeZone": "America/Los_Angeles"
	},
	"end": {
		"dateTime": "2019-11-05T13:30:00-08:00",
		"timeZone": "America/Los_Angeles"
	},
	"recurringEventId": "_6sp3gdj160qjgbb4cksmab9kc4rjeb9p68r3gb9p6gqm8chhcgp66phocg",
	"originalStartTime": {
		"dateTime": "12:30",
		"timeZone": "America/Los_Angeles"
	},
	"visibility": "private",
	"iCalUID": "7286a058-de9e-4a77-9268-945d21d2cf8d",
	"sequence": 4,
	"reminders": {
		"useDefault": false,
		"overrides": [
			{
				"method": "popup",
				"minutes": "5"
			},
			{
				"method": "popup",
				"minutes": "15"
			},
			{
				"method": "popup",
				"minutes": "30"
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
	"speak": "<s>Your  meeting about \"Adaptive Card design session\"<break strength='weak'/> is starting at ${formatDateTime(start.dateTime, 'HH:mm')}pm</s><s>Do you want to snooze <break strength='weak'/> or do you want to send a late notification to the attendees?</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "${summary}",
			"size": "large",
			"weight": "bolder",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": " ${location} ",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${formatDateTime(start.dateTime, 'HH:mm')} - ${formatDateTime(end.dateTime, 'hh:mm')}",
			"isSubtle": true,
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "Input.ChoiceSet",
			"id": "snooze",
			"label": "Snooze for",
			"value": "${reminders.overrides[0].minutes}",
			"choices": [
				{
					"$data": "${reminders.overrides}",
					"title": "${minutes} minutes",
					"value": "${minutes}"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.Submit",
			"title": "Snooze",
			"data": {
				"x": "snooze"
			}
		},
		{
			"type": "Action.Submit",
			"title": "I'll be late",
			"data": {
				"x": "late"
			}
		}
	]
}
```
