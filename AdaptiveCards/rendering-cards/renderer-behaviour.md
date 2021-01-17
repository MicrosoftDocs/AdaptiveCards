

---
title: Renderer Behaviour Guide
ms.topic: article
---


# Adaptive Card Renderer Behaviour Guideline

The following specification describes the design guideline to be followed when implementing the behaviour of a renderer with respect to parsing the relationship between the card elements. 
> [!IMPORTANT]
> 
> This content is not finished yet. Check back shortly.


## Behaviours 

The Renderer **MUST** take care to the following behaviours when rendering card elements with respect to the attributes provided. 

1. **Constraints**
2. **Image Size**
3. **Action.Submit**

## Constraints

The **Constraints** behaviour takes into the account the various factors such as margin, padding, height and width etc configuration of the card elements and its children. It also specifies the order of precedence at which the constraints will be set up when multiple attributes are provided in a nested setup. 


## Width 

2. Possible values  `auto` and `stretch` 
3. Fixed values can also be provided in terms of `weightage` and `pixels`
4. `auto` provides sufficient space for expansion of width (supports min expansion)
5. `stretch` takes up the remaining width (supports max expansion)

Below below scenarios describes how the constraints are affected with different width combinations for columns

### `auto` vs `stretch`
1. Columns with `auto` and `stretch` width.

![Column with auto and stretch width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_1_auto_stretch.png)

The first column with auto width takes sufficient space to display the content and the second column with stretch width takes up the entire space.

2. Columns with only `stretch` width

![Column with only stretch width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_2_stretch_stretch.png)

Columns with only stretch width takes up the remaining spaces after dividing it equally.

3. `auto`,`stretch` and `auto` 

![Column with auto and stretch combination width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width3_auto_stretch_auto.png)

The **first** and **third** columns width is adjusted first to accommodate the elements sufficiently and the **second** column with stretched width takes up the remaining space. 

4. Order of displaying elements with `auto` width columns

![Columns with auto width](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width6_all_auto.png)

The columns with all auto width is adjusted to occupy the text block sufficiently. The image sizes in the first and second column is readjusted to make room for the text block in column three. 

### `weighted` vs `pixels`

1. Columns with `weight` and `pixel width` combination

![Columns with weightage and pixel width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width_4_w50_p100_w50.png)

The above card has three columns with the following width configuration - \
*Column1* Weighted 50, *Column2* Pixel width 100, *Column3* Weighted 50\
The width of Column 2 is determined by the **pixel value** \ 
The width of Column 1 and 3 is adjusted based on the **weight value** and the calculated **weight ratio**.

2. Columns with `weight`, `pixel width` and `auto` attributes

![Columns with weightage and pixel width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/width5_w50_p100_w50_auto.png)

The above card has the same configuration as the one before this with addition to a column with `auto` width.\
The `pixel width` and `weighted` takes more priority as `auto` as  the last column had to adjust the image size accordingly. 

### Precedence order of displaying elements with the width attribute
`pixels` > `weighted` > `auto` > `stretch` 


## Height 

 Possible values  `auto` and `stretch` 

Below  scenarios describes how the constraints are affected with different height combinations for card elements

1. Elements expand freely vertically when card is not of fixed height

![Columns with weightage and pixel width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/height1_text_wrap_off.png)

Both the columns can expand sufficiently vertically irrespective of `auto` and `stretch` values\
This is with the `wrap` property disabled for the text block.

![Columns with weightage and pixel width combination](https://github.com/manujai/AdaptiveCards/blob/doc_renderer_behaviour/AdaptiveCards/content/height2_text_wrap_on.png)

This card has the `wrap` property enabled for the text block. 



