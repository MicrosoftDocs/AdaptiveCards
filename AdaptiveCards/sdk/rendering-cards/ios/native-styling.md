---
title: Native styling - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: concept-article
---

# Native styling - iOS

Use XIB for fine-grained styling.

The following XIBs exist

| XIB | Usage |
|---|---|
| ACRButton.xib | buttons |
| ACRCellForCompactMode.xib   | ChoiceSet compact mode|
| ACRDatePicker.xib | DatePicker for Input.Date |
| ACRDateTextField.xib  | TextField for Input.Date |
| ACRInputTableView.xib   | Container for Inputs |
| ACRLabelView.xib  | TextBlock |
| ACRPickerView.xib | ChoiceSet |
| ACRQuickActionMultilineView.xib  | Quick Actions with multilines |
| ACRQuickActionView.xib | Quick Actions |
| ACRTextField.xib | Input |

XIB can be edited through XCode IB.
Once XIBs are edited to the specification.
From a terminal
```
ibtool --compile name.nib name.xib 
```

For example, to style a button
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

The generated nib files can be then replaced at AdaptiveCards.framework
