---
title:  Sample of Flight Details
author: luywang
description: This page provides a sample code for Flight Details Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Flight Details

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.



## Flight details sample

The following section displays the JSON for a "Flight details" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Details",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Container",
							"backgroundImage": "https://adaptivecards.io/content/TxP_Background.png",
							"items": [
								{
									"type": "Image",
									"horizontalAlignment": "center",
									"url": "https://adaptivecards.io/content/TxP_Flight.png",
									"altText": "Departing airplane"
								}
							],
							"bleed": true,
							"style": "emphasis"
						},
						{
							"type": "Container",
							"spacing": "none",
							"style": "emphasis",
							"items": [
								{
									"type": "TextBlock",
									"size": "extraLarge",
									"weight": "lighter",
									"color": "accent",
									"text": "Flight to JFK",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "small",
									"text": "Continental Air Lines flight UA110",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "none",
									"text": "Confirmation code: RXJ34P",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "none",
									"text": "4 hours 15 minutes",
									"wrap": true
								}
							],
							"bleed": true,
							"height": "stretch"
						}
					],
					"width": 45
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "Container",
							"height": "stretch",
							"items": [
								{
									"type": "ColumnSet",
									"columns": [
										{
											"type": "Column",
											"items": [
												{
													"type": "TextBlock",
													"size": "extraLarge",
													"weight": "lighter",
													"text": "SFO",
													"wrap": true
												}
											],
											"width": "1"
										},
										{
											"type": "Column",
											"verticalContentAlignment": "center",
											"items": [
												{
													"type": "Image",
													"url": "https://adaptivecards.io/content/smallairplane.png",
													"height": "16px",
													"altText": "Flight to"
												}
											],
											"width": "auto"
										},
										{
											"type": "Column",
											"items": [
												{
													"type": "TextBlock",
													"horizontalAlignment": "right",
													"size": "extraLarge",
													"weight": "lighter",
													"text": "JFK",
													"wrap": true
												}
											],
											"width": "1"
										}
									]
								},
								{
									"type": "ColumnSet",
									"columns": [
										{
											"type": "Column",
											"items": [
												{
													"type": "RichTextBlock",
													"inlines": [
														{
															"type": "TextRun",
															"size": "medium",
															"text": "8:15 PM\n"
														},
														{
															"type": "TextRun",
															"text": "Sat, Mar 4, 2017\n",
															"isSubtle": true
														},
														{
															"type": "TextRun",
															"text": "San Francisco",
															"isSubtle": true
														}
													]
												}
											],
											"width": 1
										},
										{
											"type": "Column",
											"items": [
												{
													"type": "RichTextBlock",
													"horizontalAlignment": "right",
													"inlines": [
														{
															"type": "TextRun",
															"size": "medium",
															"text": "3:30 AM\n"
														},
														{
															"type": "TextRun",
															"text": "Sat, Mar 4, 2017\n",
															"isSubtle": true
														},
														{
															"type": "TextRun",
															"text": "New York",
															"isSubtle": true
														}
													]
												}
											],
											"width": 1
										}
									]
								},
								{
									"type": "ActionSet",
									"separator": true,
									"actions": [
										{
											"type": "Action.Submit",
											"title": "Check in",
											"style": "positive"
										},
										{
											"type": "Action.Submit",
											"title": "View"
										}
									],
									"spacing": "medium"
								}
							]
						}
					],
					"width": 55
				}
			],
			"height": "stretch"
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5"
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
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "TextBlock",
			"text": "Your Flight Details",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Container",
							"backgroundImage": "https://adaptivecards.io/content/TxP_Background.png",
							"items": [
								{
									"type": "Image",
									"horizontalAlignment": "center",
									"url": "https://adaptivecards.io/content/TxP_Flight.png",
									"altText": "Departing airplane"
								}
							],
							"bleed": true
						},
						{
							"type": "Container",
							"spacing": "none",
							"style": "emphasis",
							"items": [
								{
									"type": "TextBlock",
									"size": "extraLarge",
									"weight": "lighter",
									"color": "accent",
									"text": "Flight to ${reservationFor.arrivalAirport.iataCode}",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "small",
									"text": "${reservationFor.provider.name}  Air Lines flight ${reservationFor.flightNumber} ",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "none",
									"text": "Confirmation code: ${reservationId}",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "none",
									"text": "4 hours 15 minutes",
									"wrap": true
								}
							],
							"bleed": true,
							"height": "stretch"
						}
					],
					"width": 45,
					"height": "stretch"
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "Container",
							"height": "stretch",
							"items": [
								{
									"type": "ColumnSet",
									"columns": [
										{
											"type": "Column",
											"items": [
												{
													"type": "TextBlock",
													"size": "extraLarge",
													"weight": "lighter",
													"text": "${reservationFor.departureAirport.iataCode}",
													"wrap": true
												}
											],
											"width": "1"
										},
										{
											"type": "Column",
											"spacing": "small",
											"verticalContentAlignment": "center",
											"items": [
												{
													"type": "Image",
													"url": "https://adaptivecards.io/content/smallairplane.png",
													"height": "16px",
													"altText": "Flight to"
												}
											],
											"width": "auto"
										},
										{
											"type": "Column",
											"items": [
												{
													"type": "TextBlock",
													"horizontalAlignment": "right",
													"size": "extraLarge",
													"weight": "lighter",
													"text": "${reservationFor.arrivalAirport.iataCode}",
													"wrap": true
												}
											],
											"width": "1"
										}
									]
								},
								{
									"type": "ColumnSet",
									"columns": [
										{
											"type": "Column",
											"items": [
												{
													"type": "RichTextBlock",
													"inlines": [
														{
															"type": "TextRun",
															"size": "medium",
															"text": "{{TIME(${string(reservationFor.departureTime)})}}\\n",
															"wrap": true
														},
														{
															"type": "TextRun",
															"text": "{{DATE(${string(reservationFor.departureTime)}, SHORT)}}\\n",
															"isSubtle": true,
															"wrap": true
														},
														{
															"type": "TextRun",
															"text": "${reservationFor.departureAirport.city}",
															"isSubtle": true,
															"wrap": true
														}
													]
												}
											],
											"width": 1
										},
										{
											"type": "Column",
											"items": [
												{
													"type": "RichTextBlock",
													"horizontalAlignment": "right",
													"inlines": [
														{
															"type": "TextRun",
															"size": "medium",
															"text": "{{TIME(${string(reservationFor.arrivalTime)})}}\\n",
															"wrap": true
														},
														{
															"type": "TextRun",
															"text": "{{DATE(${string(reservationFor.arrivalTime)}, SHORT)}}\\n",
															"isSubtle": true,
															"wrap": true
														},
														{
															"type": "TextRun",
															"text": "${reservationFor.arrivalAirport.city}",
															"isSubtle": true,
															"wrap": true
														}
													]
												}
											],
											"width": 1
										}
									]
								},
								{
									"type": "ActionSet",
									"separator": true,
									"actions": [
										{
											"type": "Action.Submit",
											"title": "Check in",
											"style": "positive"
										},
										{
											"type": "Action.Submit",
											"title": "View"
										}
									],
									"spacing": "medium"
								}
							]
						}
					],
					"width": 55
				}
			],
			"height": "stretch"
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5"
}
```

