---
title: Renderer Status
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
---

# Renderer Status
The tables below show the current status of each renderer, based on their public published versions.

### Parsing

|Functionality | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Return validation failures | ✅ | ✅ | ✅ | ✅ | ✅ |
|Parse unknown properties | ✅ | ✅ | ✅ | ✅ | ✅ |

### Card Rendering

|Functionality | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Check for supported version | ✅ | ✅ | ✅ | ✅ | ✅  |
|Render full schema | ✅ | ✅ | ✅ | ✅ | ✅ |
|Render actions bar | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignore unknown Elements | ✅ | ✅ | ✅ | ✅ | ✅ |
|Host Config support | ✅ | ✅ | ✅ | ✅ | ✅ |
|Native platform styling | ✅ | ✅ | ✅ | ✅ | ❌ |

### Element Rendering

|Functionality | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Spacing and Separator | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock DATE/TIME formatting](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[TextBlock Markdown support](../authoring-cards/text-features.md#markdown-commonmark-subset) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Input Validation and Labels | ❌ | ✅ | ✅ | ✅ | ✅ |

\* The HTML renderer doesn’t include built-in Markdown support in order to minimize the size of the library and to let consuming applications use their preferred Markdown processor. The HTML renderer will however automatically use Markdown-It if it is loaded.

### Extensibility

|Functionality | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Override Element Renderer | ✅ | ✅ | ✅ | ✅ | ✅ |
|Add new Element Renderer | ✅ | ✅ | ✅ | ✅ | ✅ |
|Remove Element Renderer | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Override/add/remove Action Renderer](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ✅ | ✅ | ✅ |

### Actions

| Functionality | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Action.OpenUrl support | ✅ | ✅ | ✅ | ✅ | ✅  |
| Action.ShowCard support  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Action.Submit support  | ✅ | ✅ | ✅ | ✅ | ✅  |
| selectAction support | ✅ | ✅ | ✅ | ✅ | ✅ |

### Events

|       Functionality        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Element visibility changed |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

