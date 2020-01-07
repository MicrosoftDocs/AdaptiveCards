---
title: FeatureRegistration class - Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
---

# Feature Registration

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## Summary

| Public methods | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## Public Methods

---

### <a id="addfeature"></a> AddFeature
<p style='text-align:right'>Added in version 0.1.0</p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

Adds a feature containing its name and version to the renderer feature registration.

| Parameters | |
| --- | --- |
| featureName | ```string``` |
| featureVersion | ```string``` |

#### Sample

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a> GetFeatureVersion
<p style='text-align:right'>Added in version 0.1.0</p>

```csharp
public string GetFeatureVersion (string featureName)
```

Retrieves the version for a given feature. 

| Parameters | |
| --- | --- |
| featureName | ```string``` |

| Returns | |
| --- | --- |
| ```string``` | Feature version for the given feature |

#### Sample

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a> RemoveFeature
<p style='text-align:right'>Added in version 0.1.0</p>

```csharp
public void RemoveFeature (string featureName)
```

Removes the given feature from the feature dictionary.

| Parameters | |
| --- | --- |
| featureName | ```string``` |

#### Sample

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```