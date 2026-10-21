---
title: Kaggle News Timestamp
layout: page
hide: true
permalink: timestamps/kagglenews
---
# Kaggle Newspapers Secure Timestamp
On Sept 27, 2026, I encoded a multi-language corpus of newspaper articles sourced from Kaggle into a Merkle tree and wrote the root hash on the Bitcoin blockchain in [block 968774](https://www.blockchain.com/explorer/transactions/btc/19904600876b03f56bf89ec9191c3fa89caa426e95a6394e02040247c0c7ce80). This comprises a secure timestamp of the Kaggle newspaper articles corpus. In other words, the Merkle tree and the block containing its root hash provide cryptographic-strength proof that each newspaper article in the corpus existed in September 2026. 

Read more about how this works, and why I did it in the first place, [here](../overview.md).

## Corpus Details
This timestamp covers an assortment of newspaper datasets sourced from Kaggle. It includes roughly 12 million newspaper articles in plain text, in a variety of languages. The datasets were downloaded over a period of several weeks in August/September 2026. They were chosen because they were publicly available collections of newspaper articles and I have not done any verification of the datasets aside from cursory checks for completeness, formatting, etc.

The corpus includes newspaper articles written in Albanian, Arabic, Farsi, Vietnamese, Tamil, Brazilian Portuguese, German, English, Dutch, Thai, Bangla, Russian, and Turkish.

I provide a zipped archive of the corpus alongside this timestamp. It contains a subdirectory for each Kaggle dataset included in this corpus. Each dataset subdirectory contains:
- about.txt, a text file containing the data card description of the dataset on Kaggle
- data/, a subdirectory containing articles as .txt files.

## Timestamp Details

This timestamp was produced with a prototype of the Amber secure timestamp utility. See the source code [here](https://github.com/tenchd/amber).

You can download the Merkle tree and its accompanying explanatory document below, as well as a .tar.gz file containing the complete Kaggle Newspapers corpus.

[Merkle tree](https://drive.proton.me/urls/G047P9GQZW#FqXz6J71PDZT) (1.1 GB)
SHA256 hash ```4a31e2fa1cd7bba6f95110d51366b998ebc0c5e23761b369082b1c3f5561d7b9```

[Explanatory document](https://drive.proton.me/urls/JEVX26FPAM#CrhcOPmh8LtR) (57 KB)
SHA256 hash ```6fe7fa9131c3e4cbb931af565bccdcfa18d5cdae3fbe07fa55b302359d098da1```

[Kaggle Newspapers corpus from Aug-Sept 2026](https://drive.proton.me/urls/FAYVS0EXJR#01xz2RsK7YYs) (11 GB, uncompresses to 12305783 .txt files)
SHA256 hash ```d2f844f4fdbe1a72c7644c042098dfbb81114a7da19453bf8add675db4f9b71b```