---
title:  Fact Element
author: luywang
description: This page provides documentation for the `Fact` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Fact Element

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

This page documents the **Fact** element, which describes a single key/value pair within a `FactSet` container.

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Fact

Describes a Fact in a FactSet as a key/value pair.

### Fact Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **title** | `string` | Yes | The title of the fact. | 1.0 |
| **value** | `string` | Yes | The value of the fact. | 1.0 |

-----

## Example

### FactSet with Facts Example (JSON)

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.0",
	"body": [
		{
			"type": "FactSet",
			"facts": [
				{
					"title": "Fact 1",
					"value": "Value 1"
				},
				{
					"title": "Fact 2",
					"value": "Value 2"
				},
				{
					"title": "Fact 3",
					"value": "Value 3"
				},
				{
					"title": "Fact 4",
					"value": "Value 5"
				}
			]
		}
	]
}
```

## Properties

### title

The title of the fact.

  * **Type**: `string`
  * **Required**: Yes

### value

The value of the fact.

  * **Type**: `string`
  * **Required**: Yes

