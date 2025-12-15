---
title:  TextRun Element
author: luywang
description: This page provides documentation for the `TextRun` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# TextRun Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **TextRun** element, which defines a single run of formatted text. It is commonly used within a `RichTextBlock` element.

> A TextRun with no properties set can be represented in the JSON as a simple string containing the text as a shorthand for the JSON object. These two representations are equivalent.


> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## TextRun

Defines a single run of formatted text.

**Introduced in version 1.2**

### TextRun Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `&quot;TextRun&quot;` | Yes | Must be `&quot;TextRun&quot;`. | 1.2 |
| **text** | `string` | Yes | Text to display. Markdown is not supported. | 1.2 |
| **color** | `Colors?` | No | Controls the color of the text. | 1.2 |
| **fontType** | `FontType?` | No | The type of font to use | 1.2 |
| **highlight** | `boolean` | No | If `true`, displays the text highlighted. | 1.2 |
| **isSubtle** | `boolean?` | No | If `true`, displays text slightly toned down to appear less prominent. | 1.2 |
| **italic** | `boolean` | No | If `true`, displays the text using italic font. | 1.2 |
| **selectAction** | `ISelectAction` | No | Action to invoke when this text run is clicked. Visually changes the text run into a hyperlink. `Action.ShowCard` is not supported. | 1.2 |
| **size** | `FontSize?` | No | Controls size of text. | 1.2 |
| **strikethrough** | `boolean` | No | If `true`, displays the text with strikethrough. | 1.2 |
| **underline** | `boolean` | No | If `true`, displays the text with an underline. | 1.3 |
| **weight** | `FontWeight?` | No | Controls the weight of the text. | 1.2 |

## Properties

### text

Text to display. Markdown is not supported.

  * **Type**: `string`
  * **Required**: Yes

### color

Controls the color of the text.

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

### fontType

The type of font to use

  * **Type**: `FontType?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"monospace"`

### highlight

If `true`, displays the text highlighted.

  * **Type**: `boolean`
  * **Required**: No

### isSubtle

If `true`, displays text slightly toned down to appear less prominent.

  * **Type**: `boolean?`
  * **Required**: No

### italic

If `true`, displays the text using italic font.

  * **Type**: `boolean`
  * **Required**: No

### selectAction

Action to invoke when this text run is clicked. Visually changes the text run into a hyperlink. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`
      * `Action.OpenUrl`
      * `Action.Submit`
      * `Action.ToggleVisibility`

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

### strikethrough

If `true`, displays the text with strikethrough.

  * **Type**: `boolean`
  * **Required**: No

### underline

If `true`, displays the text with an underline.

  * **Type**: `boolean`
  * **Version**: 1.3
  * **Required**: No

### weight

Controls the weight of the text.

  * **Type**: `FontWeight?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"lighter"`
      * `"bolder"`

