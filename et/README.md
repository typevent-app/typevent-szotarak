# Estonian (et) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Estonian dictionary comes from **LibreOffice et_EE — word list by the Eesti Keele Instituut, affix rules by Jaak Pruulmann**. The word list is under the EKI software licence; the affix rules are under the GNU LGPL. Both texts are in source/README_et_EE.txt (the LGPL text there is version 2.1).

The GNU LGPL asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `et_EE.dic` | 4383841 | `cd1378434aefeaa8a31f49369dbf71caf4e6340badb5c2cf7a55820933ed4f13` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/et_EE/et_EE.dic |
| `et_EE.aff` | 236336 | `2fa53b7853762ec8c63ffa14b2d96d23433e3f2c2d3d218ad7c2461673099f95` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/et_EE/et_EE.aff |
| `README_et_EE.txt` | 55978 | `4cff6a48ea9168d545316ab96bac24eff4745bf198cbdd9f57eb10a9d8f93f0d` | https://raw.githubusercontent.com/LibreOffice/dictionaries/master/et_EE/README_et_EE.txt |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `et-alakok.txt` | 3148636 | `4bba4abe0455aec423b9fdadae2ae4609f34b9f9c6f8b00614471d148f6cc51d` | every word form expanded from the .dic and .aff files (affix expansion) |
| `et-alakok.txt.meta.json` | 620 | `821a433bc2bae8eba09cf39e2f919a9d0d501b03be25adebb6ad603d3122cc42` | build record of the file above (JSON) |
| `et-l1.tsv` | 4807106 | `bb4333fabb8caf1ec75811b450058880b733bced922c72ce1071257146ae7eef` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `et-l1.tsv.meta.json` | 1642 | `b0fc12378174096a590a3cbe117a96b1343eb005f6184bb7bd808f4004be8a87` | build record of the file above (JSON) |
| `et.typd` | 10731520 | `6005053c20e6e526d42af4f2e02d9e71e68c989c7aae78bf90e78b994ad9c4c0` | the dictionary file exactly as it ships in the app (binary) |
| `et.typd.meta.json` | 1225 | `23444020d1c7a5e3e9139f366e3264e7a4fed0f1f9cf51fdebc0d5f04a1413f6` | build record of the file above (JSON) |

`et.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/et.typd` in TypEvent, commit `f99d12b`).

## Recipe

1. `affix expansion of et_EE.dic with et_EE.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv et --tagsag nyers/nyelvek/et/et-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/et/korpusz-et-leipzig.tsv --ki nyers/et-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: et.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `et.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Everyday-speech frequency weights: OPUS — OpenSubtitles 2018 release. Only word frequencies, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the GNU Lesser General Public License, version 2.1 or (at your option) any later version (text in source/README_et_EE.txt), together with the EKI licence of the word list (same file); the data from other sources inside them stays under the licences listed above.
