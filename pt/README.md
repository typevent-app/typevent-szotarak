# Portuguese (Portugal) (pt) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Portuguese (Portugal) dictionary comes from **Natura Hunspell pt_PT — José João de Almeida, Rui Vilela, Alberto Simões**. Its authors offer it under GPL 2, LGPL 2.1 and MPL 1.1 (source/README_pt_PT.txt); asked in writing (2026-11-13), they agreed to its use under the Mozilla Public License 1.1 alone (https://www.mozilla.org/MPL/1.1/).

The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `pt_PT.dic` | 1485977 | `e29ba2d7aa8a2ad43e9cb46ac6473064b661545c87002aea90e18899d98d3cc9` | https://natura.di.uminho.pt/download/sources/Dictionaries/hunspell/LATEST/hunspell-pt_PT-latest.tar.gz (kibontva: pt_PT.dic) |
| `pt_PT.aff` | 95089 | `975a209fcc892cb382fa5f34a28c391a39668661ce373ae071287809c5fcae24` | https://natura.di.uminho.pt/download/sources/Dictionaries/hunspell/LATEST/hunspell-pt_PT-latest.tar.gz (kibontva: pt_PT.aff) |
| `COPYING` | 70247 | `9d308fe32d21acca4109538342af16506eecbb25c3b40fcb7ee4f201509c56ad` |  |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `pt-alakok.txt` | 15151174 | `a2c36bc5a9ebfd57ec24579703ba07eaf250f0a039ccbd714c9aa16c237bfa9d` | every word form expanded from the .dic and .aff files (affix expansion) |
| `pt-alakok.txt.meta.json` | 747 | `674c8338f34b6a8cd022db62967e0a422cdf63e3ea8821ff2509405ba1565f3a` | build record of the file above (JSON) |
| `pt-l1.tsv` | 2172346 | `41fd702617f9a058f3e6f1869a0ae307b84b2e34175726bbf14cedb8e7900f4d` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `pt-l1.tsv.meta.json` | 1860 | `ff1a278a2d47960606f9ac2413f69067d9482b7b0daca6e02d427fbc5409886f` | build record of the file above (JSON) |
| `pt.typd` | 5718016 | `f35e2fac0b822dfd893f38896c4ad611ffb9e76952de282f4f04b1d2019497c6` | the dictionary file exactly as it ships in the app (binary) |
| `pt.typd.meta.json` | 1234 | `42056d7bb4f292a3e4c66d8a6d8915dca9929ae80695ca1a22a01f96c2eedc13` | build record of the file above (JSON) |

`pt.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/pt.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `affix expansion of pt_PT.dic with pt_PT.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv pt --tagsag nyers/nyelvek/pt/pt-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/pt/kimenet1/korpusz-pt-leipzig-szurt.tsv --ki nyers/nyelvek/pt/kimenet1/pt-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: pt.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `pt.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
