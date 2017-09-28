---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
---

# Android library
This is a renderer which targets Android native controls.

## Create Adaptive Card Object Instance from JSON Text
```java
AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText);
```
## Render a card
```java
View view = AdaptiveCardRenderer.getInstance().render(getApplicationContext(), getSupportFragmentManager(), adaptiveCard, showCardActionHandler, submitActionHandler, new HostConfig());
```

### HostConfig 

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../HostConfig.md) for the full description.)

> The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.

### UI Framework styling
*Coming soon*

## Next steps

* [Implement a renderer](../ImplementingRenderer.md)  
