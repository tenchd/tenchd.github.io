---
title: PG Corpus Timestamp
layout: page
hide: true
permalink: timestamp
---
# Project Gutenberg Corpus Secure Timestamp
On June 26, 2026, I encoded the Project Gutenberg corpus into a Merkle tree and wrote the root hash on the Bitcoin blockchain at [block 955522](https://blockstream.info/tx/b82b914e29fb08e65e49156231b68c38c3bcb246f6a7d8ec22477478a9f1b832?expand). This comprises a secure timestamp of the Project Gutenberg corpus. In other words, the Merkle tree and the block containing its root hash provide cryptographic-strength proof that each Project Gutenberg text existed in June 2026. 

Read more about how this works, and why I did it in the first place, here(TODO).

I have published the source code for my secure timestamp reference implementation [here](https://github.com/tenchd/secure_timestamp).

You can download the Merkle tree and its accompanying explanatory document below, as well as a .tar.gz file containing the Project Gutenberg corpus.

[Merkle tree](downloads/pgmerkle.txt) (6.7 MB)
SHA256 hash ```518f265e76d92d06aa863f294efef01f2e2a3c6c1d19012d55b1505e0be8b86b```

[Explanatory document](downloads/explain.txt) (17 KB)
SHA256 hash ```deb4859fb5f483d0251cbe9ebe9908e0591a53511311ee07b134354eac324e22```

[Project Gutenberg corpus from June 11, 2026](https://drive.proton.me/urls/TREXY65MA8#ku23FKKn2Nbm) (10.42 GB, uncompresses to 77113 .txt files)
SHA256 hash ```fc9b698275724a6616d7a3c2fe41c2dcac6739b5d0cc0ce892d3109f1652c955```
