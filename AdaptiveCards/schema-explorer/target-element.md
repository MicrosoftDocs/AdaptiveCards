---
title:  Action.TargetElement Action
author: luywang
description: This page provides documentation for the `Action.TargetElement` action in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

I have converted the HTML content for the **Adaptive Cards TargetElement** type from the Schema Explorer into a structured Markdown format.

# TargetElement

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


This page documents the **TargetElement** type, which represents an entry used to specify elements whose visibility should be changed by an `Action.ToggleVisibility` action.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## TargetElement

Represents an entry for `Action.ToggleVisibility`'s `targetElements` property.

### TargetElement Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **elementId** | `string` | Yes | Element ID of element to toggle. | 1.0 |
| **isVisible** | `boolean?` | No | If `true`, always show target element. If `false`, always hide target element. If not supplied, toggle target element's visibility. | 1.0 |

## Properties

### elementId (Version 1.0)

Element ID of element to toggle

  * **Type**: `string`
  * **Required**: Yes

### isVisible (Version 1.0)

If `true`, always show target element. If `false`, always hide target element. If not supplied, toggle target element's visibility.

  * **Type**: `boolean?`
  * **Required**: No
