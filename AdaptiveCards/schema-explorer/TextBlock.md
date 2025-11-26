# TextBlock Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page provides documentation for the `TextBlock` element in the Adaptive Cards schema.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a **[label](https://docs.microsoft.com/en-us/adaptive-cards/authoring-cards/input-validation#labels)** property on Inputs to improve accessibility. If the **[Host app you are targeting](https://docs.microsoft.com/en-us/adaptive-cards/resources/partners)** supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## TextBlock

Displays text, allowing control over font sizes, weight, and color.

### TextBlock Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;TextBlock&quot;` | Yes | Must be `&quot;TextBlock&quot;`. | 1.0 |
| **text** | `string` | Yes | Text to display. A subset of markdown is supported ([https://aka.ms/ACTextFeatures](https://aka.ms/ACTextFeatures)) | 1.0 |
| **color** | `Colors?` | No | Controls the color of `TextBlock` elements. | 1.0 |
| **fontType** | `FontType?` | No | Type of font to use for rendering | 1.2 |
| **horizontalAlignment** | `HorizontalAlignment?` | No | Controls the horizontal text alignment. When not specified, the value of horizontalAlignment is inherited from the parent container. If no parent container has horizontalAlignment set, it defaults to Left. | 1.0 |
| **isSubtle** | `boolean?` | No | If `true`, displays text slightly toned down to appear less prominent. | 1.0 |
| **maxLines** | `number` | No | Specifies the maximum number of lines to display. | 1.0 |
| **size** | `FontSize?` | No | Controls size of text. | 1.0 |
| **weight** | `FontWeight?` | No | Controls the weight of `TextBlock` elements. | 1.0 |
| **wrap** | `boolean` | No | If `true`, allow text to wrap. Otherwise, text is clipped. | 1.0 |
| **style** | `TextBlockStyle?` | No, default: `&quot;default&quot;` | The style of this TextBlock for accessibility purposes. | 1.5 |

### Inherited properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **fallback** | `Element`, `FallbackOption` | No | Describes what to do when an unknown element is encountered or the requires of this or any children can’t be met. | 1.2 |
| **height** | `BlockElementHeight` | No | Specifies the height of the element. | 1.1 |
| **separator** | `boolean` | No | When `true`, draw a separating line at the top of the element. | 1.0 |
| **spacing** | `Spacing` | No | Controls the amount of spacing between this element and the preceding element. | 1.0 |
| **id** | `string` | No | A unique identifier associated with the item. | 1.0 |
| **isVisible** | `boolean` | No, default: `true` | If `false`, this item will be removed from the visual tree. | 1.2 |
| **requires** | `Dictionary<string>` | No | A series of key/value pairs indicating features that the item requires with corresponding minimum version. When a feature is missing or of insufficient version, fallback is triggered. | 1.2 |

-----

## Example

### Basic TextBlock Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "This is some text",
			"size": "large"
		},
		{
			"type": "TextBlock",
			"text": "It doesn't wrap by default",
			"weight": "bolder"
		},
		{
			"type": "TextBlock",
			"text": "So set **wrap** to true if you plan on showing a paragraph of text",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "You can also use **maxLines** to prevent it from getting out of hand",
			"wrap": true,
			"maxLines": 2
		},
		{
			"type": "TextBlock",
			"text": "You can even draw attention to certain text with color",
			"wrap": true,
			"color": "attention"
		}
	]
}
```

## Properties

### text

Text to display. A subset of markdown is supported ([https://aka.ms/ACTextFeatures](https://aka.ms/ACTextFeatures))

  * **Type**: `string`
  * **Required**: Yes

### color

Controls the color of `TextBlock` elements.

  * **Type**: `Colors?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"dark"`
      * `"light"`
      * `"accent"`
      * `"good"`
      * `"warning"`
      * `"attention"`

#### Color Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
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
}
```

### fontType

Type of font to use for rendering

  * **Type**: `FontType?`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"monospace"`

#### FontType Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.2",
	"body": [
		{
			"type": "TextBlock",
			"text": "Font type not set."
		},
		{
			"type": "TextBlock",
			"text": "Font type set to *default*.",
			"fontType": "default"
		},
		{
			"type": "TextBlock",
			"text": "Font type set to *monospace*.",
			"fontType": "monospace"
		}
	]
}
```

### horizontalAlignment

Controls the horizontal text alignment. When not specified, the value of horizontalAlignment is inherited from the parent container. If no parent container has horizontalAlignment set, it defaults to Left.

  * **Type**: `HorizontalAlignment?`
  * **Required**: No
  * **Allowed values**:
      * `"left"`
      * `"center"`
      * `"right"`

#### HorizontalAlignment Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "**horizontalAlignment:left**",
			"horizontalAlignment": "left"
		},
		{
			"type": "TextBlock",
			"text": "**horizontalAlignment:center**",
			"horizontalAlignment": "center"
		},
		{
			"type": "TextBlock",
			"text": "**horizontalAlignment:right**",
			"horizontalAlignment": "right"
		}
	]
}
```

### isSubtle

If `true`, displays text slightly toned down to appear less prominent.

  * **Type**: `boolean?`
  * **Required**: No

#### isSubtle Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "isSubtle:false",
			"isSubtle": false
		},
		{
			"type": "TextBlock",
			"text": "isSubtle:true",
			"isSubtle": true
		}
	]
}
```

### maxLines

Specifies the maximum number of lines to display.

  * **Type**: `number`
  * **Required**: No

#### maxLines Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
			"wrap": true,
			"maxLines": 1
		},
		{
			"type": "TextBlock",
			"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
			"wrap": true,
			"maxLines": 2
		}
	]
}
```

### size

Controls size of text.

  * **Type**: `FontSize?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"small"`
      * `"medium"`
      * `"large"`
      * `"extraLarge"`

#### Size Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "size:default"
		},
		{
			"type": "TextBlock",
			"text": "size:small",
			"size": "small"
		},
		{
			"type": "TextBlock",
			"text": "size:default",
			"size": "default"
		},
		{
			"type": "TextBlock",
			"text": "size:medium",
			"size": "medium"
		},
		{
			"type": "TextBlock",
			"text": "size:large",
			"size": "large"
		},
		{
			"type": "TextBlock",
			"text": "size:extraLarge",
			"size": "extraLarge"
		}
	]
}
```

### weight

Controls the weight of `TextBlock` elements.

  * **Type**: `FontWeight?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"lighter"`
      * `"bolder"`

#### Weight Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "weight: lighter",
			"weight": "lighter"
		},
		{
			"type": "TextBlock",
			"text": "weight: default",
			"weight": "default"
		},
		{
			"type": "TextBlock",
			"text": "weight: bolder",
			"weight": "bolder"
		}
	]
}
```

### wrap

If `true`, allow text to wrap. Otherwise, text is clipped.

  * **Type**: `boolean`
  * **Required**: No

#### Wrap Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "TextBlock",
			"text": "**wrap: false** Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat",
			"wrap": false
		},
		{
			"type": "TextBlock",
			"text": "**wrap: true** Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
			"wrap": true
		}
	]
}
```

### style

The style of this TextBlock for accessibility purposes.

  * **Type**: `TextBlockStyle?`
  * **Version**: 1.5
  * **Required**: No, default: `"default"`
  * **Allowed values**:
      * `"default"`: This is the default style which provides no special styling or behavior.
      * `"heading"`: The `TextBlock` is a heading. This will apply the heading styling defaults and mark the `TextBlock` as a heading for accessiblity.

#### Style Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "TextBlock",
			"text": "Style set to heading",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Style set to heading, color set to good",
			"style": "heading",
			"color": "good",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Style set to default",
			"style": "default",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "Style unset",
			"wrap": true
		}
	]
}
```

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
