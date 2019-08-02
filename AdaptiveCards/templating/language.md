---
title:  Adaptive Card Template Language
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
---

# Introduction 

> Please read this for an [Overview of Adaptive Card Templating](index.md)

Templating enables the separation of **data** from **view** in your Adaptive Card.

> [!IMPORTANT] 
> 
> These features are **in preview and subject to change**. Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.

The templating SDKs make it easy to combine your data and template to produce a populated Adaptive Card that is ready to render.

The data can be provided inline with the `AdaptiveCard` payload, or at runtime using new APIs.

## Specify data within the card

To specify data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).

## Binding to the data

Then you can bind to the data within the `body` or `actions` of the card.

* Binding syntax starts with `{` and ends with `}`. E.g., `{myProperty}`
* Dot-notation to access sub-objects
* Indexer syntax to retrieve properties by key or items in an array
* Graceful null handling for deep hierarchies
* *Escape syntax documentation to come soon*

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
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

## Separating the template from the data

Alternatively, you could create a re-usable card "template" without the data:

**EmployeeCard.json**

```json
{
    "type": "AdaptivCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

And provide the data to the template at runtime:

**C# example**

```cs
var myEmployee = new Employee() 
{ 
    Name = "Matt",
    Manager = "Thomas",
    Peers = new List<Employee>() 
    { 
        new Employee() { Name = "Andrew" },
        new Employee() { Name = "Lei" },
        new Employee() { Name = "Mary Anne" },
        new Employee() { Name = "Adam" },
    }
};

var card = AdaptiveCard.FromJson("EmployeeCard.json", myEmployee);
```

# Designer Support

The Adaptive Card Designer has also been updated to support templating. 

> Try it out now: **http://vnext.adaptivecards.io/designer**

[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)

 
This "vnext" URL is going to have bugs and will deploy frequently. **Clear your cache daily** to make sure you have the latest, and if you find bugs please let us know!

* **Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode." There is a small button in this pane to populate the Data Structure from the existing sample data.
* **Data Structure** - This is the structure of your sample data. Fields can be dragged onto the design surface to create a binding to them 
* **Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience
* **Open Sample** - click this button to open various sample payloads

# Advanced binding

## Binding scopes

There are a few reserved keywords to access various binding scopes. 

*Note:* not all of these are implemented in the preview.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

## Assigning a data context to elements

To assign a data context to any element add a `$data` attribute to the element.

```json
{
    "type": "Container",
    "$data": "{mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': {mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: {$root}"
        }
    ]
}
```

## Repeating items in an array

This part is a bit of "dark magic".

* If an element's `$data` context is assigned to an **array**, then the element **will be repeated for each item in the array.** 
* As it is being repeated, `$data` becomes scoped to the **individual item** within the array.

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
            "text": "{name}"
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

## Functions

We will provide a set of functions that work on every SDK. 

The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:

### String functions

* substr
* indexOf *(not working yet)*
* toUpper *(not working yet)*
* toLower *(not working yet)*

### Number functions

* Formatting (currency, decimal, etc) *(not working yet)*

### Date functions

* Parsing well-known date string formats *(not working yet)*
* Formatting for well-known date/time representations *(not working yet)*

### Data manipulation

* JSON.parse - ability to parse a JSON string 

**JSON.parse Example**

This is an Azure DevOps response where the `message` property is a JSON-serialized string. In order to access values within the string, we need to use the `JSON.parse` function in our template.

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
    "text": "{JSON.parse(message).releaseName}"
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

We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported. We are still evaluating this.

## Conditional layout

We currently expose a `$when` clause allowing a template to toggle the visibility of an element based on the evaluation of a binding. 

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "{price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "{price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```


### Composing templates

Currently there is no support for composing template "parts" together. But we are exploring options and hope to share more soon. Any thoughts here welcome!


# Examples

We only have a limited amount of samples created so far, but take a look here to get started.

* Load samples within the [designer](http://vnext.adaptivecards.io/designer) by clicking **Open Sample**
* Or just [browse a directory of them](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) directly
