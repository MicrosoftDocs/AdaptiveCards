---
title:  AuthCardButton Element
author: luywang
description: This page provides documentation for the `AuthCardButton` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# AuthCardButton

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## AuthCardButton

Defines a button as displayed when prompting a user to authenticate. This maps to the `cardAction` type defined by the Bot Framework ([https://docs.microsoft.com/dotnet/api/microsoft.bot.schema.cardaction](https://docs.microsoft.com/dotnet/api/microsoft.bot.schema.cardaction)).

**Introduced in version 1.4**

### AuthCardButton Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **type** | `string` | Yes | The type of the button. | 1.4 |
| **value** | `string` | Yes | The value associated with the button. The meaning of value depends on the button’s type. | 1.4 |
| **title** | `string` | No | The caption of the button. | 1.4 |
| **image** | `string` | No | A URL to an image to display alongside the button’s caption. | 1.4 |

---

## Properties

### type

The type of the button.

* **Type**: `string`
* **Required**: Yes

### title

The caption of the button.

* **Type**: `string`
* **Required**: No

### image

A URL to an image to display alongside the button's caption.

* **Type**: `string`
* **Required**: No

### value

The value associated with the button. The meaning of value depends on the button's type.

* **Type**: `string`
* **Required**: Yes

