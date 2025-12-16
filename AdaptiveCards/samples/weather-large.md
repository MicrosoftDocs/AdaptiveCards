---
title:  Sample of Weather Large
author: luywang
description: This page provides a sample code for Weather Large Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Weather Large

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Weather large sample

The following section displays the JSON for a "Weather large" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": 35,
					"items": [
						{
							"type": "TextBlock",
							"text": "Redmond, WA",
							"size": "large",
							"weight": "bolder",
							"wrap": true,
							"style": "heading"
						},
						{
							"type": "TextBlock",
							"text": "July 12, 5:30 PM",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "24 / 20",
							"size": "extraLarge",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "Cloudy",
							"isSubtle": true,
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
							"type": "Image",
							"url": "https://adaptivecards.io/content/MostlyCloudy.png",
							"altText": "Mostly Cloudy",
							"size": "medium",
							"horizontalAlignment": "right"
						}
					]
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
							"type": "TextBlock",
							"text": "Wind",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "10 km/h",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Precipitation",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "1.5 cm",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Humidity",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "65%",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "Fri",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/MostlyCloudy.png",
							"altText": "Mostly Cloudy",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "23",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "Sat",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/Cloudy.png",
							"altText": "Cloudy",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "21",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "Sun",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/Sunny.png",
							"altText": "Sunny",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "24",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "Mon",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/MostlyCloudy.png",
							"altText": "Mostly Cloudy",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "24",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "Tue",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/ModerateRain.png",
							"altText": "Moderate Rain",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "19",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
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
	"location": "Redmond, WA",
	"currentDate": "July 12, 5:30 PM",
	"currentTemp": "24",
	"lowTemp": "20",
	"condition": "Cloudy",
	"currentConditionImage": "https://adaptivecards.io/content/MostlyCloudy.png",
	"wind": "10 km/h",
	"precipitation": "1.5 cm",
	"humidity": "65%",
	"forecast": [
		{
			"day": "Fri",
			"image": "https://adaptivecards.io/content/MostlyCloudy.png",
			"temp": "23"
		},
		{
			"day": "Sat",
			"image": "https://adaptivecards.io/content/Cloudy.png",
			"temp": "21"
		},
		{
			"day": "Sun",
			"image": "https://adaptivecards.io/content/Sunny.png",
			"temp": "24"
		},
		{
			"day": "Mon",
			"image": "https://adaptivecards.io/content/MostlyCloudy.png",
			"temp": "24"
		},
		{
			"day": "Tue",
			"image": "https://adaptivecards.io/content/ModerateRain.png",
			"temp": "19"
		}
	]
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
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"width": 35,
					"items": [
						{
							"type": "TextBlock",
							"text": "${location}",
							"size": "large",
							"weight": "bolder",
							"style": "heading",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${currentDate}",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${currentTemp} / ${lowTemp}",
							"size": "extraLarge",
							"spacing": "none",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${condition}",
							"isSubtle": true,
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
							"type": "Image",
							"url": "${currentConditionImage}",
							"altText": "Mostly Cloudy",
							"size": "medium",
							"horizontalAlignment": "right"
						}
					]
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
							"type": "TextBlock",
							"text": "Wind",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${wind}",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Precipitation",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${precipitation}",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Humidity",
							"isSubtle": true,
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "${humidity}",
							"spacing": "small",
							"wrap": true
						}
					],
					"width": 1
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"columns": [
				{
					"$data": "${forecast}",
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "${day}",
							"weight": "bolder",
							"wrap": true
						},
						{
							"type": "Image",
							"url": "${image}",
							"altText": "Mostly Cloudy",
							"size": "small",
							"horizontalAlignment": "center"
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "${temp}",
							"spacing": "none",
							"wrap": true
						}
					],
					"width": 1
				}
			]
		}
	]
}
```

