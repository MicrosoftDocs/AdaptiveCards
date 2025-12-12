---
title:  ColumnSet Element
author: luywang
description: This page provides documentation for the `ColumnSet` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# ColumnSet Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


This page documents the **ColumnSet** element, which is a container that divides a region into multiple side-by-side **Columns**.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## ColumnSet

ColumnSet divides a region into Columns, allowing elements to sit side-by-side.

### ColumnSet Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;ColumnSet&quot;` | Yes | Must be `&quot;ColumnSet&quot;`. | 1.0 |
| **columns** | `Column[]` | No | The array of `Columns` to divide the region into. | 1.0 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the `ColumnSet` is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **style** | `ContainerStyle?` | No | Style hint for `ColumnSet`. | 1.2 |
| **bleed** | `boolean` | No | Determines whether the element should bleed through its parent’s padding. | 1.2 |
| **minHeight** | `string` | No | Specifies the minimum height of the column set in pixels, like `&quot;80px&quot;`. | 1.2 |
| **horizontalAlignment** | `HorizontalAlignment?` | No | Controls the horizontal alignment of the ColumnSet. When not specified, the value of horizontalAlignment is inherited from the parent container. If no parent container has horizontalAlignment set, it defaults to Left. | 1.0 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.0 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic ColumnSet Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				}
			]
		}
	]
}
```

## Properties

### columns

The array of `Columns` to divide the region into.

  * **Type**: `Column[]`
  * **Required**: No
  * **Allowed values**:
      * `Column`

### selectAction

An Action that will be invoked when the `ColumnSet` is tapped or selected. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`, `Action.OpenUrl`, `Action.Submit`, `Action.ToggleVisibility`

#### SelectAction Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Pick up where you left off?",
			"weight": "bolder"
		},
		{
			"type": "ColumnSet",
			"spacing": "medium",
			"columns": [
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "Image",
							"url": "https://unsplash.it/80?image=1083",
							"altText": "Silver Star Mountain",
							"size": "medium"
						}
					]
				},
				{
					"type": "Column",
					"width": 4,
					"items": [
						{
							"type": "TextBlock",
							"text": "Silver Star Mountain"
						},
						{
							"type": "TextBlock",
							"text": "Maps",
							"isSubtle": true,
							"spacing": "none"
						}
					]
				}
			],
			"selectAction": {
				"type": "Action.OpenUrl",
				"url": "https://www.msn.com",
				"tooltip": "View a map of Silver Star Mountain"
			}
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
							"url": "https://unsplash.it/80?image=1082",
							"altText": "Kitchen Remodel",
							"size": "medium"
						}
					]
				},
				{
					"type": "Column",
					"width": 4,
					"style": "emphasis",
					"items": [
						{
							"type": "TextBlock",
							"text": "Kitchen Remodel"
						},
						{
							"type": "TextBlock",
							"text": "With EMPHASIS",
							"isSubtle": true,
							"spacing": "none"
						}
					]
				}
			],
			"selectAction": {
				"type": "Action.OpenUrl",
				"url": "https://www.AdaptiveCards.io",
				"tooltip": "Remodel your kitchen with our new cabinet styles!"
			}
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
							"url": "https://unsplash.it/80?image=1080",
							"altText": "The Witcher",
							"size": "medium"
						}
					]
				},
				{
					"type": "Column",
					"width": 4,
					"items": [
						{
							"type": "TextBlock",
							"text": "The Witcher"
						},
						{
							"type": "TextBlock",
							"text": "Netflix",
							"isSubtle": true,
							"spacing": "none"
						}
					]
				}
			],
			"selectAction": {
				"type": "Action.OpenUrl",
				"url": "https://www.outlook.com",
				"tooltip": "Watch the newest episode today!"
			}
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Resume all",
			"url": "ms-cortana:resume-all"
		},
		{
			"type": "Action.OpenUrl",
			"title": "More activities",
			"url": "ms-cortana:more-activities"
		}
	]
}
```

### style

Style hint for `ColumnSet`.

  * **Type**: `ContainerStyle?`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"emphasis"`
      * `"good"`
      * `"attention"`
      * `"warning"`
      * `"accent"`

#### Style Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.2",
	"body": [
		{
			"type": "ColumnSet",
			"style": "default",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						},
						{
							"type": "TextBlock",
							"text": "(none)"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": " "
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": " "
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						},
						{
							"type": "TextBlock",
							"text": "(none)"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": " "
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": " "
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				}
			]
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"style": "default",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						},
						{
							"type": "TextBlock",
							"text": "(none)"
						}
					]
				},
				{
					"type": "Column",
					"style": "emphasis",
					"items": [
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						},
						{
							"type": "TextBlock",
							"text": "(none)"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "Container",
							"items": [
								{
									"type": "TextBlock",
									"text": "Contained container - no style",
									"color": "dark"
								}
							]
						},
						{
							"type": "Container",
							"style": "emphasis",
							"items": [
								{
									"type": "TextBlock",
									"text": "Contained container - emphasis",
									"color": "dark"
								}
							]
						},
						{
							"type": "Container",
							"style": "default",
							"items": [
								{
									"type": "TextBlock",
									"text": "Contained container - default",
									"color": "dark"
								}
							]
						}
					]
				}
			]
		}
	]
}
```

### bleed

Determines whether the element should bleed through its parent's padding.

  * **Type**: `boolean`
  * **Version**: 1.2
  * **Required**: No

#### Bleed Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "ColumnSet",
			"style": "good",
			"bleed": true,
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/cats/1.png",
							"altText": "Cat"
						}
					]
				}
			]
		}
	]
}
```

### minHeight

Specifies the minimum height of the column set in pixels, like `"80px"`.

  * **Type**: `string`
  * **Version**: 1.2
  * **Required**: No

#### minHeight Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.2",
	"body": [
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"minHeight": "200px",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"wrap": true,
							"text": "This column set has a minimum height of 200px"
						}
					]
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "FactSet",
							"facts": [
								{
									"title": "ColumnSet",
									"value": "minHeight: 200px"
								},
								{
									"title": "Column",
									"value": "minHeight: not specified"
								}
							]
						}
					]
				}
			]
		}
	]
}
```

### horizontalAlignment

Controls the horizontal alignment of the ColumnSet. When not specified, the value of `horizontalAlignment` is inherited from the parent container. If no parent container has `horizontalAlignment` set, it defaults to Left.

  * **Type**: `HorizontalAlignment?`
  * **Required**: No
  * **Allowed values**:
      * `"left"`
      * `"center"`
      * `"right"`

### fallback

Describes what to do when an unknown element is encountered or the requires of this or any children can't be met.

  * **Type**: `Element`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

### height

Specifies the height of the element.

  * **Type**: `BlockElementHeight`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"auto"`: The height of the container will be determined by the height of its contents.
      * `"stretch"`: The container will stretch its height to the available remaining height of the parent container.

### separator

When `true`, draw a separating line at the top of the element.

  * **Type**: `boolean`
  * **Required**: No

### spacing

Controls the amount of spacing between this element and the preceding element.

  * **Type**: `Spacing`
  * **Required**: No
  * **Allowed values**:
      * `"default"`, `"none"`, `"small"`, `"medium"`, `"large"`, `"extraLarge"`, `"padding"`

### id

A unique identifier associated with the item.

  * **Type**: `string`
  * **Required**: No

### isVisible

If `false`, this item will be removed from the visual tree.

  * **Type**: `boolean`
  * **Version**: 1.2
  * **Required**: No, default: `true`

### requires

A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered.

  * **Type**: `Dictionary<string>`
  * **Version**: 1.2
  * **Required**: No

