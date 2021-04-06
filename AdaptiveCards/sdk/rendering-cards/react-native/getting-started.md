---
title: ReactNative SDK
author: matthidinger
ms.author: mahiding
ms.date: 03/15/2021
ms.topic: article
---

# ReactNative Renderer

A [community-supported](https://github.com/microsoft/AdaptiveCards/blob/main/SUPPORT.MD) ReactNative renderer for Adaptive Cards, maintained by [Imaginea](https://imaginea.com).

## Getting started

> [!IMPORTANT]
>
> **Community Support Only**. This renderer is in active development but is maintained outside of Microsoft. **As such, we cannot guarantee any SLA for this SDK**. Please see our [Support policy](https://github.com/microsoft/AdaptiveCards/blob/main/SUPPORT.MD) for more details. 
>

### Install the package

`npm install adaptivecards-reactnative`

### Import the root component

`import AdaptiveCard from 'adaptivecards-reactnative'`

### Render the component with required props

```jsx
<AdaptiveCard payload={} 
               hostConfig={}
               themeConfig={}
               onExecuteAction={} 
               onParseError={} 
               containerStyle={{
                    width:100, 
                    height: 100, 
                    flexGrow:1, 
                    backgroundColor:'lightblue'
               }}
               contentContainerStyle={{
                    flexGrow: 1, 
                    justifyContent: 'space-between'
               }}
               contentHeight={500} 
               ref="referenceVariable"/>
```

### Full documentation and source code

* [Documentation](https://www.npmjs.com/package/adaptivecards-reactnative)
* [Source code](https://github.com/microsoft/AdaptiveCards/tree/master/source/community/reactnative)

## Customization and Themeing

To customize the rendering, please see the [theme config](./theme-config.md) documentation.