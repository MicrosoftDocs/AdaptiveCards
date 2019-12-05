---
title: AdaptiveCard class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# AdaptiveCard

``` C#
public class AdaptiveCard : Java.Lang.Object 
```

**Namespace**

```C#
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## Summary

| Attributes | |
| ---- | --- |
| Actions | The Actions to show in the card’s action bar. |
| BackgroundImage | Specifies the background image of the card. |
| Body | The card elements to show in the primary card region. |
| ElementType | Must be "AdaptiveCard". |
| FallbackText | Text shown when the client doesn’t support the version specified (may contain markdown). |
| Height | |
| InputNecessityIndicators | |
| Language | The 2-letter ISO-639-1 language used in the card. Used to localize any date/time functions. |
| MinHeight | Specifies the minimum height of the card. |
| SelectAction | An Action that will be invoked when the card is tapped or selected. Action.ShowCard is not supported. |
| Speak | Specifies what should be spoken for this entire card. This is simple text or SSML fragment. |
| Style | |
| Version | Schema version that this card requires. If a client is lower than this version, the fallbackText will be rendered. NOTE: Version is not required for cards within an Action.ShowCard. However, it is required for the top-level card. |
| VerticalContentAlignment | Defines how the content should be aligned vertically within the container. Only relevant for fixed-height cards, or cards with a minHeight specified. |

&nbsp;

**Public Constructors**

---

<a href="#ctor0"><div>
``` C#
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
``` C#
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
``` C#
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
``` C#
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| Public methods | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## Public Constructors
---

### <a id="ctor0"></a> AdaptiveCard
<p style='text-align:right'>Added in version 0.1</p>

``` C# 
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| Parameters | |
| --- | --- |
| version | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a> AdaptiveCard
<p style='text-align:right'>Added in version 0.1</p>

``` C# 
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| Parameters | |
| --- | --- |
| version | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| actions | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a> AdaptiveCard
<p style='text-align:right'>Added in version 0.1</p>

``` C# 
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| Parameters | |
| --- | --- |
| version | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a> AdaptiveCard
<p style='text-align:right'>Added in version 0.1</p>

``` C# 
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| Parameters | |
| --- | --- |
| version | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| actions | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## Public Methods
---
### <a id="deserializefromstring0"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### Sample

```C#
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromtring1"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

Deserializes the given adaptive card as a json string for the specified renderer version using a [ParseContext]() object to handle custom element parsing.

| Parameters | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |
| context | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### Sample

```C#
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a> MakeFallbackTextCard
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| fallbackText | ```string``` |
| language | ```string``` |
| speak | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | Adaptive card that contains the fallback text for an unrendereable card |

#### Sample

```C#
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a> Serialize
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public string Serialize ()
```

Serializes the adaptive card into it's json string form.

| Returns | |
| --- | --- |
| ```string``` | Adaptive card as a json string |

#### Sample

```C#
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a> SerializeToJsonValue
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public JsonValue SerializeToJsonValue ()
```

Serializes the adaptive card into a json value object.

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### Sample

```C#
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```