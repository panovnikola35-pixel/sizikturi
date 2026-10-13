# HaulLedger — Transport Records

A static, browser-based record-keeping tool for credit notes, fuel transactions, tolls and consistency checks. Designed for GitHub Pages; no server or database is required.

## Deploy to GitHub Pages
1. Create a new GitHub repository (for example `haulledger`).
2. Upload `index.html` and `README.md` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
5. Wait for the Pages URL shown in Settings → Pages.

## Use
- Open the deployed page in a modern browser.
- Import credit note PDFs. PDFs need selectable text; scanned documents require OCR first.
- Import fuel transaction XLSX/XLS/CSV exports. It detects common transaction export columns and uses `EUR GrossAmount` by default, falling back to `EUR NetAmount`.
- Review every imported credit note and correct fields using Edit.
- Check **Consistency checks** for duplicate note numbers, repeated shipping orders, missing fields, extracted line-total differences and possible duplicate fuel rows.
- Export CSV registers or download a full JSON backup regularly. Restore a backup from Import & export.

## Calculation notes
- Revenue = sum of printed credit-note totals.
- Fuel cost = sum of imported EUR transaction amounts.
- Tolls = sum of toll charges extracted from credit notes (editable).
- Net after fuel & tolls = revenue − fuel cost − tolls.

This is a management estimate. Credit note totals may already include toll charges; tolls are subtracted separately here because the requested calculation was revenue less fuel and tolls. Check that this matches your intended accounting treatment and avoid double-counting. The app does not provide tax/accounting advice.

## Privacy and technical notes
- Data is stored in `localStorage` in the browser profile. It does not synchronize between devices and can be lost if browser storage is cleared. Download backups regularly.
- Files are parsed client-side. The app loads SheetJS and PDF.js from public CDNs, so the browser needs internet access to load those libraries.
- No file contents are sent to a custom backend.
- This app is a starting point; verify extracted amounts against the source PDFs/spreadsheets before relying on reports.
