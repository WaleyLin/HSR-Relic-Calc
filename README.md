# HSR Relic Domain Optimizer

Stop wasting resin farming the wrong domain.

This is a single-file tool that helps you figure out which Honkai: Star Rail relic domains are actually worth your time based on how bad your current relics are across your entire roster. Rate every piece, and it tells you where to grind.

---

## The Problem It Solves

You've got 12 characters. Some have terrible boots on their cavern set. One has a bad sphere. Another has a great cavern set but a trash planar rope. You could eyeball which domain to run next — or you could feed all that info into this thing and get a ranked list in 5 seconds.

It scores your bad relics, weights them by how important they are to fix, and surfaces the domain that covers the most urgent upgrades across your whole account.

---

## How to Use It

**Open the file.** It's a single `.html` file. No install, no npm, no Python environment. Open it in Chrome or Firefox and you're done.

---

### Step 1 — Rate your relics

Each character gets a row. Pick their cavern set (4-piece, Head/Hands/Body/Boots) and their planar set (2-piece, Sphere/Rope), then give each piece a score from 1–7:

| Score | What it means |
|-------|---------------|
| 1 | Garbage — wrong main stat, wrong substats |
| 2 | Bad — needs replacing soon |
| 3 | Usable but not great |
| 4 | Decent, not prioritizing a replacement |
| 5 | Good |
| 6 | Great |
| 7 | Best in slot, don't touch |

The default scoring weights 2s heavily and gives 3s a small nudge. 4 and above contribute zero urgency — the tool doesn't care about good relics, only bad ones.

---

### Step 2 — Tune the scoring (optional)

The **Scoring Config** panel lets you change how many points each rating contributes toward farm priority. The defaults are tuned for "farm anything rated 2 or below, occasionally fix 3s" — but you can change this:

- **Strict** — only 1s and 2s matter, 3s are ignored
- **Linear** — gradual decay from 1 through 7, everything below perfect gets some weight
- **Binary** — anything 3 or below counts equally, good for when you just want volume

---

### Step 3 — Quick Entry (the fast way)

If you have your data in a spreadsheet already, paste it directly into the Quick Entry box. It accepts tab-separated rows in this format:

```
CharacterName	CavernSet	PlanarSet	score1	score2	score3	score4	score5	score6
```

Example:
```
Kafka	Ashblazing	Firmament	2	2	3	4	2	3
Acheron	Prisoner	Rutilant	3	2	4	4	3	2
Firefly	Iron	Firmament	2	3	2	4	4	3
```

The scores go in order: Head, Hands, Body, Boots (cavern), then Sphere, Rope (planar).

It also accepts a compact no-space format if you want to type fast:
```
KafkaAshblazingFirmament223423
```

Hit **Parse & Add** and it drops them into the table.

---

### Step 4 — Calculate

Hit the big **⚡ Calculate Priority** button.

You get two ranked lists:

**Sets — Farm Priority**
Which individual relic sets need the most work, scored by the total weight of bad pieces you have equipped from that set. This is useful if you already know what domain you want to run and just want confirmation.

**Domains — Farm Priority**
Which domains to actually run. A domain drops two sets, so if both sets on your roster are in bad shape, that domain ranks higher. This is the main output — look at #1 and go run it.

---

## Cavern vs Planar — What's the Difference

**Cavern Relics** come from Cavern of Corrosion domains. They're the 4-piece sets — Head, Hands, Body, Boots. Each domain drops two different cavern sets, and you can get either from a single run. These have 4-piece set bonuses.

**Planar Ornaments** come from Simulated Universe and Divergent Universe. They're the 2-piece sets — Sphere and Rope. You can't farm them from the same domains as cavern relics. These only have 2-piece bonuses.

The tool tracks them separately. The domain reference table at the bottom shows every domain with a **Cavern** or **Planar** badge so you always know what you're farming.

---

## Domain Reference Table

Scroll down to see the full list of every domain and what it drops. Use the search box to find a specific set or domain name. Useful when you're looking at a set in the results and want to know which domain drops it.

---

## Data Persistence

Everything you enter saves automatically to your browser's localStorage. If you close the tab and come back, your roster is still there. The scoring config saves too.

To start fresh, use the **Clear All** button in the top right.

---

## Tips

- Load the sample data (**Load Sample** button) to see how it all looks filled in before you enter your own characters.
- You don't need to fill in every character to get useful results. Even 3–4 characters with a shared set will show signal.
- If two characters share the same domain (e.g., both running Ashblazing), that domain will rank higher than it would for a single character — which is the whole point.
- Planar ornaments can be targeted in the Simulated Universe by selecting which path/world you want. The tool tells you which planar sets to prioritize; the SU/DU routing is up to you.

---

## No Dependencies

One `.html` file. No frameworks, no CDN calls at runtime (fonts load from Google Fonts, that's it), no accounts, no tracking. Everything runs locally in your browser.

---

## Credits

Built for personal use to stop making bad resin decisions at 1am.
