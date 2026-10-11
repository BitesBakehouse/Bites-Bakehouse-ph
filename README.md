# Bites Bake House POS (starter project)

An offline-first, single-device Progressive Web App (PWA) for a small cookie business. Built with plain HTML, CSS and JavaScript; no framework or subscription required.

## Included
- Touch-friendly product checkout and cart
- Cash and GCash payment recording
- Cash received and change calculation
- Product catalog, prices, unit costs and stock-on-hand
- Stock deduction when a sale completes
- Sales reports by date range, payment method and estimated gross profit
- JSON full backup/restore and sales CSV export
- Receipt printing through Cleanter's local print bridge (`http://localhost:9100/print`) with browser print fallback
- PWA manifest and service worker for installation and offline app shell

## Important limitations
- This is a starter app, not a certified accounting or BIR-compliant invoicing system. Confirm Philippine tax/invoicing requirements with a qualified accountant or the BIR before using it as your official sales invoice system.
- Data is stored in the browser on this tablet. There is no cloud sync, staff login, multi-device sync, or automatic off-device backup. Export a JSON backup every day.
- Browser storage can be deleted by clearing site data. Do not clear browser data before backing up.
- Estimated gross profit is sales less the per-unit cost entered for each product; it does not include labor, rent, utilities, packaging, taxes, waste or other overhead.
- Printer compatibility varies. Choose a Bluetooth Classic (SPP) ESC/POS printer and test it before your return window ends.

## Run locally on Windows for development
1. Install a current version of Python 3 from https://www.python.org/downloads/windows/ (enable “Add Python to PATH” during setup).
2. Extract this folder to a normal folder such as `C:\BitesPOS`.
3. Open Command Prompt in that folder.
4. Run `python -m http.server 8080`.
5. On the PC, open `http://localhost:8080` to test the app. This is a development server; closing the terminal stops it.

For a proper PWA install, publish these files to an HTTPS host. A simple option is GitHub Pages. Keep the repository private if you do not want the source publicly visible; availability of private Pages hosting depends on your GitHub plan/settings.

## Publish with GitHub Pages
1. Create/sign in to a GitHub account and create a repository named `bites-bake-house-pos`.
2. Upload the contents of this folder (not the enclosing folder) to the repository's root.
3. In repository Settings → Pages, select deployment from the `main` branch and `/ (root)` and save.
4. Wait for the HTTPS site URL to become available.
5. Open the URL in Chrome on the Android tablet, wait for the app to load once, then use Chrome menu → Install app or Add to Home screen.
6. Make a backup after entering products and at the end of every business day.

## Receipt printing on Android
This app supports Cleanter's local HTTP API. Cleanter is a separate Android print-bridge app; check its current availability, permissions and terms before use.
1. Buy a printer that explicitly supports Bluetooth Classic (SPP) and ESC/POS. Do not buy a Bluetooth LE-only printer for this setup.
2. Pair it in Android Settings → Bluetooth.
3. Install/open Cleanter on the same tablet, select the paired printer as default, and make sure the local service is running.
4. Open the hosted Bites POS app on that same tablet. In Settings & Backup, tap Check printer bridge, then Print test receipt.
5. If bridge printing fails, use the browser print fallback. If the browser blocks a pop-up, allow pop-ups for the POS site and retry.

## First-run checklist
- Edit sample product names, prices, costs and stock to match your actual products.
- Test a low-value sale, cash payment, GCash payment, stock deduction, report, receipt print, CSV export and full backup.
- Restore a test backup only after exporting a fresh backup, because restore replaces local data.


## Add your business logo

Place your logo image in this project folder beside `index.html` and name it exactly `logo.png`. The logo appears in the app header and in the browser-print receipt. If your original image has another format, convert it to PNG or update the `logo.png` references in `index.html` and `app.js`. The Cleanter bridge receipt uses text commands in this version, so the logo is included in the browser-print fallback; image printing through the bridge depends on whether that bridge supports image commands.
