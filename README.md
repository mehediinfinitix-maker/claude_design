# Rego Scan

Single-page web app: photograph a Victorian number plate, read it on-device with OCR (Tesseract.js), confirm/edit it, then open the official [Service Victoria registration check](https://service.vic.gov.au/checkrego) (VicRoads data) with the plate copied.

Run: `python3 -m http.server 8000` and open on your phone over HTTPS (camera capture needs a secure context on some browsers), or deploy to GitHub Pages/Netlify.

Why it doesn't auto-scrape VicRoads: the official check is a protected government service; scripting it is brittle and likely against its terms. If you get approved API access, replace the `window.open` in `index.html` with a fetch to your proxy.
