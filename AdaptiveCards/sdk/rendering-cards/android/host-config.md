---
title: Host config - Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
---

# Host config for Android

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)

To Create a HostConfig object from a string, use the DeserializeFromString method

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```