# Word Template Filler

A single-file, browser-only tool for filling `.docx` templates with dynamic values. No installation, no server, no data leaves your machine — open `index.html` and it works.

> **Requires an internet connection.** The libraries used to parse and render `.docx` files are loaded from external CDNs (unpkg, esm.sh) at runtime. The tool will not work offline.

## Usage

1. Download or clone the repository.
2. Open `index.html` directly in any modern browser.
3. Upload a `.docx` file containing tags (see below).
4. Fill in the generated form.
5. Download the filled document as `.docx` or generate a print-ready PDF.

## Tag syntax

Write tags directly in your Word document. Each tag must be typed in one continuous action — do not change formatting mid-tag, as Word may split it internally and prevent detection.

| Type | Syntax | Example | Output |
|------|--------|---------|--------|
| Text | `[FIELD]` | `[NAME]` | Free-text input |
| Date | `[FIELD:fecha]` | `[SIGN_DATE:fecha]` | Date picker, formatted as `21 de Febrero de 2026` |
| Gender | `[GROUP:masc\|fem]` | `[TENANT:el\|la]` | Toggle between two forms |

### Gender tags

All tags sharing the same group key are controlled by a single toggle. This lets you handle grammatical agreement across multiple words at once:

```
[TENANT:el|la] arrendatari[TENANT:o|a]
```

Both tags switch together when you select masculine or feminine.

### Filename substitution

Tags in the filename itself are also replaced. A template named `contract_[NAME]_[DATE:fecha].docx` will produce a download named `contract_John_21 de Febrero de 2026.docx`.

## PDF export

The "Generar PDF" button opens the browser print dialog with the filled document rendered. For a clean result, uncheck **Headers and footers** in the print dialog before saving as PDF.

## Privacy

Everything runs in the browser. No files, form values, or personal data are sent to any server. The only external requests are CDN loads for [PizZip](https://unpkg.com/pizzip@3.1.4/dist/pizzip.js) and [docx-preview](https://esm.sh/docx-preview), used to parse and render the `.docx` format.

## Browser support

Any modern Chromium-based browser (Chrome, Edge, Brave) or Firefox. The PDF rendering step uses a dynamic ES module import and works best in Chrome.

## License

MIT
