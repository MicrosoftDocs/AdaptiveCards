---
title: Card Schema
author: matthidinger
ms.author: mahiding
ms.date: 09/28/2017
ms.topic: reference
---

# Adaptive Card Schema

Cards
   * [`AdaptiveCard`](#schema-adaptivecard) - Card schema for an adaptive card

Card Elements
   * [`TextBlock`](#schema-textblock) - The TextBlock Item allows for the inclusion of text, with various font sizes, weight and color, in Adaptive Cards.
   * [`Image`](#schema-image) - The Image Item allows for the inclusion of images in an Adaptive Card.

Containers
   * [`Container`](#schema-container) - Containers group items together
   * [`ColumnSet`](#schema-columnset) - ColumnSet divides a region into Column's allowing elements to sit side-by-side
   * [`Column`](#schema-column) - Defines a container that is part of a ColumnSet
   * [`FactSet`](#schema-factset) - The FactSet Item makes it simple to display a series of facts (e.g. name/value pairs) in a tabular form.
   * [`Fact`](#schema-fact) - Describes a Fact in a FactSet as a key/value pair
   * [`ImageSet`](#schema-imageset) - The ImageSet allows for the inclusion of a collection images like a photogallery.

Actions
   * [`Action.OpenUrl`](#schema-action.openurl) - When Action.OpenUrl is invoked it will show the given url, either by launching it to an external web browser or showing in-situ with embedded web browser.
   * [`Action.Submit`](#schema-action.submit) - Submit action gathers up input fields, merges with optional data field and generates event to client asking for data to be submitted. It is up to the client to determine how that data is processed. For example: With BotFramework bots the client would send an activity through the messaging medium to the bot.
   * [`Action.ShowCard`](#schema-action.showcard) - Action.ShowCard defines an inline AdaptiveCard which is shown to the user when it is clicked.

Inputs
   * [`Input.Text`](#schema-input.text) - Input.Text collects text from the user,
   * [`Input.Number`](#schema-input.number) - Input.Number collects number from the user,
   * [`Input.Date`](#schema-input.date) - Input.Date collects Date from the user,
   * [`Input.Time`](#schema-input.time) - Input.Time collects Time from the user,
   * [`Input.Toggle`](#schema-input.toggle) - Input.Toggle collects a true/false response from the user
   * [`Input.ChoiceSet`](#schema-input.choiceset) - Shows an array of Choice objects
   * [`Input.Choice`](#schema-input.choice) - Describes a Choice input. The value should be a simple string without a ","

# Cards

<a name="schema-adaptivecard"></a>
## AdaptiveCard

Card schema for an adaptive card

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"AdaptiveCard"`|Yes|Must be AdaptiveCard|1.0
|**actions**|`Action[]`| No|The Actions to show in the card's action bar|1.0
|**body**|`array[]`| No|The Card Elements to show in the primary card region|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the card is tapped or selected. Action.ShowCard not supported|1.0
|**version**|`string`|Yes|Schema version that this card requires. If a client is lower than this version the fallbackText will be rendered.|1.0
|**fallbackText**|`string`| No|Text shown when the client doesn't support the version specified. This can be in markdown format.|1.0
|**backgroundImage**|`string`| No|An image to use as the background of the card|1.0
|**speak**|`string`| No|Specifies what should be spoken for this entire Item. This is simple text or SSML fragment|1.0
|**lang**|`string`| No|The 2-letter ISO-639-1 language used in the card. Used to localize any date/time functions|1.0


# Card Elements

<a name="schema-textblock"></a>
## TextBlock

The TextBlock Item allows for the inclusion of text, with various font sizes, weight and color, in Adaptive Cards.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**color**|`string`| No|Controls the color of TextBlock Items.|1.0
|**horizontalAlignment**|`string`| No|Controls how Items are horizontally positioned within their container.|1.0
|**isSubtle**|`boolean`| No|Indicates whether the color of the text should be slightly toned down to appear less prominent|1.0
|**maxLines**|`number`| No|When Wrap is true, you can specify the maximum number of lines to allow the textBlock to use.|1.0
|**size**|`string`| No|controls size of the text.|1.0
|**text**|`string`|Yes|The actual text to display|1.0
|**type**|`"TextBlock"`| No|Must be TextBlock|1.0
|**weight**|`string`| No|Controls the weight of TextBlock Items|1.0
|**wrap**|`boolean`| No, default: `false`|True if be is allowed to wrap|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-image"></a>
## Image

The Image Item allows for the inclusion of images in an Adaptive Card.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**altText**|`string`| No|Alternate text for the image for accessibility|1.0
|**horizontalAlignment**|`string`| No|Controls how Items are horizontally positioned within their container.|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the Image is tapped or selected. Action.ShowCard not supported|1.0
|**size**|`string`| No, default: `"auto"`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify "auto" for true image dimension or "stretch" to force it to fill the container|1.0
|**style**|`string`| No|Controls the way Images are displayed|1.0
|**type**|`"Image"`| No|Must be Image|1.0
|**url**|`string`|Yes|The URL to the image.|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


# Containers

<a name="schema-container"></a>
## Container

Containers group items together

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Container"`| No|Must be Container|1.0
|**items**|`array[]`|Yes|The Card Elements to render inside the Container|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the Container is tapped or selected. Action.ShowCard not supported|1.0
|**style**|`string`| No|Style hint for Container|1.0
|**verticalContentAlignment**|`string`| No, default: `"top"`|Defines how the content should be aligned vertically within the container. `top` indicates that content should be placed at the top. `center` and `bottom` function the same other than simply placing at center or at bottom.|1.1
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-columnset"></a>
## ColumnSet

ColumnSet divides a region into Column's allowing elements to sit side-by-side

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**columns**|`Column[]`| No|The array of Columns to divide the region into|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the ColumnSet is tapped or selected. Action.ShowCard not supported|1.0
|**type**|`"ColumnSet"`| No|Must be ColumnSet|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-column"></a>
## Column

Defines a container that is part of a ColumnSet

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**items**|`array[]`|Yes|The Card Elements to include in the Column|1.0
|**selectAction**|`object`| No|An Action that will be invoked when the Column is tapped or selected. Action.ShowCard not supported|1.0
|**style**|`string`| No|Style hint for Column|1.0
|**width**|`string,number`| No|"auto", "stretch", or a number representing relative width of the column in the column group|1.0
|**type**|`"Column"`| No|Must be Column|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-factset"></a>
## FactSet

The FactSet Item makes it simple to display a series of facts (e.g. name/value pairs) in a tabular form.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**facts**|`Fact[]`|Yes|The array of Facts|1.0
|**type**|`"FactSet"`| No|Must be FactSet|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-fact"></a>
## Fact

Describes a Fact in a FactSet as a key/value pair

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Fact"`| No|&nbsp;|1.0
|**title**|`string`|Yes|The title of the fact|1.0
|**value**|`string`|Yes|The value of the fact|1.0


<a name="schema-imageset"></a>
## ImageSet

The ImageSet allows for the inclusion of a collection images like a photogallery.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**images**|`Image[]`|Yes|The array of Image elements to show|1.0
|**imageSize**|`string`| No, default: `"auto"`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify "auto" for true image dimension or "stretch" to force it to fill the container|1.0
|**type**|`"ImageSet"`| No|Must be ImageSet|1.0
|**id**|`string`| No|A unique Id associated with the element|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


# Actions

<a name="schema-action.openurl"></a>
## Action.OpenUrl

When Action.OpenUrl is invoked it will show the given url, either by launching it to an external web browser or showing in-situ with embedded web browser.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.OpenUrl"`|Yes|Must be Action.OpenUrl|1.0
|**title**|`string`|Yes|Label for button or link that represents this action|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**url**|`string`|Yes|The URL to open|1.0


<a name="schema-action.submit"></a>
## Action.Submit

Submit action gathers up input fields, merges with optional data field and generates event to client asking for data to be submitted. It is up to the client to determine how that data is processed. For example: With BotFramework bots the client would send an activity through the messaging medium to the bot.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.Submit"`|Yes|Must be Action.Submit|1.0
|**title**|`string`|Yes|Label for button or link that represents this action|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**data**|`string,object`| No|initial data that input fields will be combined with. This is essentially 'hidden' properties|1.0


<a name="schema-action.showcard"></a>
## Action.ShowCard

Action.ShowCard defines an inline AdaptiveCard which is shown to the user when it is clicked.

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.ShowCard"`|Yes|Must be Action.ShowCard|1.0
|**title**|`string`|Yes|Label for button or link that represents this action|1.0
|**iconUrl**|`string`| No|Optional icon to be shown on the action in conjunction with the title|1.1
|**card**|`object`|Yes|Card schema for an adaptive card|1.0


# Inputs

<a name="schema-input.text"></a>
## Input.Text

Input.Text collects text from the user,

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is clicked)|1.0
|**isMultiline**|`boolean`| No|Do you want to allow multiple lines of input|1.0
|**maxLength**|`number`| No|hint of maximum length characters to collect (may be ignored by some clients)|1.0
|**placeholder**|`string`| No|Title Description of the input desired|1.0
|**style**|`string`| No|Style hint for Input.Text.|1.0
|**type**|`"Input.Text"`| No|Input.Text|1.0
|**value**|`string`| No|The initial value for a field|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.number"></a>
## Input.Number

Input.Number collects number from the user,

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is clicked)|1.0
|**max**|`number`| No|hint of maximum value (may be ignored by some clients)|1.0
|**min**|`number`| No|hint of minimum value (may be ignored by some clients)|1.0
|**placeholder**|`string`| No|Title Description of the input desired|1.0
|**type**|`"Input.Number"`| No|The type must be Input.Number|1.0
|**value**|`number`| No|The initial value for a field|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.date"></a>
## Input.Date

Input.Date collects Date from the user,

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is clicked)|1.0
|**max**|`string`| No|hint of maximum value expressed in ISO-8601 format (may be ignored by some clients)|1.0
|**min**|`string`| No|hint of minimum value expressed in ISO-8601 format (may be ignored by some clients)|1.0
|**placeholder**|`string`| No|Title Description of the input desired|1.0
|**type**|`"Input.Date"`| No|The type must be Input.Date|1.0
|**value**|`string`| No|The initial value for a field expressed in ISO-8601 format|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.time"></a>
## Input.Time

Input.Time collects Time from the user,

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is clicked)|1.0
|**max**|`string`| No|hint of maximum value (may be ignored by some clients)|1.0
|**min**|`string`| No|hint of minimum value (may be ignored by some clients)|1.0
|**placeholder**|`string`| No|Title Description of the input desired|1.0
|**type**|`"Input.Time"`| No|The type must be Input.Time|1.0
|**value**|`string`| No|The initial value for a field expressed in ISO-8601 format|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.toggle"></a>
## Input.Toggle

Input.Toggle collects a true/false response from the user

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is clicked)|1.0
|**title**|`string`|Yes|Title for the toggle|1.0
|**type**|`"Input.Toggle"`| No|Input.Toggle|1.0
|**value**|`string`| No, default: `"false"`|The current selected value. If the item is selected that `valueOn` will be used, otherwise `valueOff`|1.0
|**valueOff**|`string`| No, default: `"false"`|The value when toggle is off|1.0
|**valueOn**|`string`| No, default: `"true"`|The value when toggle is on|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.choiceset"></a>
## Input.ChoiceSet

Shows an array of Choice objects

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**choices**|`Input.Choice[]`|Yes|the choice options|1.0
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when Action.Submit is invoked)|1.0
|**isMultiSelect**|`boolean`| No|allow multiple choices to be selected|1.0
|**style**|`string`| No|Style hint for Input.ChoiceSet|1.0
|**type**|`"Input.ChoiceSet"`| No|Must be Input.ChoiceInput|1.0
|**value**|`string`| No|The initial choice (or set of choices) that should be selected. For multi-select, specifcy a comma-separated string of values|1.0
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.|1.0
|**separator**|`boolean`| No|The Separator object type describes the look and feel of a separation line between two elements.|1.0


<a name="schema-input.choice"></a>
## Input.Choice

Describes a Choice input. The value should be a simple string without a ","

|Property|Type|Required|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Input.Choice"`| No|&nbsp;|1.0
|**title**|`string`|Yes|The text for a choice|1.0
|**value**|`string`|Yes|The raw value for the choice. NOTE: do not use a "," in the value, since MultiSelect ChoiceSet returns a comma-delimited string of choice values|1.0




