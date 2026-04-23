# HSR Relic Farming Planner

A Honkai: Star Rail spreadsheet that scores your current relic quality across every character and tells you exactly which Cavern of Corrosion to farm for maximum account-wide improvement.

![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat&logo=googlesheets&logoColor=white)
![HSR](https://img.shields.io/badge/Game-Honkai%3A%20Star%20Rail-blueviolet?style=flat)

---

## What It Does

Instead of guessing which domain to farm, this sheet answers:

> *"Based on how bad my relics currently are, which Cavern of Corrosion gives the most account-wide improvement per resin spent?"*

It works by converting your relic ratings into upgrade priority points, aggregating them per set, then ranking every domain by the combined value of its two relic sets.

---

## How to Use It

### Step 1 — Open the file

- **Excel**: Open `HSR_Relic.xlsx` directly. All formulas are live.
- **Google Sheets**: Go to **File → Import → Upload** and select the file. Choose *Replace spreadsheet* when prompted.

### Step 2 — Fill in the Characters tab

This is the only tab you type into. Everything else updates automatically.

For each character, fill in:

| Column | What to enter |
|--------|--------------|
| A | Character name |
| B | Their 4-piece relic set name |
| C | Their 2-piece planar ornament set name |
| D–G | Rating (1–9) for each of their 4 relic pieces (head, hands, body, feet) |
| H–I | Rating (1–9) for each of their 2 planar ornament pieces (sphere, rope) |

**Rating guide:**

| Rating | Meaning |
|--------|---------|
| 1–2 | Terrible — needs replacing urgently |
| 3 | Below average — worth upgrading eventually |
| 4–7 | Acceptable to good |
| 8–9 | Near-perfect or BiS |

To add a new character, just type into the next empty row. To remove one, clear the row entirely.

### Step 3 — Read the SetValues tab

This tab is read-only — don't edit it.

It automatically lists every relic set used across your roster and shows each set's **farm priority score**. Higher score = more characters are wearing weak relics from that set = more reason to farm it.

The score is calculated by summing the point values of all relic pieces for that set across all characters:

| Relic rating | Points |
|--------------|--------|
| ≤ 2 | 1.00 |
| 3 | 0.25 |
| 4–9 | 0.00 |

So a set worn by three characters all with rating-2 relics scores much higher than a set worn by one character with all rating-5 pieces.

### Step 4 — Read the Domain tab

This tab is also read-only.

Each row is a Cavern of Corrosion or Simulated Universe world. The tab looks up the farm score for each domain's two sets and adds them together, giving you a **total domain priority score**. The higher the score, the more your account benefits from farming there right now.

Use the domain score as your daily/weekly resin routing guide.

---

## Tab Reference

### Tab 1 — Characters

| Columns | Content |
|---------|---------|
| A | Character name |
| B | 4-piece relic set |
| C | 2-piece planar ornament set |
| D–G | Individual relic piece ratings (4 pieces) |
| H–I | Individual ornament piece ratings (2 pieces) |
| J–M | Auto-calculated point value for each relic piece |
| N–O | Auto-calculated point value for each ornament piece |
| P | Total farm priority score for the 4-piece set |
| Q | Total farm priority score for the 2-piece set |

> Columns J–Q are formula-driven and update automatically. Do not edit them.

### Tab 2 — SetValues

| Column | Content |
|--------|---------|
| A | Relic set name (auto-populated from Characters tab) |
| B | Total farm priority score for that set (sum across all characters) |

### Tab 3 — Domain

| Column | Content |
|--------|---------|
| A | Domain name |
| B | First relic set dropped here |
| C | Second relic set dropped here |
| D | Farm score of set B (pulled from SetValues) |
| E | Farm score of set C (pulled from SetValues) |
| F | Combined domain priority score (D + E) |

---


## Project Structure

```
HSR-Relic-Planner/
├── HSR_Relic.xlsx    # The spreadsheet — open this
└── README.md
```

Everything lives in the single `.xlsx` file across three tabs. No macros, no add-ins, no external data connections required.

---

## Tips

- **Ratings are subjective** — the sheet doesn't know what stats rolled; use your own judgement for what counts as a 3 vs a 4.
- **Re-rate after farming** — update ratings whenever you replace a piece so the domain scores stay accurate.
- **Zero means skip** — a domain with a score of 0 means none of your current characters need upgrades there. Save your resin.
- **Ties are fine** — if two domains score the same, pick the one whose sets you'll use on more upcoming characters.
