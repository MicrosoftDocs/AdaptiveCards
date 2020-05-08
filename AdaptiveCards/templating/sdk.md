---
title:  Templating SDKs
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
---

# Adaptive Card Templating SDKs

The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.

> Please read this for an [overview of Adaptive Card Templating](index.md)

> [!IMPORTANT] 
> 
> These features are **in preview and subject to change**. Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.

## JavaScript

The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN. See the package link for full documentation.

### npm

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
            "text": "Hello {name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new ACData.EvaluationContext();
context.$root = {
    "name": "Mickey Mouse"
};
 
// "Expand" the template - this generates the final Adaptive Card,
// ready to render
var card = template.expand(context);
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(card);
 
var htmlElement = adaptiveCard.render();
```

## .NET 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> Consider changing the version above to the latest published version

### Usage
Import the library 

```cs
using AdaptiveCards.Templating
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

var dataJson = @"{
    ""person"": { 
        ""name"": ""Mickey Mouse""
    }
}";

// Create a Template instance from the template payload
AdaptiveCardTemplate template = new AdaptiveCardTemplate(jsonTemplate);

// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new EvaluationContext
{
    Root = dataJson 
};


// "Expand" the template - this generates the final Adaptive Card,
string cardJson = template.Expand(context);
```

Alternatively, an object or a string in json format can be directly called with Expand method
```cs
// without creating the context, expand using dataJson directly
string cardJson = template.Expand(dataJson);
```

```cs
AdaptiveCardParseResult parseResult = AdaptiveCard.FromJson(cardJson);

// ready to render
AdaptiveCard card = parseResult.Card;

// Render the card
RenderedAdaptiveCard renderedCard = Renderer.RenderCard(card);
```

### Custom Function
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
Expression.Functions.Add("stringFormat", (args) =>
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