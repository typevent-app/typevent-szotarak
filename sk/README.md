# Slovak (sk) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Slovak dictionary comes from **sk-spell (hunspell-sk)**. Mozilla Public License 2.0 (source/LICENSE).

The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `sk_SK.dic` | 3366232 | `d23ea17501a1078f1a8c2382779d1196c7ee858ba910c6e85cbcf2f7dd510217` | https://raw.githubusercontent.com/sk-spell/hunspell-sk/master/sk_SK.dic |
| `sk_SK.aff` | 226516 | `29af83949cbeb355ad1621c48636400b2fe597ca1aa2988d8ebea912d793fca1` | https://raw.githubusercontent.com/sk-spell/hunspell-sk/master/sk_SK.aff |
| `LICENSE` | 16725 | `1f256ecad192880510e84ad60474eab7589218784b9a50bc7ceee34c2b91f1d5` | https://raw.githubusercontent.com/sk-spell/hunspell-sk/master/LICENSE |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `sk-alakok.txt.gz` | 5415750 | `cdb7f143888404deacaf6b53eac1402dfe8b0c32f034ace5f23208eb15a92d42` | every word form expanded from the .dic and .aff files (affix expansion); gzip-compressed for GitHub’s 25 MiB browser limit — unpacked, its sha256 is `fa8039bfd1b70a80431ff4667fcbf6545b39140328d7f8436fa8bed09efb8851` |
| `sk-alakok.txt.meta.json` | 595 | `b40329aede998b278f0967063517619de2c6dd1ca3b4b68e28162ca6dec39572` | build record of the file above (JSON) |
| `sk-l1.tsv` | 5399718 | `77ce0d057b208dea7429adbd547e631ceb5e50393f41887d4eea4951c04fe28c` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `sk-l1.tsv.meta.json` | 1643 | `132bfbcd846cce8f243c214d6e5899ab4686bdbe35c6884fff591867cbf0cfe9` | build record of the file above (JSON) |
| `sk.typd` | 12664832 | `3f90ab8e0a2163c90e02f43562c608cc801de86dc2cfcced71569ba1ef0ca1ce` | the dictionary file exactly as it ships in the app (binary) |
| `sk.typd.meta.json` | 1225 | `51d3a89f169ce5918b90648933074b4e70659896d7aa3df1f284145c43de461b` | build record of the file above (JSON) |

`sk.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/sk.typd` in TypEvent, commit `f99d12b`).

## Recipe

1. `affix expansion of sk_SK.dic with sk_SK.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv sk --tagsag nyers/nyelvek/sk/sk-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/sk/korpusz-sk-leipzig.tsv --ki nyers/sk-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: sk.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `sk.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
