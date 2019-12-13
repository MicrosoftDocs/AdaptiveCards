---
title: RenderedAdaptiveCard class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# RenderedAdaptiveCard

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### Summary

| Attributes | |
| ---- | --- |
| AdaptiveCard | Logical representation of the rendered adaptive card. |
| Inputs | Dictionary of input element and information added by the user. |
| View | Visual result from the rendering process. |
| Warnings | List of warnings produced from the rendering process. |

&nbsp;

| Public methods | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## Public Methods

---

### <a id="addwarning"></a> AddWarning
<p style='text-align:right'>Added in version 0.1</p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

Adds a warning to the warning list.

| Parameters | |
| --- | --- |
| warning | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
