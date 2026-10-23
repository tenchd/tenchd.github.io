---
title: Explaining the Amber Project
layout: page
hide: true
permalink: timestamp_overview
---
# Amber: Secure Timestamping
[Amber](timestamp) is a software utility and part of an ongoing effort to create secure timestamps of the digital historical record.

This page covers the motivations behind this effort, the techniques that make Amber work, and how you can help. If you don't know what a secure timestamp is, read [this page](timestamp) first.

This page is written to be accessible to a reader who is computer-literate but doesn't necessarily have deep technical computer science expertise.

Note that this page is also still a work in progress. I'm refining the writing and adding to it regularly.

## What is a secure timestamp?
A secure timestamp is a digital artifact that proves that texts from a corpus existed at a particular date (and therefore could not have been created after that date). 

When I say "text", I specifically mean not just a text file, but any data that means something to humans. This includes text files and ebooks, but also images, audio recordings, videos, source code, webpages, etc. When I say "corpus", I mean a collection of texts, usually from the same source or concerning the same topic. Examples of well-known corpuses include Project Gutenberg, the Library of Congress's Television Commercial collections, and NOAA's weather and climate data archive.

## Motivation: hardening the pre-AI historical record
Here's a message I wrote in the first secure timestamp I ever created, in June 2026:

> While the primary challenge of literary and historical conservation efforts across the centuries has been preserving texts, it has also been vital to identify forgeries because they obscure our view of the past.

> If current technological trends continue, large-language models (LLMs) and other forms of generative AI will drastically reduce the cost of creating convincing forgeries of historical texts. In such a case, we can expect a massive flood of such forgeries to be created, for the same reason that spam email is ubiquitous: because spamming is cheap and low-risk for the spammer, and might give them some small benefit. Some of the forgeries will be made maliciously, by political, religious, or corporate actors that seek to rewrite inconvenient aspects of the historical record. More will be the result of error, misconfiguration, and laziness. 

> Imagine the plight of our descendants two hundred years from now, who might wish to read a transcript of John Brown's remarks upon being found guilty of treason and insurrection. Even if the true transcript survives, it may be indistinguishable among many convincingly altered versions. Intentional, politically-motivated alterations could include intensifying or removing Brown's appeals to Christianity, removing his denial of treasonous intent, or rewriting his professed abolitionist motivations into something cruder and more mercenary. Any one of these changes would fundamentally alter the text, and the historical understanding of any reader who accepted it as real. And how could our descendants know which is real, for this or any other text? What truths about our past we have managed to preserve would be lost to a totalizing cultural and historical dementia.

When I wrote that, I was imagining that if LLMs improved enough to get good at historical forgery, the improvement would be gradual and easy to see coming.

A lot has changed in the months since (as I write today it is October 21, 2026). Maybe most shockingly, OpenAI recently announced that an unreleased frontier model produced proofs to a significant fraction of the top open problems in mathematics, including one of the Millennium problems. While it will be a while before the truth of these claims is established, it is now not inconceivable that LLMs are better than humans at doing original mathematics research. This possibility has shaken the world of mathematics research to its core. We'll see what happens when the dust clears, but it's obvious that mathematics research will be fundamentally different from now on, and the community was completely unprepared for these changes.

Put more crudely, AI techniques are advancing very quickly and accomplishing feats that seemed impossible a few years ago. Of course no one knows for certain how AI capabilities will continue to progress. But it is clear now that we should think very carefully about what risks we face and how to prepare for them. 

This project is about anticipating and preventing one of these risks. Specifically, I want to convince you that:
- **LLMs (and other generative AI technologies) might one day pose an existential threat to the historical record.**
- **Secure timestamping mitigates this threat - if we act soon.**

Then I'll explain how we can easily make secure timestamps for essentially no cost, using decades-old, tested-and-true computer science techniques.

### How LLMs might rewrite history
In the 4th century AD, the Roman emperor Constantine the Great issued an imperial decree which transferred authority over Rome and the western part of the Roman Empire, including Jerusalem, to Pope Sylvester I. This document came to be known as the Donation of Constantine, and it was cited in political and religious conflicts for centuries during the Middle Ages. It was used by the papacy to claim authority over kings and emperors.

It was also a lie. Constantine never issued such a decree in the fourth century. Using early linguistic analysis techniques, in the fourteenth century the Donation of Constantine was conclusively established as a forgery. The true details of its creation are unclear, but it was likely produced during the eighth century, either to justify expansion of papal power or as a ploy in internal church politics.

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

I'm saying "if" and "may" a lot, because of course I can't predict the course of AI development. Maybe tomorrow all progress on AI research will hit a mysterious wall and grind to a halt for decades. But we have to acknowledge that forgery-capable generative AI is a credible possibility.

Like I said earlier, we observe on today's internet that spam email is ubiquitous simply because it is cheap for the spammer to send it, and might get them some small benefit. If generating fake history is cheap, it will probably be done at scale too. In the worst-case scenario, large portions of our true history may be lost, even though genuine documents survive, because they are hidden among so many convincing fakes that determining the truth of history is extremely difficult. Imagine millions of documents like the Donation of Constantine, except more expertly written, internally consistent, etc. 

Even if the spam-storm worst-case doesn't happen, things might still be pretty bad. The existence of large-scale forgery tools fundamentally casts doubt on ANY digital document, because how do you know it wasn't created by the super-LLM?

### Timestamping data makes forgery harder
Detecting forgeries is a big and complicated topic, and most of it is out of scope for this project. I'm just going to point out that information about when something existed is often an important clue about its authenticity. Part of the reason the Donation of Constantine was found to be a forgery is that the language used in it was not period-appropriate. As another example, the Shroud of Turin was found via radiocarbon dating to be from the Middle Ages, not the 1st century AD. In this case, since the historical artifact was a physical object, scientists could examine it to estimate how old it was. 

But as I said earlier, digital texts do not inherently show signs of age, and in general they can be altered in ways that leave no trace. Sure, a text file might have a "Date Modified" metadata field, but it can be edited as easily as the file itself.

Let's imagine that wasn't true. Let's imagine that, specifically, there was a way to attach a non-forgeable, always-accurate "Date Modified" label to a file. As an example, imagine I took a picture of myself today, October 21, 2026, and attached this trustable timestamp label to it. That label would prove two things: First, that the picture existed on October 21, 2026, and second that it had not subsequently been altered - that it had been unchanged since that day. Actually let's say that I took a bunch of selfies in my room today, at different angles and in different lighting, each with an unforgeable timestamp.

If future historians later find my selfie collection and want to know whether the pictures are real, this un-fakeable timestamp would be incredibly helpful. Why? Because **a timestamp constrains the forgery methods that could have been used to create the files, if they were fake**.<sup>[1](#myfootnote1)</sup> It's true that I could have doctored each photo using Photoshop, or fabricated it wholesale using a generative AI tool. But it's difficult with photoshop or today's gen AI tools to ensure that a hundred photos of me and my room at various angles are spacially and informationally consistent, look realistic, and avoid the relatively reliable techniques available today to detect photo forgery. It would certainly be very difficult and take some human expertise. It might be impossible, I'm not sure.

Imagine then that in 2030 someone invents a gen AI tool that CAN actually generate such a collection of pictures, and is statistically indistinguishable from real photographs. Let's say that it is SO good and SO convincing that no one EVER figures out how to detect its forgeries. Without the timestamp, historians would be out of luck. They would have no way to tell whether my photo collection was real or forged. But the timestamp tells them that the photos existed before the invention of the undetectable AI tool, and had not been edited in any way since. So after ruling out detectable pre-2026 forgery methods, they could conclude that the photographs were probably real.

It seems unlikely that someone will invent a forgery method that is forever undetectable. More likely, forgery and detection methods both improve over time in an arms race; old forgery methods become detectable and stop being used, and new temporarily-undetectable methods are discovered. It's not unthinkable that the status quo is that the latest forgery methods are hard to detect, but after a few years people work out reliable detection techniques. In this case, knowing that a file existed a long time ago is still enough to determine authenticity.

The bottom line is, creating secure timestamps of historically important digital texts might be necessary for retaining the bulk of our historical knowledge over time. Secure timestamps are more useful the older they are, because that rules out more potential forgery techniques. If we wait until some super-forgery-LLM gets invented, it will be too late to make maximally useful timestamps. We must timestamp as much of the historical record as we can BEFORE such technology emerges. Since it is very difficult to estimate how quickly AI techniques will advance, I feel that timestamping is an urgent conservation task. Our descendants' access to verifiably unaltered records of the past is at stake.

## How to make a secure timestamp
So far I've asked you to trust me that it's possible to create a non-forgeable, accurate "Date Modified"-style timestamp of a collection of digital files. Now I'm going to explain how to do this using existing, well-tested and reliable computer science techniques. I didn't come up with this method of secure timestamping - people have used essentially these same techniques to timestamp the existence of digital data before, primarily for financial or legal purposes. However, none of these existing services get the details quite right for our use case, which is what prompted me to create Amber.

I will first explain the method concisely, assuming you have a strong technical background. If you don't have that technical background, skip ahead to [Warm up: Timestamping a single file](#warm-up-timestamping-a-single-file) for a gentler, non-technical explanation.

### A quick technical explanation
We have a corpus of digital texts. The first step is to construct a Merkle tree from the texts. Specifically, the Merkle tree is constructed in the same way a Bitcoin miner computes the Merkle root hash of a block of transactions. That is to say, define an arbitrary ordering over the files in the corpus. First, compute the double SHA256 hash of each file. These comprise the leaves of the Merkle tree. Then for each adjacent pair of leaves in the ordering, double hash the concatenation of their hashes to produce the hash of their parent node. The process is repeated at each level until the root is reached. If there is an odd number of nodes at some level, the last node's hash is concatenated with itself and then double SHA256 hashed to get the parent hash. Amber writes the Merkle tree in a human-readable text file, where each node hash is represented in base64. The text file contains some helpful information in commented-out header lines before listing the nodes.

In addition to the Merkle tree file, Amber automatically constructs a text file which explains what the timestamp is, how the Merkle tree was constructed, how it can be verified on the blockchain, and how to use it to prove that corpus files existed when the timestamp was created. It also contains user-generated descriptions of the corpus and the user who is making the timestamp (with the option for the user to include a cryptographic signature to establish their identity). The explanatory document is designed to be completely self-contained. Even if the timestamp is later discovered by someone who knows nothing about secure timestamps or Amber, if they can read English and write a simple computer program (or get a coding LLM to do it for them), they will have all the information they need to verify and use the secure timestamp.

After creating the Merkle tree and the explanatory text file, Amber writes a 76-byte message to the Bitcoin blockchain via an OP_RETURN script. The message contains an 8-byte ASCII identifier which is listed in the explanatory document, a 4-byte integer encoding the number of leaves in the Merkle tree, the 32-byte root hash of the Merkle tree, and the 32-byte double SHA256 hash of the explanatory document.

Taken together, the Merkle tree file, the explanatory file, and the blockchain message comprise the secure timestamp of the corpus. For a more detailed description, you can check out the explanatory document for any of the secure timestamps I have already made: [1](timestamps/pgtimestamp.md), [2](timestamps/kagglenews.md), [3](timestamps/timemag.md).

The next few sections are a non-technical summary of the above points. Skip ahead to [Limitations of Secure Timestamps](#limitations-of-secure-timestamps).

### Warm-up: Timestamping a single file
The first technique we need for timestamping is a fingerprinting algorithm. The Wikipedia definition is pretty good: 
>In computer science, a fingerprinting algorithm is a procedure that maps an arbitrarily large data item (such as a computer file) to a much shorter bit string, its fingerprint, that uniquely identifies the original data for all practical purposes just as human fingerprints uniquely identify people for practical purposes.

We will use a fingerprinting algorithm called the SHA256 hash function. You don't need to know the details of how this algorithm works. You only need to know the following facts about it:
1. The input to the function is any data you want (any size, any format, etc.), and the output is a single 32-byte value. We call this output value the **fingerprint** of the input data.
2. Let's say I have two different inputs. The probability that the algorithm returns the same output for those two inputs is roughly 1 in 2^256. That's incredibly unlikely! We can safely assume the outputs are unique.
3. Even if the two inputs are almost the same (say they differ only by a single bit), their outputs will still be completely different from each other. 

Note that fingerprinting is a one-way operation: if you have the original data, you can run the fingerprinting algorithm on it to discover the fingerprint. But if you just have the fingerprint, you can't "run the algorithm backwards" to get the original data, any more than you could reconstruct a person's body and mind just by knowing what their right pinky fingerprint looks like.

The second thing we need for timestamping is a medium we can write messages to with the following properties:
1. The medium is permanent and tamper-proof. This means that once someone writes something to the medium, it cannot be changed or deleted.
2. The medium is inherently timestamped. This means that any message written to the medium is assigned an accurate timestamp of the date and time it was written, and this timestamp is also permanent and tamper-proof.
3. The medium is publicly available. This means that anyone with a computer, an internet connection, and some simple software should be able to read the messages written on the medium themselves.

What medium has these properties? The answer is blockchains. This might surprise you, because blockchains are now mostly associated with cryptocurrencies. But in fact the 1990 paper that introduced the core ideas that underlie all blockchain technology was titled [How to Timestamp a Digital Document](https://link.springer.com/article/10.1007/BF00196791)! Later people realized that if you can timestamp a bunch of records of the form "Alice sends 5 dollars to Bob" and these records can never be edited or erased, you can keep track of an entirely virtual currency (I am of course massively oversimplifying, but that's the basic idea).

Amber uses the Bitcoin blockchain as its timestamping medium. I made this decision because anyone can write short messages to the Bitcoin blockchain, and it has remained untampered-with for over a decade despite enormous incentives to scammers, thieves, governments, and corporations to edit its contents or take it down altogether.<sup>[2](#myfootnote2)</sup> It's also widely used and therefore easily accessible. And if it ever looks like the Bitcoin blockchain might fail, there is a way to "transfer" its timestamps to a different, more stable timestamping medium if one exists (though explaining how that works is too technical for this writeup).

We now have the two ingredients we need for a secure timestamp of a file. First we compute the file's fingerprint, and then write this fingerprint on the Bitcoin blockchain. The (permanent and untamperable) blockchain message proves that the fingerprint existed on the day we wrote it to the chain. Since a fingerprint uniquely identifies its input, this also proves that the input data existed on that day too.

Why bother with the fingerprinting step at all? Why not just write the file contents to the blockchain? Well, it turns out that for a number of reasons it is only feasible and cost-effective to write a small amount of data to the blockchain. If we want to timestamp large data (say, a hi-res video file), the cost of writing it to the blockchain would be prohibitive. A 32-byte fingerprint, on the other hand, is almost free to write to the chain.

### Timestamping an entire corpus of files
Let's say we have a corpus of a million files we want to timestamp. We could fingerprint each file individually and write each fingerprint on the blockchain, but this is expensive for the same reasons writing an entire file on the chain would be.

Instead, we will use a technique to combine all the individual fingerprints into one "master" 32-byte fingerprint. 

The core trick is pretty simple, and I'll illustrate it with a small example first.  Take text 1 and text 2 from the corpus. Each of them has a fingerprint. We concatenate those two fingerprints together, creating a 64-byte bit string. This bit string is data, just like anything else, which means we can also compute *its* fingerprint. So we do that. This "paired" fingerprint can be written to the blockchain to prove the existence of both text 1 and text 2! We have to make sure to write down fingerprint 1, fingerprint 2, and the paired fingerprint. Then, later, if we want to verify that text 1 was timestamped, we compute its fingerprint and confirm that it matches one of the fingerprints we wrote down earlier. Then we check the blockchain and find the paired timestamp there. We've done it! We verified that the paired fingerprint existed at the date of the timestamp because we see it directly on the blockchain. And we see from our stored copies of fingerprints 1 and 2 that the paired fingerprint can only exist because fingerprint 1 existed. So that proves fingerprint 1 existed on that date, and therefore text 1 did as well. We've timestamped two texts, but only written a single fingerprint to the blockchain.

We apply this trick not just for texts 1 and 2 but for each pair of texts in the corpus. We started with a million fingerprints, and now we have 500,000 "paired" fingerprints. Each "paired" fingerprint proves the existence of the two fingerprints that were its input. We can repeat this process again to get 250,000 "four-way" fingerprints and so on until we end up with a single fingerprint that is a combination of each of the original million fingerprints. This method of combining and recombining fingerprints produces a tree structure which is called a Merkle tree, and that last fingerprint is called the "root fingerprint" because it's at the root of the tree structure.

Now we write the root fingerprint on the blockchain, and hang onto the sequence of fingerprint-pairings we used to compute the Merkle tree. If we want to verify whether some file is timestamped, we verify that the root fingerprint is on the blockchain. Then we fingerprint the file and see if it matches one of the fingerprints in the tree. If it does, we've proven the file existed at the date of the timestamp, and we only wrote a single 32-byte fingerprint to the chain.

[Read more about Merkle trees here if you're interested](https://en.wikipedia.org/wiki/Merkle_tree). They are used for lots of purposes in computer science and have been around for almost fifty years.

## Limitations of secure timestamps

### The big one: timestamps ONLY prove when something existed
Secure timestamps don't tell us anything special about the timestamped data, other than the fact that it existed at a certain time and hasn't been edited since. It does not certify that the data is "true" in any sense, or authentic, or has been written by the person that claims to have written it. As a concrete example, if I timestamp an ebook copy of Don Quixote, that timestamp would not conclusively prove that it was truly a novel published in the early seventeenth century by Miguel de Cervantes, or that it was a faithful and accurate translation into English from the original Spanish. It also would not rule out the possibility that a malicious actor modified the text shortly before it was timestamped. It would merely establish that the ebook, in its timestamped form, existed in 2026.

When you think about it, this puts historians roughly in the same position as when they have a physical historical document that they can carbon date. They can verify with some degree of certainty that the text is of the time it claims to be, but of course the text could contain lies, bias, fabrications, translation errors, etc. And historical texts containing lies are not even necessarily a bad thing for historians. If you know that a historical text contains intentional lies about something, that is actually very interesting (provided the text is truly as old as you think it is).

If secure timestamping is widely adopted, I expect the benefit to be that establishing the provenance of digital texts would have roughly the same challenges as that of physical texts. This would remain true even if the spam-storm LLM-history-rewriting nightmare I described earlier comes to pass. 

Secure timestamping will not be a magic solution to modern worries about misinformation or fake news. There is also nothing preventing malicious actors from intentionally timestamping false information of all kinds. For the time being, however, I expect that creating convincing false information to timestamp is expensive enough and has low enough payoff in the short term that it is unlikely to happen at scale. And happily, the cost of timestamping large, existing legitimate corpuses is very low.

### Timestamped texts must be preserved exactly
Let's say I have a timestamped corpus of text files, timestamped September 1, 2026. Each of these files corresponds to a leaf in the merkle tree, and the root of the merkle tree is written to the blockchain. To verify that one of the files existed in Sept. 2026, you would first verify that the merkle root hash is in the blockchain in some block on Sept 1, 2026. Then you would verify that the SHA256 hash of the file exactly matched one of the merkle tree leaf hashes.

This works great, unless you edited the text file somehow. It doesn't have to be a malicious edit; let's say you found and fixed a typo. Now the SHA256 hash of the file is completely different, and so it won't match any of the Merkle tree leaf hashes. From the perspective of the timestamp, this edited file is no different than any other completely unrelated file. It's simply not in the timestamped corpus.

The problem is that many archives periodically edit their files for a variety of reasons. For example, [Project Gutenberg has an errata process where volunteers can submit changes to ebooks to fix typos, translation errors, formatting problems, etc](https://www.gutenberg.org/help/errata.html). This means that any text in the Project Gutenberg corpus can change at any time. If someone made a timestamp of the corpus, and didn't back up the files in exactly their timestamped form, they run the risk of many of the texts getting edited. Any such text would no longer be timestamped. (By the way, when I timestamped the Project Gutenberg corpus in June, [I did save an exact copy of the texts, and I make it available for download](timestamps/pgtimestamp.md).)

So for a timestamp to remain useful far into the future, the corpus it timestamps must be preserved exactly. This is not difficult to do in a technical sense, but does require a little planning. If the corpus being timestamped is frequently used and updated, it's probably safest to make a backup copy that is rarely touched, and timestamp that backup copy.

## We need to start now

Finally, I want to reiterate my earlier point about urgency. We don't know if or when generative AI or some other new computational technique will make it cheap to generate large corpuses of false but internally-consistent digital texts. It could never happen, or it could happen tomorrow. Secure timestamps are at their most useful when they are created BEFORE the invention of powerful forgery techniques. The sooner we can timestamp the digital historical record, the safer it will be.

## How you can help
TODO. For now, if you think this is interesting and want to get involved for any reason, email me.

## Notes
<a name="myfootnote1">1</a>: It also constrains the motivations someone could have to make the forgery, which is useful as well, but outside the scope of this writeup.

<a name="myfootnote2">2</a>: To be clear, malicious actors do all sorts of nasty things related to Bitcoin including scamming people and stealing from them. However, importantly, none of these nasty acts have ever involved editing confirmed blocks in the blockchain - they trick their victims in some other way.