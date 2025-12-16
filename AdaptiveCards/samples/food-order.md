---
title:  Sample of Food Order
author: luywang
description: This page provides a sample code for Food Order Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Food Order

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Food order sample

The following section displays the JSON for a "Food order" Adaptive Card sample, shown with and without templating.

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
			"text": "Your registration is almost complete",
			"size": "medium",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "What type of food do you prefer?",
			"wrap": true
		},
		{
			"type": "ImageSet",
			"imageSize": "medium",
			"images": [
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/steak.jpeg",
					"altText": "Steak cut with fries"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/chicken.jpeg",
					"altText": "Fried chicken with lettuce"
				},
				{
					"type": "Image",
					"url": "https://adaptivecards.io/content/tofu.jpeg",
					"altText": "Tofu topped with red sauce"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Steak",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.ChoiceSet",
						"id": "SteakTemp",
						"style": "expanded",
						"label": "How would you like your steak prepared?",
						"isRequired": true,
						"errorMessage": "Please select one of the above options",
						"choices": [
							{
								"title": "Rare",
								"value": "rare"
							},
							{
								"title": "Medium-Rare",
								"value": "medium-rare"
							},
							{
								"title": "Well-done",
								"value": "well-done"
							}
						]
					},
					{
						"type": "Input.Text",
						"id": "SteakOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Steak"
						}
					}
				]
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "Chicken",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Toggle",
						"id": "ChickenAllergy",
						"valueOn": "noPeanuts",
						"valueOff": "peanuts",
						"title": "I'm allergic to peanuts",
						"label": "Do you have any allergies?"
					},
					{
						"type": "Input.Text",
						"id": "ChickenOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Chicken"
						}
					}
				]
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "Tofu",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Toggle",
						"id": "Vegetarian",
						"title": "Please prepare it vegan",
						"label": "Would you like it prepared vegan?",
						"valueOn": "vegan",
						"valueOff": "notVegan"
					},
					{
						"type": "Input.Text",
						"id": "VegOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Vegetarian"
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
	"@context": "http://schema.org",
	"@type": "Restaurant",
	"url": "https://www.thisisarestaurant.com",
	"name": "The Restaurant",
	"image": "https://www.example.com/image-of-some-restaurant.jpg",
	"description": "This is an example restaurant that serves American cuisine.",
	"servesCuisine": ["American cuisine"],
	"hasMenu": {
		"@type": "Menu",
		"name": "Dine-In Menu",
		"description": "Menu for in-restaurant dining only.",
		"hasMenuSection": [
			{
				"@type": "MenuSection",
				"name": "Steak",
				"description": "How would you like your steak prepared?",
				"image": "https://contososcubademo.azurewebsites.net/assets/steak.jpg",
				"offers": {
					"@type": "Offer",
					"availabilityEnds": "T8:22:00",
					"availabilityStarts": "T8:22:00"
				},
				"hasMenuSection": [
					{
						"@type": "MenuSection",
						"name": "Chicken",
						"description": "Do you have any allergies?",
						"image": "https://contososcubademo.azurewebsites.net/assets/chicken.jpg",
						"offers": {
							"@type": "Offer",
							"availabilityEnds": "T8:22:00",
							"availabilityStarts": "T8:22:00"
						},
						"hasMenuItem": {
							"@type": "MenuItem",
							"name": "Potato Skins",
							"description": "Small serving of stuffed potato skins.",
							"offers": {
								"@type": "Offer",
								"price": "7.49",
								"priceCurrency": "USD"
							},
							"suitableForDiet": "http://schema.org/GlutenFreeDiet"
						}
					},
					{
						"@type": "MenuSection",
						"name": "Tofu",
						"description": "Would you like it prepared vegan?",
						"image": "https://contososcubademo.azurewebsites.net/assets/tofu.jpg",
						"offers": {
							"@type": "Offer",
							"availabilityEnds": "T8:22:00",
							"availabilityStarts": "T8:22:00"
						},
						"hasMenuItem": {
							"@type": "MenuItem",
							"name": "Pea Soup",
							"description": "Creamy pea soup topped with melted cheese and sourdough croutons.",
							"offers": {
								"@type": "Offer",
								"price": "3.49",
								"priceCurrency": "USD"
							}
						}
					}
				]
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
			"text": "Your registration is almost complete",
			"size": "medium",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "What type of food do you prefer?",
			"wrap": true
		},
		{
			"type": "ImageSet",
			"imageSize": "medium",
			"images": [
				{
					"type": "Image",
					"url": "${hasMenu.hasMenuSection[0].image}",
					"altText": "${hasMenu.hasMenuSection[0].name}"
				},
				{
					"type": "Image",
					"url": "${hasMenu.hasMenuSection[0].hasMenuSection[0].image}",
					"altText": "${hasMenu.hasMenuSection[0].hasMenuSection[0].name}"
				},
				{
					"type": "Image",
					"url": "${hasMenu.hasMenuSection[0].hasMenuSection[1].image}",
					"altText": "${hasMenu.hasMenuSection[0].hasMenuSection[1].name}"
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "${hasMenu.hasMenuSection[0].name}",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.ChoiceSet",
						"id": "SteakTemp",
						"style": "expanded",
						"label": "${hasMenu.hasMenuSection[0].description}",
						"isRequired": true,
						"errorMessage": "Please select one of the above options",
						"choices": [
							{
								"title": "Rare",
								"value": "rare"
							},
							{
								"title": "Medium-Rare",
								"value": "medium-rare"
							},
							{
								"title": "Well-done",
								"value": "well-done"
							}
						]
					},
					{
						"type": "Input.Text",
						"id": "SteakOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Steak"
						}
					}
				],
				"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "${hasMenu.hasMenuSection[0].hasMenuSection[0].name}",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Toggle",
						"id": "ChickenAllergy",
						"valueOn": "noPeanuts",
						"valueOff": "peanuts",
						"title": "I'm allergic to peanuts",
						"label": "${hasMenu.hasMenuSection[0].hasMenuSection[0].description}"
					},
					{
						"type": "Input.Text",
						"id": "ChickenOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Chicken"
						}
					}
				],
				"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
			}
		},
		{
			"type": "Action.ShowCard",
			"title": "${hasMenu.hasMenuSection[0].hasMenuSection[1].name}",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Toggle",
						"id": "Vegetarian",
						"title": "Please prepare it vegan",
						"label": "${hasMenu.hasMenuSection[0].hasMenuSection[1].description}",
						"valueOn": "vegan",
						"valueOff": "notVegan"
					},
					{
						"type": "Input.Text",
						"id": "VegOther",
						"isMultiline": true,
						"label": "Any other preparation requests?"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK",
						"data": {
							"FoodChoice": "Vegetarian"
						}
					}
				],
				"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
			}
		}
	]
}
```

