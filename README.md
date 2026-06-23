# PDFTerms — Controlled-vocabulary term search for VOSviewer

**A directed text-mining tool driven by a controlled vocabulary: you define the terms, the app counts their occurrences and co-occurrences across your PDFs and generates a JSON file ready for VOSviewer.**

It complements [PDFWords](../textminingprojeto1), which performs open extraction of every word. Here the logic is reversed: the vocabulary is controlled by you, which makes it well suited to evaluating sustainability reports and to systematic reviews.

---

## Difference from PDFWords

| | PDFWords | PDFTerms |
|---|---|---|
| Approach | Open, data-driven | Directed, theory-driven |
| Who chooses the terms | The algorithm | You |
| Typical use | Initial exploration | Report evaluation, systematic review |

---

## Features

- Upload of multiple PDFs by drag & drop (text extraction is 100% local)
- You type one term per line; the app expands the synonyms automatically
- Built-in maritime and port sustainability term library (Brazilian Portuguese + English)
- Manual synonym grouping with `=` (advanced mode, takes priority)
- Thematic categories with `[ ]` that become coloured clusters in VOSviewer
- Compound-term search (e.g. `shore power`) and wildcards (`emission*`)
- Case-insensitive and accent-insensitive matching
- Binary counting per document or co-occurrence per sentence
- Coverage diagnostics: lists the terms with zero occurrences
- Exports: VOSviewer JSON, term × document matrix (CSV), frequencies (CSV)
- Save and load term lists (.txt)

---

## Term library

The library was built empirically rather than by guesswork. A corpus of 188 peer-reviewed articles on maritime sustainability, ship emissions and port decarbonisation was processed by text extraction, and the document frequency of each candidate term was measured. The terms that actually occur across the literature were then organised into 17 categories with bilingual synonyms (82 entries, 353 variants).

The corpus mining was cross-checked against established frameworks:

- **ESPO / EcoPorts** — top-10 environmental priorities of European ports (climate change, air quality, energy efficiency, water, noise, dredging, waste, port development)
- **IMO / MARPOL** — EEXI, EEDI, CII, EEOI, emission control areas (ECA/SECA), sulphur cap, MRV
- **GRI / CSRD / ESG** — materiality, stakeholders, transparency, sustainability reporting
- **UN SDGs / Agenda 2030**

The `// df` comment next to each entry in `index.html` records how many of the 188 articles contain that term. The library is extensible: new terms and synonyms can be added to the `THESAURUS` object in `index.html`.

---

## How to use

1. Upload one or more PDFs (for example, the sustainability reports of the ports under study)
2. Type your search terms, one per line
3. Keep "Expand synonyms automatically" enabled to use the library
4. Adjust the co-occurrence scope and the minimum thresholds
5. Click **Count terms and generate network**
6. Download the JSON and open it at [app.vosviewer.com](https://app.vosviewer.com) → Open → VOSviewer JSON file

> Scanned PDFs (image only) require OCR before processing.

---

## Term format

```
CO2                              # expands via the library
ballast water                    # compound term, expands automatically
[Energy] hydrogen = H2; green hydrogen   # manual, with a category
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
