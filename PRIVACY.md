# Privacy Policy

## Summary

This tool runs entirely in your browser. No data is collected, stored, or transmitted. However, **an internet connection is required** — the libraries that handle `.docx` parsing and PDF rendering are loaded from external CDNs at runtime.

## What happens to your files

The `.docx` file you upload is read locally by your browser using the [File API](https://developer.mozilla.org/en-US/docs/Web/API/File_API). It is never uploaded to any server. Processing — unpacking the ZIP structure, reading the XML, replacing tags, and repacking — happens entirely in memory within your browser session.

The filled document is generated as a local blob and downloaded directly to your device. No copy is retained after the page is closed or refreshed.

## Form data

Values you enter into the form fields exist only in the browser's memory for the duration of your session. They are not persisted to local storage, cookies, or any external service.

## External requests

The only network requests made by this tool are to load two open-source libraries from public CDNs:

- **PizZip** — loaded from `unpkg.com`, used to read and write the `.docx` ZIP format.
- **docx-preview** — loaded from `esm.sh` on demand when you use the PDF export feature, used to render the document for printing.

These requests are subject to the respective CDN providers' privacy policies. No personal data or document content is included in these requests.

## Cookies and tracking

This tool sets no cookies and performs no analytics or tracking of any kind.

## Changes

This policy may be updated alongside the tool. The current version is always available in the repository.
