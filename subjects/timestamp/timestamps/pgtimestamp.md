---
title: PG Corpus Timestamp
layout: page
hide: true
permalink: timestamps/pgtimestamp
---
# Project Gutenberg Corpus Secure Timestamp
On June 26, 2026, I encoded the Project Gutenberg corpus into a Merkle tree and wrote the root hash on the Bitcoin blockchain in [block 955522](https://blockstream.info/tx/b82b914e29fb08e65e49156231b68c38c3bcb246f6a7d8ec22477478a9f1b832?expand). This comprises a secure timestamp of the Project Gutenberg corpus. In other words, the Merkle tree and the block containing its root hash provide cryptographic-strength proof that each Project Gutenberg text existed in June 2026. 

This is the first secure timestamp I produced, and as far as I know, it is the first time anyone has used blockchain existence proofs for historical preservation purposes. Read more about how this works, and why I did it in the first place, [here](../overview.md).

## Corpus Details

I downloaded the Project Gutenberg corpus directly from their website on June 11th. They make nearly all of their texts available as zipped tar file, updated weekly, [here](https://www.gutenberg.org/cache/epub/feeds/txt-files.tar.zip). This collection omits texts in the corpus that have no plain text version available (such as PG40) or that are not really books (such as PG50, which simply lists the first 1 million digits of pi). The highest PG ID in the collection I downloaded was 78827, but the number of texts in the corpus is a little lower than that, because of these missing texts.

## Timestamp Details

I have published the source code for my secure timestamp reference implementation [here](https://github.com/tenchd/secure_timestamp).

You can download the Merkle tree and its accompanying explanatory document below, as well as a .tar.gz file containing the Project Gutenberg corpus.

[Merkle tree](downloads/pgmerkle.txt) (6.7 MB)
SHA256 hash ```518f265e76d92d06aa863f294efef01f2e2a3c6c1d19012d55b1505e0be8b86b```

[Explanatory document](downloads/explain.txt) (17 KB)
SHA256 hash ```deb4859fb5f483d0251cbe9ebe9908e0591a53511311ee07b134354eac324e22```

[Project Gutenberg corpus from June 11, 2026](https://drive.proton.me/urls/TREXY65MA8#ku23FKKn2Nbm) (10.42 GB, uncompresses to 77113 .txt files)
SHA256 hash ```fc9b698275724a6616d7a3c2fe41c2dcac6739b5d0cc0ce892d3109f1652c955```
