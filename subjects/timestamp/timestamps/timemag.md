---
title: TIME Magazine Timestamp
layout: page
hide: true
permalink: timestamps/timemag
---
# TIME Magazine 1923-2015 Secure Timestamp
On Sept 28, 2026, I encoded the TIME Magazine corpus into a Merkle tree and wrote the root hash on the Bitcoin blockchain in [block 969003](https://www.blockchain.com/explorer/transactions/btc/d5f5811800e195cbd865f504bb8e9bd2277eba4c15b72856fab6de7da06f4662). This comprises a secure timestamp of the TIME magazine corpus. In other words, the Merkle tree and the block containing its root hash provide cryptographic-strength proof that each TIME Magazine text existed in Sept 2026. 

Read more about how this works, and why I did it in the first place, [here](../overview.md).

## Corpus Details
This timestamp covers the complete corpus of TIME magazine from 1923-2015. From Wikipedia:

"Time is an American news magazine based in New York City. It was published weekly for nearly a century. Starting in March 2020, it was published every other week. It was first published in New York City on March 3, 1923, and for many years it was run by its co-founder, Henry Luce.
Since 2018, Time has been owned by Salesforce founder Marc Benioff, who acquired it from Meredith Corporation. Benioff currently publishes the magazine through the company Time USA, LLC."

### Provenance
I obtained this corpus from [Kaggle](https://www.kaggle.com/thegupta/time-magazine-part-1-1923-to-1930); someone else scraped the Time magazine archive to produce it.

I provide a zipped archive of the corpus alongside this timestamp. It contains a subdirectory for each year from 1923-2015. Each year directory contains a directory for each weekly issue of the magazine, and these folders contain .jpg images of each page of the issue. There are a total of 448125 .jpg pages in the corpus, and these .jpg files map 1-to-1 to leaves of the Merkle tree.

## Timestamp Details

This timestamp was produced with a prototype of the Amber secure timestamp utility. See the source code [here](https://github.com/tenchd/amber).

You can download the Merkle tree and its accompanying explanatory document below, as well as a .tar.gz file containing the complete TIME Magazine corpus.

[Merkle tree](https://drive.proton.me/urls/RT5QVH6H68#PMjnqbttcnwz) (38 MB)
SHA256 hash ```ce2d2c5b3dbbe87ac2b744bdb3da65d7c9175be389c11bf41c8e84c4810b9e89```

[Explanatory document](https://drive.proton.me/urls/VACJRBWXJ8#Qo8GRRoM4j0Y) (56 KB)
SHA256 hash ```99c0ebc9ea7aa344a59a779134bb4ab0a010895fc67554fb7b96a8d11bca227a```

[TIME Magazine corpus from Sept 2026](https://drive.proton.me/urls/FJV11VZWXC#btBaKyri8Qii) (120 GB, uncompresses to 448125 .jpg files)
SHA256 hash ```9b7cbe02d93d548e1364dc4e0d331ed9fa945daebde409e6232fb06674c1901b```