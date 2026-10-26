# Serbian (sr) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Serbian dictionary comes from **dict-sr (hunspell-sr) — Goran Rakić and contributors**. Its authors offer it under LGPL 2.1+, MPL 1.1+ or GPL 2+ (source/README_sr.txt). TypEvent uses it under the Mozilla Public License 2.0, which the “1.1 or later” wording allows.

The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `sr-Latn.dic` | 2489827 | `a41302b3e707c7a344560bc7df6db739db254f87be0442108a68f4ed2a34782d` | https://raw.githubusercontent.com/grakic/hunspell-sr/master/sr-Latn.dic |
| `sr-Latn.aff` | 704 | `9112fdbd53c8a20ac06397e736884450d61df0c6c5be6f5512210ed58229f939` | https://raw.githubusercontent.com/grakic/hunspell-sr/master/sr-Latn.aff |
| `README_sr.txt` | 1412 | `272cfe7e4b339cbad1750806139576f062f9dbb8a966a55acd3d8700c51daeca` | https://raw.githubusercontent.com/grakic/hunspell-sr/master/README_sr.txt |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `sr-alakok-latin.txt` | 2489789 | `4f31bafbd6d9591f33ece3ce02422777aacdb332d8a7e4ac8d044ed996d20c45` | intermediate affix expansion (Latin script) |
| `sr-alakok-latin.txt.meta.json` | 787 | `b2e34fb566051361b1f7a8c81a8ac54e0311481e754d5db5a0922560d13d13e1` | build record of the file above (JSON) |
| `sr-alakok.txt` | 6937587 | `ccbf2567501aca3ef41cb24e6854aaaa3f5dab4a3bb6e9e26f3dc5481d6b7111` | every word form expanded from the .dic and .aff files (affix expansion) |
| `sr-alakok.txt.meta.json` | 1345 | `1cae70a41c22ad0c2301cca7284242e95a86dac6e9729bf8a6d2dc50a408cfbf` | build record of the file above (JSON) |
| `sr-l1.tsv` | 5754394 | `eeee781b36b9b762b22c1280f821ca6c77726c3d1b609bc37d5dc9743431aacd` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `sr-l1.tsv.meta.json` | 1642 | `4074c30e0d3e9e32e692bd8914ff4dfa7b7b9892b9f3dba5781cf07f345271eb` | build record of the file above (JSON) |
| `sr.typd` | 8863744 | `8a88c1547e6554447741c5bca8944f9b90f6047e0dec0b2d6ee029045b7746ec` | the dictionary file exactly as it ships in the app (binary) |
| `sr.typd.meta.json` | 1226 | `7632fd6cf6a1fc33424589d7f65d01a0edc019d4f6a766e7e6f649051b7dc94e` | build record of the file above (JSON) |

`sr.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/sr.typd` in TypEvent, commit `f99d12b`).

## Recipe

1. `python3 tools/nyelvi_kibontas.py --nyelv sr --dic nyers/nyelvek/sr/sr-Latn.dic --aff nyers/nyelvek/sr/sr-Latn.aff --ki nyers/nyelvek/sr/sr-alakok-latin.txt && python3 tools/nyelvi_atiras.py --be nyers/nyelvek/sr/sr-alakok-latin.txt --ki nyers/nyelvek/sr/sr-alakok.txt --mindketto`
2. `python3 tools/nyelvi_tabla.py --nyelv sr --tagsag nyers/nyelvek/sr/sr-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/sr/korpusz-sr-leipzig.tsv --ki nyers/sr-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: sr.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `sr.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
