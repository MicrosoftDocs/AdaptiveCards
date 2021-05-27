---
title: Getting Started
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
---

# Getting Started 

An Adaptive Card is a JSON-serialized card object model.

## Adaptive Card structure

The basic structure of a card is as follows:

* `AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.
* `body` - The body of the card is made up of building-blocks known as `elements`. Elements can be composed in nearly infinite arrangements to create many types of cards. 
* `actions` - Many cards have a set of actions a user may take on it. This property describes those actions which typically get rendered in an "action bar" at the bottom.

### Example Card

This sample card which includes a single line of text followed by an image.

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## `Type` property

Every element has a `type` property which identifies what kind of object it is. Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.

All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML). However, you can use a `ColumnSet` to create side-by-side columns of containers.

## Adaptive Elements

The most fundamental elements are:

* **TextBlock** - adds a block of text with properties to control what the text looks like
* **Image** - adds an image with properties to control what the image looks like

## Container elements

Cards can also have containers, which arrange a collection of child elements.

* **Container** - Defines a a collection of elements
* **ColumnSet/Column** - Defines a collection of columns, each column is a container
* **FactSet** - Container of Facts
* **ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.

## Input elements

Input elements allow you to ask for native UI to build simple forms:

* **Input.Text** - get text content from the user
* **Input.Date** - get a Date from the user
* **Input.Time** - get a Time from the user
* **Input.Number** - get a Number from the user
* **Input.ChoiceSet** - Give the user a set of choices and have them pick
* **Input.Toggle** - Give the user a single choice between two items and have them pick

## Actions

Actions add buttons to the card. These can perform a variety of actions, like opening a URL or submitting some data.

* **Action.OpenUrl** - the button opens an external URL for viewing
* **Action.ShowCard** - Requests a sub-card to be shown to the user.
* **Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.

> **Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.

## Learn More

* [Browse Sample cards](https://adaptivecards.io/samples/) for inspiration
* Use the [Schema Explorer](https://adaptivecards.io/explorer) to browse the available elements
* Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/)
* [Get in touch](https://adaptivecards.io/connect) with any feedback you have
