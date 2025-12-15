---
title:  MediaSource Element
author: luywang
description: This page provides documentation for the `MediaSource` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# MediaSource Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **MediaSource** element, a type used within the `Media` element in the Adaptive Cards schema.


> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## MediaSource

Defines a source for a Media element.

**Introduced in version 1.1**

### MediaSource Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **url** | `uri` | Yes | URL to media. Supports data URI in version 1.2+. | 1.1 |
| **mimeType** | `string` | No | Mime type of associated media (e.g. `"video/mp4"`). For YouTube and other Web video URLs, `mimeType` can be omitted. | 1.1 |

## Properties

### mimeType

Mime type of associated media (e.g. `"video/mp4"`). For YouTube and other Web video URLs, `mimeType` can be omitted.

  * **Type**: `string`
  * **Required**: No

### url

URL to media. Supports data URI in version 1.2+.

  * **Type**: `uri`
  * **Required**: Yes
