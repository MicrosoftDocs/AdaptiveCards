---
title:  Table Element
author: luywang
description: This page provides documentation for the `Table` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Table Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


This page documents the **Table** element, which provides a way to display data in a tabular form.

**Introduced in version 1.5**

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Table

Provides a way to display data in a tabular form.

**Introduced in version 1.5**

### Table Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;Table&quot;` | Yes | Must be `&quot;Table&quot;`. | 1.5 |
| **columns** | `TableColumnDefinition[]` | No | Defines the number of columns in the table, their sizes, and more. | 1.5 |
| **rows** | `TableRow[]` | No | Defines the rows of the table. | 1.5 |
| **firstRowAsHeader** | `boolean` | No, default: `true` | Specifies whether the first row of the table should be treated as a header row, and be announced as such by accessibility software. | 1.5 |
| **showGridLines** | `boolean` | No, default: `true` | Specifies whether grid lines should be displayed. | 1.5 |
| **gridStyle** | `ContainerStyle?` | No, default: `&quot;default&quot;` | Defines the style of the grid. This property currently only controls the grid’s color. | 1.5 |
| **horizontalCellContentAlignment** | `HorizontalAlignment?` | No | Controls how the content of all cells is horizontally aligned by default. When not specified, horizontal alignment is defined on a per-cell basis. | 1.5 |
| **verticalCellContentAlignment** | `VerticalAlignment?` | No | Controls how the content of all cells is vertically aligned by default. When not specified, vertical alignment is defined on a per-cell basis. | 1.5 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.5 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.5 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.5 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary&lt;string&gt;` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic Table Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "Table",
			"gridStyle": "accent",
			"firstRowAsHeaders": true,
			"columns": [
				{
					"width": 1
				},
				{
					"width": 1
				},
				{
					"width": 3
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Name",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Type",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Description",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						}
					],
					"style": "accent"
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"style": "good",
							"items": [
								{
									"type": "TextBlock",
									"text": "columns",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "warning",
							"items": [
								{
									"type": "TextBlock",
									"text": "ColumnDefinition[]",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "accent",
							"items": [
								{
									"type": "TextBlock",
									"text": "Defines the table's columns (number of columns, and column sizes).",
									"wrap": true
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"style": "good",
							"items": [
								{
									"type": "TextBlock",
									"text": "rows",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "accent",
							"items": [
								{
									"type": "TextBlock",
									"text": "TableRow[]",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "attention",
							"items": [
								{
									"type": "TextBlock",
									"text": "Defines the rows of the Table, each being a collection of cells. Rows are not required, which allows empty Tables to be generated via templating without breaking the rendering of the whole card.",
									"wrap": true
								}
							]
						}
					]
				}
			]
		},
		{
			"type": "Table",
			"gridStyle": "accent",
			"firstRowAsHeaders": true,
			"showGridLines" : false,
			"columns": [
				{
					"width": 1
				},
				{
					"width": 1
				},
				{
					"width": 3
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Name",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Type",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Description",
									"wrap": true,
									"weight": "Bolder"
								}
							]
						}
					],
					"style": "accent"
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"style": "good",
							"items": [
								{
									"type": "TextBlock",
									"text": "columns",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "warning",
							"items": [
								{
									"type": "TextBlock",
									"text": "ColumnDefinition[]",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "accent",
							"items": [
								{
									"type": "TextBlock",
									"text": "Defines the table's columns (number of columns, and column sizes).",
									"wrap": true
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"style": "good",
							"items": [
								{
									"type": "TextBlock",
									"text": "rows",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "accent",
							"items": [
								{
									"type": "TextBlock",
									"text": "TableRow[]",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"style": "attention",
							"items": [
								{
									"type": "TextBlock",
									"text": "Defines the rows of the Table, each being a collection of cells. Rows are not required, which allows empty Tables to be generated via templating without breaking the rendering of the whole card.",
									"wrap": true
								}
							]
						}
					]
				}
			],
			"showGridLines": false
		}
	]
}
```

## Properties

### columns

Defines the number of columns in the table, their sizes, and more.

  * **Type**: `TableColumnDefinition[]`
  * **Required**: No
  * **Allowed values**:
      * `TableColumnDefinition`

### rows

Defines the rows of the table.

  * **Type**: `TableRow[]`
  * **Required**: No
  * **Allowed values**:
      * `TableRow`

### firstRowAsHeader

Specifies whether the first row of the table should be treated as a header row, and be announced as such by accessibility software.

  * **Type**: `boolean`
  * **Required**: No, default: `true`

### showGridLines

Specifies whether grid lines should be displayed.

  * **Type**: `boolean`
  * **Required**: No, default: `true`

#### showGridLines Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Table with gridlines",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Table",
			"columns": [
				{
					"width": 1
				},
				{
					"width": 1
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "showGridLines value",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Behavior",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "true",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Cells are separated by 1px width gridlines",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "false",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Cells are separated by the cell spacing value configued in hostconfig",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				}
			]
		},
		{
			"type": "TextBlock",
			"text": "Table without gridlines",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "Table",
			"columns": [
				{
					"width": 1
				},
				{
					"width": 1
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "showGridLines value",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Behavior",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "true",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Cells are separated by 1px width gridlines",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "false",
									"wrap": true
								}
							],
							"style": "accent"
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Cells are separated by the cell spacing value configued in hostconfig",
									"wrap": true
								}
							],
							"style": "accent"
						}
					]
				}
			],
			"showGridLines": false
		}
	]
}
```

### gridStyle

Defines the style of the grid. This property currently only controls the grid's color.

  * **Type**: `ContainerStyle?`
  * **Required**: No, default: `"default"`
  * **Allowed values**:
      * `"default"`
      * `"emphasis"`
      * `"good"` (Added in version 1.2)
      * `"attention"` (Added in version 1.2)
      * `"warning"` (Added in version 1.2)
      * `"accent"` (Added in version 1.2)

#### gridStyle Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "GridStyle sets the color of the gridlines to the corresponding border color defined in host config",
			"wrap": true,
			"weight": "Bolder"
		},
		{
			"type": "Table",
			"verticalCellContentAlignment": "Center",
			"columns": [
				{
					"width": 1
				},
				{
					"width": 3
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "gridStyle Value",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Sample table",
									"wrap": true
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Good",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"gridStyle": "good"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Warning",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"gridStyle": "warning"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Attention",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"gridStyle": "attention"
								}
							]
						}
					]
				}
			],
			"showGridLines": false,
			"firstRowAsHeaders": true
		}
	]
}
```

### horizontalCellContentAlignment

Controls how the content of all cells is horizontally aligned by default. When not specified, horizontal alignment is defined on a per-cell basis.

  * **Type**: `HorizontalAlignment?`
  * **Required**: No
  * **Allowed values**:
      * `"left"`
      * `"center"`
      * `"right"`

#### horizontalCellContentAlignment Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "You can configure the horizontal alignment of table content with HorizontalCellContentAlignement",
			"wrap": true,
			"weight": "Bolder"
		},
		{
			"type": "Table",
			"columns": [
				{
					"width": 1
				},
				{
					"width": 3
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Left",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"horizontalCellContentAlignment": "Left"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Center",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"horizontalCellContentAlignment": "Center"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Right",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "Data",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"horizontalCellContentAlignment": "Right"
								}
							]
						}
					]
				}
			],
			"showGridLines": false,
			"firstRowAsHeaders": false,
			"verticalCellContentAlignment": "Center"
		}
	]
}
```

### verticalCellContentAlignment

Controls how the content of all cells is vertically aligned by default. When not specified, vertical alignment is defined on a per-cell basis.

  * **Type**: `VerticalAlignment?`
  * **Required**: No
  * **Allowed values**:
      * `"top"`
      * `"center"`
      * `"bottom"`

#### verticalCellContentAlignment Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "You can configure the vertical alignment of table content with VerticalCellContentAlignement",
			"wrap": true,
			"weight": "Bolder"
		},
		{
			"type": "Table",
			"columns": [
				{
					"width": 1
				},
				{
					"width": 3
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Top",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"verticalCellContentAlignment": "Top"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Center",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"verticalCellContentAlignment": "Center"
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Bottom",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "Table",
									"columns": [
										{
											"width": 1
										},
										{
											"width": 1
										}
									],
									"rows": [
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										},
										{
											"type": "TableRow",
											"cells": [
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A little bit of text.",
															"wrap": true
														}
													]
												},
												{
													"type": "TableCell",
													"items": [
														{
															"type": "TextBlock",
															"text": "A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. A lot of text. ",
															"wrap": true
														}
													]
												}
											]
										}
									],
									"firstRowAsHeaders": false,
									"verticalCellContentAlignment": "Bottom"
								}
							]
						}
					]
				}
			],
			"showGridLines": false,
			"firstRowAsHeaders": false,
			"verticalCellContentAlignment": "Center"
		}
	]
}
```

### fallback

Describes what to do when an unknown element is encountered or the requirements of this or any children can't be met.

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

