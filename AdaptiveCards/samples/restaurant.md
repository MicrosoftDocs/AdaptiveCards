---
title:  Sample of Restaurant
author: luywang
description: This page provides a sample code for Restaurant Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Restaurant

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!


These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Restaurant sample

The following section displays the JSON for a "Restaurant" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "Image",
			"url": "https://adaptivecards.io/content/WestSeattle.jpg",
			"altText": "A photograph of an aerial view of a city street at sunset.",
			"size": "stretch"
		},
		{
			"type": "TextBlock",
			"text": "The Restaurant",
			"size": "large",
			"weight": "bolder",
			"wrap": true,
			"style": "heading"
		},
		{
			"type": "TextBlock",
			"text": "4507 SW Genesee St, Seattle, WA 98116",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "This is an example restaurant that serves American cuisine. Open Tuesday to Friday from 11:30 AM to 1:30 PM and 4 PM to 9 PM, Saturday and Sunday from 4 PM to 9 PM, closed on Monday.",
			"wrap": true
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Visit Website",
			"url": "http://contososcubademo.azurewebsites.net"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Call Now",
			"url": "tel:555-555-5555"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Order Online",
			"url": "http://contososcubademo.azurewebsites.net"
		}
	]
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"@context": "http://schema.org",
	"@type": "Restaurant",
	"url": "http://contososcubademo.azurewebsites.net",
	"name": "The Restaurant",
	"image": "https://adaptivecards.io/content/WestSeattle.jpg",
	"description": "This is an example restaurant that serves American cuisine.",
	"servesCuisine": ["American cuisine"],
	"telephone": "555-555-5555",
	"address": {
		"@type": "PostalAddress",
		"streetAddress": "4507 SW Genesee St",
		"addressLocality": "Seattle",
		"addressRegion": "WA",
		"postalCode": "98116"
	},
	"openingHoursSpecification": [
		{
			"@type": "OpeningHoursSpecification",
			"dayOfWeek": ["Tuesday", "Wednesday", "Thursday", "Friday"],
			"opens": "11:30",
			"closes": "13:30",
			"opens2": "16:00",
			"closes2": "21:00"
		},
		{
			"@type": "OpeningHoursSpecification",
			"dayOfWeek": ["Saturday", "Sunday"],
			"opens": "16:00",
			"closes": "21:00"
		},
		{
			"@type": "OpeningHoursSpecification",
			"dayOfWeek": ["Monday"],
			"closed": true
		}
	]
}
```

**Template JSON**

```json
{
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"type": "AdaptiveCard",
	"version": "1.5",
	"body": [
		{
			"type": "Image",
			"url": "${image}",
			"altText": "A photograph of an aerial view of a city street at sunset.",
			"size": "stretch"
		},
		{
			"type": "TextBlock",
			"text": "${name}",
			"size": "large",
			"weight": "bolder",
			"style": "heading",
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${address.streetAddress}, ${address.addressLocality}, ${address.addressRegion} ${address.postalCode}",
			"isSubtle": true,
			"wrap": true
		},
		{
			"type": "TextBlock",
			"text": "${description} Open ${openingHoursSpecification[0].dayOfWeek[0]} to ${openingHoursSpecification[0].dayOfWeek[3]} from ${openingHoursSpecification[0].opens} AM to ${openingHoursSpecification[0].closes} PM and ${openingHoursSpecification[0].opens2} PM to ${openingHoursSpecification[0].closes2} PM, ${openingHoursSpecification[1].dayOfWeek[0]} and ${openingHoursSpecification[1].dayOfWeek[1]} from ${openingHoursSpecification[1].opens} PM to ${openingHoursSpecification[1].closes} PM, closed on ${openingHoursSpecification[2].dayOfWeek[0]}.",
			"wrap": true
		}
	],
	"actions": [
		{
			"type": "Action.OpenUrl",
			"title": "Visit Website",
			"url": "${url}"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Call Now",
			"url": "tel:${telephone}"
		},
		{
			"type": "Action.OpenUrl",
			"title": "Order Online",
			"url": "${url}"
		}
	]
}
```

