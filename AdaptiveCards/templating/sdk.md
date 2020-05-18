---
title:  Templating SDKs
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
---

# Adaptive Card Templating SDKs

The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.

> Please read this for an [overview of Adaptive Card Templating](index.md)

> [!IMPORTANT] 
> 
> **Breaking changes** in the **May 2020 Release Candidate**
>
> We've been hard at work getting templating released, and we're finally in the home stretch! We had to make some minor breaking changes as we close on the release.

## Breaking changes as of May 2020

1. The binding syntax changed from `{...}` to `${...}`. 
    * For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`
2. The JavaScript API no longer contains an `EvaluationContext` object. Simply pass your data to the `expand` function. Please see the [SDK page](sdk.md) for full details.
3. The .NET API was redesigned to more closely match the JavaScript API. Please below for full details.

## JavaScript

The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN. See the package link for full documentation.

### npm

[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)

```console
npm install adaptivecards-templating
```

### CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### Usage

The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card. 

If you don't plan on rendering the card then you can remove the `parse` and `render` code. 

```js
import * as ACData from "adaptivecards-templating";
import * as AdaptiveCards from "adaptivecards";
 
// Define a template payload
var templatePayload = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello ${name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Expand the template with your `$root` data object.
// This binds it to the data and produces the final Adaptive Card payload
var cardPayload = template.expand({
   $root: {
      name: "Matt Hidinger"
   }
});
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(cardPayload);
 
var htmlElement = adaptiveCard.render();
```

## .NET 

[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)

```console
dotnet add package AdaptiveCards.Templating
```

### Usage

```cs
// Import the library 
using AdaptiveCards.Templating;
```

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.2"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello ${name}!""
        }
    ]
}";

// Create a Template instance from the template payload
AdaptiveCardTemplate template = new AdaptiveCardTemplate(templateJson);

// You can use any serializable object as your data
var myData = new
{
    Name = "Matt Hidinger"
};

// "Expand" the template - this generates the final Adaptive Card payload
string cardJson = template.Expand(myData);
```

### Custom Functions

Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.

In the below example, stringFormat custom function is added, and the funtion is used to format a string.
```cs
string jsonTemplate = @"{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [{
        ""type"": ""TextBlock"",
        ""text"": ""${stringFormat(strings.myName, person.firstName, person.lastName)}""
    }]
}";

string jsonData = @"{
    ""strings"": {
        ""myName"": ""My name is {0} {1}""
    },
    ""person"": {
        ""firstName"": ""Andrew"",
        ""lastName"": ""Leader""
    }
}";

AdaptiveCardTemplate template = new AdaptiveCardTemplate(jsonTemplate);

var context = new EvaluationContext
{
    Root = jsonData
};

// a custom function is added
AdaptiveExpressions.Expression.Functions.Add("stringFormat", (args) =>
{
    string formattedString = "";

    // argument is packed in sequential order as defined in the template
    // For example, suppose we have "${stringFormat(strings.myName, person.firstName, person.lastName)}"
    // args will have following entries
    // args[0]: strings.myName
    // args[1]: person.firstName
    // args[2]: strings.lastName
    if (args[0] != null && args[1] != null && args[2] != null) 
    {
        string formatString = args[0];
        string[] stringArguments = {args[1], args[2] };
        formattedString = string.Format(formatString, stringArguments);
    }
    return formattedString;
});

string cardJson = template.Expand(context);
```
