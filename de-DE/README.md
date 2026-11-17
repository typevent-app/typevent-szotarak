# German (de-DE) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the German dictionary comes from **german-nouns (German Wiktionary) · UniMorph deu (English Wiktionary) · Wikidata lexemes · kaikki.org Wiktionary extract**. german-nouns and the Wiktionary extract are under CC BY-SA 4.0, UniMorph deu under CC BY-SA 3.0 (which allows a later version), the Wikidata lexemes under CC0. The files made from them are under CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/legalcode).

The CC BY-SA licence asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `german-nouns.csv` | 20194356 | `7b34ca76bb753fa5d3d2b683ecc987824ae874b375ac999a797074fafba2768e` | https://raw.githubusercontent.com/gambolputty/german-nouns/master/german_nouns/nouns.csv |
| `unimorph-deu.tsv` | 18932560 | `8bc98487e3caf86188e2c072ebf2dc734f2ca35afef016bb399eb5a43e69d7c0` | https://raw.githubusercontent.com/unimorph/deu/master/deu |
| `latest-lexemes.json.bz2` (not copied here: over GitHub’s 25 MiB limit; freely available from its publisher, downloaded 2026-11-12) | 493410363 | `1911de77d3c6ca2a9de7ed35e18cbc1fdc6df28d556231082effa347f011f879` | https://dumps.wikimedia.org/wikidatawiki/entities/latest-lexemes.json.bz2 |
| `LICENSE-cc-by-sa-4.0-legalcode.txt` | 20138 | `28a9529c7d0bb4dc51f4bf5c116a3d16ef247a052f7591466768ddf563fd1cf5` |  |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `de-alakok-5.txt` | 11813312 | `549e46559d4a4323aacc719910b475ed5847d6752675448b1e7e7e6980660ceb` | every word form expanded from the .dic and .aff files (affix expansion) |
| `de-alakok-5.txt.meta.json` | 1857 | `e5fac7440b8a729ad8b827d4d0560be9a4ff66572a42add5ab10dc26534cc240` | build record of the file above (JSON) |
| `de-DE-l1.tsv` | 4908501 | `396cc10a027427901fa38d4db63d8d5a3566dfbc7f7c626a1d4672e488e22f33` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `de-DE-l1.tsv.meta.json` | 1941 | `2beb4077ea990a9ee63d5379fe2a159e4a3dec3e09c0afffe69356f864f2638a` | build record of the file above (JSON) |
| `de-DE.typd` | 13090816 | `c980220e53c405c1f1e8cf4b748443f94a60dd8c8e83010c3a7865416545f8a8` | the dictionary file exactly as it ships in the app (binary) |
| `de-DE.typd.meta.json` | 1248 | `a22a670bd3c2b36b22a50cf9c93c4a4db6576bf63e2c9918c8ad53307de3e6b9` | build record of the file above (JSON) |

`de-DE.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/de-DE.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `affix expansion of german-nouns.csv with unimorph-deu.tsv — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv de --tagsag nyers/nyelvek/de/kimenet5/de-alakok-5.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/de/kimenet1/korpusz-de-leipzig-szurt.tsv --ki nyers/nyelvek/de/kimenet5/de-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: de-DE.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `de-DE.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the same Creative Commons BY-SA licence as their source; the data from other sources inside them stays under the licences listed above.
