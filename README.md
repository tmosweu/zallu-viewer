# Zallu clinician viewer

Static page that renders a pre-consultation summary from the URL fragment (`#...`) written into the patient's QR code.

- No build step, no server logic, no storage. The fragment never leaves the browser.
- Host `index.html` anywhere static (GitHub Pages, Netlify, Cloudflare Pages, an NHS-hosted bucket) at the address set in
  `EXPO_PUBLIC_VIEWER_URL` (default `https://zallu.app/v`). The app writes `<that URL>#<payload>` into the QR.
- Payload: JSON (see `src/lib/handover.ts`, `HandoverPayload` v1) → deflate-raw → base64url. `fflate` is inlined for decoding.
- Fonts load from Google Fonts; everything else is inline. Works offline once cached; falls back to system fonts.
