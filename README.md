# TypEvent — dictionary files and their sources

This repository holds the dictionary files of the **TypEvent** iOS keyboard that are built from, or with the help of, copyleft-licensed sources (MPL 2.0, LGPL), together with the exact source files and the recipe. It exists to meet those licences.

The TypEvent app itself is not open source. Its code is not here, and these licences do not cover it.

| folder | language | source | why it is here |
|---|---|---|---|
| [`es/`](es/) | Spanish | RLA-ES Hunspell dictionary (es_ES) | MPL |
| [`et/`](et/) | Estonian | LibreOffice et_EE — word list by the Eesti Keele Instituut, affix rules by Jaak Pruulmann | LGPL |
| [`fr/`](fr/) | French | Grammalecte dictionary — Olivier R. and contributors | MPL |
| [`hu/`](hu/) | Hungarian | Magyar Ispell (Hunspell hu_HU) — László Németh and Ferenc Godó | MPL |
| [`sk/`](sk/) | Slovak | sk-spell (hunspell-sk) | MPL |
| [`sr/`](sr/) | Serbian | dict-sr (hunspell-sr) — Goran Rakić and contributors | MPL |

In every folder:

- `source/` — the source files exactly as downloaded, unmodified, with their own licence or README;
- `<lang>.typd` — the dictionary file exactly as it ships in the app (byte-identical; `.typd.gz` where it is over GitHub’s 25 MiB browser limit — unpacked, it is the same file);
- the intermediate lists and their build records (`.meta.json`; where there is a `parancs` field, it is the command);
- `README.md` — sources, licences, sha256 checksums, the recipe and what was changed.

Built from TypEvent commit `f99d12b` (2026-10-25). To check the files: `shasum -a 256 -c SHA256SUMS.txt`.

Questions, or a mistake in the credits: legal@typevent.app

---

## Magyarul

Ez a tár a TypEvent iOS-billentyűzet azon szótárfájljait tartalmazza, amelyek MPL 2.0 vagy LGPL licencű forrás felhasználásával készültek: spanyol (`es/`), észt (`et/`), francia (`fr/`), magyar (`hu/`), szlovák (`sk/`), szerb (`sr/`). Mellettük a felhasznált forrásfájlok változatlanul, és a recept. A TypEvent forráskódja nincs itt.
