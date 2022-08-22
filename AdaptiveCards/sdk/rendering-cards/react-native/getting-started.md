---
title: ReactNative SDK
description: Adaptive Card rendering SDK for ReactNative
author: matthidinger
ms.author: mahiding
ms.date: 08/03/2022
ms.topic: article
---

# ReactNative Renderer

A [community-supported](/lifecycle/end-of-support/end-of-support-2020) ReactNative renderer for Adaptive Cards, maintained by [BigThinkCode](https://www.bigthinkcode.com).

> [!IMPORTANT]
>
> **Community Support Only**. This renderer is in active development but is maintained outside of Microsoft. **As such, we cannot guarantee any SLA for this SDK**. Please see our [Support policy](/lifecycle/end-of-support/end-of-support-2020) for more details. 
>

## Getting started

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

## Full documentation and source code

* [Documentation](https://www.npmjs.com/package/adaptivecards-reactnative)
* [Source code](https://github.com/BigThinkcode/AdaptiveCards/tree/master/source/community/reactnative)

## Customization and Themeing

To customize the rendering, please see the [theme config](./theme-config.md) documentation.
