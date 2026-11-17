# Greek (el) — TypEvent dictionary file and its sources

## Why this folder exists

The word list of the Greek dictionary comes from **elspell el_GR — Steve Stavropoulos and contributors**. Its maintainer offers it under MPL 1.1, GPL 2.0 and LGPL 2.1 (source/README_el_GR.txt) and agreed in writing (2026-11-12) to its use under the Mozilla Public License 1.1 alone (https://www.mozilla.org/MPL/1.1/).

The GNU LGPL and The Mozilla Public License 2.0 asks that the files used and the files made from them be available, with their exact versions and the recipe. They are all here.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `el.wl` | 19421960 | `f911c0deb56886dcc6d5755ba042b87fa23e8f6eef6391eb9db6f707b13101b1` | https://raw.githubusercontent.com/stevestavropoulos/elspell/ac157be50878644aaa5346bf7951a737067a8e6e/el.wl |
| `el_GR.aff` | 20191 | `f5b7731de065123d6abf3a47f3afc9e457e0f036934c8a81d78936c7fff0ca87` | https://raw.githubusercontent.com/stevestavropoulos/elspell/ac157be50878644aaa5346bf7951a737067a8e6e/myspell/el_GR.aff |
| `README_el_GR.txt` | 2232 | `1528aac33d453fe84e01972c051c8d227237ed8d096755a18964c3ee42e2545b` |  |

## Files made from them

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `el-alakok.txt` | 19421960 | `f911c0deb56886dcc6d5755ba042b87fa23e8f6eef6391eb9db6f707b13101b1` | every word form expanded from the .dic and .aff files (affix expansion) |
| `el-alakok.txt.meta.json` | 1201 | `6cb7d0453063466fcc529643b5248a4991db231601b7151f4bd274d14a7b531c` | build record of the file above (JSON) |
| `el-l1.tsv` | 6696730 | `3c9bde69454d9f62f75600af6ec1f5d73fad935221bde0283f0291cb8b96326b` | the word forms that also occur in the ranking corpus, with their counts (word, tab, count) |
| `el-l1.tsv.meta.json` | 1719 | `29089f18690685c4e5711260d49ba7ff2102a60e02fca2f148e87148c441d07d` | build record of the file above (JSON) |
| `el.typd` | 10993664 | `c55e88f53bbffc5cb23e2b395c121b8a002ea6f34f42a77ccae6841c6c8299e7` | the dictionary file exactly as it ships in the app (binary) |
| `el.typd.meta.json` | 1234 | `f355255fc260dfe1f7631911d8350c7e67b914998f193064a985aaf4588e28bc` | build record of the file above (JSON) |

`el.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/el.typd` in TypEvent, commit `27f4b788`).

## Recipe

1. `affix expansion of el.wl with el_GR.aff — tools/nyelvi_kibontas.py`
2. `python3 tools/nyelvi_tabla.py --nyelv el --tagsag nyers/nyelvek/el/el-alakok.txt --tagsag-alak sima --tagsag-fejlec 0 --rangsor nyers/nyelvek/el/kimenet1/korpusz-el-leipzig-szurt.tsv --ki nyers/nyelvek/el/kimenet1/el-l1.tsv`
3. `python3 tools/typd_konverter.py … (the build record: el.typd.meta.json)`

The tools named here belong to TypEvent and are not published; the commands and the build records are here so that every step and every file version can be checked.

## Changes

The files in `source/` are not modified. The files made from them are filtered (only forms that occur in the ranking corpus), given frequency counts, and compiled into TypEvent’s own binary format.

## Other data inside `el.typd`

- Frequency ranking: Leipzig Corpora Collection, Universität Leipzig. Licence: CC BY 4.0. Only word counts, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. The files TypEvent made from them are available under the GNU Lesser General Public License, version 2.1 or (at your option) any later version (text in source/README_et_EE.txt), together with the EKI licence of the word list (same file) and the Mozilla Public License 2.0 (LICENSE-MPL-2.0.txt); the data from other sources inside them stays under the licences listed above.
