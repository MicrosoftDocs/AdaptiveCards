---
title:  Input.Choice Action
author: luywang
description: This page provides documentation for the `Input.Choice` input in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Input.Choice

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Input.Choice

Describes a choice for use in a ChoiceSet.

### Input.Choice Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **title** | `string` | Yes | Text to display. | 1.0 |
| **value** | `string` | Yes | The raw value for the choice. **NOTE:** do not use a `,` in the value, since a `ChoiceSet` with `isMultiSelect` set to `true` returns a comma-delimited string of choice values. | 1.0 |

## Properties

### title (Version 1.0)
Text to display.
* **Type**: `string`
* **Required**: Yes

### value (Version 1.0)
The raw value for the choice. **NOTE:** do not use a `,` in the value, since a `ChoiceSet` with `isMultiSelect` set to `true` returns a comma-delimited string of choice values.
* **Type**: `string`
* **Required**: Yes