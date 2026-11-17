# Latvian (lv) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Latvian dictionary comes from **Tēzaurs.lv 2026 — AiLab, IMCS, University of Latvia (CLARIN-LV)**. Tēzaurs.lv is under CC BY-SA 4.0 (confirmed in writing by its publisher, 2026-11-16). The files made from it are under CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/legalcode).

The CC BY-SA licence asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `tezaurs_2026_04.ispell.zip` | 8574869 | `e45d6cdd860a4f095c5d6eace2c1ac9b2b065df6621999adbacb78b9125dd984` | https://repository.clarin.lv/repository/xmlui/bitstream/handle/20.500.12574/162/tezaurs_2026_04.ispell.zip?sequence=4&isAllowed=y |
| `tezaurs_2026_4_wordforms_tei.xml.zip` (not copied here: over GitHub’s 25 MiB limit; freely available from its publisher, downloaded 2026-11-16) | 224116217 | `22e2f6d9acd330150d57e324a7a9f54272da8e09e262aa5ba46cc536150f9e10` | https://repository.clarin.lv/repository/xmlui/bitstream/handle/20.500.12574/162/tezaurs_2026_4_wordforms_tei.xml.zip?sequence=2&isAllowed=y |
| `LICENSE-CC-BY-SA-4.0-legalcode.txt` | 20138 | `28a9529c7d0bb4dc51f4bf5c116a3d16ef247a052f7591466768ddf563fd1cf5` | https://creativecommons.org/licenses/by-sa/4.0/legalcode.txt |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `tagsag-lv.txt.part1.gz` | 13033983 | `f85bd83589f68237c11aaa890424d8a7c6d58debd381e26ae496cae404f69ca3` | every word form expanded from the .dic and .aff files (affix expansion) — part of `tagsag-lv.txt` |
| `tagsag-lv.txt.part2.gz` | 13356000 | `62e8b9751aafe8839878698d34625d5f3dcf98c46fde5b49b320417cf83b5028` | every word form expanded from the .dic and .aff files (affix expansion) — part of `tagsag-lv.txt` |

`tagsag-lv.txt` is split into 2 parts for GitHub’s 25 MiB browser limit. To rebuild it: `gzip -dc tagsag-lv.txt.part1.gz tagsag-lv.txt.part2.gz > tagsag-lv.txt` — its sha256 is `5d555618be049a939d1ae91a37d3130f510f3a99da72265d514c10e7e532d484`.

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `tagsag-lv.txt.meta.json` | 1155 | `9e29e91384a378a3d67f9c2d7bf4cbf7c192e83eab915e439867bdf990e2c101` | build record of the file above (JSON) |
| `lv-l1.tsv` | 5592171 | `449ab59bb19f701ecc789a9dd6a848f5d228708230978f7fc3954bb13605ad9a` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `lv-l1.tsv.meta.json` | 1863 | `f173aaa85ac868438c4e146b3a5fa803fcec0115c33aaffbc643c3f77146c775` | build record of the file above (JSON) |
| `kisbetus-lv.txt` | 537 | `16cc9e5d0eaf4e00989fadc6649e3a957faa3a1e79b3abf424cb298884c4b3ca` | words the dictionary keeps lower-case (interjections, from the source's INT tag); one per line |
| `kisbetus-lv.txt.meta.json` | 1425 | `2fec81e776e0bfb394f7f194934b0002bd3f7790618bb420d8019d5cb17e31ff` | build record of the file above (JSON) |
| `lv.typd` | 12894208 | `273edbba1928aaab9805c6a5f8c29f255e1bb761987e09b0839f848ea8716f14` | the dictionary file exactly as it ships in the app (binary) |
| `lv.typd.meta.json` | 1246 | `92fd4e300e54dc955bbe6b53c796d7cb19460e816941bb08fd13662cfa3c69c0` | build record of the file above (JSON) |

`lv.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/lv.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `affix expansion of tezaurs_2026_04.ispell.zip with ? — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv lv --tagsag nyers/nyelvek/lv/kimenet2/tagsag-lv.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/lv/kimenet1/korpusz-lv-leipzig-szurt.tsv --ki nyers/nyelvek/lv/kimenet2/lv-l1.tsv`
3. `python3 tools/nyelvi_kisbetus.py … (the list and its build record: kisbetus-lv.txt.meta.json)`
4. `python3 tools/typd_konverter.py … (the build record: lv.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `lv.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the same Creative Commons BY-SA licence as their source; the data from other sources inside them stays under the licences listed above.
