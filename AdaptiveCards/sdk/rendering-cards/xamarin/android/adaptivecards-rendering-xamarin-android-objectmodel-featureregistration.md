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

| Public methods | &nbsp; |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## Public Methods

---

### <a id="addfeature"></a> AddFeature
<p>Added in version 0.1</p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

Adds a feature containing its name and version to the renderer feature registration.

| Parameters | &nbsp; |
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
<p>Added in version 0.1</p>

```csharp
public string GetFeatureVersion (string featureName)
```

Retrieves the version for a given feature. 

| Parameters | &nbsp; |
| --- | --- |
| featureName | ```string``` |

| Returns | &nbsp; |
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
<p>Added in version 0.1</p>

```csharp
public void RemoveFeature (string featureName)
```

Removes the given feature from the feature dictionary.

| Parameters | &nbsp; |
| --- | --- |
| featureName | ```string``` |

#### Sample

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```