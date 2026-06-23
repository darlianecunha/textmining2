# PDFTerms — Controlled-vocabulary term search for VOSviewer

**A subject-neutral, directed text-mining tool: you define the terms, the app counts their occurrences and co-occurrences across your PDFs and generates a JSON file ready for VOSviewer.**

It complements [PDFWords](../textminingprojeto1), which performs open extraction of every word. Here the logic is reversed: the vocabulary is controlled by you, which makes it well suited to evaluating reports and to systematic reviews in any field.

---

## Subject-neutral, with domain packs

The app is not tied to any topic. The term library is loaded at runtime as a **domain pack**, so the same app serves decarbonisation, the SDGs, ESG, or any other subject.

- A domain pack is a plain-text file in the term format: `[Category] Canonical label = variant1; variant2; wildcard*`
- Load one with **Load library (domain pack)**. Bare terms you type then expand to their variants automatically.
- Without a pack, terms are searched literally (still fully usable).
- Build a pack by writing terms in area A and clicking **Save terms (.txt)**; that file can be reloaded later as a library.
- An example pack for maritime/port decarbonisation, aligned to Fadiga et al. (2024), is included: `decarbonisation-keywords-fadiga.txt`.

---

## Difference from PDFWords

| | PDFWords | PDFTerms |
|---|---|---|
| Approach | Open, data-driven | Directed, theory-driven |
| Who chooses the terms | The algorithm | You |
| Typical use | Initial exploration | Report evaluation, systematic review |

---

## Features

- Two clearly separated areas: **A**, where you type the keywords you want, and **B**, where the app shows the synonyms it generated for each one (your study's thesaurus)
- Upload of multiple PDFs by drag & drop (text extraction is 100% local)
- Loadable domain packs (libraries) for any subject; bilingual variants supported (e.g. English + Portuguese)
- Manual synonym grouping with `=` (always takes priority over the library)
- Thematic categories with `[ ]` that become coloured clusters in VOSviewer
- Compound-term search (e.g. `shore power`) and wildcards (`emission*`)
- Case-insensitive and accent-insensitive matching
- Binary counting per document or co-occurrence per sentence
- Coverage diagnostics: lists the terms with zero occurrences
- Exports: VOSviewer JSON, thesaurus mapping (CSV), term × document matrix (CSV), frequencies (CSV)
- Save and load term lists / libraries (.txt)

---

## How to use

1. Upload one or more PDFs
2. (Optional) Load a domain pack for your topic with **Load library**
3. Type your search terms in area A, one per line; check area B to confirm the synonyms
4. Adjust the co-occurrence scope and the minimum thresholds
5. Click **Count terms and build network**
6. Download the JSON and open it at [app.vosviewer.com](https://app.vosviewer.com) → Open → VOSviewer JSON file

> Scanned PDFs (image only) require OCR before processing.

---

## Term and pack format

```
CO2                              # bare term, expands if the loaded pack knows it
ballast water                    # compound term
[Energy] hydrogen = H2; green hydrogen   # manual entry with a category
govern*                          # wildcard
```

---

## Technologies

| Technology | Use |
|---|---|
| HTML / CSS / JavaScript | Interface and logic |
| PDF.js (v3.11) | Text extraction from PDFs |
| VOSviewer | Network visualisation |
| Vercel | Hosting |

---

## Privacy

All processing happens in the browser. No file is sent to any server.

---

## Author

**Darliane Ribeiro Cunha, PhD**
Researcher in sustainability governance, environmental analytics and the SDGs
[ORCID: 0000-0003-2548-1237](https://orcid.org/0000-0003-2548-1237)
