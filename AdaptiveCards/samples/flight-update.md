---
title:  Sample of Flight Update
author: luywang
description: This page provides a sample code for Flight Update Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Flight Update

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!



These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Flight update sample

The following section displays the JSON for a "Flight update" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"speak": "<s>Flight KL0605 to San Fransisco has been delayed.</s><s>It will not leave until 10:10 AM.</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Update",
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
							"size": "small",
							"altText": "Airplane",
							"url": "https://adaptivecards.io/content/airplane.png"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Flight Status",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "DELAYED",
							"horizontalAlignment": "right",
							"spacing": "none",
							"size": "large",
							"color": "attention",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Passengers",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Sarah Hum",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Jeremy Goldberg",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Evan Litvak",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "Seat",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14A",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14B",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14C",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Flight",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "KL605",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs",
							"isSubtle": true,
							"horizontalAlignment": "center",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "2:20 AM",
							"color": "attention",
							"weight": "bolder",
							"horizontalAlignment": "center",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "8:20 PM",
							"color": "attention",
							"horizontalAlignment": "right",
							"weight": "bolder",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Amsterdam Airport",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "AMS",
							"size": "extraLarge",
							"color": "accent",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": " ",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"altText": "Flight to",
							"size": "small"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "San Francisco Airport",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "SFO",
							"horizontalAlignment": "right",
							"size": "extraLarge",
							"color": "accent",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"@context": "http://schema.org",
	"@type": "FlightReservation",
	"reservationId": "RXJ34P",
	"reservationStatus": "http://schema.org/ReservationConfirmed",
	"passengerPriorityStatus": "Fast Track",
	"passengerSequenceNumber": "ABC123",
	"securityScreening": "TSA PreCheck",
	"underName": {
		"@type": "Person",
		"name": "Sarah Hum"
	},
	"reservationFor": {
		"@type": "Flight",
		"flightNumber": "KL605",
		"provider": {
			"@type": "Airline",
			"name": "KLM",
			"iataCode": "KL",
			"boardingPolicy": "http://schema.org/ZoneBoardingPolicy"
		},
		"seller": {
			"@type": "Airline",
			"name": "KLM",
			"iataCode": "KL"
		},
		"departureAirport": {
			"@type": "Airport",
			"name": "Amsterdam Airport",
			"iataCode": "AMS"
		},
		"departureTime": "2017-03-04T09:20:00-01:00",
		"arrivalAirport": {
			"@type": "Airport",
			"name": "San Francisco Airport",
			"iataCode": "SFO"
		},
		"arrivalTime": "2017-03-05T08:20:00+04:00"
	}
}
```

**Template JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"speak": "<s>Flight KL0605 to San Fransisco has been delayed.</s><s>It will not leave until 10:10 AM.</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Update",
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
							"size": "small",
							"url": "https://adaptivecards.io/content/airplane.png",
							"altText": "Airplane"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Flight Status",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "DELAYED",
							"horizontalAlignment": "right",
							"spacing": "none",
							"size": "large",
							"color": "attention",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"text": "Passengers",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${underName.name}",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Jeremy Goldberg",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Evan Litvak",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "Seat",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14A",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14B",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "14C",
							"horizontalAlignment": "right",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Flight",
							"isSubtle": true,
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${reservationFor.flightNumber}",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs",
							"isSubtle": true,
							"horizontalAlignment": "center",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "{{TIME(${string(reservationFor.departureTime)})}}",
							"color": "attention",
							"weight": "bolder",
							"horizontalAlignment": "center",
							"spacing": "small",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "{{TIME(${string(reservationFor.arrivalTime)})}}",
							"color": "attention",
							"horizontalAlignment": "right",
							"weight": "bolder",
							"spacing": "small",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "${reservationFor.departureAirport.name}",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${reservationFor.departureAirport.iataCode}",
							"size": "extraLarge",
							"color": "accent",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": " ",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"altText": "Airplane",
							"size": "small"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "${reservationFor.arrivalAirport.name}",
							"isSubtle": true,
							"horizontalAlignment": "right",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${reservationFor.arrivalAirport.iataCode}",
							"horizontalAlignment": "right",
							"size": "extraLarge",
							"color": "accent",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		}
	]
}
```

