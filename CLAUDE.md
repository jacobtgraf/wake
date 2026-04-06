# Jacob & Ryan Europe Trip — Claude Code Context

## What This Repo Is
A mobile-first HTML travel companion for Jacob Graf & Ryan Fitzgerald's Europe trip (Apr 2–14, 2026). Built iteratively with Claude Code from Gmail confirmation emails. Single self-contained HTML file — no build step, no dependencies, works offline once loaded.

**Live URL:** https://jacobtgraf.github.io/wake/
**Repo:** https://github.com/jacobtgraf/wake
**GitHub Pages:** main branch root → `index.html`

---

## Files
| File | Purpose |
|------|---------|
| `index.html` | The live trip board (v2, mobile-first, light mode) |
| `link-test.html` | Quick link tester for verifying deep links on iPhone |
| `europe-trip-board-original.html` | Original v1 desktop kanban (dark mode, horizontal scroll) |

---

## Trip Overview
**Route:** San Francisco → Miami → London → Bath (day trip) → Cotswolds → Paris → San Francisco
**Travelers:** Jacob Graf & Ryan Fitzgerald

| Date | Location | Key Event |
|------|----------|-----------|
| Apr 2 | San Francisco | Depart SFO→FLL (UA 1230, conf DHEXJD) |
| Apr 3–5 | Miami Beach | Hyrox Miami (Ryan competing, Jacob spectating) |
| Apr 6 | MIA→LHR | DL 5966 / Virgin Atlantic, departs 6:25 PM EDT |
| Apr 7 | London | Arrive LHR 8:05 AM BST · Sandy's (Kindred) · Fallow dinner |
| Apr 8 | Bath day trip | GWR train · Roman Baths · La Terra · Thermae Bath Spa |
| Apr 9 | London | Free day · Dishoom Carnaby (8 guests, 9 PM) |
| Apr 10 | → Cotswolds | Enterprise car pickup 12 PM · Drive to Grittleton |
| Apr 11 | Grittleton | Francesca & Keith's wedding 💍 |
| Apr 12 | → Paris | Check out · Chippenham train · Eurostar 12:31 · Le Pigalle · Eiffel Tower |
| Apr 13 | Paris | Louvre · Ardent Paris dinner (anniversary) |
| Apr 14 | CDG→SFO | DL 8726 / Air France, departs 10:20 AM CEST, arrives 12:50 PM PDT |

---

## All Bookings with Gmail Deep Links

Gmail link format: `https://mail.google.com/mail/u/0/#inbox/MESSAGE_ID`

| Event | Key Details | Gmail Message ID |
|-------|-------------|-----------------|
| ✈ MIA→LHR (DL 5966) | Departs 6:25 PM EDT · Jacob: 58B, Ryan: 58A · Conf **F77XBA** | `19d5fc0e246cc461` |
| ✈ CDG→SFO (DL 8726) | Departs 10:20 AM CEST · Jacob: 33J · Conf **F77XBA** | `19bb0639bc202d70` |
| 🏨 Sandy's London (Kindred) | Unit 11 · 10 Montagu Mews S, W1H 7ER · **Door code: 1340** (lockbox) · Check-in after 4 PM | `19d6220ecdd39389` |
| 🍽 Fallow Restaurant | 52 Haymarket SW1Y 4RP · 7 PM · 2 guests · Ref **3YWXGL6DLSNN** | `19d5d1e03ba0daf3` |
| 🚂 GWR Bath (both ways) | Paddington 06:28 Coach A 13&14 · Bath 19:43 Coach A 27&28 · Ref **B-GWR-ERL0JAU3G** | `19d22ef42abc7ced` |
| 🏛 Roman Baths | 9:15 AM · 2 adults · £53 · Ref **RBOYDP1TXZRDM** | `19d22ebd3da5f12f` |
| 🍽 La Terra Bath | 2 John St BA1 2JL · 12:30 PM · 2 guests · Ref **BNK36TL9** | `19d22f482aa4d0ea` |
| ♨️ Thermae Bath Spa | Hot Bath St BA1 1SJ · 4:30 PM · Conf **#1963102** · links to thermaebathspa.com/user/login | not in Gmail |
| 🍽 Dishoom Carnaby | 22 Kingly St W1B 5QP · 9 PM · 8 guests · Ref **8EH6NT35UUCF** (Ryan's booking) | `19d2298a4ecdb7a9` |
| 🚗 Enterprise Car | NCP 170 Marylebone Rd NW1 5AR · 12 PM · Nissan Qashqai (auto) · Conf **2101387643** | `19d2e0038583934f` |
| 🚄 Eurostar | St Pancras→Gare du Nord 12:31–16:01 · Jacob: Coach 5 Seat 52, Ryan: Seat 51 · **Arrive by 11:16** · Ref **6DJ26K** | `19d41c5424f63226` |
| 🏨 Hôtel Le Pigalle | 9 Rue Frochot, 75009 Paris · Room: Pigalle 35 · Conf **65706SG045052** · City tax at checkout | `19d08f1fe518d26c` |
| 🗼 Eiffel Tower | 7:30 PM CEST · 2nd floor by lift + champagne · 2 adults · Purchase **262010165929** | `19d25d8b060481e5` |
| 🖼 Louvre | 2 adults · Order **C260900001308** · Sale Ref **V26078735832** · **Nominative — bring photo ID** | `19d41c085807775b` |
| 🍽 Ardent Paris | 40 Rue Richer 75009 · 8:30 PM · 2 people · Window table · Anniversary · Res **1733397499** | `19d1e452d3046bf8` |
| 🏋️ Hyrox spectator tickets | Ryan forwarded · PDF attachment | `19d1bcaf1719b71c` |

---

## Deep Link Decisions (already implemented)

| Link type | Implementation | Notes |
|-----------|---------------|-------|
| ✈ Delta app | `https://www.delta.com/MyTrips` | Confirmed universal link via Delta's AASA file — opens Delta app if installed |
| 📧 Gmail | `https://mail.google.com/mail/u/0/#inbox/MESSAGE_ID` | Opens specific email in Safari (no iOS URL scheme for specific messages in Gmail app) |
| 📍 Apple Maps | `https://maps.apple.com/?q=PLACE+NAME+ADDRESS` | Opens location pin/card (not directions) — user navigates from there |
| 🌐 Thermae | `https://www.thermaebathspa.com/user/login` | Conf not in Gmail; links to their website login |
| 🎟 Train tickets | Gmail deep link to email | GWR and Eurostar tickets are in email |

---

## Design Decisions

- **Layout:** Vertical single-column timeline (replaced horizontal kanban from v1)
- **Mode:** Light mode — white cards on `#f2f2f7` background (iOS system palette)
- **Today logic:** JS auto-collapses past days, expands today, shows "Up Next" hero card at top
- **Up Next:** Computes from UTC timestamps embedded in JS events array; updates dynamically
- **Chips:** Tap-to-copy booking refs — uses `navigator.clipboard` with `input`-based fallback
- **Clipboard / universal links:** Require HTTPS — work correctly on GitHub Pages, not from `file://`
- **Offline:** Pure HTML/CSS/vanilla JS, zero CDN dependencies — works after first HTTPS load
- **Home screen:** `apple-mobile-web-app-capable` meta tag — user can Save to Home Screen in Safari

---

## Outstanding / Future Work

- [ ] **Test on iPhone via GitHub Pages URL** — verify Delta universal link, Gmail links, Apple Maps pin, clipboard chips all work over HTTPS
- [ ] **Sandy's door code** — confirm `1340` is correct once Jacob arrives (surfaced prominently in the card)
- [ ] **Louvre timing** — no specific entry time in the booking; check confirmation email for slot
- [ ] **Chippenham → Paddington train (Apr 12)** — no ticket booked yet (per original board); may need to buy day-of
- [ ] **Link test cleanup** — `link-test.html` can be removed once iPhone testing is confirmed

---

## Technical Notes

- **Repo push:** Used `gh auth setup-git` with HTTPS remote (SSH key not linked to account)
- **gh CLI path:** `/opt/homebrew/bin/gh` (not in default PATH during Claude Code sessions — use full path)
- **No package.json / no dev server** — this is a pure static project; `python3 -m http.server 8080` works for local testing
- **Git root:** `/Users/Jacob` (home directory repo) — unrelated to this project; Trip Planner files lived at `~/Documents/Claude/Trip Planner/`
