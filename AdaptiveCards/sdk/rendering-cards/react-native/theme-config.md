---
title: ReactNative Themeing and Customization
description: Styling and customization options for the card rendering
author: matthidinger
ms.author: mahiding
ms.date: 03/15/2021
ms.topic: article
---

# ReactNative Customization

## Extensibility Theme Config
* For customizing UI styles of elements, Host App can pass styles (plain JSON object) as an optional prop to root element `<AdaptiveCards/>`.

* Currently below elements are supported in the theme config.
    * input 
    * button
    * choice Set
    * date picker
    * time picker

* Host app can provide `platform-specific` styles as mentioned in the below example. For the same styles across platforms, pass the styles without the platform. 
    * Please note that if you want to provide `platform-specific` styles then you must provide different styles for all the platforms `iOS`, `Android`, and `Windows` explicitly. Please find the below example.

* The `color` and `textTransform` property in the `button` will be applied to the button title. Remaining all styles in the `button` will apply to the React-Native button component.


### Example
In this example, styles passed for element `input` are applied to all the platforms whereas for `button` platform-specific styles are applied. 
```css
    customThemeConfig = {
        input: {
            borderColor: "#000000",
            backgroundColor: "#F5F5F5",
            borderRadius: 4,
            borderWidth: 1,
        },
        button: {
            "ios": {
                color: 'white',
                backgroundColor: "#1D9BF6",
            },
            "android": {
                color: 'white',
                backgroundColor: "#1D9BF6",
            },
            "windows": {
                color: 'white',
                backgroundColor: "#1D9BF6",
            }
        }
    }
    
<AdaptiveCards themeConfig={customThemeConfig} payload={payload} />
```

### Default Theme config

Currently, AdaptiveCards take the below theme config by default. But, the adaptive card developer can override below styles or add new styles using the custom theme config. Please note that the custom styles that are passing to the below elements should be supported in respective React-Native components. 

```css
defaultThemeConfig = {
    button: {
        ios: {
            borderRadius: 15,
            backgroundColor: "#1D9BF6",
            color: "white",
            textTransform: "none"
        },
        android: {
            borderRadius: 15,
            backgroundColor: "#1D9BF6",
            color: "white"
            textTransform: undefined
        },
        windows: {
            borderRadius: 15,
            backgroundColor: "#1D9BF6",
            color: "white",
            textTransform: "none"
        }
    },
    input: {
        borderColor: "#dcdcdc",
        backgroundColor: "white",
        borderRadius: 5,
        borderWidth: 1
    },
    inputDate: {
        width: "100%",
        height: 44,
        padding: 5,
        borderWidth: 1,
        backgroundColor: "white",
        borderColor: "lightgrey",
        borderRadius: 5
    },
    inputTime: {
        width: "100%",
        height: 44,
        padding: 5,
        borderWidth: 1,
        backgroundColor: "white",
        borderColor: "lightgrey",
        borderRadius: 5
    },
    radioButton: {
        width: 24,
        height: 24,
        activeColor: "#000000",
        inactiveColor: "#404040"
    },
    radioButtonText: {
        marginLeft: 8,
        flexShrink: 1,
        activeColor: "#000000",
        inactiveColor: "#404040"
    },
    checkBox: {
        width: 28,
        height: 28,
        activeColor: "#000000",
        inactiveColor: "#404040"
    },
    checkBoxText: {
        marginLeft: 8,
        flexShrink: 1,
        activeColor: "#000000",
        inactiveColor: "#404040"
    },
    dropdown: {
        flexDirection: "row",
        justifyContent: "space-between",
        alignItems: "flex-end",
        borderWidth: 1,
        backgroundColor: "white",
        borderColor: "lightgrey",
        borderRadius: 5
    },
    dropdownText: {
        color: "#000000",
        textAlign: "left",
        marginTop: 10,
        marginLeft: 8,
        height: 30
    }
};
```

