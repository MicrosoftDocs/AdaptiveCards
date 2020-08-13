---
title:  Adaptive Cards Template Language
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
---

# Adaptive Cards Template Language

Templating enables the separation of **data** from **layout** in your Adaptive Card. The template langauge is the syntax used to author a template. 

> Please read this for an [overview of Adaptive Card Templating](index.md)

> [!IMPORTANT] 
> 
> **Breaking changes** in the **May 2020 Release Candidate**
>
> We've been hard at work getting templating released, and we're finally in the home stretch! We had to make some minor breaking changes as we close on the release.

## Breaking changes as of May 2020

1. The binding syntax changed from `{...}` to `${...}`
    * For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`
    
## Binding to data

Writing a template is as simple as replacing the "non-static" content of your card with "binding expressions".

### Static card payload

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### Template payload

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* Binding expressions can be placed just about anywhere that static content can be
* The binding syntax starts with `${` and ends with `}`. E.g., `${myProperty}`
* Use *Dot-notation* to access sub-objects of an object hierarchy. E.g., `${myParent.myChild}`
* Graceful null handling ensures you won't get exceptions if you access a null property in an object graph
* Use *Indexer syntax* to retrieve properties by key or items in an array. E.g., `${myArray[0]}`

## Providing the data

Now that you have a template, you'll want to provide the data that makes it complete. You have two options to do this:

1. **Option A: Inline within the template payload**. You can provide the data inline within the `AdaptiveCard` template payload. To do so, simply add a `$data` attribute to the root `AdaptiveCard` object.
2. **Option B: As a separate data object**. With this option you provide two separate objects to the [Templating SDK](sdk.md) at runtime: the `template` and the `data`. This will be the more common approach, since typically you will create a template and want to provide dynamic data later.

### Option A: Inline data

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    },
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

### Option B: Separating the template from the data

Alternatively (and more likely), you'll create a re-usable card template without including the data. This template could be stored as a file and added to source control.

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).

**JavaScript example**

Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var card = template.expand({
    $root: {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    }
});

// Now you have an AdaptiveCard ready to render!
```

## Designer Support

The Adaptive Card Designer has been updated to support templating. 

> Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**

[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode." There is a small button in this pane to populate the Data Structure from the existing sample data.
* **Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience
* **Open Sample** - click this button to open various sample payloads

## Advanced binding

### Binding scopes

There are a few reserved keywords to access various binding scopes. 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### Assigning a data context to elements

To assign a "data context" to any element add a `$data` attribute to the element.

```json
{
    "type": "Container",
    "$data": "${mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': ${mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: ${$root}"
        }
    ]
}
```

## Repeating items in an array

* If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.** 
* Any binding expressions (`${myProperty}`) used in property values will be scoped to the **individual item** within the array.
* If binding to an array of strings, use `${$data}` to access the individual string element. E.g., `"text": "${$data}"`

For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array. Notice how the `text` property is bound to the `name` property of an individual object within the array. 

```json
{
    "type": "Container",
    "items": [
        {
            "type": "TextBlock",
            "$data": [
                { "name": "Matt" }, 
                { "name": "David" }, 
                { "name": "Thomas" }
            ],
            "text": "${name}"
        }
    ]
}
```

**Resulting in:**

```json
{
    "type": "Container",
    "items": [ 
        {
            "type": "TextBlock",
            "text": "Matt"
        },
        {
            "type": "TextBlock",
            "text": "David"
        }
        {
            "type": "TextBlock",
            "text": "Thomas"
        }
    ]
}
```

## Built-in functions

No templating language is complete without a rich suite of helper functions. Adaptive Card Templating is built on top of the [Adaptive Expression Language](https://aka.ms/adaptive-expressions) (AEL), which is an open standard for declaring expressions that can be evaluated on many different platforms. And it's a proper superset of "Logic Apps", so you can use similar syntax as Power Automate, etc.

**This is just a small sampling of the built-in functions.**

Check out the full list of [Adaptive Expression Language Pre-built functions](https://docs.microsoft.com/en-us/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0).

### Conditional evaluation

* if(*expression*, *trueValue*, *falseValue*)

**`if` example**

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### Parsing JSON

* json(*jsonString*) - Parse a JSON string

**`json` example**

This is an Azure DevOps response where the `message` property is a JSON-serialized string. In order to access values within the string, we need to use the `json` function in our template.

**Data** 

```json
{
    "id": "1291525457129548",
    "status": 4,
    "author": "Matt Hidinger",
    "message": "{\"type\":\"Deployment\",\"buildId\":\"9542982\",\"releaseId\":\"129\",\"buildNumber\":\"20180504.3\",\"releaseName\":\"Release-104\",\"repoProvider\":\"GitHub\"}",
    "start_time": "2018-05-04T18:05:33.3087147Z",
    "end_time": "2018-05-04T18:05:33.3087147Z"
}
```

**Usage**

```json
{
    "type": "TextBlock",
    "text": "${json(message).releaseName}"
}
```

**Resulting In**

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### Custom functions

Custom functions are supported via APIs in the [Templating SDKs](sdk.md). 

## Conditional layout with `$when`

To drop an entire element if a condition is met, use the `$when` property. If `$when` evaluates to `false` the element will not appear to the user.

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "${price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "${price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### Composing templates

Currently there is no support for composing template "parts" together. But we are exploring options and hope to share more soon. Any thoughts here welcome!

## Examples

Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.
