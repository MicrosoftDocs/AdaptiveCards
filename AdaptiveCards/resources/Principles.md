---
title: Adaptive Card Guiding Principles
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
---

# Motivations behind the Adaptive Card format

- In early 2016, several teams at Microsoft (including Outlook, Windows and the Bot Framework) came to the realization that they all wanted something extremely similar ("cards") and that each of them were designing their own solutions independently:

    - Windows had its own Live Tiles and Notifications format
    - The Bot framework was using a set of predefined card templates developers could choose from when sending Bot messages
    - Outlook was using its own MessageCard format for its Actionable Messages feature

- At the same time, other platforms such as LINE, FaceBook Messenger, Slack and more were also using their own, proprietary "card" format
- So a few Microsoft employees gathered up and started an effort to define one card format and a set of SDKs that:

    - Would facilitate the interchange of cards between hosts
    - Would allow each host to keep control over the styling of cards to ensure visual consistency
    - Would make it easy for a host application to display cards with minimum coding effort via ready-to-use SDKs
    - And that would also provide value to third parties and eventually get adopted widely by the industry

# Principles guiding the Adaptive Card format

1.  **Adaptive Card is a _simple_ and _declarative_ card format**

    1.  It is not meant as an HTML or XAML replacement/alternative

    2.  There is **no "code behind"** with Adaptive Cards

        i. Card authors cannot embed custom/arbitrary code with their payloads, and as a result an Adaptive Card host never needs to run third party code

        ii. Dynamism and interactivity are achieved solely via declarative markup

    3.  This ensures that the effort necessary to build an Adaptive Card SDK for a new platform remains be reasonable

2.  **The Adaptive Card format can't impose the use of any particular underlying technology**

    1.  The Adaptive Card format does not rely on JavaScript, C#, Python or any other language

    2.  Similarly it doesn't rely on HTML or XAML or any other graphic/UI framework

    3.  This way, Adaptive Cards can be rendered natively on any platform for as long as a renderer exists

3.  **The Adaptive Card format is a _shared property_**

    1.  Along with its SDKs, the format is to be open source and its evolution community driven

    2.  The format is therefore not owned nor driven by any one team

4.  **The Adaptive Card format is not designed "just for Microsoft's use"**

    1.  Instead it is designed to suit the needs of a wide variety of applications and use cases

5.  **The _Adaptive Card Working Group_ governs the evolution of the format**

    1.  This working group is comprised of a set of Microsoft employees that are all deeply involved in the success of the format

    2.  The Working Group conducts weekly meetings (currently on Monday) during which feature proposals are reviewed, open issues are discussed 
    and triaged and overall progress on vNext work items is tracked

    3.  The Working Group uses feedback from the community at large, including internal Microsoft teams, to decide how the format evolves

    4.  To be approved by the Working Group, proposed new features:

        i. Must be justified by real life use cases

        ii. Must have a functional specification

    5.  Approved new feature are added to the backlog and considered for vNext

        i. The criteria used to prioritize new features include the breadth of scenarios the feature enables, its complexity/maintainability and more

        ii. When in doubt, keep it out! It's a lot easier to introduce a well designed feature later than to live with a mistake forever.

    6.  All new features are implemented in all supported SDKs

    7.  All new features are documented and associated with a test card published in the samples folder

    8.  New versions of the format and SDKs go through a beta phase

    9.  The release schedule for Adaptive Card schema and SDK versions is driven by quality, not date

6.  **The format needs to be extensible**

    1.  Hosts should have the freedom of adding support for custom elements or custom actions that go beyond what the format is capable of

    2.  This is particularly important for actions, as various hosts don't necessarily support the same set of actions

    3.  These additions are at the discretion of the host

        i. They are not a *de facto* addition to the Adaptive Card specification

        ii. As such, they make a payload that uses them incompatible with the mainstream Adaptive Card format

        iii. They can however be presented to the Working Group and proposed as new features for a future version of the format, as described in point #5

7.  **Card authors own the content, host apps own the look and feel**

    1.  Host apps impose their styling so cards look and feel like they are native extensions of the app's experience

    2.  Card authors can still specify styling, but only via semantic expressions of colors, sizes, etc.

8.  **SDKs are available for the most popular developer platforms**

    1.  SDKs make it easy to render Adaptive Card payloads in any host

    2.  This ensures the barrier to entry is as low as can be both for third party developers and Microsoft teams

    3.  A this time, Adaptive Cards offers SDKs for:

        i. HTML/JavaScript (suitable for ReactJS development)

        ii. iOS (UIKit)

        iii. Android

        iv. UWP

        v. ASP.NET

        vi. .NET WPF

        vii. Server-side rendering to image using WPF

        viii. Xamarin in preview

        ix. A React Native SDK is underway