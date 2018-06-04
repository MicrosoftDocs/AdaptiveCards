---
title: Renderer Status
author: matthidinger
ms.author: mahiding
ms.date: 09/28/2017
ms.topic: article
---

# Renderer Status
The following functionality should be included in every Adaptive Cards renderer.

### Parsing

Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Return validation failures | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ 
Parse unknown properties | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ 

### Card Rendering

Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Check for supported version | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ 
Render full schema | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Render actions bar | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Ignore unknown Elements | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Host Config support | ✅ | ✅ | ✅ | ✅ | ✅ | ❌
Native platform styling | ✅ | ✅ | ❌ | ❌ | ❌ | ❌

### Element Rendering

Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Spacing and Separator | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ 
TextBlock DATE/TIME formatting | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
TextBlock Markdown support | ❌* | ❌ | ❌ | ❌ | ❌ | ❌
Full Input support | ✅ | ✅ | ✅ | ❌ | ❌ | ❌

\* The HTML renderer doesn’t include built-in Markdown support in order to minimize the size of the library and to let consuming applications use their preferred Markdown processor. The HTML renderer will however automatically use Markdown-It if it is loaded.

### Extensbility

Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Override Element Renderer | ✅ | ✅ | ✅ | ❌ | ✅ | ❌
Add new Element Renderer | ✅ | ✅ | ✅ | ❌ | ✅ | ❌
Remove Element Renderer | ✅ | ✅ | ✅ | ❌ | ✅ | ❌

### Actions

Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Action.OpenUrl support | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Action.ShowCard support  | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Action.Submit support  | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
selectAction support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

### Events

|       Functionality        | HTML | .NET | UWP | iOS | Android | React |
|----------------------------|------|------|-----|-----|---------|-------|
| Element visibility changed |  ✅   |  ❌   |  ❌  |  ❌  |    ❌    |   ❌   |

