---
title: Extensibility - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Extensibility - iOS

## Changing per element rendering

Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.
Following example shows how one can change background color of NumberInput.

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## Additional Property

 Developers can also send in additional properties as part of json payload.
 For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.
 Additional property is returned as NSData and accessbile from `ACOBaseCardElement` and `ACOBaseActionElement`. The NSData should be deserialized into NSDictionary to access. 

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```
### Objective-C Example
 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```

### Swift Example
```swift
if let props = acoElem.additionalProperty() {
            if let dictionary = try JSONSerialization .jsonObject(with: props, options: JSONSerialization.ReadingOptions.mutableLeaves) as? [NSString: Any]{
                let radius = (dictionary["radius"] as! NSNumber).floatValue
            }       
```
 ## Custom Parsing

Developers can also have custom parsing and have new UI element added to adpative card such as progress bar. Please check CustomProgressBarRenderer.mm for detail.
Custom parser must implement ACOIBaseCardElementParser protocol. deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```

## Resource Resolver
AdaptiveCards renderer users can use resource resolver to have more control in the image loading. 
1. Create ACOResourceResolvers
2. Create ADCResolver
3. Register the ADCResolver to the ACOResourceResolvers per URL scheme; the scheme can be any string.
4. Call fromJson method of ACOHostConfig with the ACOResourceResolvers

```objective-c
        ACOResourceResolvers resolvers = [[ACOResourceResolvers alloc] init];
        ADCResolver *resolver = [[ADCResolver alloc] init];
        [resolvers setResourceResolver:resolver scheme:@"http"];
        [resolvers setResourceResolver:resolver scheme:@"https"];
        [resolvers setResourceResolver:resolver scheme:@"data"];
        // register a custom scheme bundle with resolver
        [resolvers setResourceResolver:resolver scheme:@"bundle"];
        ACOHostConfigParseResult *hostconfigParseResult = [ACOHostConfig fromJson:hostConfig
                                                            resourceResolvers:resolvers];
```

### [ADCResolver](https://github.com/microsoft/AdaptiveCards/blob/main/source/ios/AdaptiveCards/ADCIOSVisualizer/ADCIOSVisualizer/ADCResolver.m)
- Adopts [ACOIResourceResolver](https://github.com/microsoft/AdaptiveCards/blob/main/source/ios/AdaptiveCards/AdaptiveCards/AdaptiveCards/ACOIResourceResolver.h) protocol
- AdaptiveCards renderer asks UIImageView via `(UIImageView *)resolveImageViewResource:(NSURL *)url`. ADCResolver can either hand over UIImageView with empty UIImage or UIImageView with UIImage.
- If the UIImage was empty, when UIImage is set to the UIImageView in the resolver, the renderer will get notified via KVO and trigger layout update.
- simple objective-c example

```objective-c
- (UIImageView *)resolveImageViewResource:(NSURL *)url
{
    __block UIImageView *imageView = [[UIImageView alloc] init];
    // check if custom scheme bundle exists
    if ([url.scheme isEqualToString:@"bundle"]) {
        // if bundle scheme, load an image from sample's main bundle
        UIImage *image = [UIImage imageNamed:url.pathComponents.lastObject];
        imageView.image = image;
    } else {
        NSURLSessionDownloadTask *downloadPhotoTask = [[NSURLSession sharedSession]
            downloadTaskWithURL:url
              completionHandler:^(NSURL *location, NSURLResponse *response, NSError *error) {
                  // iOS uses NSInteger as HTTP URL status
                  NSInteger status = 200;
                  if ([response isKindOfClass:[NSHTTPURLResponse class]]) {
                      status = ((NSHTTPURLResponse *)response).statusCode;
                  }
                  if (!error && status == 200) {
                      UIImage *image = [UIImage imageWithData:[NSData dataWithContentsOfURL:location]];
                      if (image) {
                          dispatch_async(dispatch_get_main_queue(), ^{
                              imageView.image = image;
                          });
                      }
                  }
              }];
        [downloadPhotoTask resume];
    }
    return imageView;
}
```
