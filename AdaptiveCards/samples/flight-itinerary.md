---
title:  Sample of Flight Itinerary
author: luywang
description: This page provides a sample code for Flight Itinerary Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Flight Itinerary

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!



These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.



## Flight itinerary sample

The following section displays the JSON for a "Flight itinerary" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"type": "AdaptiveCard",
	"speak": "<s>Your flight is confirmed for you and 3 other passengers from San Francisco to Amsterdam on Friday, October 10 8:30 AM</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Itinerary",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Passengers",
			"weight": "bolder",
			"isSubtle": false,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Sarah Hum",
			"separator": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Jeremy Goldberg",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Evan Litvak",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "2 Stops",
			"weight": "bolder",
			"spacing": "medium",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Tue, May 30, 2017 12:25 PM",
			"weight": "bolder",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs From",
							"wrap": true,
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"text": "San Francisco",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"text": "SFO",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"verticalContentAlignment": "center",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"size": "small",
							"spacing": "none",
							"altText": "Flight to"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives At",
							"wrap": true,
							"horizontalAlignment": "right",
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"text": "Amsterdam",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"size": "extraLarge",
							"color": "accent",
							"text": "AMS",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Non-Stop",
			"weight": "bolder",
			"spacing": "medium",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Fri, Jun 2, 2017 1:55 PM",
			"weight": "bolder",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs From",
							"wrap": true,
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"text": "Amsterdam",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"text": "AMS",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"verticalContentAlignment": "center",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"size": "small",
							"spacing": "none",
							"altText": "Flight to"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives At",
							"wrap": true,
							"horizontalAlignment": "right",
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"text": "San Francisco",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"size": "extraLarge",
							"color": "accent",
							"text": "SFO",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"width": "1",
					"items": [
						{
							"type": "TextBlock",
							"text": "Total",
							"size": "medium",
							"isSubtle": true,
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
							"horizontalAlignment": "right",
							"text": "$4,032.54",
							"size": "medium",
							"weight": "bolder",
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
		"name": "Eva Green"
	},
	"reservationFor": {
		"@type": "Flight",
		"flightNumber": "UA110",
		"provider": {
			"@type": "Airline",
			"name": "Continental",
			"iataCode": "CO",
			"boardingPolicy": "http://schema.org/ZoneBoardingPolicy"
		},
		"seller": {
			"@type": "Airline",
			"name": "United",
			"iataCode": "UA"
		},
		"departureAirport": {
			"@type": "Airport",
			"name": "San Francisco Airport",
			"city": "San Francisco",
			"iataCode": "SFO"
		},
		"departureTime": "2017-03-04T20:15:00-08:00",
		"arrivalAirport": {
			"@type": "Airport",
			"name": "John F. Kennedy International Airport",
			"city": "New York",
			"iataCode": "JFK"
		},
		"arrivalTime": "2017-03-05T06:30:00-05:00"
	}
}
```

**Template JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"type": "AdaptiveCard",
	"speak": "<s>Your flight is confirmed for you and 3 other passengers from San Francisco to Amsterdam on Friday, October 10 8:30 AM</s>",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Itinerary",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "Passengers",
			"weight": "bolder",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Sarah Hum",
			"separator": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Jeremy Goldberg",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Evan Litvak",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "2 Stops",
			"weight": "bolder",
			"spacing": "medium",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "{{DATE(${string(Segments[0].DepartureDateTime)}, SHORT)}} {{TIME(${string(Segments[0].DepartureDateTime)})}}",
			"weight": "bolder",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs From",
							"wrap": true,
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[0].OriginStation == 11235}",
							"text": "${Places[0].Name}",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[0].OriginStation == 13554}",
							"text": "${Places[1].Name}",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[0].OriginStation == 11235}",
							"text": "${Places[0].Code}",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[0].OriginStation == 13554}",
							"text": "${Places[1].Code}",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"verticalContentAlignment": "center",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"altText": "Flight to",
							"size": "small",
							"spacing": "none"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives At",
							"wrap": true,
							"horizontalAlignment": "right",
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[0].DestinationStation == 11235}",
							"text": "${Places[0].Name}",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[0].DestinationStation == 13554}",
							"text": "${Places[1].Name}",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[0].DestinationStation == 11235}",
							"text": "${Places[0].Code}",
							"horizontalAlignment": "right",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[0].DestinationStation == 13554}",
							"text": "${Places[1].Code}",
							"horizontalAlignment": "right",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Non-Stop",
			"weight": "bolder",
			"spacing": "medium",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "{{DATE(${string(Segments[1].ArrivalDateTime)}, SHORT)}} {{TIME(${string(Segments[1].ArrivalDateTime)})}}",
			"weight": "bolder",
			"spacing": "none",
			"wrap": true
		},
		{
			"type": "ColumnSet",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Departs From",
							"wrap": true,
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[1].OriginStation == 11235}",
							"text": "${Places[0].Name}",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[1].OriginStation == 13554}",
							"text": "${Places[1].Name}",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[1].OriginStation == 11235}",
							"text": "${Places[0].Code}",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[1].OriginStation == 13554}",
							"text": "${Places[1].Code}",
							"spacing": "none",
							"wrap": true
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"verticalContentAlignment": "center",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/airplane.png",
							"altText": "Flight to",
							"size": "small",
							"spacing": "none"
						}
					]
				},
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Arrives At",
							"wrap": true,
							"horizontalAlignment": "right",
							"style": "default",
							"weight": "bolder",
							"color": "light"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[1].DestinationStation == 11235}",
							"text": "${Places[0].Name}",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"$when": "${Segments[1].DestinationStation == 13554}",
							"text": "${Places[1].Name}",
							"horizontalAlignment": "right",
							"isSubtle": true,
							"wrap": true,
							"spacing": "none"
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[1].DestinationStation == 11235}",
							"text": "${Places[0].Code}",
							"horizontalAlignment": "right",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"size": "extraLarge",
							"color": "accent",
							"$when": "${Segments[1].DestinationStation == 13554}",
							"text": "${Places[1].Code}",
							"horizontalAlignment": "right",
							"spacing": "none",
							"wrap": true
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"width": 1,
					"items": [
						{
							"type": "TextBlock",
							"text": "Total",
							"size": "medium",
							"isSubtle": true,
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
							"horizontalAlignment": "right",
							"text": "$${formatNumber(BookingOptions[0].BookingItems[0].Price, 2)}",
							"size": "medium",
							"weight": "bolder",
							"wrap": true
						}
					]
				}
			]
		}
	]
}
```

