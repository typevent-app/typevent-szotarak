# Italian (it) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Italian dictionary comes from **Morph-it! 0.48 — Marco Baroni and Eros Zanchetta**. Its authors offer it under the Creative Commons Attribution-ShareAlike 2.0 licence and the GNU LGPL (source/readme-morph-it.txt). TypEvent uses it under CC BY-SA 2.0 (https://creativecommons.org/licenses/by-sa/2.0/legalcode); the files made from it are under the same licence.

The GNU LGPL and The CC BY-SA licence asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `morph-it.tgz` | 2617548 | `b137343dc095e038ebfaef7c743185e85ec35f5322a1b8629b600e6e898c7024` | Miklos bongeszobol, a pontos cim nincs rogzitve (a jogosult oldala: https://docs.sslmit.unibo.it/doku.php?id=resources:morph-it) (a morph-it.tgz-bol) |
| `readme-morph-it.txt` | 11735 | `1dda9b918cca8c3b2c8b6fe93bf864321ba865da56ab89c43f328bc3dc870f02` | Miklos bongeszobol, a pontos cim nincs rogzitve (a jogosult oldala: https://docs.sslmit.unibo.it/doku.php?id=resources:morph-it) (a morph-it.tgz-bol kicsomagolva) |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `it-alakok.txt` | 4811538 | `72e5d4750176086814347d0aa58bb72e65a154840ff6b3de049514d131f5d9d8` | every word form expanded from the .dic and .aff files (affix expansion) |
| `it-alakok.txt.meta.json` | 842 | `a34d25ab34322debbd7387809268f0dab2d27278753d949d2f1625e1a42d5441` | build record of the file above (JSON) |
| `it-l1.tsv` | 2204306 | `9b487fb53b6372c5900b6e83cf62d8277c49c3cdc0fd6cab362d105ac53696b1` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `it-l1.tsv.meta.json` | 1851 | `644e135cacd0dbc2b0dfe5a492db8bc6804fe534f3c571166f2cdbbf477b78f9` | build record of the file above (JSON) |
| `kisbetus-it.txt` | 651 | `29e88421561dc19a74acd7ed0cccaf5953f0722c2b50a496b42df6460b4da69b` | words the dictionary keeps lower-case (interjections, from the source's INT tag); one per line |
| `kisbetus-it.txt.meta.json` | 938 | `402273b85355efc069fb793c144cd8d5c5b097e779c71edf2d9ee54d2812cc52` | build record of the file above (JSON) |
| `ekezethibas-it.txt` | 394 | `b18d38d1c89ae83639407d64543f1b9ca17473326359c2cc9f2075359ba3b6ae` | wrongly accented forms left out of the dictionary (so the correctly accented one is offered); one per line |
| `ekezethibas-it.txt.meta.json` | 2279 | `28a9d44f53877063e3c283dedb15c503785c30db3dade16e4d0c8712165e24cf` | build record of the file above (JSON) |
| `it.typd` | 6815744 | `23b9773396e6a5e8f560fd951ab6a61c858160eddc0fe1ac1f11e871bb26b2cc` | the dictionary file exactly as it ships in the app (binary) |
| `it.typd.meta.json` | 1265 | `c9c11dfba8c6275d5ccf50f26a25501cf705e22120f6c318ec4fa612dc217067` | build record of the file above (JSON) |

`it.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/it.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `iconv -f ISO-8859-1 -t UTF-8 nyers/nyelvek/it/current_version/morph-it_048.txt | cut -f1 | LC_ALL=C sort -u > nyers/nyelvek/it/it-alakok.txt`
2. `python3 tools/nyelvi_tabla.py --nyelv it --tagsag nyers/nyelvek/it/it-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/it/korpusz-it-leipzig.tsv --ki nyers/it-l1.tsv`
3. `python3 tools/nyelvi_kisbetus.py … (the list and its build record: kisbetus-it.txt.meta.json)`
4. `python3 tools/nyelvi_ekezethibas.py … (the list and its build record: ekezethibas-it.txt.meta.json)`
5. `python3 tools/typd_konverter.py … (the build record: it.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `it.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own (partly from LDNOOBW — © 2012–2020 Shutterstock, Inc., licence CC BY 4.0). That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the GNU Lesser General Public License, version 2.1 or (at your option) any later version (text in source/README_et_EE.txt), together with the EKI licence of the word list (same file) and the same Creative Commons BY-SA licence as their source; the data from other sources inside them stays under the licences listed above.
