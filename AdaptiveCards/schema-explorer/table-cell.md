---
title:  TableCell Element
author: luywang
description: This page provides documentation for the `TableCell` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# TableCell Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **TableCell** element, which represents an individual cell within a row (`TableRow`) of a `Table` element.

**Introduced in version 1.5**

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## TableCell

Represents a cell within a row of a Table element.

**Introduced in version 1.5**

### TableCell Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **items** | `Element[]` | Yes | The card elements to render inside the `TableCell`. | 1.5 |
| **selectAction** | `ISelectAction` | No | An Action that will be invoked when the `TableCell` is tapped or selected. `Action.ShowCard` is not supported. | 1.1 |
| **style** | `ContainerStyle?` | No | Style hint for `TableCell`. | 1.5 |
| **verticalContentAlignment** | `VerticalContentAlignment?` | No | Defines how the content should be aligned vertically within the container. When not specified, the value of verticalContentAlignment is inherited from the parent container. If no parent container has verticalContentAlignment set, it defaults to Top. | 1.1 |
| **bleed** | `boolean` | No | Determines whether the element should bleed through its parent’s padding. | 1.2 |
| **backgroundImage** | `BackgroundImage`, `uri` | No | Specifies the background image. Acceptable formats are PNG, JPEG, and GIF. | 1.2 |
| **minHeight** | `string` | No | Specifies the minimum height of the container in pixels, like `&quot;80px&quot;`. | 1.2 |
| **rtl?** | `boolean?` | No | When `true` content in this container should be presented right to left. When ‘false’ content in this container should be presented left to right. When unset layout direction will inherit from parent container or column. If unset in all ancestors, the default platform behavior will apply. | 1.5 |

## Properties

### items

The card elements to render inside the `TableCell`.

  * **Type**: `Element[]`
  * **Required**: Yes
  * **Allowed values**:
      * `ActionSet`, `ColumnSet`, `Container`, `FactSet`, `Image`, `ImageSet`, `Input.ChoiceSet`, `Input.Date`, `Input.Number`, `Input.Text`, `Input.Time`, `Input.Toggle`, `Media`, `RichTextBlock`, `Table`, `TextBlock`

### selectAction

An Action that will be invoked when the `TableCell` is tapped or selected. `Action.ShowCard` is not supported.

  * **Type**: `ISelectAction`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `Action.Execute`, `Action.OpenUrl`, `Action.Submit`, `Action.ToggleVisibility`

### style

Style hint for `TableCell`.

  * **Type**: `ContainerStyle?`
  * **Required**: No
  * **Allowed values**:
      * `"default"`
      * `"emphasis"`
      * `"good"` (Added in version 1.2)
      * `"attention"` (Added in version 1.2)
      * `"warning"` (Added in version 1.2)
      * `"accent"` (Added in version 1.2)

### verticalContentAlignment

Defines how the content should be aligned vertically within the container. When not specified, the value of `verticalContentAlignment` is inherited from the parent container. If no parent container has `verticalContentAlignment` set, it defaults to Top.

  * **Type**: `VerticalContentAlignment?`
  * **Version**: 1.1
  * **Required**: No
  * **Allowed values**:
      * `"top"`
      * `"center"`
      * `"bottom"`

### bleed

Determines whether the element should bleed through its parent's padding.

  * **Type**: `boolean`
  * **Version**: 1.2
  * **Required**: No

### backgroundImage

Specifies the background image. Acceptable formats are PNG, JPEG, and GIF.

  * **Type**: `BackgroundImage`, `uri`
  * **Version**: 1.2
  * **Required**: No
  * **Allowed values**:
      * `BackgroundImage`
      * `uri`

### minHeight

Specifies the minimum height of the container in pixels, like `"80px"`.

  * **Type**: `string`
  * **Version**: 1.2
  * **Required**: No

### rtl?

When `true` content in this container should be presented right to left. When 'false' content in this container should be presented left to right. When unset, layout direction will inherit from parent container or column. If unset in all ancestors, the default platform behavior will apply.

  * **Type**: `boolean?`
  * **Required**: No

