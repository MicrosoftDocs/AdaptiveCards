---
title:  Column Element
author: luywang
description: This page provides documentation for the `Column` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Column Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Column** element, which defines a container that is part of a `ColumnSet`.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Column

Defines a container that is part of a ColumnSet.

### Column Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **items** | `Element[]` | No | The card elements to render inside the `Column`. | 1.0 |
| **backgroundImage** | `BackgroundImage`, `uri` | No | Specifies the background image. Acceptable formats are PNG, JPEG, and GIF. | 1.2 |
| **bleed** | `boolean` | No | Determines whether the column should bleed through its parent’s padding. | 1.2 |
| **fallback** | `Column`, `FallbackOption` | No | Describes what to do when an unknown item is encountered or the requires of this or any children can’t be met. | 1.2 |
| **minHeight** | `string` | No | Specifies the minimum height of the column in pixels, like `&quot;80px&quot;`. | 1.2 |
| **rtl** | `boolean?` | No | When `true` content in this column should be presented right to left. When ‘false’ content in this column should be presented left to right. When unset layout direction will inherit from parent container or column. If unset in all ancestors, the default platform behavior will apply. | 1.5 |
| **separator** | `boolean` | No | When `true`, draw a separating line between this column and the previous column. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this column and the preceding column. | 1.0 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the `Column` is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **style** | `ContainerStyle?` | No | Style hint for `Column`. | 1.0 |
| **verticalContentAlignment** | `VerticalContentAlignment?` | No | Defines how the content should be aligned vertically within the column. When not specified, the value of verticalContentAlignment is inherited from the parent container. If no parent container has verticalContentAlignment set, it defaults to Top. | 1.1 |
| **width** | `string`, `number` | No | `"auto"`, `"stretch"`, a number representing relative width of the column in the column group, or in version 1.1 and higher, a specific pixel width, like `"50px"`. | 1.0 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **id** | `string` | No | A unique identifier associated with the item. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic Column Example (JSON)

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

### items

The card elements to render inside the `Column`.

  * **Type**: `Element[]`
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`

### backgroundImage

Specifies the background image. Acceptable formats are PNG, JPEG, and GIF.

  * **Type**: `BackgroundImage`, `uri`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `BackgroundImage`
      * `uri`

#### BackgroundImage Example (JSON)

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": "https://adaptivecards.io/content/AlkiBeach.jpg",
                    "width": "auto"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/GoldenGardensPark.jpg",
                        "verticalAlignment": "Center"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": "https://adaptivecards.io/content/BainbridgeIsland.jpg",
                    "width": "auto"
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "You can even repeat the background image..."
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/uparrow.png",
                        "fillMode": "Repeat"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "horizontalAlignment": "Center",
                    "verticalContentAlignment": "Center",
                    "items": [
                        {
                            "type": "TextBlock",
                            "horizontalAlignment": "Center",
                            "text": "Those are some neat arrows",
                            "wrap": true
                        }
                    ],
                    "width": "stretch"
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Horizontal repeat..."
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/downarrow.png",
                        "fillMode": "RepeatHorizontally"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/uparrow.png",
                        "fillMode": "RepeatHorizontally",
                        "verticalAlignment": "Center"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/uparrow.png",
                        "fillMode": "RepeatHorizontally",
                        "verticalAlignment": "Bottom"
                    },
                    "width": "stretch"
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Vertical repeat..."
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/uparrow.png",
                        "fillMode": "RepeatVertically"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/downarrow.png",
                        "fillMode": "RepeatVertically",
                        "horizontalAlignment": "Center"
                    },
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "minHeight": "50px",
                    "backgroundImage": {
                        "url": "https://adaptivecards.io/content/uparrow.png",
                        "fillMode": "RepeatVertically",
                        "horizontalAlignment": "Right"
                    },
                    "width": "stretch"
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

### bleed

Determines whether the column should bleed through its parent's padding.

  * **Type**: `boolean`
  * **Version**: 1.2
  * **Required**: No

#### Bleed Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "TextBlock",
			"text": "Bleed left"
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"style": "good",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						}
					],
					"bleed": true,
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "attention",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						}
					],
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "warning",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						}
					],
					"width": "stretch"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Bleed center"
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"style": "good",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						}
					],
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "attention",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						}
					],
					"bleed": true,
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "warning",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						}
					],
					"width": "stretch"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Bleed right"
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"style": "good",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						}
					],
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "attention",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						}
					],
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "warning",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						}
					],
					"bleed": true,
					"width": "stretch"
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Bleed all"
		},
		{
			"type": "ColumnSet",
			"style": "emphasis",
			"columns": [
				{
					"type": "Column",
					"style": "good",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						}
					],
					"bleed": true,
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "attention",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 2"
						}
					],
					"bleed": true,
					"width": "stretch"
				},
				{
					"type": "Column",
					"style": "warning",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 3"
						}
					],
					"bleed": true,
					"width": "stretch"
				}
			]
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.0"
}
```

### fallback

Describes what to do when an unknown item is encountered or the requires of this or any children can't be met.

  * **Type**: `Column`, `FallbackOption`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `Column`
      * `"drop"`: Causes this element to be dropped immediately when unknown elements are encountered. The unknown element doesn't bubble up any higher.

#### Fallback Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "ColumnSet",
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "Graph"
						}
					],
					"fallback": {
						"type": "Column",
						"items": [
							{
								"type": "TextBlock",
								"text": "Fallback"
							}
						]
					},
					"width": "auto"
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "Graph"
						}
					],
					"fallback": "drop"
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "This is a column",
							"wrap": true
						}
					]
				}
			]
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.0"
}
```

### minHeight

Specifies the minimum height of the column in pixels, like `"80px"`.

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
			"minHeight": "100px",
			"columns": [
				{
					"type": "Column",
					"style": "default",
					"minHeight": "200px",
					"items": [
						{
							"type": "TextBlock",
							"wrap": true,
							"text": "The columnset has a minHeight of 100px while this column has a minHeight of 200px so it should override"
						}
					]
				},
				{
					"type": "Column",
					"style": "default",
					"minHeight": "50px",
					"items": [
						{
							"type": "FactSet",
							"facts": [
								{
									"title": "ColumnSet",
									"value": "MinHeight: 100px"
								},
								{
									"title": "Column 1",
									"value": "MinHeight: 200px"
								},
								{
									"title": "Column 2",
									"value": "MinHeight: 50px"
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

### rtl

When `true` content in this column should be presented right to left. When 'false' content in this column should be presented left to right. When unset, layout direction will inherit from parent container or column. If unset in all ancestors, the default platform behavior will apply.

  * **Type**: `boolean?`
  * **Version**: 1.5
  * **Required**: No

#### rtl Example (JSON)

```json
{
  "type": "AdaptiveCard",
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.5",
  "body": [
    {
      "type": "TextBlock",
      "text": "The middle column is set to rtl",
      "wrap": true,
      "size": "Medium"
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "items": [
            {
              "type": "TextBlock",
              "text": "Column One",
              "wrap": true
            }
          ]
        },
        {
          "type": "Column",
          "rtl": true,
          "items": [
            {
              "type": "TextBlock",
              "text": "العمود الثاني",
              "wrap": true
            }
          ]
        },
        {
          "type": "Column",
          "items": [
            {
              "type": "TextBlock",
              "wrap": true,
              "text": "Column three"
            }
          ]
        }
      ],
      "spacing": "Medium"
    }
  ]
}
```

### separator

When `true`, draw a separating line between this column and the previous column.

  * **Type**: `boolean`
  * **Required**: No

### spacing

Controls the amount of spacing between this column and the preceding column.

  * **Type**: `Spacing`
  * **Required**: No
  * **Allowed values**:
      * `"default"`, `"none"`, `"small"`, `"medium"`, `"large"`, `"extraLarge"`, `"padding"`

#### Spacing Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"speak": "The Seattle Seahawks beat the Carolina Panthers 40-7",
	"body": [
		{
			"type": "Container",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"width": "auto",
							"items": [
								{
									"type": "Image",
									"url": "https://adaptivecards.io/content/cats/3.png",
									"altText": "Shades cat team emblem",
									"size": "medium"
								},
								{
									"type": "TextBlock",
									"text": "SHADES",
									"horizontalAlignment": "center",
									"weight": "bolder"
								}
							]
						},
						{
							"type": "Column",
							"width": "stretch",
							"separator": true,
							"spacing": "medium",
							"items": [
								{
									"type": "TextBlock",
									"text": "Dec 4",
									"horizontalAlignment": "center"
								},
								{
									"type": "TextBlock",
									"text": "Final",
									"spacing": "none",
									"horizontalAlignment": "center"
								},
								{
									"type": "TextBlock",
									"text": "7 - 40",
									"size": "extraLarge",
									"horizontalAlignment": "center"
								}
							]
						},
						{
							"type": "Column",
							"width": "auto",
							"separator": true,
							"spacing": "medium",
							"items": [
								{
									"type": "Image",
									"url": "https://adaptivecards.io/content/cats/2.png",
									"altText": "Skins cat team emblem",
									"size": "medium",
									"horizontalAlignment": "center"
								},
								{
									"type": "TextBlock",
									"text": "SKINS",
									"horizontalAlignment": "center",
									"weight": "bolder"
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

### selectAction

An Action that will be invoked when the `Column` is tapped or selected. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`, `Action.OpenUrl`, `Action.Submit`, `Action.ToggleVisibility`

#### SelectAction Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Try clicking a column!",
			"weight": "bolder"
		},
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
					],
					"selectAction": {
						"type": "Action.OpenUrl",
						"tooltip": "cool link",
						"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
					}
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
					],
					"selectAction": {
						"type": "Action.OpenUrl",
						"tooltip": "another cool link",
						"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
					}
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
					],
					"selectAction": {
						"type": "Action.OpenUrl",
						"tooltip": "a third cool link",
						"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
					}
				}
			]
		}
	]
}
```

### style

Style hint for `Column`.

  * **Type**: `ContainerStyle?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`, `"emphasis"`, `"good"` (v1.2+), `"attention"` (v1.2+), `"warning"` (v1.2+), `"accent"` (v1.2+)

#### Style Example (JSON)

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
							"text": "No Style"
						}
					]
				},
				{
					"type": "Column",
					"style": "default",
					"items": [
						{
							"type": "TextBlock",
							"text": "Default Style"
						}
					]
				},
				{
					"type": "Column",
					"style": "emphasis",
					"items": [
						{
							"type": "TextBlock",
							"text": "Emphasis Style"
						},
						{
							"type": "Container",
							"items": [
								{
									"type": "TextBlock",
									"text": "Container no style"
								}
							]
						},
						{
							"type": "Container",
							"style": "default",
							"items": [
								{
									"type": "TextBlock",
									"text": "Container default style"
								}
							]
						},
						{
							"type": "Container",
							"style": "emphasis",
							"items": [
								{
									"type": "TextBlock",
									"text": "Container emphasis style"
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

### verticalContentAlignment

Defines how the content should be aligned vertically within the column. When not specified, the value of `verticalContentAlignment` is inherited from the parent container. If no parent container has `verticalContentAlignment` set, it defaults to Top.

  * **Type**: `VerticalContentAlignment?`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"top"`, `"center"`, `"bottom"`

#### VerticalContentAlignment Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.1",
	"verticalContentAlignment": "center",
	"body": [
		{
			"type": "TextBlock",
			"text": "Hi,"
		},
		{
			"type": "TextBlock",
			"text": "MasterHip",
			"isSubtle": true
		},
		{
			"type": "ColumnSet",
			"height": "stretch",
			"columns": [
				{
					"type": "Column",
					"verticalContentAlignment": "bottom",
					"items": [
						{
							"type": "TextBlock",
							"text": "Column 1"
						}
					]
				}
			]
		}
	]
}
```

### width

Controls the width of the column.

  * **Type**: `string`, `number`
  * **Required**: No
  * **Possible values**:
      * `"auto"`: Column takes up the width needed for its contents.
      * `"stretch"`: Column takes up the remaining available width.
      * A `number`: Represents relative width in the column group (e.g., a column with width `2` next to a column with width `1` means the first is twice as wide as the second).
      * A specific pixel width, like `"50px"` (v1.1+).

#### Width Example (JSON)

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
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "(auto)"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/adaptive-card-50.png",
							"altText": "Adaptive cards logo"
						}
					]
				},
				{
					"type": "Column",
					"width": "stretch",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "center",
							"text": "(stretch)"
						},
						{
							"type": "Image",
							"horizontalAlignment": "center",
							"url": "https://adaptivecards.io/content/adaptive-card-50.png",
							"altText": "Adaptive cards logo"
						}
					]
				},
				{
					"type": "Column",
					"width": "auto",
					"items": [
						{
							"type": "TextBlock",
							"text": "(auto)"
						},
						{
							"type": "Image",
							"url": "https://adaptivecards.io/content/adaptive-card-50.png",
							"altText": "Adaptive cards logo"
						}
					]
				}
			]
		}
	]
}
```

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

