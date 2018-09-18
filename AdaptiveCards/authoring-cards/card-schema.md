---
title: Card Schema
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
---

# Card Schema

Cards
   * [`AdaptiveCard`](#schema-adaptivecard) - Root element in an Adaptive Card.

Card Elements
   * [`TextBlock`](#schema-textblock) - Displays text, allowing control over font sizes, weight, and color.
   * [`Image`](#schema-image) - Displays an image.
   * [`Media`](#schema-media) - Displays a media player for audio or video content.
   * [`MediaSource`](#schema-mediasource) - Defines a source for a Media element

Containers
   * [`Container`](#schema-container) - Containers group items together.
   * [`ColumnSet`](#schema-columnset) - ColumnSet divides a region into Columns, allowing elements to sit side-by-side.
   * [`Column`](#schema-column) - Defines a container that is part of a ColumnSet.
   * [`FactSet`](#schema-factset) - The FactSet element displays a series of facts (i.e. name/value pairs) in a tabular form.
   * [`Fact`](#schema-fact) - Describes a Fact in a FactSet as a key/value pair.
   * [`ImageSet`](#schema-imageset) - The ImageSet displays a collection of Images similar to a gallery.

Actions
   * [`Action.OpenUrl`](#schema-action.openurl) - When invoked, show the given url either by launching it in an external web browser or showing in-situ with embedded web browser.
   * [`Action.Submit`](#schema-action.submit) - Gathers input fields, merges with optional data field, and sends an event to the client. It is up to the client to determine how this data is processed. For example: With BotFramework bots, the client would send an activity through the messaging medium to the bot.
   * [`Action.ShowCard`](#schema-action.showcard) - Defines an AdaptiveCard which is shown to the user when the button or link is clicked.

Inputs
   * [`Input.Text`](#schema-input.text) - Lets a user enter text.
   * [`Input.Number`](#schema-input.number) - Allows a user to enter a number.
   * [`Input.Date`](#schema-input.date) - Lets a user choose a date.
   * [`Input.Time`](#schema-input.time) - Lets a user select a time.
   * [`Input.Toggle`](#schema-input.toggle) - Lets a user choose between two options.
   * [`Input.ChoiceSet`](#schema-input.choiceset) - Allows a user to input a Choice.
   * [`Input.Choice`](#schema-input.choice) - Describes a choice for use in a ChoiceSet.

# Cards

<a name="schema-adaptivecard"></a>
## AdaptiveCard

Root element in an Adaptive Card.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"AdaptiveCard"`|Yes|Must be `"AdaptiveCard"`.|1.0
|**actions**|`Action[]`| No|The Actions to show in the card's action bar.|1.0
|**body**|`array[]`| No|The card elements to show in the primary card region.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the card is tapped or selected. `Action.ShowCard` is not supported.|1.0
|**version**|`string`|Yes|Schema version that this card requires. If a client is **lower** than this version, the `fallbackText` will be rendered.|1.0
|**fallbackText**|`string`| No|Text shown when the client doesn't support the version specified (may contain markdown).|1.0
|**backgroundImage**|`string`| No|An image to use as the background of the card.|1.0
|**speak**|`string`| No|Specifies what should be spoken for this entire card. This is simple text or SSML fragment.|1.0
|**lang**|`string`| No|The 2-letter ISO-639-1 language used in the card. Used to localize any date/time functions.|1.0


# Card Elements

<a name="schema-textblock"></a>
## TextBlock

Displays text, allowing control over font sizes, weight, and color.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**color**|`string`| No|Controls the color of `TextBlock` elements.|1.0
|**horizontalAlignment**|`string`| No, default: `"left"`|Controls how elements are horizontally positioned within their container.|1.0
|**isSubtle**|`boolean`| No, default: `false`|If `true`, displays text slightly toned down to appear less prominent.|1.0
|**maxLines**|`number`| No|Specifies the maximum number of lines to display.|1.0
|**size**|`string`| No|Controls size of text.|1.0
|**text**|`string`|Yes|Text to display.|1.0
|**type**|`"TextBlock"`|Yes|Must be `"TextBlock"`.|1.0
|**weight**|`string`| No|Controls the weight of `TextBlock` elements.|1.0
|**wrap**|`boolean`| No, default: `false`|If `true`, allow text to wrap. Otherwise, text is clipped.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-image"></a>
## Image

Displays an image.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**altText**|`string`| No|Alternate text describing the image.|1.0
|**horizontalAlignment**|`string`| No, default: `"left"`|Controls how elements are horizontally positioned within their container.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the `Image` is tapped or selected. `Action.ShowCard` is not supported.|1.0
|**size**|`string`| No, default: `"auto"`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify `"auto"` for true image dimension, or `"stretch"` to force it to fill the container.|1.0
|**style**|`string`| No|Controls how this `Image` is displayed.|1.0
|**type**|`"Image"`|Yes|Must be `"Image"`.|1.0
|**url**|`string`|Yes|The URL to the image.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-media"></a>
## Media

Displays a media player for audio or video content.

#### Introduced in version 1.1

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Media"`|Yes|Must be `"Media"`.|1.1
|**sources**|`object` `[]`| No|Array of media sources to attempt to play.|1.1
|**poster**|`string`| No|URL of an image to display before playing.|1.1
|**altText**|`string`| No|Alternate text describing the audio or video.|1.1
|**id**|`string`| No|A unique identifier associated with the element.|1.1
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.1
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.1


<a name="schema-mediasource"></a>
## MediaSource

Defines a source for a Media element

#### Introduced in version 1.1

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**mimeType**|`string`|Yes|Mime type of associated media (e.g. `"video/mp4"`).|1.1
|**url**|`string`|Yes|URL to media.|1.1


# Containers

<a name="schema-container"></a>
## Container

Containers group items together.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Container"`|Yes|Must be `"Container"`.|1.0
|**items**|`array[]`|Yes|The card elements to render inside the `Container`.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the `Container` is tapped or selected. `Action.ShowCard` is not supported.|1.0
|**style**|`string`| No|Style hint for `Container`.|1.0
|**verticalContentAlignment**|`string`| No, default: `"top"`|Defines how the content should be aligned vertically within the container.|1.1
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-columnset"></a>
## ColumnSet

ColumnSet divides a region into Columns, allowing elements to sit side-by-side.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**columns**|`Column[]`| No|The array of `Columns` to divide the region into.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the `ColumnSet` is tapped or selected. `Action.ShowCard` is not supported.|1.0
|**type**|`"ColumnSet"`|Yes|Must be `"ColumnSet"`.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-column"></a>
## Column

Defines a container that is part of a ColumnSet.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**items**|`array[]`|Yes|The card elements to include in the `Column`.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the `Column` is tapped or selected. `Action.ShowCard` is not supported.|1.0
|**style**|`string`| No|Style hint for `Column`.|1.0
|**width**|`string,number`| No|`"auto"`, `"stretch"`, or a number representing relative width of the column in the column group.|1.0
|**type**|`"Column"`| No|Must be `"Column"`.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-factset"></a>
## FactSet

The FactSet element displays a series of facts (i.e. name/value pairs) in a tabular form.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**facts**|`Fact[]`|Yes|The array of `Fact`s.|1.0
|**type**|`"FactSet"`|Yes|Must be `"FactSet"`.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-fact"></a>
## Fact

Describes a Fact in a FactSet as a key/value pair.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Fact"`| No|&nbsp;|1.0
|**title**|`string`|Yes|The title of the fact.|1.0
|**value**|`string`|Yes|The value of the fact.|1.0


<a name="schema-imageset"></a>
## ImageSet

The ImageSet displays a collection of Images similar to a gallery.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**images**|`Image[]`|Yes|The array of `Image` elements to show.|1.0
|**imageSize**|`string`| No, default: `"auto"`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify `"auto"` for true image dimension, or `"stretch"` to force it to fill the container.|1.0
|**type**|`"ImageSet"`|Yes|Must be `"ImageSet"`.|1.0
|**id**|`string`| No|A unique identifier associated with the element.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


# Actions

<a name="schema-action.openurl"></a>
## Action.OpenUrl

When invoked, show the given url either by launching it in an external web browser or showing in-situ with embedded web browser.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.OpenUrl"`|Yes|Must be `"Action.OpenUrl"`.|1.0
|**title**|`string`|Yes|Label for button or link that represents this action.|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**url**|`string`|Yes|The URL to open.|1.0


<a name="schema-action.submit"></a>
## Action.Submit

Gathers input fields, merges with optional data field, and sends an event to the client. It is up to the client to determine how this data is processed. For example: With BotFramework bots, the client would send an activity through the messaging medium to the bot.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.Submit"`|Yes|Must be `"Action.Submit"`.|1.0
|**title**|`string`|Yes|Label for button or link that represents this action.|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**data**|`string,object`| No|Initial data that input fields will be combined with. These are essentially 'hidden' properties.|1.0


<a name="schema-action.showcard"></a>
## Action.ShowCard

Defines an AdaptiveCard which is shown to the user when the button or link is clicked.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.ShowCard"`|Yes|Must be `"Action.ShowCard"`.|1.0
|**title**|`string`|Yes|Label for button or link that represents this action.|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**card**|`object`|Yes|Root element in an Adaptive Card.|1.0


# Inputs

<a name="schema-input.text"></a>
## Input.Text

Lets a user enter text.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**isMultiline**|`boolean`| No, default: `false`|If `true`, allow multiple lines of input.|1.0
|**maxLength**|`number`| No|Hint of maximum length characters to collect (may be ignored by some clients).|1.0
|**placeholder**|`string`| No|Description of the input desired. Displayed when no text has been input.|1.0
|**style**|`string`| No, default: `"text"`|Style hint for `Input.Text`.|1.0
|**type**|`"Input.Text"`|Yes|Must be `"Input.Text"`.|1.0
|**value**|`string`| No|The initial value for this field.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.number"></a>
## Input.Number

Allows a user to enter a number.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**max**|`number`| No|Hint of maximum value (may be ignored by some clients).|1.0
|**min**|`number`| No|Hint of minimum value (may be ignored by some clients).|1.0
|**placeholder**|`string`| No|Description of the input desired. Displayed when no selection has been made.|1.0
|**type**|`"Input.Number"`|Yes|Must be `"Input.Number"`.|1.0
|**value**|`number`| No|Initial value for this field.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.date"></a>
## Input.Date

Lets a user choose a date.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**max**|`string`| No|Hint of maximum value expressed in ISO-8601 format (may be ignored by some clients).|1.0
|**min**|`string`| No|Hint of minimum value expressed in ISO-8601 format (may be ignored by some clients).|1.0
|**placeholder**|`string`| No|Description of the input desired. Displayed when no selection has been made.|1.0
|**type**|`"Input.Date"`|Yes|Must be `"Input.Date"`.|1.0
|**value**|`string`| No|The initial value for this field expressed in ISO-8601 format.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.time"></a>
## Input.Time

Lets a user select a time.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**max**|`string`| No|Hint of maximum value (may be ignored by some clients).|1.0
|**min**|`string`| No|Hint of minimum value (may be ignored by some clients).|1.0
|**placeholder**|`string`| No|Description of the input desired. Displayed when no time has been selected.|1.0
|**type**|`"Input.Time"`|Yes|Must be `"Input.Time"`.|1.0
|**value**|`string`| No|The initial value for this field expressed in ISO-8601 format.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.toggle"></a>
## Input.Toggle

Lets a user choose between two options.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**title**|`string`|Yes|Title for the toggle|1.0
|**type**|`"Input.Toggle"`|Yes|Input.Toggle|1.0
|**value**|`string`| No, default: `"false"`|The current selected value. If the item is selected that "valueOn" will be used, otherwise "valueOff"|1.0
|**valueOff**|`string`| No, default: `"false"`|The value when toggle is off|1.0
|**valueOn**|`string`| No, default: `"true"`|The value when toggle is on|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.choiceset"></a>
## Input.ChoiceSet

Allows a user to input a Choice.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**choices**|`Input.Choice[]`|Yes|`Choice` options.|1.0
|**id**|`string`|Yes|Unique identifier for the value. Used to identify collected input when the Submit action is performed.|1.0
|**isMultiSelect**|`boolean`| No, default: `false`|Allow multiple choices to be selected.|1.0
|**style**|`string`| No, default: `"compact"`|Style hint for `Input.ChoiceSet`.|1.0
|**type**|`"Input.ChoiceSet"`|Yes|Must be `"Input.ChoiceInput"`.|1.0
|**value**|`string`| No|The initial choice (or set of choices) that should be selected. For multi-select, specify a comma-separated string of values.|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the preceding element.|1.0
|**separator**|`boolean`| No, default: `false`|When `true`, draw a separating line at the top of the element.|1.0


<a name="schema-input.choice"></a>
## Input.Choice

Describes a choice for use in a ChoiceSet.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Input.Choice"`| No|&nbsp;|1.0
|**title**|`string`|Yes|Text to display.|1.0
|**value**|`string`|Yes|The raw value for the choice. **NOTE:** do not use a `,` in the value, since a `ChoiceSet` with `isMultiSelect` set to `true` returns a comma-delimited string of choice values.|1.0
