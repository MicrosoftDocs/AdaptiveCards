---
title:  Container Element
author: luywang
description: This page provides documentation for the `Container` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Container Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Container** element, which is used to group items together, often for structuring and styling content within an Adaptive Card.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Container

Containers group items together.

### Container Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Container&quot;` | Yes | Must be `&quot;Container&quot;`. | 1.0 |
| **items** | `Element[]` | Yes | The card elements to render inside the `Container`. | 1.0 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the `Container` is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **style** | `ContainerStyle?` | No | Style hint for `Container`. | 1.0 |
| **verticalContentAlignment** | `VerticalContentAlignment?` | No | Defines how the content should be aligned vertically within the container. When not specified, the value of verticalContentAlignment is inherited from the parent container. If no parent container has verticalContentAlignment set, it defaults to Top. | 1.1 |
| **bleed** | `boolean` | No | Determines whether the element should bleed through its parent’s padding. | 1.2 |
| **backgroundImage** | `BackgroundImage`, `uri` | No | Specifies the background image. Acceptable formats are PNG, JPEG, and GIF. | 1.2 |
| **minHeight** | `string` | No | Specifies the minimum height of the container in pixels, like `&quot;80px&quot;`. | 1.2 |
| **rtl?** | `boolean?` | No | When `true` content in this container should be presented right to left. When ‘false’ content in this container should be presented left to right. When unset layout direction will inherit from parent container or column. If unset in all ancestors, the default platform behavior will apply. | 1.5 |

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

### Basic Container Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "Container",
			"items": [
				{
					"type": "TextBlock",
					"text": "This is some text"
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
```

## Properties

### items

The card elements to render inside the `Container`.

  * **Type**: `Element[]`
  * **Required**: Yes
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`

### selectAction

An Action that will be invoked when the `Container` is tapped or selected. `Action.ShowCard` is not supported.

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
			"type": "Container",
			"items": [
				{
					"type": "TextBlock",
					"text": "Cool link"
				}
			],
			"selectAction": {
				"type": "Action.OpenUrl",
				"tooltip": "Go to a url",
				"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
			}
		},
		{
			"type": "Container",
			"style": "emphasis",
			"items": [
				{
					"type": "TextBlock",
					"text": "Emphasis link"
				}
			],
			"selectAction": {
				"type": "Action.OpenUrl",
				"tooltip": "Go to a different url",
				"url": "https://msn.com"
			}
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "TextBlock",
					"text": "Submit action"
				}
			],
			"selectAction": {
				"type": "Action.Submit",
				"tooltip": "Submit action",
				"data": {
					"info": "My submit action data"
				}
			}
		}
	]
}
```

### style

Style hint for `Container`.

  * **Type**: `ContainerStyle?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"emphasis"`
      * `"good"` (Added in version 1.2)
      * `"attention"` (Added in version 1.2)
      * `"warning"` (Added in version 1.2)
      * `"accent"` (Added in version 1.2)

#### Style Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"style": "emphasis",
	"body": [
		{
			"type": "TextBlock",
			"text": "The card has the emphasis style"
		},
		{
			"type": "Container",
			"style": "default",
			"items": [
				{
					"type": "TextBlock",
					"text": "This container has the default style"
				},
				{
					"type": "TextBlock",
					"text": "color: default",
					"color": "default"
				},
				{
					"type": "TextBlock",
					"text": "color: accent",
					"color": "accent"
				},
				{
					"type": "TextBlock",
					"text": "color: good",
					"color": "good"
				},
				{
					"type": "TextBlock",
					"text": "color: warning",
					"color": "warning"
				},
				{
					"type": "TextBlock",
					"text": "color: attention",
					"color": "attention"
				},
				{
					"type": "TextBlock",
					"text": "color: light",
					"color": "light"
				},
				{
					"type": "TextBlock",
					"text": "color: dark",
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
					"text": "This container has the emphasis style"
				},
				{
					"type": "TextBlock",
					"text": "color: default",
					"color": "default"
				},
				{
					"type": "TextBlock",
					"text": "color: accent",
					"color": "accent"
				},
				{
					"type": "TextBlock",
					"text": "color: good",
					"color": "good"
				},
				{
					"type": "TextBlock",
					"text": "color: warning",
					"color": "warning"
				},
				{
					"type": "TextBlock",
					"text": "color: attention",
					"color": "attention"
				},
				{
					"type": "TextBlock",
					"text": "color: light",
					"color": "light"
				},
				{
					"type": "TextBlock",
					"text": "color: dark",
					"color": "dark"
				},
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
```

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.2",
  "body": [
    {
      "type": "Container",
      "style": "default",
      "items": [
        {
          "type": "TextBlock",
          "text": "This container has the default style"
        },
        {
          "type": "TextBlock",
          "text": "color: default",
          "color": "default"
        },
        {
          "type": "TextBlock",
          "text": "color: accent",
          "color": "accent"
        },
        {
          "type": "TextBlock",
          "text": "color: good",
          "color": "good"
        },
        {
          "type": "TextBlock",
          "text": "color: warning",
          "color": "warning"
        },
        {
          "type": "TextBlock",
          "text": "color: attention",
          "color": "attention"
        },
        {
          "type": "TextBlock",
          "text": "color: light",
          "color": "light"
        },
        {
          "type": "TextBlock",
          "text": "color: dark",
          "color": "dark"
        }
      ]
    },
    {
      "type": "Container",
      "style": "accent",
      "items": [
        {
          "type": "TextBlock",
          "text": "This container has the accent style"
        },
        {
          "type": "TextBlock",
          "text": "color: default",
          "color": "default"
        },
        {
          "type": "TextBlock",
          "text": "color: accent",
          "color": "accent"
        },
        {
          "type": "TextBlock",
          "text": "color: good",
          "color": "good"
        },
        {
          "type": "TextBlock",
          "text": "color: warning",
          "color": "warning"
        },
        {
          "type": "TextBlock",
          "text": "color: attention",
          "color": "attention"
        },
        {
          "type": "TextBlock",
          "text": "color: light",
          "color": "light"
        },
        {
          "type": "TextBlock",
          "text": "color: dark",
          "color": "dark"
        },
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
        },
        {
          "type": "Container",
          "style": "good",
          "items": [
            {
              "type": "TextBlock",
              "text": "Contained container - good",
              "color": "dark"
            }
          ]
        },
        {
          "type": "Container",
          "style": "warning",
          "items": [
            {
              "type": "TextBlock",
              "text": "Contained container - warning",
              "color": "dark"
            }
          ]
        },
        {
          "type": "Container",
          "style": "attention",
          "items": [
            {
              "type": "TextBlock",
              "text": "Contained container - attention",
              "color": "dark"
            }
          ]
        },
        {
          "type": "Container",
          "style": "accent",
          "items": [
            {
              "type": "TextBlock",
              "text": "Contained container - accent",
              "color": "dark"
            }
          ]
        }
      ]
    }
  ]
}
```

### verticalContentAlignment

Defines how the content should be aligned vertically within the container. When not specified, the value of `verticalContentAlignment` is inherited from the parent container. If no parent container has `verticalContentAlignment` set, it defaults to Top.

  * **Type**: `VerticalContentAlignment?`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"top"`
      * `"center"`
      * `"bottom"`

#### VerticalContentAlignment Example (JSON)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
    "version": "1.1",	
    "minHeight": "150px",
    "body": [
        {
            "type": "TextBlock",
            "text": "I'm a regular TextBlock..."
        },
        {
            "type": "Container",
            "height": "stretch",
            "verticalContentAlignment": "center",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "But I'm centered..."
                }
            ]
        },
        {
            "type": "Container",
            "verticalContentAlignment": "bottom",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "And I'm like a footer!"
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
			"type": "Container",
			"style": "good",
			"bleed": true,
			"items": [
				{
					"type": "TextBlock",
					"text": "This Container bleeds into its parent padding for a nice visual appearance!",
					"wrap": true
				}
			]
		},
		{
			"type": "Container",
			"style": "warning",
			"items": [
				{
					"type": "TextBlock",
					"text": "This Container is just a plain ol' container, it looks nice too though!",
					"wrap": true
				}
			]
		}
	]
}
```

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
            "type": "Container",
            "minHeight": "150px",
            "backgroundImage": "https://adaptivecards.io/content/AlkiBeach.jpg",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "What a beautiful background"
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "They can even repeat a bunch of different ways..."
        },
        {
            "type": "Container",
            "minHeight": "100px",
            "backgroundImage": {
                "url": "https://adaptivecards.io/content/uparrow.png",
                "fillMode": "Repeat"
            }
        },
        {
            "type": "Container",
            "backgroundImage": {
                "url": "https://adaptivecards.io/content/uparrow.png",
                "fillMode": "RepeatHorizontally",
                "verticalAlignment": "Center"
            }
        },
        {
            "type": "Container",
            "minHeight": "100px",
            "backgroundImage": {
                "url": "https://adaptivecards.io/content/uparrow.png",
                "fillMode": "RepeatVertically",
                "horizontalAlignment": "Center"
            }
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

### minHeight

Specifies the minimum height of the container in pixels, like `"80px"`.

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
			"type": "Container",
			"minHeight": "100px",
			"style": "emphasis",
			"items": [
				{
					"type": "TextBlock",
					"wrap": true,
					"text": "This textblock is inside a container with a min height of 100px"
				}
			]
		}
	]
}
```

### rtl?

When `true` content in this container should be presented right to left. When 'false' content in this container should be presented left to right. When unset, layout direction will inherit from the parent container or column. If unset in all ancestors, the default platform behavior will apply.

  * **Type**: `boolean?`
  * **Version**: 1.5
  * **Required**: No

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

