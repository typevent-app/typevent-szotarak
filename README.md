# TypEvent — dictionary files and their sources

This repository holds the dictionary files of the **TypEvent** iOS keyboard that are built from, or with the help of, copyleft-licensed sources (MPL 2.0, LGPL), together with the exact source files and the recipe. It exists to meet those licences.

The TypEvent app itself is not open source. Its code is not here, and these licences do not cover it.

| folder | language | source | why it is here |
|---|---|---|---|
| [`cs/`](cs/) | Czech | MULTEXT-East Lexica V4 wfl-cs (Tomaž Erjavec, CLARIN.SI) · UniMorph ces (Wiktionary) · Wikidata lexemes | CC BY-SA |
| [`de-DE/`](de-DE/) | German | german-nouns (German Wiktionary) · UniMorph deu (English Wiktionary) · Wikidata lexemes · kaikki.org Wiktionary extract | CC BY-SA |
| [`el/`](el/) | Greek | elspell el_GR — Steve Stavropoulos and contributors | LGPL, MPL |
| [`es/`](es/) | Spanish | RLA-ES Hunspell dictionary (es_ES) | MPL |
| [`et/`](et/) | Estonian | LibreOffice et_EE — word list by the Eesti Keele Instituut, affix rules by Jaak Pruulmann | LGPL |
| [`fr/`](fr/) | French | Grammalecte dictionary — Olivier R. and contributors | MPL |
| [`hu/`](hu/) | Hungarian | Magyar Ispell (Hunspell hu_HU) — László Németh and Ferenc Godó | MPL |
| [`it/`](it/) | Italian | Morph-it! 0.48 — Marco Baroni and Eros Zanchetta | LGPL, CC BY-SA |
| [`lv/`](lv/) | Latvian | Tēzaurs.lv 2026 — AiLab, IMCS, University of Latvia (CLARIN-LV) | CC BY-SA |
| [`pt/`](pt/) | Portuguese (Portugal) | Natura Hunspell pt_PT — José João de Almeida, Rui Vilela, Alberto Simões | MPL |
| [`sk/`](sk/) | Slovak | sk-spell (hunspell-sk) | MPL |
| [`sr/`](sr/) | Serbian | dict-sr (hunspell-sr) — Goran Rakić and contributors | MPL |

In every folder:

- `source/` — the source files exactly as downloaded, unmodified, with their own licence or README;
- `<lang>.typd` — the dictionary file exactly as it ships in the app (byte-identical; `.typd.gz` where it is over GitHub’s 25 MiB browser limit — unpacked, it is the same file);
- the intermediate lists and their build records (`.meta.json`; where there is a `parancs` field, it is the command);
- `README.md` — sources, licences, sha256 checksums, the recipe and what was changed.

Built from TypEvent commit `27f4b788` (2026-11-16). To check the files: `shasum -a 256 -c SHA256SUMS.txt`.

Questions, or a mistake in the credits: legal@typevent.app

---

## Magyarul

Ez a tár a TypEvent iOS-billentyűzet azon szótárfájljait tartalmazza, amelyek MPL 2.0 vagy LGPL licencű forrás felhasználásával készültek: cseh (`cs/`), német (`de-DE/`), görög (`el/`), spanyol (`es/`), észt (`et/`), francia (`fr/`), magyar (`hu/`), olasz (`it/`), lett (`lv/`), portugál (`pt/`), szlovák (`sk/`), szerb (`sr/`). Mellettük a felhasznált forrásfájlok változatlanul, és a recept. A TypEvent forráskódja nincs itt.
