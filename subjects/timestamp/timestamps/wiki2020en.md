---
title: English Wikipedia 2020 Timestamp
layout: page
hide: true
permalink: timestamps/wiki2020en
---
# English Wikipedia January 2020 Secure Timestamp
On November 2, 2026, we encoded the January 2020 plain text English language Wikipedia corpus into a Merkle tree and wrote the root hash on the Bitcoin blockchain in [block 974217](https://www.blockchain.com/explorer/transactions/btc/4d2b9ebe096f51ae68d46b4e998d06e679bafccb2747dbfbc5056dd276a2860e). This comprises a secure timestamp of the Wikipedia corpus. In other words, the Merkle tree and the block containing its root hash provide cryptographic-strength proof that each English-language Wikipedia article existed in November 2026. 

Read more about how this works, and why we did it in the first place, [here](../overview.md).

## Corpus Details
This timestamp covers all English-language Wikipedia articles as of January 1, 2020. Each article is made available as an HTML file that can be opened in a web browser. The timestamped corpus does not include most non-text data (images, audio, etc).

We targeted a 2020 snapshot of Wikipedia for timestamping because it predates modern LLMs. We also recently timestamped an [October 2026 snapshot of Wikipedia](wiki2026en.md) as well.

### Provenance
The source data was obtained from the Internet Archive in early October 2026. See the explanatory document for details.

## Timestamp Details

This timestamp was produced with a prototype of the Amber secure timestamp utility. See the source code [here](https://github.com/tenchd/amber).

You can download the Merkle tree and its accompanying explanatory document below, as well as a .tar.gz file containing the complete corpus.

[Merkle tree](https://drive.proton.me/urls/RB7JS35SD0#8ydUrJ4Ta08A) (515 MB)
SHA256 hash ```69fa90a72f40f3daf479747aad681dcd40818f42853486cd3f38ec6e49fa337e```

[Explanatory document](https://drive.proton.me/urls/TBK0R64334#r9y2OeJSrDGF) (17 KB)
SHA256 hash ```86759ebd6ce8dff95664eec2e2919b070c521e45a44ba7fdd5fb17d639386477```

[English Wikipedia corpus from Jan 2020](https://drive.proton.me/urls/QPGCZ46HQR#RHWQwD9ay9f6) (33 GB)
SHA256 hash ```9b7cbe02d93d548e1364dc4e0d331ed9fa945daebde409e6232fb06674c1901b```