# Czech (cs) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Czech dictionary comes from **MULTEXT-East Lexica V4 wfl-cs (Tomaž Erjavec, CLARIN.SI) · UniMorph ces (Wiktionary) · Wikidata lexemes**. wfl-cs is under CC BY-SA 4.0 (confirmed in writing by its publisher, 2026-11-13), UniMorph ces under CC BY-SA 3.0 (which allows a later version), the Wikidata lexemes under CC0. The files made from them are under CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/legalcode).

The CC BY-SA licence asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `ces` | 4875289 | `4c0a1841a78d45cfa8a3f447943f9c2135baa9c986ae9de0ba704b3d99da5d42` | https://raw.githubusercontent.com/unimorph/ces/f0d4a4dfaec45b1f4a0ba0a1db1298f3d64af503/ces |
| `latest-lexemes.json.bz2` (not copied here: over GitHub’s 25 MiB limit; freely available from its publisher, downloaded 2026-11-12) | 493410363 | `1911de77d3c6ca2a9de7ed35e18cbc1fdc6df28d556231082effa347f011f879` | https://dumps.wikimedia.org/wikidatawiki/entities/latest-lexemes.json.bz2 |
| `wfl-cs.txt.gz` | 773998 | `d25ba8acd1803ae9fe8606d2692a31a8f49c0ce2f67978cc729b3cfa1af3440e` | https://www.clarin.si/repository/xmlui/bitstream/handle/11356/1041/wfl-cs.txt.gz?sequence=4&isAllowed=y |
| `00README-multext-east.txt` | 4517 | `ae266b6f760f71467c5292f65325b4d4ce6ebcc3d678bf0b257a52ac0cd0e336` | https://www.clarin.si/repository/xmlui/bitstream/handle/11356/1041/00README.txt?sequence=14&isAllowed=y |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `cs-alakok-5.txt` | 3331502 | `51f8c9a20b9619f3a03ac796d01089d2613baa5328b59fdc7917408dae1b34c0` | every word form expanded from the .dic and .aff files (affix expansion) |
| `cs-alakok-5.txt.meta.json` | 2134 | `f14a766049b08884ffcb99c9b699db0024d782b60985a90f11f5d9f169e79cf2` | build record of the file above (JSON) |
| `cs-l1.tsv` | 2415698 | `2901b1a575923389adaa4125f0942188392e865559358578c9f4f0105232a4e8` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `cs-l1.tsv.meta.json` | 1984 | `6c69141c7216c3bdb69456f74bb9aae508f690256c7c4688a105fac30273bc68` | build record of the file above (JSON) |
| `cs.typd` | 5718016 | `a7cc72fe0c07fab4b5ae0e6a225b94a03ec143e0cbd0348ae2316173740f44d8` | the dictionary file exactly as it ships in the app (binary) |
| `cs.typd.meta.json` | 1230 | `e639c8e0043f6498a990f7b54625bd9c0909ab29e665628bee73100444df8999` | build record of the file above (JSON) |

`cs.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/cs.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `nyers/nyelvek/cs/eszkozok/cs_wikidata_tiszta.py (W'); a tobbi a recept 8. pontja szerint (Python, a lap szovegeben)`
2. `python3 tools/nyelvi_tabla.py --nyelv cs --tagsag nyers/nyelvek/cs/cs-alakok-5.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/cs/korpusz-cs-leipzig-szurt.tsv --ki nyers/cs-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: cs.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `cs.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the same Creative Commons BY-SA licence as their source; the data from other sources inside them stays under the licences listed above.
