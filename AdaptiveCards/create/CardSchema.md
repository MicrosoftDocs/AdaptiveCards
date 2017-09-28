# Card Schema

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

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**type**|`"AdaptiveCard"`|Yes|Must be AdaptiveCard
|**actions**|`Action[]`| No|The Actions to show in the card's action bar
|**body**|`array[]`| No|The Card Elements to show in the primary card region
|**version**|`string`|Yes|version of schema that this card was authored 
|**minVersion**|`string`| No|if a client doesn't support the minVersion the card should be rejected and return the fallbackText.  If it does, then the elements that are not supported are safe to ignore
|**fallbackText**|`string`| No|if a client is not able to show the card, show fallbackText to the user. This can be in markdown format. 
|**speak**|`string`| No|Specifies what should be spoken for this entire Item. This is simple text or SSML fragment


# Card Elements

<a name="schema-textblock"></a>
## TextBlock

The TextBlock Item allows for the inclusion of text, with various font sizes, weight and color, in Adaptive Cards.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**color**|`string`| No|Controls the color of TextBlock Items.
|**horizontalAlignment**|`string`| No|Controls how Items are horizontally positioned within their container.
|**isSubtle**|`boolean`| No|Indicates whether the color of the text should be slightly toned down to appear less prominent
|**maxLines**|`number`| No|When Wrap is true, you can specify the maximum number of lines to allow the textBlock to use.
|**size**|`string`| No|controls size of the text.
|**text**|`string`|Yes|The actual text to display
|**type**|`"TextBlock"`| No|Must be TextBlock
|**weight**|`string`| No|Controls the weight of TextBlock Items
|**wrap**|`boolean`| No|True if be is allowed to wrap
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-image"></a>
## Image

The Image Item allows for the inclusion of images in an Adaptive Card.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**altText**|`string`| No|Alternate text for the image for accessibility
|**horizontalAlignment**|`string`| No|Controls how Items are horizontally positioned within their container.
|**selectAction**|`object`| No|An Action that will be invoked when the Image is tapped or selected
|**size**|`object`| No, default: `auto`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify "auto" for true image dimension or "stretch" to force it to fill the container
|**style**|`string`| No|Controls the way Images are displayed
|**type**|`"Image"`| No|Must be Image
|**url**|`string`|Yes|The URL to the image.
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


# Containers

<a name="schema-container"></a>
## Container

Containers group items together

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**items**|`array[]`|Yes|The Card Elements to render inside the Container
|**selectAction**|`object`| No|An Action that will be invoked when the Image is tapped or selected
|**style**|`string`| No|Style hint for Container
|**type**|`"Container"`| No|Must be Container
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-columnset"></a>
## ColumnSet

ColumnSet divides a region into Column's allowing elements to sit side-by-side

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**columns**|`Column[]`| No|The array of Columns to divide the region into
|**selectAction**|`object`| No|The Action that is executed when the ColumnSet is clicked/tapped
|**type**|`"ColumnSet"`| No|Must be ColumnSet
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-column"></a>
## Column

Defines a container that is part of a ColumnSet

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**items**|`array[]`|Yes|The Card Elements to include in the Column
|**selectAction**|`object`| No|An Action that will be invoked when the Column is tapped or selected
|**width**|`string,number`| No|"auto", "stretch", or a number representing relative width of the column in the column group
|**type**|`"Column"`| No|Must be Column
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-factset"></a>
## FactSet

The FactSet Item makes it simple to display a series of facts (e.g. name/value pairs) in a tabular form.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**facts**|`Fact[]`|Yes|The array of Facts
|**type**|`"FactSet"`| No|Must be FactSet
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-fact"></a>
## Fact

Describes a Fact in a FactSet as a key/value pair

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**type**|`"Fact"`| No|&nbsp;
|**title**|`string`|Yes|The title of the fact
|**value**|`string`|Yes|The value of the fact


<a name="schema-imageset"></a>
## ImageSet

The ImageSet allows for the inclusion of a collection images like a photogallery.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**images**|`Image[]`|Yes|The array of Image elements to show
|**imageSize**|`string`| No, default: `"auto"`|Controls the approximate size of the image. The physical dimensions will vary per host. Specify "auto" for true image dimension or "stretch" to force it to fill the container
|**type**|`"ImageSet"`| No|Must be ImageSet
|**id**|`string`| No|A unique Id associated with the element
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


# Actions

<a name="schema-action.openurl"></a>
## Action.OpenUrl

When Action.OpenUrl is invoked it will show the given url, either by launching it to an external web browser or showing in-situ with embedded web browser.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**title**|`string`| No|Label for button or link that represents this action
|**type**|`"Action.OpenUrl"`|Yes|Must be Action.OpenUrl
|**url**|`string`|Yes|The URL to open


<a name="schema-action.submit"></a>
## Action.Submit

Submit action gathers up input fields, merges with optional data field and generates event to client asking for data to be submitted. It is up to the client to determine how that data is processed. For example: With BotFramework bots the client would send an activity through the messaging medium to the bot.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**type**|`"Action.Submit"`|Yes|Must be Action.Submit
|**title**|`string`| No|Label for button or link that represents this action
|**data**|`string,object`| No|initial data that input fields will be combined with. This is essentially 'hidden' properties


<a name="schema-action.showcard"></a>
## Action.ShowCard

Action.ShowCard defines an inline AdaptiveCard which is shown to the user when it is clicked.

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**type**|`"Action.ShowCard"`|Yes|Must be Action.ShowCard
|**title**|`string`| No|Label for button or link that represents this action
|**card**|`object`|Yes|Card schema for an adaptive card


# Inputs

<a name="schema-input.text"></a>
## Input.Text

Input.Text collects text from the user,

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**isMultiline**|`boolean`| No|Do you want to allow multiple lines of input
|**maxLength**|`number`| No|hint of maximum length characters to collect (may be ignored by some clients)
|**placeholder**|`string`| No|Title Description of the input desired
|**style**|`string`| No|Style hint for Input.Text.
|**type**|`"Input.Text"`| No|Input.Text
|**value**|`string`| No|The initial value for a field
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.number"></a>
## Input.Number

Input.Number collects number from the user,

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**max**|`number`| No|hint of maximum value (may be ignored by some clients)
|**min**|`number`| No|hint of minimum value (may be ignored by some clients)
|**placeholder**|`string`| No|Title Description of the input desired
|**type**|`"Input.Number"`| No|The type must be Input.Number
|**value**|`number`| No|The initial value for a field
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.date"></a>
## Input.Date

Input.Date collects Date from the user,

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**max**|`string`| No|hint of maximum value expressed in ISO-8601 format (may be ignored by some clients)
|**min**|`string`| No|hint of minimum value expressed in ISO-8601 format (may be ignored by some clients)
|**placeholder**|`string`| No|Title Description of the input desired
|**type**|`"Input.Date"`| No|The type must be Input.Date
|**value**|`string`| No|The initial value for a field expressed in ISO-8601 format
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.time"></a>
## Input.Time

Input.Time collects Time from the user,

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**max**|`string`| No|hint of maximum value (may be ignored by some clients)
|**min**|`string`| No|hint of minimum value (may be ignored by some clients)
|**placeholder**|`string`| No|Title Description of the input desired
|**type**|`"Input.Time"`| No|The type must be Input.Time
|**value**|`string`| No|The initial value for a field expressed in ISO-8601 format
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.toggle"></a>
## Input.Toggle

Input.Toggle collects a true/false response from the user

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**title**|`string`|Yes|Title for the toggle
|**type**|`"Input.Toggle"`| No|Input.Toggle
|**value**|`string`| No|The current selected value (default:false)
|**valueOff**|`string`| No|The value when toggle is off (default:false)
|**valueOn**|`string`| No|The value when toggle is on (default:true)
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.choiceset"></a>
## Input.ChoiceSet

Shows an array of Choice objects

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**choices**|`Input.Choice[]`|Yes|the choice options
|**id**|`string`|Yes|Id for the value (will be used to identify collected input when SUBMIT is clicked)
|**isMultiSelect**|`boolean`| No, default: `false`|allow multiple choices to be selected
|**style**|`string`| No|Style hint for Input.ChoiceSet
|**type**|`"Input.ChoiceSet"`| No|Must be Input.ChoiceInput
|**value**|`string`| No|The initial choice (or set of choices) that should be selected. For multi-select, specifcy a comma-separated string of values
|**spacing**|`string`| No|Controls the amount of spacing between this element and the previous element.
|**separator**|`boolean`| No, default: `false`|The Separator object type describes the look and feel of a separation line between two elements.


<a name="schema-input.choice"></a>
## Input.Choice

Describes a Choice input. The value should be a simple string without a ","

|Property|Type|Required|Description|
|--------|----|--------|-----------|
|**type**|`"Input.Choice"`| No|&nbsp;
|**title**|`string`|Yes|The text for a choice
|**value**|`string`|Yes|The raw value for the choice. NOTE: do not use a "," in the value, since MultiSelect ChoiceSet returns a comma-delimited string of choice values


