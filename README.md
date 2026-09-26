# Buyery Scout — mobile-first PWA MVP

## Included
- Installable responsive PWA for Android and iPhone (Add to Home Screen after HTTPS hosting).
- Barcode camera scanning where the browser supports BarcodeDetector; manual barcode fallback.
- Photo capture/preview **with manual model confirmation**. Automatic AI visual identification is **not implemented**; it would require a secure image-recognition backend and user review.
- Optional private eBay Production Browse API proxy for live **active asking prices only**.
- Manual entry of **verified** 90-day sold and comparable active units with evidence provenance. No fabricated sold figures. Marketplace Insights automated sold-data access is **not implemented** and requires separately approved access.
- £10 profit / 40% verified STR proxy decision thresholds; margin displayed without a fixed margin gate; maximum purchase price; device-local saved history and JSON export.

## Publish mobile frontend
Host the root static files over HTTPS, e.g. GitHub Pages (public repository: no supplier data or credentials in repo). Add the resulting URL to the phone home screen. HTTPS is required for camera features and service workers. Browser BarcodeDetector support varies; manual fallback is provided.

## Private backend (optional)
Deploy `backend` separately on a private server with HTTPS. Set `EBAY_CLIENT_ID`, `EBAY_CLIENT_SECRET` (Production, **never Sandbox for live data**), and `SCOUT_ALLOWED_ORIGINS` to the exact hosted frontend origin. Install backend requirements and start `uvicorn main:app --host 0.0.0.0 --port 8000`. Protect and rate-limit this backend before public deployment; CORS is not authentication. Enter its HTTPS base URL in Scout Settings.

## Important limitations
Photo capture does not yet run AI identification. There is no automatic verified sold-data connector until an authorised source is provided. Without verified sold evidence, otherwise profitable items show INSUFFICIENT DATA. Prices, matching and fees must be verified; returns, VAT and overheads are not automatically modelled. Device history is not synchronised and can be lost if browser data is cleared.

## Security
Never put eBay secrets, supplier credentials or private research exports in GitHub Pages, HTML or JavaScript. Rotate any previously exposed eBay secret.
