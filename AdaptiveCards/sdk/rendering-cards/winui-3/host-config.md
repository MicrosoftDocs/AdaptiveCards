---
title: Host config - WinUI 3 SDK
author: jproca
ms.author: jproca
ms.date: 05/04/2023
ms.topic: article
---

# Host config - WinUI 3

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)

> The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.

Example:

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> Alternatively, you can load the HostConfig from a JSON string.

Example:

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

When you pass it in to the WinUI3Renderer you are setting the default HostConfig to use for every card you render.