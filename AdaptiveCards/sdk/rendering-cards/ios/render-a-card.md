---
title: Render a card - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Render a card - iOS

Here's how to render a card using the iOS SDK.

## Create a card from a JSON string

AdaptiveCard is generated from JSON string

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## Render a Card

Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### Example

```objective-c
ACRRenderResult *renderResult;
ACOHostConfigParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
ACOAdaptiveCardsParseResult *cardParseResult       = [ACOAdaptiveCards FromJson:jsonStr];

// checking parse result
if(hostconfigParseResult.IsValid == YES && cardParseResult.IsValid == YES)
{
    renderResult = [ACRRenderer render:cardParseResult.card
                                config:hostconfigParseResult.config
                       widthConstraint:300.0];
}	
    
if(renderResult.Suceeded == YES)
{
    // access returned UIView object
    ACRView *adaptiveView = renderResult.view;
    [self.view addSubview:adcVc.view];
}
```

### Render a Card as UIViewController

AdaptiveCard renderer can also return UIViewController.

```objective-c
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];

renderResult.viewif(renderResult.Suceeded == YES)
{
    ACRViewController *adaptiveViewController = renderResult.viewcontroller;
    [self addChildViewController:adaptiveViewController];
    [self.view addSubview:adaptiveViewController.view];
    [adaptiveViewController didMoveToParentViewController:self];
    ...
}
```

Returned UIView uses autolayout. Width will be constraint to the value set by widthConstraint. If 0 value is used, it won't be bound.
Height is not bound, and when returned it will have the height of sums of all contents rendered. To bound the view dimension, please use NSLayoutConstraint. The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.


### Compact Style Input.ChoiceSet

UI representation of Input.ChoiceSet has UINavigationController, and it needs to be presented to a presently active UIViewController to transition into UIView that allows user selection.

To accomplish that, please implement didFecthSecondaryView of ACRActionDelegate.

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

If the delgate has not been hooked up, do so.

```objective-c
adaptiveView.acrActionDelegate = self
```