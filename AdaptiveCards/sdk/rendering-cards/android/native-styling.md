---
title: Native styling - Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
---

# Native styling - Android

Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:

## Action Sentiment

Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## Inline Action

Text inputs with an inline action allows styling for the action being rendered. This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> All item names must be kept as shown here as the renderer looks for those exact names
