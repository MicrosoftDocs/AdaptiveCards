---
title: CardRendererRegistration class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# CardRendererRegistration

```csharp
public class CardRendererRegistration : Java.Lang.Object
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### Summary

| Public methods | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](#registerfeatureregistration) |

## Public Methods

--- 

### <a id="registerfeatureregistration"></a> RegisterFeatureRegistration
<p style='text-align:right'>Added in version 0.1.0</p>

```csharp
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Registers a [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) object for the card renderer to use.

| Parameters | |
| --- | --- |
| featureRegistration | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) |

#### Sample

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```