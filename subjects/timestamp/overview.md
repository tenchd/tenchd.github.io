---
title: Explaining the Amber Project
layout: page
hide: true
permalink: timestamp_overview
---
# Amber: Secure Timestamping
[Amber](timestamp) is a software utility and part of an ongoing effort to create secure timestamps of the digital historical record.

This page covers the motivations behind this effort, the techniques that make Amber work, and how you can help. If you don't know what a secure timestamp is, read [this page](timestamp) first.

Note that this page is also still a work in progress. I'm refining the writing and adding to it regularly.

## Motivation: Hardening the Pre-AI Historical Record
Here's a message I wrote in the first secure timestamp I ever created, in June 2026:

> While the primary challenge of literary and historical conservation efforts across the centuries has been preserving texts, it has also been vital to identify forgeries because they obscure our view of the past.

> If current technological trends continue, large-language models (LLMs) and other forms of generative AI will drastically reduce the cost of creating convincing forgeries of historical texts. In such a case, we can expect a massive flood of such forgeries to be created, for the same reason that spam email is ubiquitous: because spamming is cheap and low-risk for the spammer, and might give them some small benefit. Some of the forgeries will be made maliciously, by political, religious, or corporate actors that seek to rewrite inconvenient aspects of the historical record. More will be the result of error, misconfiguration, and laziness. 

> Imagine the plight of our descendants two hundred years from now, who might wish to read a transcript of John Brown's remarks upon being found guilty of treason and insurrection. Even if the true transcript survives, it may be indistinguishable among many convincingly altered versions. Intentional, politically-motivated alterations could include intensifying or removing Brown's appeals to Christianity, removing his denial of treasonous intent, or rewriting his professed abolitionist motivations into something cruder and more mercenary. Any one of these changes would fundamentally alter the text, and the historical understanding of any reader who accepted it as real. And how could our descendants know which is real, for this or any other text? What truths about our past we have managed to preserve would be lost to a totalizing cultural and historical dementia.

A lot has changed in the months since I wrote that. Maybe most shockingly, OpenAI announced that an unreleased frontier model produced proofs to a significant fraction of the top open problems in mathematics, including one of the Millennium problems. While it will be a while before the truth of these claims is established, it is now not inconceivable that LLMs are better than humans at doing original mathematics research. This possibility has shaken the world of mathematics research to its core. We'll see what happens when the dust clears, but it's obvious that mathematics research will be fundamentally different from now on, and the community was completely unprepared for these changes.

Put more crudely, AI techniques are advancing very quickly and accomplishing shocking feats that seemed in the realm of science fiction just a few years ago. Of course no one knows for certain how AI capabilities will continue to progress. But it is clear now that we should think very carefully about what risks we face and how to prepare for them. In particular, this project is motivated by a threat I think AI could pose to the historical record.

Specifically, I am going to try to convince you that:
- **LLMs (and other generative AI technologies) might make rewriting history cheap.**
- **Secure timestamping mitigates this threat - if we act soon.**

Then I'll explain how we can easily make secure timestamps for essentially no cost, using decades-old, tested-and-true computer science techniques.

### How LLMs might rewrite history
In the 4th century AD, the Roman emperor Constantine the Great issued an imperial decree which transferred authority over Rome and the western part of the Roman Empire, including Jerusalem, to Pope Sylvester I. This document came to be known as the Donation of Constantine, and it was cited in political and religious conflicts for centuries during the Middle Ages. It was used by the papacy to claim authority over kings and emperors.

It was also a lie. Constantine never issued such a decree in the fourth century. Via early linguistic analysis techniques, in the fourteenth century the Donation of Constantine was conclusively established as a forgery. The true details of its creation are unclear, but it was likely produced during the eighth century, either to justify expansion of papal power or as a ploy in internal church politics.

When archivists work to preserve history, much of the focus is on preserving genuine versions of historical texts - protecting them against decay, theft, or accidental destruction. While detecting forgeries is also important, it has largely been a secondary consideration. This is because, historically, producing a good forgery is expensive. Why? 
1. Physical documents inherently age, and the signs of age are difficult to fake.
2. Choosing the exact contents of a convincing forgery requires expertise and time, an expensive combination.
3. A false historical document may conflict with existing, genuine historical documents.

E.g., If China wants to claim that Tibet was always a vassal state, they have to make fake scrolls or whatever, use historical experts to write the fake, and still the utility is limited because of the existence of many genuine historical documents that refer to Tibet as a foreign nation.

E.g., Creating the original version of the Donation of Constantine required an expert to write it. And the power of the Catholic church to disseminate it widely. And it was eventually found to be a forgery because it got some historical facts about the church in the 4th century wrong, and used language which did not match the language used in other documents of the period.

But producing forgeries of important historical documents is becoming much cheaper, and this trend will continue. Here are some reasons why:

- Our records are increasingly digitized.

Many historical documents are backed up digitally, or only exist digitally with no physical source (web data, sensor readings). Digital documents do not inherently carry signs of age like physical documents, and are easy to alter arbitrarily. Moreover, [many physical books (some of them quite rare) are being destroyed in the process of being scanned as training data for LLMs](https://www.404media.co/ai-companies-are-buying-tons-of-old-books-because-theyre-free-of-ai-slop/). While this preserves the informational content of the books, it destroys the physical evidence that establishes their age.

- LLMs (and gen AI in general) are improving at forgery sub-tasks.

You have undoubtedly already seen yourself how ubiquitous AI-generated content has become on the internet. Here are just a few examples: [AI-generated images polluting databases of images of wildife](https://www.nature.com/articles/s41559-026-03141-y), [another example of AI wildlife photos](https://www.theguardian.com/environment/2026/jul/20/ai-slop-manipulated-fake-images-birds-citizen-science-aoe), [same problem, but in astrophotography](https://www.cloudynights.com/forums/topic/984879-regarding-the-use-of-ai-in-astrophoto-processing/), [people are openly using video-generating models to create fake historical footage](https://x.com/berningman16/status/2082670658845368503).

None of these examples constitute successful historical forgeries (by definition, since we've detected them) and they are not yet particularly convincing, but they are MUCH more convincing than AI generated content was five years ago.

- Producing MANY forged documents telling a coherent (but false) version of history may become possible, obviating limitation #3. 

If generative AI keeps improving, it may one day become possible to use it to create a large collection of self-consistent digital historical texts which provide a convincing but false view of some aspect of history or culture. Moreover, it might be **cheap** to do this.

Like I said earlier, we observe on today's internet that spam email is ubiquitous simply because it is cheap for the spammer to send it, and might get them some small benefit. If generating fake history is cheap, it will probably be done at scale too. In the worst-case scenario, large portions of our true history may be lost, even though genuine documents survive, because they are hidden among so many convincing fakes that determining the truth of history is extremely difficult. Imagine millions of documents like the Donation of Constantine, except more expertly written, internally consistent, etc. 

Even if the spam-storm worst-case doesn't happen, things might still be pretty bad. The existence of large-scale forgery tools fundamentally casts doubt on ANY digital document, because how do you know it wasn't created by the super-LLM?

### Timestamping data makes forgery harder
Detecting forgeries is a huge complicated topic, and most of it is out of scope for this project. I'm just going to point out that information about when something existed is often an important clue about its authenticity. Part of the reason the Donation of Constantine was found to be a forgery is that the language used in it was not period-appropriate. As another example, the Shroud of Turin was found via radiocarbon dating to be from the Middle Ages, not the 1st century AD. In this case, since the historical artifact was a physical object, scientists could examine it to estimate how old it was. 

But as I said earlier, digital texts do not inherently show signs of age, and in general they can be altered in ways that leave no trace. Sure, a text file might have a "Date Modified" metadata field, but it can be edited as easily as the file itself.

Let's imagine that wasn't true. Let's imagine that, specifically, there was a way to attach a non-forgeable "Date Modified" label to a file. Maybe it's a picture I took of myself, dated today (October 21, 2026). That label would prove two things: First, that the picture existed on October 21, 2026, and second that it had not subsequently been altered - that it had been unchanged since that day. Actually let's say that I took a bunch of selfies in my room today, at different angles and in different lighting, each with an unforgeable "Date Modified" timestamp.

If future historians later find my selfie collection and want to know whether the pictures are real, this un-fakeable "Date Modified" field would be incredibly helpful. Why? Because **a timestamp constrains the forgery methods that could have been used to create the files, if they were fake**. It's true that I could have doctored each photo using Photoshop, or fabricated it wholesale using a generative AI tool. But it's difficult with photoshop or today's gen AI tools to ensure that a hundred photos of me and my room at various angles are spacially and informationally consistent, look realistic, and avoid the relatively reliable techniques available today to detect photo forgery. It would certainly be very difficult and take some human expertise. It might be impossible, I'm not sure.

Imagine then that in 2030 someone invents a gen AI tool that CAN actually generate such a collection of pictures, and is statistically indistinguishable from real photographs. Let's say that it is SO good and SO convincing that no one EVER figures out how to detect its forgeries. Without the timestamp, historians would be out of luck. They would have no way to tell whether my photo collection was real or forged. But the timestamp tells them that the photos existed before the invention of the undetectable AI tool, and had not been edited in any way since. So after ruling out detectable pre-2026 forgery methods, they could conclude that the photographs were likely real.

It seems unlikely that someone will invent a forgery method that is forever undetectable. More likely, forgery and detection methods both improve over time in an arms race; old forgery methods become detectable and stop being used, and new temporarily-undetectable methods are discovered. It's not unthinkable that the status quo is that the latest forgery methods are hard to detect, but after a few years people work out reliable detection techniques. In this case, knowing that a file existed a long time ago is still enough to determine authenticity.

## How to make a secure timestamp
TODO. For now, read the explanatory document of any of the timestamps I have posted on my website. They describe in detail how the timestamps were constructed. Check back here soon for a gentler, more detailed explanation of the techniques involved.