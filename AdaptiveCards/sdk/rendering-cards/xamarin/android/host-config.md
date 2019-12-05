---
title: Host config - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# Host config - Android

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)

To create a ```HostConfig``` object from a string, use the ```DeserializeFromString``` method like this:

```c#
HostConfig Config = HostConfig.DeserializeFromString(configJson);
```