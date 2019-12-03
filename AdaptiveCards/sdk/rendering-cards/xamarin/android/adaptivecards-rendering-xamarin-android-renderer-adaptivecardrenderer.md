---
title: AdaptiveCardRenderer class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

### AdaptiveCardRenderer

``` C#
public class AdaptiveCardRenderer : global::Java.Lang.Object
```

**Namespace**
``` C#
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### Summary

| Public methods | |
| --- | ---- |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler)```](http://something.com) |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler, HostConfig hostConfig)```]() |

## Public Methods

---

### <a href="adaptivecardrenderer-func-render0"></a> Render
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public RenderedAdaptiveCard Render (Context context, 
                                    FragmentManager fragmentManager, 
                                    AdaptiveCard adaptiveCard,
                                    ICardActionHandler cardActionHandler)
```

Renders the specified adaptive card with default values for the host config.

| Parameters | |
| --- | --- |
| context | ```Android.Content.Context``` |
| fragmentManager | ```Android.Support.V4.App.FragmentManager``` |
| adaptiveCard | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` |
| cardActionHandler | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler``` |

| Returns |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard``` | |

#### Sample

``` C#
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler);
```

---

### <a href="adaptivecardrenderer-func-render1"></a> Render
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
RenderedAdaptiveCard Render (Context context, 
                            FragmentManager fragmentManager, 
                            AdaptiveCard adaptiveCard, 
                            ICardActionHandler cardActionHandler, 
                            HostConfig hostConfig)
```

Renders the specified adaptive card with using the given host config.

| Parameters | |
| --- | --- |
| context | ```Android.Content.Context``` |
| fragmentManager | ```Android.Support.V4.App.FragmentManager``` |
| adaptiveCard | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` |
| cardActionHandler | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler``` |
| hostConfig | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HostConfig``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard``` | |

#### Sample

``` C#
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler, hostConfig);
```