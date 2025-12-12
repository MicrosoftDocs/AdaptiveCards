---
title:  CaptionSource Element
author: luywang
description: This page provides documentation for the `CaptionSource` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# CaptionSource Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


This page documents the **CaptionSource** element, a type used to define sources for media captions, typically within the `Media` element in the Adaptive Cards schema.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## CaptionSource

Defines a source for captions.

**Introduced in version 1.6**

### CaptionSource Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **mimeType** | `string` | Yes | Mime type of associated caption file (e.g. `"vtt"`). For rendering in JavaScript, only `"vtt"` is supported. For rendering in UWP, `"vtt"` and `"srt"` are supported. | 1.6 |
| **url** | `uri` | Yes | URL to captions. | 1.6 |
| **label** | `string` | Yes | Label of this caption to show to the user. | 1.6 |

## Properties

### mimeType

Mime type of associated caption file (e.g. `"vtt"`). For rendering in JavaScript, only `"vtt"` is supported, while for rendering in UWP, `"vtt"` and `"srt"` are supported.

  * **Type**: `string`
  * **Required**: Yes

### url

URL to captions.

  * **Type**: `uri`
  * **Required**: Yes

### label

Label of this caption to show to the user.

  * **Type**: `string`
  * **Required**: Yes

