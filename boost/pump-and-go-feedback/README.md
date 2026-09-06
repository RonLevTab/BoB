# Pump & Go — Pit Stop Check

A single self-contained web page for collecting quick satisfaction feedback at the
Pump & Go bike station (Breda University of Applied Sciences). Visitors tap one of
three faces — **Not great / Okay / Great** — and each response is recorded with a
date and time.

Everything runs locally. There is no server and no build step — `index.html` is the
whole app.

## Run it

Double-click **`index.html`** (or drag it into Chrome / Edge). For a kiosk, press
**F11** for fullscreen so visitors only see the question. After each tap the screen
shows a short thank-you and returns to the question after ~4 seconds.

> Fonts load from Google Fonts when online; offline it falls back to system fonts
> and still works.

## Where responses go

Each response is stored in the browser under `localStorage` (key
`pumpgo_responses_v1`) as `{rating, timestamp}`. This means results live on the
**one device + browser** used as the kiosk. Don't clear site data or use private
browsing on that machine.

## Getting the data into Excel / CSV

Open the results panel: press **R**, tap the **bottom-left corner 5×**, or add
**`?results`** to the URL. From there:

| Button | What it does |
|--------|--------------|
| **Link a CSV file** | *(Chrome / Edge only)* Pick a `.csv` file once. From then on, every new tap rewrites that file automatically — a live spreadsheet on disk. After a full browser restart, reopen the panel and click **Reconnect file** once. |
| **Download CSV** | Saves `pumpgo-feedback-YYYY-MM-DD.csv` with all responses. Opens directly in Excel. |
| **Download Excel** | Saves a `.xls` with real columns. Excel may show a "format and extension don't match" notice — click **Yes** to open; the data is fine. |
| **Copy** | Copies the CSV text to the clipboard (works everywhere, including on locked-down machines). |
| **Clear all data** | Wipes stored responses. Double-tap to confirm. Does not touch an already-saved CSV file. |

Columns: `Rating, Label, Date, Time, Timestamp` (dates as `YYYY-MM-DD`, times as
`HH:MM:SS`, plus the full ISO timestamp).

## Recommended workflow

1. On the kiosk machine, open `index.html` in Chrome or Edge.
2. Open the results panel (`R`), click **Link a CSV file**, save it somewhere like
   `Documents/pump-and-go-feedback.csv`.
3. Leave the page open. Every tap now appends to that file — open it in Excel
   whenever you want to review.
4. As a backup, hit **Download CSV** at the end of each day.
