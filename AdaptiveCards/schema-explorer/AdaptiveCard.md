# AdaptiveCard Element

This page documents the `AdaptiveCard` element, which is the root element of an Adaptive Card.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](https://docs.microsoft.com/en-us/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](https://docs.microsoft.com/en-us/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## AdaptiveCard

An Adaptive Card, containing a free-form body of card elements, and an optional set of actions.

### AdaptiveCard Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;AdaptiveCard&quot;` | Yes | Must be `&quot;AdaptiveCard&quot;`. | 1.0 |
| **version** | `string` | Yes | Schema version that this card requires. If a client is **lower** than this version, the `fallbackText` will be rendered. NOTE: Version is not required for cards within an `Action.ShowCard`. However, it *is* required for the top-level card. | 1.0 |
| **refresh** | `Refresh` | No | Defines how the card can be refreshed by making a request to the target Bot. | 1.4 |
| **authentication** | `Authentication` | No | Defines authentication information to enable on-behalf-of single sign on or just-in-time OAuth. | 1.4 |
| **body** | `Element[]` | No | The card elements to show in the primary card region. | 1.0 |
| **actions** | `Action[]` | No | The Actions to show in the card’s action bar. | 1.0 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the card is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **fallbackText** | `string` | No | Text shown when the client doesn’t support the version specified (may contain markdown). | 1.0 |
| **backgroundImage** | `BackgroundImage`, `uri` | No | Specifies the background image of the card. | 1.2, 1.0 |
| **metadata** | `Metadata` | No | Defines various metadata properties typically not used for rendering the card | 1.6 |
| **minHeight** | `string` | No | Specifies the minimum height of the card. | 1.2 |
| **rtl** | `boolean?` | No | When `true` content in this Adaptive Card should be presented right to left. When ‘false’ content in this Adaptive Card should be presented left to right. If unset, the default platform behavior will apply. | 1.5 |
| **speak** | `string` | No | Specifies what should be spoken for this entire card. This is simple text or SSML fragment. | 1.0 |
| **lang** | `string` | No | The 2-letter ISO-639-1 language used in the card. Used to localize any date/time functions. | 1.0 |
| **verticalContentAlignment** | `VerticalContentAlignment` | No | Defines how the content should be aligned vertically within the container. Only relevant for fixed-height cards, or cards with a `minHeight` specified. | 1.1 |
| **$schema** | `uri` | No | The Adaptive Card schema. | 1.0 |

-----

## Example

### Basic AdaptiveCard Example (JSON)

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
					"text": "Publish Adaptive Card schema",
					"weight": "bolder",
					"size": "medium"
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
									"url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
									"altText": "Matt Hidinger",
									"size": "small",
									"style": "person"
								}
							]
						},
						{
							"type": "Column",
							"width": "stretch",
							"items": [
								{
									"type": "TextBlock",
									"text": "Matt Hidinger",
									"weight": "bolder",
									"wrap": true
								},
								{
									"type": "TextBlock",
									"spacing": "none",
									"text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
									"isSubtle": true,
									"wrap": true
								}
							]
						}
					]
				}
			]
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "TextBlock",
					"text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
					"wrap": true
				},
				{
					"type": "FactSet",
					"facts": [
						{
							"title": "Board:",
							"value": "Adaptive Card"
						},
						{
							"title": "List:",
							"value": "Backlog"
						},
						{
							"title": "Assigned to:",
							"value": "Matt Hidinger"
						},
						{
							"title": "Due date:",
							"value": "Not set"
						}
					]
				}
			]
		}
	],
	"actions": [
		{
			"type": "Action.ShowCard",
			"title": "Comment",
			"card": {
				"type": "AdaptiveCard",
				"body": [
					{
						"type": "Input.Text",
						"id": "comment",
						"isMultiline": true,
						"placeholder": "Enter your comment"
					}
				],
				"actions": [
					{
						"type": "Action.Submit",
						"title": "OK"
					}
				]
			}
		},
		{
			"type": "Action.OpenUrl",
			"title": "View",
			"url": "https://adaptivecards.io"
		}
	]
}
```

## Properties

### version

Schema version that this card requires. If a client is **lower** than this version, the `fallbackText` will be rendered. NOTE: Version is not required for cards within an `Action.ShowCard`. However, it *is* required for the top-level card.

  * **Type**: `string`
  * **Required**: No

### refresh

Defines how the card can be refreshed by making a request to the target Bot.

  * **Type**: `Refresh`
  * **Version**: 1.4
  * **Required**: No
  * **Allowed values**:
      * `Refresh`

#### Refresh Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"version": "1.3",
	"refresh": {
		"action": {
			"type": "Action.Execute",
			"verb": "refreshCard"
		},
		"userIds": [
			"user1",
			"user2"
		]
	},
	"body": [
		{
			"type": "TextBlock",
			"text": "This is a card that will be refreshed."
		}
	]
}
```

### authentication

Defines authentication information to enable on-behalf-of single sign on or just-in-time OAuth.

  * **Type**: `Authentication`
  * **Version**: 1.4
  * **Required**: No
  * **Allowed values**:
      * `Authentication`

#### Authentication Example (JSON)

```json
{
	"type": "AdaptiveCard",
	"version": "1.4",
	"authentication": {
		"connectionName": "myConnection",
		"text": "Please Authenticate your account",
		"tokenExchangeResource": {
			"id": "myTokenId",
			"providerId": "myProviderId",
			"uri": "https: //mytoken.exchange/resource"
		},
		"buttons": [
			{
				"type": "signin",
				"title": "Click here to Sign In!"
			}
		]
	},
	"body": [
		{
			"type": "TextBlock",
			"text": "This is a card that has authentication"
		}
	]
}
```

### body

The card elements to show in the primary card region.

  * **Type**: `Element[]`
  * **Required**: No
  * **Allowed values**:
      * `ActionSet`
      * `ColumnSet`
      * `Container`
      * `FactSet`
      * `Image`
      * `ImageSet`
      * `Input.ChoiceSet`
      * `Input.Date`
      * `Input.Number`
      * `Input.Text`
      * `Input.Time`
      * `Input.Toggle`
      * `Media`
      * `RichTextBlock`
      * `Table`
      * `TextBlock`

### actions

The Actions to show in the card's action bar.

  * **Type**: `Action[]`
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`
      * `Action.OpenUrl`
      * `Action.ShowCard`
      * `Action.Submit`
      * `Action.ToggleVisibility`

### selectAction

An Action that will be invoked when the card is tapped or selected. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`
      * `Action.OpenUrl`
      * `Action.Submit`
      * `Action.ToggleVisibility`

### fallbackText

Text shown when the client doesn't support the version specified (may contain markdown).

  * **Type**: `string`
  * **Required**: No

### backgroundImage

Specifies the background image of the card.

  * **Type**: `BackgroundImage`, `uri`
  * **Version**: 1.2, 1.0
  * **Required**: No
  * **Allowed values**:
      * `BackgroundImage`
      * `uri`

### metadata

Defines various metadata properties typically not used for rendering the card

  * **Type**: `Metadata`
  * **Version**: 1.6
  * **Required**: No
  * **Allowed values**:
      * `Metadata`

### minHeight

Specifies the minimum height of the card.

  * **Type**: `string`
  * **Version**: 1.2
  * **Required**: No

#### minHeight Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.2",
	"minHeight": "100px",
	"body": [
		{
			"type": "TextBlock",
			"wrap": true,
			"text": "This card has a minHeight of 100px"
		}
	]
}
```

### rtl

When `true` content in this Adaptive Card should be presented right to left. When 'false' content in this Adaptive Card should be presented left to right. If unset, the default platform behavior will apply.

  * **Type**: `boolean?`
  * **Version**: 1.5
  * **Required**: No

#### rtl Example (JSON)

```json
{
  "type": "AdaptiveCard",
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.5",
  "rtl": true,
  "body": [
    {
      "type": "TextBlock",
      "text": "هذه كتلة نص",
      "wrap": true
    },
    {
      "type": "TextBlock",
      "text": "זהו בלוק טקסט",
      "wrap": true
    },
    {
      "type": "TextBlock",
      "text": "This is a text block",
      "wrap": true
    }
  ]
}
```

### speak

Specifies what should be spoken for this entire card. This is simple text or SSML fragment.

  * **Type**: `string`
  * **Required**: No

### lang

The 2-letter ISO-639-1 language used in the card. Used to localize any date/time functions.

  * **Type**: `string`
  * **Required**: No

### verticalContentAlignment

Defines how the content should be aligned vertically within the container. Only relevant for fixed-height cards, or cards with a `minHeight` specified.

  * **Type**: `VerticalContentAlignment`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"top"`
      * `"center"`
      * `"bottom"`

### $schema

The Adaptive Card schema.

  * **Type**: `uri`
  * **Required**: No

