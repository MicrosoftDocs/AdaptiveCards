---
title:  TokenExchangeResource Element
author: luywang
description: This page provides documentation for the `TokenExchangeResource` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# TokenExchangeResource

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## TokenExchangeResource

Defines information required to enable on-behalf-of single sign-on user authentication. It maps to the [`TokenExchangeResource`](/dotnet/api/microsoft.bot.schema.tokenexchangeresource) type defined by the Bot Framework.

**Introduced in version 1.4**

### TokenExchangeResource Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **id** | `string` | Yes | The unique identified of this token exchange instance. | 1.4 |
| **uri** | `string` | Yes | An application ID or resource identifier with which to exchange a token on behalf of. This property is identity provider- and application-specific. | 1.4 |
| **providerId** | `string` | Yes | An identifier for the identity provider with which to attempt a token exchange. | 1.4 |

---

## Properties

### id

The unique identified of this token exchange instance.

* **Type**: `string`
* **Required**: Yes

### uri

An application ID or resource identifier with which to exchange a token on behalf of. This property is identity provider- and application-specific.

* **Type**: `string`
* **Required**: Yes

### providerId

An identifier for the identity provider with which to attempt a token exchange.

* **Type**: `string`
* **Required**: Yes

