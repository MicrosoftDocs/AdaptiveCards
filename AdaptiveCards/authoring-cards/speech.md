---
title: Speech and Advanced Customization
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
---

# Speech and advanced customization
We live in an era of speech interaction via services like Cortana.  Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.

The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving. 

## Speak property
To support speech we have a `speak` property which contains text to say to the user. The text can be annotated using speech synthesis markup language
([SSML](/previous-versions/office/developer/speech-technologies/hh361578(v=office.14))). SSML controls the speed, tone, and inflection of the speech.  It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.

There are two patterns for speak property usage by a host application:

* **On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.
* **On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element. The client may read a Speak property  for each element in the card.

### Examples

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## Speech content design

Content designed for speech is different from content designed for visual display. When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them. When designing for speech, you should think about how to verbally describe the content in a way that delights the user.