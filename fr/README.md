# French (fr) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the French dictionary comes from **Grammalecte dictionary — Olivier R. and contributors**. Mozilla Public License 2.0 (source/README_dict_fr.txt).

The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `fr.dic` | 1236490 | `b78a868e31dd6e373b6c3217969afb898a9acde828a5e7ef97308da42218c88c` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/fr_FR/dictionaries/fr.dic |
| `fr.aff` | 199870 | `c176610cd5dc4846806a65ddd029f422d87978bf58f224aa44222662a16a2de5` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/fr_FR/dictionaries/fr.aff |
| `README_dict_fr.txt` | 2758 | `4a25abf740ad6ba5e8d0cfc0d2ffadc3c13c303f8fe389f323b061a389350f83` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/fr_FR/dictionaries/README_dict_fr.txt |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `fr-alakok.txt` | 7410943 | `567127f7918815411f6744989406ced71e0b112266efb32f818bfeef72e47ecb` | every word form expanded from the .dic and .aff files (affix expansion) |
| `fr-alakok.txt.meta.json` | 588 | `0edd17bbe923923a07d8938c5e237348f65de4f4175e5205d75d8fa50a5007fa` | build record of the file above (JSON) |
| `fr-l1.tsv` | 2368387 | `475c6e92af62304b99f3eea4694aa0fcbc930ba8751e8b5044f81580a40f3e24` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `fr-l1.tsv.meta.json` | 1640 | `b6450ca78e58fe14ab82756d3d3dd3611e44a0aa9d49a94a486708973931bcfe` | build record of the file above (JSON) |
| `fr.typd` | 7127040 | `794ecc8301cb13176c7282082a294c6fb51d94bd7f0c3350ef4dadd0c3948d0d` | the dictionary file exactly as it ships in the app (binary) |
| `fr.typd.meta.json` | 1229 | `c758379568d813eada0608d8def850bf940670e59ed11559259c942976575b3e` | build record of the file above (JSON) |

`fr.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/fr.typd` in TypEvent, commit `f99d12b`).

## Recipe

1. `affix expansion of fr.dic with fr.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv fr --tagsag nyers/nyelvek/fr/fr-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/fr/korpusz-fr-leipzig.tsv --ki nyers/fr-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: fr.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `fr.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
