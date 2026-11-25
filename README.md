# Rego Scan

Single-page web app: photograph a Victorian number plate, read it on-device with OCR (Tesseract.js), confirm/edit it, then open the official [Service Victoria registration check](https://service.vic.gov.au/checkrego) (VicRoads data) with the plate copied.

Run: `python3 -m http.server 8000` and open on your phone over HTTPS (camera capture needs a secure context on some browsers), or deploy to GitHub Pages/Netlify.

Why it doesn't auto-scrape VicRoads: the official check is a protected government service; scripting it is brittle and likely against its terms. If you get approved API access, replace the `window.open` in `index.html` with a fetch to your proxy.

---

# Crewboard (`crewboard/index.html`)

A one-file control panel for a "company" of AI agents, inspired by the open-source Paperclip project. You set goals, give work to agents arranged in an org chart, and review what they produce.

- **Goals → tasks**: every task carries its goal chain, so agents know why the work matters.
- **Org chart**: agents with a role, instructions, model, manager and budget. You can hire, edit, pause or remove them.
- **Heartbeats**: one click, or a timer while the tab is open, wakes each active agent. Each agent takes its top To-do task and does it through the Claude API.
- **Governance**: finished work goes to *Review*, where you approve it or request changes. If approval is required, tasks that agents propose wait in *Approvals*.
- **Budgets**: cost is tracked per agent and per task. You get a warning at 80%, and the agent is paused automatically at 100%.

Run: open `crewboard/index.html` in a browser (or `python3 -m http.server`). Then go to Settings, add an Anthropic API key and click **Run heartbeat**. All data stays in your browser's localStorage. Use Export/Import to back it up.

Limits compared with Paperclip: agents can only write (they can't browse, run code or send messages), nothing runs when the tab is closed, and there is one company per browser.
