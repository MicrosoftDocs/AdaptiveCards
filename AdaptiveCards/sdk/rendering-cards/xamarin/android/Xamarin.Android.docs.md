# Xamarin.Android API Documentation

## Table of Contents 

1. [Object Model](#object-model)
    1. [AdaptiveCard]()
        1. [Summary](#adaptive-card-summary)
        1. [Public Constructors](#adaptive-card-public-ctors)
        1. [Public Methods](#adaptive-card-public-methods)
    1. [FeatureRegistration]() 
        1. [Summary]()
        1. [Public Methods]()
    1. [ParseResult]
        1. [Summary]()
        1. [Public Constructors]()
1. [Renderer](#renderer)
    1. 
1.

## <a name="object-model"></a> Object Model

--- 

### AdaptiveCard

``` C#
public class AdaptiveCard : Java.Lang.Object 
```

### Summary

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

<strong>Public Constructors</strong>
<hr/>

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

| Public methods | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](http://something.com) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```]() |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```]() |
| ```string``` | [```Serialize()```]() |
| ```JsonValue``` | [```SerializeToJsonValue()```]() |

## Public Constructors
<hr/>

### <a name="ctor0"></a> AdaptiveCard
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
| version | string |
| fallbackText | string |
| backgroundImage | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage |
| style | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle |
| speak | style |
| language | string |
| verticalContentAlignment | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment |
| height | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType |
| minHeight | long |

<br/><br/>

### <a name="ctor1"></a> AdaptiveCard
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
| version | string |
| fallbackText | string |
| backgroundImage | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage |
| style | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle |
| speak | style |
| language | string |
| verticalContentAlignment | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment |
| height | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType |
| minHeight | long |
| body | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector |
| actions | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector |

<br/><br/>

### <a name="ctor2"></a> AdaptiveCard
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
| version | string |
| fallbackText | string |
| backgroundImage | string |
| style | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle |
| speak | style |
| language | string |
| verticalContentAlignment | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment |
| height | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType |
| minHeight | long |

<br/><br/>

### <a name="ctor3"></a> AdaptiveCard
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
| version | string |
| fallbackText | string |
| backgroundImage | string |
| style | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle |
| speak | style |
| language | string |
| verticalContentAlignment | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment |
| height | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType |
| minHeight | long |
| body | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector |
| actions | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector |


## Public Methods

### <a href="funcDeserializeFromString"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| jsonString | string |
| rendererVersion | string |

| Returns | |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult | |

#### Sample

Here goes a sample :)

### <a href="funcDeserializeFromString"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| jsonString | string |
| rendererVersion | string |
| AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext | context |

| Returns | |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult | |

#### Sample

Here goes a sample :)

### <a href="funcDeserializeFromString"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| fallbackText | string |
| language | string |
| speak | string |

| Returns | |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard  | |

#### Sample

Here goes a sample :)

### <a href="funcDeserializeFromString"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public string Serialize ()
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Returns | |
| --- | --- |
| string | |

### <a href="funcDeserializeFromString"></a> DeserializeFromString
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public JsonValue SerializeToJsonValue ()
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Returns | |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue | |



























--- 

### Feature Registration

``` C#
public class FeatureRegistration : Java.Lang.Object 
```

### Summary

| Public methods | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](http://something.com) |
| ```string``` | [```GetFeatureVersion(string featureName)```]() |
| ```void``` | [```RemoveFeature (string featureName)```]() |

## Public Methods

### <a href="feature-registation-func-addfeature"></a> AddFeature
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public void AddFeature (string featureName, 
                        string featureVersion)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| featureName | string |
| featureVersion | string |

#### Sample

Here goes a sample :)

### <a href="funcDeserializeFromString"></a> GetFeatureVersion
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public string GetFeatureVersion (string featureName)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| featureName | string |

| Returns | |
| --- | --- |
| string | |

#### Sample

Here goes a sample :)

### <a href="funcDeserializeFromString"></a> RemoveFeature
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public void RemoveFeature (string featureName)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| featureName | string |

#### Sample

Here goes a sample :)







































--- 

### ParseResult

``` C#
public class ParseResult : Java.Lang.Object 
```

### Summary

| Attributes | |
| ---- | --- |
| AdaptiveCard | The Actions to show in the card’s action bar. |
| Warnings | Specifies the background image of the card. |

<strong>Public Constructors</strong>
<hr/>

<a href="#parse-result-ctor0"><div>

``` C#
public ParseResult (AdaptiveCard adaptiveCard, AdaptiveCardParseWarningVector warnings)
```
</div></a>

## Public Constructors
<hr/>

### <a name="parse-result-ctor0"></a> AdaptiveCard
<p style='text-align:right'>Added in version 0.1</p>

``` C# 
public ParseResult (AdaptiveCard adaptiveCard, 
                    AdaptiveCardParseWarningVector warnings)
```

| Parameters | |
| --- | --- |
| adaptiveCard | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard |
| warnings | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCardParseWarningVector |









































## <a name="object-model"></a> Renderer

--- 

### ICardActionHandler

``` C#
public interface ICardActionHandler : IJavaObject 
```

### Summary

| Public methods | |
| --- | ---- |
| ```abstract void``` | [```OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)```](http://something.com) |
| ```abstract void``` | [```OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)```]() |
| ```abstract void``` | [```OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)```]() |

## Public Methods

### <a href="icardactionhandler-func-onaction"></a> OnAction
<p style='text-align:right'>Added in version 0.1</p>

``` C#
void OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| p0 | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElement |
| p1 | AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard |

#### Sample

Here goes a sample :)

### <a href="icardactionhandler-func-onmediaplay"></a> OnMediaPlay
<p style='text-align:right'>Added in version 0.1</p>

``` C#
void OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| p0 | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement |
| p1 | AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard |

#### Sample

Here goes a sample :)

### <a href="icardactionhandler-func-onmediastop"></a> OnMediaStop
<p style='text-align:right'>Added in version 0.1</p>

``` C#
void OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| p0 | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement |
| p1 | AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard |

#### Sample

Here goes a sample :)








































### AdaptiveCardRenderer

``` C#
public class AdaptiveCardRenderer : global::Java.Lang.Object
```

### Summary

| Public methods | |
| --- | ---- |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler)```](http://something.com) |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler, HostConfig hostConfig)```]() |

## Public Methods

### <a href="adaptivecardrenderer-func-render0"></a> Render
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public RenderedAdaptiveCard Render (Context context, 
                                    FragmentManager fragmentManager, 
                                    AdaptiveCard adaptiveCard,
                                    ICardActionHandler cardActionHandler)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| context | Android.Content.Context |
| fragmentManager | Android.Support.V4.App.FragmentManager |
| adaptiveCard | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard |
| cardActionHandler | AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler |

| Returns |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard | |

#### Sample

Here goes a sample :)

### <a href="adaptivecardrenderer-func-render1"></a> Render
<p style='text-align:right'>Added in version 0.1</p>

``` C#
RenderedAdaptiveCard Render (Context context, 
                            FragmentManager fragmentManager, 
                            AdaptiveCard adaptiveCard, 
                            ICardActionHandler cardActionHandler, 
                            HostConfig hostConfig)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| context | Android.Content.Context |
| fragmentManager | Android.Support.V4.App.FragmentManager |
| adaptiveCard | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard |
| cardActionHandler | AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler |
| hostConfig | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HostConfig |

| Returns | |
| --- | --- |
| AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard | |

#### Sample

Here goes a sample :)


























### CardRendererRegistration

``` C#
public class CardRendererRegistration : Java.Lang.Object
```

### Summary

| Public methods | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](http://something.com) |

## Public Methods

### <a href="cardrendererregistration-func-registerfeatureregistration"></a> RegisterFeatureRegistration
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| featureRegistration | AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration |

#### Sample

Here goes a sample :)
















































### RenderedAdaptiveCard

``` C#
public class RenderedAdaptiveCard : Java.Lang.Object
```

### Summary

| Attributes | |
| ---- | --- |
| AdaptiveCard | <Info> |
| Inputs | <Info> |
| View | <Info> |
| Warnings | <Info> |

| Public methods | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](http://something.com) |

## Public Methods

### <a href="renderedadaptivecard-func-addwarning"></a> AddWarning
<p style='text-align:right'>Added in version 0.1</p>

``` C#
public void AddWarning (AdaptiveWarning warning)

```

Deserializes the given adaptive card as a json string for the specified renderer version.

| Parameters | |
| --- | --- |
| warning | AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning |


#### Sample

Here goes a sample :)