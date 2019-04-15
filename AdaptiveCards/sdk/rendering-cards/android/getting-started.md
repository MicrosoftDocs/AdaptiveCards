---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
---

# Getting started - Android

This is a renderer which targets Android native controls.

## Install Maven package

[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

You can find the published packages ![here](https://search.maven.org/search?q=g:io.adaptivecards)

To include library to your project you must include this line into your project gradle.build under the dependencies section

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
You need to change the version number depending on the version you want to include into your project

## Add import

To include the object model, add this import

```
 import io.adaptivecards.objectmodel.*;
```

To include the renderer, add this import

```
 import io.adaptivecards.renderer.*;
```

## Next steps

See [Render a card](render-a-card.md) for the next steps!
