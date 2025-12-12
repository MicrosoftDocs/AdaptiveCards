---
title:  BackgroundImage Element
author: luywang
description: This page provides documentation for the `BackgroundImage` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# BackgroundImage

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## BackgroundImage

Specifies a background image. Acceptable formats are PNG, JPEG, and GIF.

**Introduced in version 1.2**

### BackgroundImage Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **url** | `uri` | Yes | The URL (or data url) of the image. Acceptable formats are PNG, JPEG, and GIF. | 1.2 |
| **fillMode** | `ImageFillMode` | No | Describes how the image should fill the area. | 1.2 |
| **horizontalAlignment** | `HorizontalAlignment` | No | Describes how the image should be aligned if it must be cropped or if using repeat fill mode. | 1.2 |
| **verticalAlignment** | `VerticalAlignment` | No | Describes how the image should be aligned if it must be cropped or if using repeat fill mode. | 1.2 |

---

## Properties

### url

The URL (or data url) of the image. Acceptable formats are PNG, JPEG, and GIF.

* **Type**: `uri`
* **Required**: Yes

### fillMode

Describes how the image should fill the area.

* **Type**: `ImageFillMode`
* **Required**: No
* **Allowed values**:
    * `"cover"`: The background image covers the entire width of the container. Its aspect ratio is preserved. Content may be clipped if the aspect ratio of the image doesn't match the aspect ratio of the container. **verticalAlignment** is respected (**horizontalAlignment** is meaningless since it's stretched width). This is the default mode and is the equivalent to the current model.
    * `"repeatHorizontally"`: The background image isn't stretched. It is repeated in the x axis as many times as necessary to cover the container's width. **verticalAlignment** is honored (default is **top**), **horizontalAlignment** is ignored.
    * `"repeatVertically"`: The background image isn't stretched. It is repeated in the y axis as many times as necessary to cover the container's height. **verticalAlignment** is ignored, **horizontalAlignment** is honored (default is **left**).
    * `"repeat"`: The background image isn't stretched. It is repeated first in the x axis then in the y axis as many times as necessary to cover the entire container. Both **horizontalAlignment** and **verticalAlignment** are honored (defaults are **left** and **top**).

### horizontalAlignment

Describes how the image should be aligned if it must be cropped or if using repeat fill mode.

* **Type**: `HorizontalAlignment`
* **Required**: No
* **Allowed values**:
    * `"left"`
    * `"center"`
    * `"right"`

### verticalAlignment

Describes how the image should be aligned if it must be cropped or if using repeat fill mode.

* **Type**: `VerticalAlignment`
* **Required**: No
* **Allowed values**:
    * `"top"`
    * `"center"`
    * `"bottom"`

