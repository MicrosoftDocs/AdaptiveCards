---
title:  Handling Speech
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Handling speech

To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.

The speech tag can be annotated using  [SSML markup](/previous-versions/office/developer/speech-technologies/hh361578(v=office.14)). 
SSML gives you the ability control the speed, tone, inflection of the speech.  It even allows you to stream audio or a render a TTS audio stream
from your own service, giving you a great deal of customization.

There are 2 patterns for speak property usage by a host application:
* **on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.
* **on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.  
This allows for clients to read each element to recipients with accessibility requirements.