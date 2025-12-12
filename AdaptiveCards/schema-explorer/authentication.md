---
title:  Authentication Element
author: luywang
description: This page provides documentation for the `Authentication` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Authentication

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Authentication

Defines authentication information associated with a card. This maps to the [`OAuthCard`](/dotnet/api/microsoft.bot.schema.oauthcard) type defined by the Bot Framework.

**Introduced in version 1.4**

### Authentication Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **text** | `string` | No | Text that can be displayed to the end user when prompting them to authenticate. | 1.4 |
| **connectionName** | `string` | No | The identifier for registered OAuth connection setting information. | 1.4 |
| **tokenExchangeResource** | `TokenExchangeResource` | No | Provides information required to enable on-behalf-of single sign-on user authentication. | 1.4 |
| **buttons** | `AuthCardButton[]` | No | Buttons that should be displayed to the user when prompting for authentication. The array MUST contain one button of type “signin”. Other button types are not currently supported. | 1.4 |

---

## Properties

### text

Text that can be displayed to the end user when prompting them to authenticate.

* **Type**: `string`
* **Required**: No

### connectionName

The identifier for registered OAuth connection setting information.

* **Type**: `string`
* **Required**: No

### tokenExchangeResource

Provides information required to enable on-behalf-of single sign-on user authentication.

* **Type**: `TokenExchangeResource`
* **Required**: No
* **Allowed values**:
    * `TokenExchangeResource`

### buttons

Buttons that should be displayed to the user when prompting for authentication. The array MUST contain one button of type "signin". Other button types are not currently supported.

* **Type**: `AuthCardButton[]`
* **Required**: No
* **Allowed values**:
    * `AuthCardButton`

