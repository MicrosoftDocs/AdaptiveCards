# Renderer Status
The following functionality should be included in every Adaptive Cards renderer.

> [!IMPORTANT]
> 
> This content is not finished yet and some major pieces are missing. Check back shortly.


### Parsing
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Return validation failures | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Parse unknown properties | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

### Card Rendering
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Check for supported version | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
Render full schema | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Render actions bar | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Ignore unknown Elements | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Host Config support | ✅ | ✅ | ✅ | ✅ | ✅ | ❌
Native platform styling | ✅ | ✅ | ❌ | ❌ | ❌ | ❌

### Element Rendering
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Spacing and Separator | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ 
TextBlock DATE/TIME formatting | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ 
TextBlock Markdown support | ✅ | ✅ | ❌ | ❌ | ❌ | ❌
Full Input support | ✅ | ✅ | ✅ | ❌ | ❌ | ❌

### Extensbility
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Override Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌
Add new Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌
Remove Element Renderer | ✅ | ✅ | ❌ | ❌ | ✅ | ❌

### Actions
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Action.OpenUrl support | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Action.ShowCard support  | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
Action.Submit support  | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ 
selectAction support | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 

### Events
Functionality | HTML | .NET | UWP | iOS | Android | React
--- | --- | --- | --- | --- | --- | ---
Element visibility changed | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ 
