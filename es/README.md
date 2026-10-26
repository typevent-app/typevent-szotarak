# Spanish (es) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Spanish dictionary comes from **RLA-ES Hunspell dictionary (es_ES)**. Its authors offer it under GPL 3+, LGPL 3+ or MPL 1.1+ (source/LICENSE.md). TypEvent uses it under the Mozilla Public License 2.0, which the “1.1 or later” wording allows.

The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `es_ES.dic` | 715989 | `6975dddec3d5d2c676069537bc67b4b5f786c65c5d4cf6703a82acf779ac9ec1` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/es/es_ES.dic |
| `es_ES.aff` | 169202 | `e73a9bf8e1383f4986a5dc9e2fbed49371c0c61f511c626d15586bd433c1cad9` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/es/es_ES.aff |
| `LICENSE.md` | 991 | `2b70fd5cb8d3b34cc6ae322c969557a2270b99017594addb2531ef5ffd9e1b17` | https://raw.githubusercontent.com/sbosio/rla-es/master/LICENSE.md |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `es-alakok.txt` | 7646749 | `8306f2d3e11a033ed58e4669bf77d5e9fefe616dd621ae4bcdf5acaa497cc5e4` | every word form expanded from the .dic and .aff files (affix expansion) |
| `es-alakok.txt.meta.json` | 592 | `7567905ea2cb202a7edab6bfb99944ceae6f40f8d3e10bb9b38c157d5599044a` | build record of the file above (JSON) |
| `es-l1.tsv` | 2553720 | `1d983e09f20580169a8a540b1b7a3a56f7ccb407ffa752bc78c9ffb5f610d678` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `es-l1.tsv.meta.json` | 1640 | `09a29629705a8575cf592267ccce35fe0dfefa42056f331302475258e49df50d` | build record of the file above (JSON) |
| `es.typd` | 7028736 | `11e0c7b7f5365eb165b6d377da829e26745ff1bf0546ae96fcaac3091e753769` | the dictionary file exactly as it ships in the app (binary) |
| `es.typd.meta.json` | 1226 | `8d0dabc55d24bc5839b4b7dac5dcd3dd9a0dedd289f908fd067a6e83fb8e1092` | build record of the file above (JSON) |

`es.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/es.typd` in TypEvent, commit `f99d12b`).

## Recipe

1. `affix expansion of es_ES.dic with es_ES.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv es --tagsag nyers/nyelvek/es/es-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/es/korpusz-es-leipzig.tsv --ki nyers/es-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: es.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `es.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Everyday-speech frequency weights: OPUS — OpenSubtitles 2018 release. Only word frequencies, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
