---
title:  Adaptive Cards Overview
author: matthidinger
description: Provides an overview of the Adaptive Cards rendering platform
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: concept-article
---

# Adaptive Cards Overview

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

Adaptive Cards are an open card exchange format enabling developers to exchange UI content in a common and consistent way.

> [!VIDEO https://cdn.adaptivecards.io/assets/AdaptiveCardsOverviewVideo.mp4]

**A whole new way to deliver UI**: Adaptive Cards are platform-agnostic snippets of UI, authored in JSON, that apps and services can openly exchange. When delivered to a specific app, the JSON is transformed into native UI that automatically adapts to its surroundings. It helps design and integrate light-weight UI for all major platforms and frameworks.

> [!VIDEO https://cdn.adaptivecards.io/assets/AdaptiveIntroVideo.mp4]

Adaptive Cards are made for:
* [Android](sdk/rendering-cards/android/getting-started.md)
* [iOS](sdk/rendering-cards/ios/getting-started.md)
* [JavaScript](sdk/rendering-cards/javascript/getting-started.md)
* [ASP.NET](sdk/rendering-cards/net-html/getting-started.md)
* [.NET WPF](sdk/rendering-cards/net-wpf/getting-started.md)
* [Windows](sdk/rendering-cards/uwp/getting-started.md)
* [ReactNative](sdk/rendering-cards/react-native/getting-started.md)

### Meet your users where they are
Modern digital life is hectic. Users are constantly switching between devices, apps, and services to get their job done. Adaptive Cards help you increase engagement and efficiency by injecting your actionable content directly into the apps they use every day.

> [!VIDEO https://cdn.adaptivecards.io/assets/Video-MeetYourUsersWhereTheyAre.mp4]

**Integrate into existing apps:**

* [**Teams Adaptive Cards**](/microsoftteams/platform/task-modules-and-cards/cards/cards-reference#adaptive-card): As the digital hub for many modern workers, Teams offers multiple extensibilty points for apps to integrate with. A conversational agent powered by Adaptive Cards can greatly simplify business workflows on your web site or through other channels.
* [**Outlook Actionable Messages**](/outlook/actionable-messages/adaptive-card): Email has long been life-blood of an information worker, and now you can deliver actionable content directly to their inbox.
* [**Windows Timeline**](getting-started/windows.md): Help users resume their activities on any device.

### Open your apps to extensibility

There's an ecosystem of developers out there who want to integrate with your apps, but how can you do so safely and without their content sticking out like a sore thumb? Adaptive Cards are always native and blend seamlessly into the surrounding UI - and they work on every major platform!

[Install the Rendering SDKs >](rendering-cards/getting-started.md)

> [!VIDEO https://cdn.adaptivecards.io/assets/Video-RenderingCards.mp4]

* **Native performance**: Adaptive Cards render native UI on any platform.
* **Adapts to the surrounding UI**: Cards automatically adaptive to the surrounding UI.
* **Fully extensible**: The schema is open-ended so you can add your own element.
* **Dynamic and interactive**: Interactivity is expressed declaratively to help reduce risk of custom code injection

### Design cards anywhere

You don't have to send your users to this website to design cards. Just like Adaptive Cards blend into their surroundings, so does the Adaptive Card Designer. The SDK includes a full configuration API allowing you to deeply integrate card workflows into your existing toolchain.

[Install the Designer SDK >](sdk/designer.md)

> [!VIDEO https://cdn.adaptivecards.io/assets/Video-Designer.mp4?refresh=2019-09-10]

### Create, share, and discover reusable templates

What if you could instantly display any type of data? It could be your own app's data, your organization's data, or data from the web. With Adaptive Card Templating you can separate the data from card layout, and when coupled with a new template service a whole new ecosystem of card exchange becomes possible.

[Create reusable card templates >](templating/index.md)

> [!VIDEO https://cdn.adaptivecards.io/assets/Video-RenderingCards.mp4]

* **Rich designer integration**: Sample data allows you to preview your template without leaving the designer.
* **Simplify development workflows**: Create your template in the designer, use it without your services, then paste it right back into the designer to make changes.
* **Discover and share templates using a REST service**: The template service finds a template for your data, and will even populate it for you.
* **We want to hear from you**: We don't have a release date for this preview yet, but we're waiting to learn from you.

## How they work

[**Card Authors**](authoring-cards/getting-started.md) describe their content as a simple JSON object. That content can then be rendered natively inside a [**Host Application**](rendering-cards/getting-started.md), automatically adapting to the look and feel of the Host.

For example, Contoso Bot can author an Adaptive Card through the Bot Framework, and when delivered to Skype, it will look and feel like a Skype card. When that same payload is sent to Microsoft Teams, it will look and feel like Microsoft Teams. As more host apps start to support Adaptive Cards, that same payload will automatically light up inside these applications, yet still feel entirely native to the app.

Users win because everything feels familiar. Host apps win because they control the user experience. And Card Authors win because their content gets broader reach without any additional work.

## Goals

The goals for Adaptive Cards are:

* **Portable** - To any app, device, and UI framework
* **Open** - Libraries and schema are open source and shared
* **Low cost** - Easy to define, easy to consume
* **Expressive** - Targeted at the long tail of content that developers want to produce
* **Purely declarative** - No code is needed or allowed
* **Automatically styled** - To the Host application UX and brand guidelines

## For Card Authors
Adaptive Cards are great for card authors:

* **One schema** - You get a single format, minimizing the cost of creating a card and maximizing the number of places it can be used.
* **Richer expression** - Your content can more closely align with what you want to say because you have a richer palette to paint with.
* **Broad reach** - Your content will work across a broader set of applications without you having to learn new schemas.
* **Input controls** - Your card can include input controls for gathering information from the user that is viewing the card.
* **Better tooling** - An open card ecosystem means better tooling that is shared by everyone.

## For Experience Owners
If you are an app developer who wants to tap into an ecosystem of third-party content you will love Adaptive Cards because:

* **Consistent user experience** - You guarantee a consistent experience for your users, because you own the style of the rendered card.
* **Native performance** - You get native performance as it targets your UI framework directly.
* **Safe** - Content is delivered in safe payloads so you don't have to open up your UI framework to raw markup and scripting.
* **Easy to implement** - You get off the shelf libraries to easily integrate on any platform you support
* **Free documentation** - You save time because you don't have to invent, implement, and document a proprietary schema.
* **Shared tooling** - You save time because you don't have to create custom tooling.

## Core Design Principles

Adaptive Cards are driven by a set of [guiding principles](resources/principles.md) that have been useful for keeping the design on track.

### Semantic instead of pixel-perfect
We have striven as much as possible for semantic values and concepts as opposed to pure pixel-perfect layout.
Examples of semantic expression show up in colors, sizes, and in elements like FactSet and ImageSet. These all allow the host application to make better decisions about the actual look and feel.

### Card Authors own the content, Host App owns the look and feel
The card authors own what they want to say, but the application displaying it owns the look and feel of the card in the context of their application.

### Keep it simple, but expressive
We want Adaptive Cards to be expressive and general purpose, but we don't want to build a UI framework.  The goal is to create an intermediate layer which is "expressive enough" in the same way Markdown is expressive enough for documents.

By focusing on keeping it simple and expressive, Markdown created an easy and consistent description of document content.  In the
same way, we believe that Adaptive Cards can create a simple, expressive means of describing card content.

### When in doubt, keep it out
It is easier to add later than it is to live with a mistake. If we found ourselves debating whether we should add something or not, we opted to leave it out.  It is always easier to add a property than to live with a legacy we wish we didn't have to support.
