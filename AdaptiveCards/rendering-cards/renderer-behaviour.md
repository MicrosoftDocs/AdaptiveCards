---
title: Renderer Behaviour Guideline
author: manujai
ms.author: manujai
---


# Adaptive Card Renderer Behaviour Guideline

The following specification describes the design guideline to be followed when implementing the behaviour of a renderer with respect to parsing the relationship between the card elements. 
> [!IMPORTANT]
> 
> This content is not finished yet. Check back shortly.


## Behaviours 

The Renderer **MUST** take care to the following behaviours when rendering card elements with respect to the attributes mentioned in this doc. 

1. **Constraints**
2. **Image Size**
3. **Action.Submit**

## Constraints

The renderer should manage **Constraints** taking into account the various factors such as margin, padding, height and width etc configuration of the card elements and its children.

## Width 

1. Allowed values - `auto`, `stretch` and fixed values in terms of `pixels` and `weight`
2. `auto` provides sufficient space for expansion of width (supports min expansion)
3. `stretch` takes up the remaining width (supports max expansion)

Below below scenarios describes how the constraints are affected with different width combinations for columns

### `auto` vs `stretch`
1. Columns with `auto` and `stretch` width.

![Column with auto and stretch width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_1_auto_stretch.png)

* The first column with `auto` width takes sufficient space to display the content and the second column with `stretch` width takes up the entire space.

2. Columns with only `stretch` width

![Column with only stretch width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_2_stretch_stretch.png)

* Columns with only stretch width takes up the remaining spaces after dividing it equally.

3. `auto`,`stretch` and `auto` 

![Column with auto and stretch combination width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width3_auto_stretch_auto.png)

The **first** and **third** columns width is adjusted first to accommodate the elements sufficiently and the **second** column with stretched width takes up the remaining space. 

4. Order of displaying elements with `auto` width columns

![Columns with auto width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width6_all_auto.png)

* Columns with `auto` will position themselves to provide ample space for the content to render. 
* In case of **Image views**, images will downscale to fit the remaining width. 
* **Note:** Images will downscale only for `stretch` and `auto` image size, but not for fixed width and height in pixels.    

### `weights` vs `pixels`

1. Columns with `weight` and `pixel` width combination

![Columns with weightage and pixel width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_4_w50_p100_w50.png)

* The above card has three columns with the following width configuration - 
* `Column1: Weight 50`, `Column2: 100px`, `Column3: Weight 50`
* The width of Column 2 is determined by the `pixel value`
* The width of Column 1 and 3 is adjusted based on the `weights` and the calculated `weight ratio`.

2. Columns with `weight`, `pixel width` and `auto` attributes

![Columns with wight, pixel width and auto combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width5_w50_p100_w50_auto.png)

* The above card has four columns with the following width configuration - 
* `Column1: Weight 50`, `Column2: 100px`, `Column3: Weight 50`, and `Column4: auto`
* **Note:** Image view with `auto` width column downscales to adjust to the remaining space. 

### Precedence order of displaying elements with the width attribute
`px` > `weight` > `auto` > `stretch`


## Height 

 Allowed values - `auto` and `stretch` 

Below  scenarios describes how the constraints are affected with different height combinations for card elements

1. Elements expand freely vertically when card is not of fixed height

![Columns with auto and stretch height](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/height1_text_wrap_off.png)

* Both the columns can expand sufficiently vertically irrespective of `auto` and `stretch` values
* This is with the `wrap` property disabled for the text block.

2. The card below has the `wrap` property enabled for the text block. 

![Column with wrap property for text block](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/height2_text_wrap_on.png)


## Spacing and Separator

 1. **Spacing** - Allowed values `none`, `small`, `default`, `medium`, `large`, `extra large` and `padding` 

* Spacing attribute adds spacing between this element and the preceding element.

![Elements with different spacing combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/spacing1.png)

* Spacing attribute does not have any effect when its the first element in the view container. 

![Element where spacing has no effect](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/spacing_no_effect.png)

* The elements marked with arrow are the first elements among its siblings, so spacing has no effect. 

 2. **Separator** - Possible values (on/off toggle)

* Draws a seperating line at the top of the element.

![Elements with seperator attribute](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/spacing3_seperator.png)

3. **Spacing and Seperator combination**

* The constraints of the spacing and the seperator combination are illustrated below. 

![Spacing and seperator combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/spacing4_with_seperator.png)

* The overall spacing distance is maintained with respect to the values provided.
* The seperator is added halfway in the middle of the spaced distance.

[Note. Need to confirm the distance where the seperator is inserted in the spacing area. Seems like the middle]

## Container Styles

* Provides styling hints for containers such as columns and columnset
* Allowed values `none`, `default`, `emphasis`, `good`, `attention`, `warning` and `accent`
* These predefined style options provides padding for the elements within the container and background color


![Columns and ColumnSet Style Combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/style1.png)

1. Card A illustrates columns and columnset with no style options
2. Card B illustrates columnset with **Attention** style. Notice the padding within the columnset container and the change in background color. 
3. Card C illustrates columns with styling only. Similar to the previous one, column includes padding and background change. 
4. Card D illustrates columns and columnset both with style options.

[Note. Need to check how the padding amount is determined. Is it determined by the host? ]

## Bleed

* This property allows the container such as columns and columnset to bleed through its parent. 
* Possible values `on` and `off`.


![Column with bleed property](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/style2_withBleed.png)

1. Card A illustrates columns and columnset with regular styling.
2. Card B illustrates the first column with bleed option. The content just bleeds through its boundaries to its parent's. 
 
## Image Size

### `Size` attribute
* Allowed values - `auto`, `stretch`, `small`, `medium`, `large`
* `auto` : Images will scale down to fit if needed, but will not scale up to fill the area.
* `stretch` : Image with both scale down and up to fit as needed.
* `small`, `medium` and `large`: Image is displayed with a fixed width, where the width is determined by the host.

1. `auto` vs `stretch`

![Image with auto and stretch behaviour](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/image_size_auto_stretch.png)

2. Column width and Image Size combination

![Column width and image size combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/imagesize2.png)

* Generally, Columns with `stretch` width allow images to upscale freely with `stretch` size.
* Columns with `auto` width allows image to occupy exact space irrespective of `auto` and `stretch` size of image.
* Column width takes more precedence in determining the image size in this arrangement.

### Image `Width (in pixels)` attribute
* This provides the desired on-screen width of the image. 
* `size` property is overriden when a value is specified

![Column width and image width in pixels combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/image_size_3.png)
* The column with `auto` width will have more precedence than `stretch` in providing room for image content in this arrangement. 

### Column Width (weight and pixel) and Image size (auto and stretch) Combination

![Column width and image size combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/column_width_image_width_2.png)
* Images with `auto` size takes sufficient space for expansion (or downscales) within the column constraints of `weight` and `pixel` width. 
* Images with `stretch` size can expand to fill the remaining space within the constraints of column `weight` and `pixel` width. 

## Action.Submit
* `Action.Submit` element gathers input fields, merges with optional data field, and sends an event to the client.
* A significant difference in the element behaviour is present between 1.x and 2.x version of the ACL renderer.

![Column width and image width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/action_submit_behaviour.png)

* `1.x Renderer` - The inputs are collected from all fields irrespective of the where in the hierarchy the input field is present. 
* `2.x Renderer` - The inputs are collected from fields present in parent container or as a sibling of the `Action.Submit` element. 

## Summary
* Column width takes more precedence in determining the size of the image than its image size (auto, stretch, min width etc). 
* The precedence of the column width taken to display its content sufficiently - `px` > `weight` > `auto` > `stretch`
* Image `size` (auto, stretch) is **ignored** when Image `width` and `height` in px is provided. 
* Image `stretch` size attribute will upscale the image only when there is remaining space and column auto is **not** `auto`.
* An image stretches itself to the limit where it maintain its aspect ratio in the space available in the column. In turn, the height expands freely.
* `Spacing` attribute will not have any effect when its the first or the only element among its sibling. 



