---
title: CardRendererRegistration class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

### CardRendererRegistration

``` C#
public class CardRendererRegistration : Java.Lang.Object
```

**Namespace**
``` C#
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### Summary

| Public methods | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](http://something.com) |

## Public Methods

--- 

### <a href="cardrendererregistration-func-registerfeatureregistration"></a> RegisterFeatureRegistration
<p style='text-align:right'>Added in version 0.1.0</p>

``` C#
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Registers a [```FeatureRegistration```]() object for the card renderer to use.

| Parameters | |
| --- | --- |
| featureRegistration | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration``` |

#### Sample

``` C#
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```