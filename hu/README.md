# Hungarian (hu) — TypEvent dictionary file and its sources

## Why this folder exists

**Magyar Ispell (Hunspell hu_HU) — László Németh and Ferenc Godó** is used, unmodified, only while building the Hungarian dictionary: as a spelling check and filter. None of its text is copied into `hu.typd`. Its authors offer it under MPL 2.0 or LGPL 3+ (source/README_hu_HU.txt). TypEvent uses it under the Mozilla Public License 2.0.

We publish the exact files we used (MPL 2.0, section 3.2(a)), and for reference the dictionary file built with their help, so that anyone can see what was used.

## Source files, unmodified — `source/`

| file | bytes | sha256 | downloaded from |
|---|---|---|---|
| `hu_HU.dic` | 1786144 | `97293d670ad4a3b8e7eebef7e25c6e8e939b914c64b6b4672b2bf416b768f990` | https://github.com/LibreOffice/dictionaries/tree/master/hu_HU |
| `hu_HU.aff` | 2316267 | `f3a2748dd535cfde2142ab17d0f7f8e4787b03fb25a60829c69ac8d493db4802` | https://github.com/LibreOffice/dictionaries/tree/master/hu_HU |
| `README_hu_HU.txt` | 1190 | `52b17fc3d53b6935eab747a71894507d702f7f0fde379c819c16cc803005fc84` | https://github.com/LibreOffice/dictionaries/tree/master/hu_HU |

## The dictionary file built with their help

| file | bytes | sha256 | what it is |
|---|---|---|---|
| `hu.typd.gz` | 9066036 | `87f26f71f1577bd88906f2160720134efb784a5a83331281e31ba91a57469aec` | the dictionary file exactly as it ships in the app (binary); gzip-compressed for GitHub’s 25 MiB browser limit — unpacked, its sha256 is `fa89a15bed8c8d92f5f580b9c6c3176022b238364a58e371ec48f9e73fc286bd` |
| `hu.typd.meta.json` | 1907 | `49cee54b3b817e79d80f3e803544e9e52702f3f08590db6102a6fcb740a8d862` | build record of the file above (JSON) |

`hu.typd` is byte-identical to the file in the app (`TypEvent/TypEventExtension/Szotarak/hu.typd` in TypEvent, commit `f99d12b`).

## Recipe

The Hungarian dictionary is built from morphdb.hu and corpus counts by TypEvent’s own tools; `hu.typd.meta.json` is its build record. Magyar Ispell is consulted during the build and does not change the output bytes of the converter.

## Changes

The files in `source/` are not modified. The dictionary file was converted to TypEvent’s own binary format.

## Other data inside `hu.typd`

- Word stems and inflection classes: morphdb.hu — Eszter Simon, Péter Rebrus, András Rung, Viktor Trón, Péter Vajda. Licence: CC BY 2.5. Modified: converted to TypEvent’s binary format; only the inflection classes and word stems are used.
- Word frequencies: counted by TypEvent from the Hungarian Wikipedia (counts only, no text).
- Word-pair frequencies and a supplementary word list: Tatoeba. Licence: CC BY 2.0 FR.
- Everyday-speech frequency weights: OPUS — OpenSubtitles v2024 release, licence ODC-BY 1.0. Only word frequencies, no text.
- Some words are marked so that the keyboard does not offer them on its own. That list itself is not published.

## Licence of this folder

The files in `source/` keep their own licences. `hu.typd` is here for reference; the data inside it stays under the licences listed above.
