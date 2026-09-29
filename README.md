# Brasileirão Wallchart

A fixture calendar for Brazilian club football: **Série A and Série B in full**, plus
every game their clubs play in the Copa do Brasil, the Supercopa do Brasil, the
Libertadores, the Sudamericana, the Recopa, the FIFA Intercontinental Cup and the
Paulista, Carioca, Mineiro and Gaúcho state championships. It refreshes itself four
times a day, keeps a record of every kick-off that moves, and picks out the
clássicos and the big-club fixtures.

A sibling of the football wallchart (`~/football-calendar/`, European leagues) and
built from the same code.

**Live page:** https://vonapets.github.io/brazil-calendar/

---

## How it runs

`.github/workflows/sync.yml` runs on GitHub Actions at **03:30, 10:30, 16:30 and
21:15 UTC**. Each run pulls the 12 competitions from ESPN, diffs them against the
previous snapshot, records anything that moved, rebuilds the page and deploys it to
GitHub Pages. No API key, no laptop.

The **03:30** run is the one that lands the results: Brazil's late kick-offs are
21:30 in Brasília (00:30 UTC) and finish around 02:30 UTC. The **21:15** run lands
the weekend 16:00 games.

To watch a run, or force one immediately:

    gh run list   --repo vonapets/brazil-calendar
    gh workflow run sync.yml --repo vonapets/brazil-calendar

**A push alone does not redeploy the page** — only the workflow publishes. After
changing code, push and then run the command above.

## Seasons

Brazilian seasons run on the **calendar year**, not August to May. The window is
1 Jan 2026 – 31 Dec 2027, so the 2026 season shows in full (results included) and
2027 fills in by itself as CBF publishes it — the state championships from January,
the Brasileirão from late January. On 29 Sep 2026 ESPN had nothing for 2027 yet.

When the 2027 season is under way, move `window_start` in `config.json` to
`2027-01-01` so the page stops carrying 2026.

## Where the data comes from

ESPN's public soccer feed (`site.api.espn.com`), one request per competition per
month, paced at 0.4 s. It is an undocumented endpoint and **it has already changed
once**: on 15 Sep 2026 it stopped accepting a date range (`?dates=20260101-20271231`
now answers HTTP 400). Month windows (`?dates=202609`) still work and were checked to
be lossless — Série A 2026 is the same 383 matches either way. `sync.py` fails the
run outright when more than half the feeds fail, so a future break shows as a red X
and an email rather than a quietly stale page.

Do not sweep ESPN's id space looking for competitions — it earned an IP ban once
(cricket wallchart). ESPN has **no feed** for the other state championships
(Paranaense, Baiano, Pernambucano, Cearense, Goiano, Catarinense…), which is why
only four are here.

## Which games are on the chart

- **Série A and Série B: every match.** Including the four Série B promotion
  play-off legs (3rd v 6th, 4th v 5th, 21 and 28 Nov 2026), which ESPN lists as
  "TBD v TBD" until the table settles.
- **Everything else: only games with a Série A or B club in them.** The clubs are
  not a hand-kept list: `sync.py` reads them off the Série A and B feeds by ESPN
  team id, so next year's promoted and relegated clubs are picked up without an
  edit. That is why the Copa do Brasil shows 103 of its 155 games and the
  Libertadores 65 of 155.
- **Undrawn finals are kept.** The Libertadores, Sudamericana and Copa do Brasil
  finals show as "TBD v TBD" on their date, because a Brazilian club may well be in
  them (three of the four 2026 Libertadores semi-finalists are Brazilian).

## Big matches

`top_teams` in `config.json` lists 23 clubs: the twelve **grandes** (tier 1 —
Flamengo, Fluminense, Vasco, Botafogo, Corinthians, Palmeiras, São Paulo, Santos,
Grêmio, Internacional, Atlético-MG, Cruzeiro) and eleven regional powers (tier 2).
Their names are bold everywhere.

Because nearly every Série A club is on that list, "both clubs listed" would make
almost every game big. So a **big match** — ringed in the grid and listed in
**Matches that matter** — is one of:

- two grandes, or a **clássico** (18 are named: Fla-Flu, Derby Paulista, Grenal,
  Choque-Rei, Majestoso, Clássico Mineiro, Ba-Vi, Atletiba, Clássico-Rei…);
- a knockout tie between two listed clubs;
- a Libertadores or Sudamericana **semi-final or final** with one listed club (the
  other side is foreign, so never on the list);
- any **final**, even before it is drawn.

The three-bar meter: one bar = big clash, two = semi-final, three = clássico or
final. **Big clubs only** (off by default) hides everything without a listed club.

Edit `top_teams` and run `python3 build.py` — no re-sync needed. If you change the
big-match rule, change it in both `isBig()` in `template.html` and
`annotate_top()` in `build.py`.

## Breaks

Série A and Série B **do not stop together** — Série B played straight through the
2026 World Cup and the Sep/Oct international window. The five 2026 breaks in
`config.json` are Série A's, read off the fixture list and cross-checked against the
FIFA calendar; each one's note says what Série B did. `sync.py` also flags any
10-day stretch without Série A football that is not already listed.

2027 breaks are not listed yet — add them when CBF publishes the 2027 tables.

## What the pieces do

| File | What it is |
|---|---|
| `config.json` | Competitions, the window, the breaks, the big-club list and clássicos. Edit this, not the code. |
| `sync.py` | Fetches fixtures, works out what changed since the last run, writes `data/`. |
| `build.py` | Turns the saved data into `calendar.html`. |
| `template.html` | The page design. |
| `test_diff.py` | Proves the reschedule detection still works. Run after changing `sync.py`. |
| `run.sh` | Sync and build locally, by hand. |
| `data/fixtures.json` | The latest snapshot — the pipeline's memory of "yesterday". |
| `data/changes.json` | Every kick-off that has moved. Never overwritten. |
| `docs/brazil-sports-on-prediction-markets.md` | Which sports Brazil follows, and which of them trade on Polymarket and Kalshi. |

## Things worth knowing

- **Times follow the device.** Kick-offs are stored in UTC and shown in the
  viewer's local time — a 21:30 Brasília game reads 01:30 in Lisbon.
- **`TBD` instead of a time** means CBF has not fixed the kick-off yet; the date is
  right. CBF confirms times in blocks of a few rounds.
- **No matchday numbers.** ESPN does not publish the Brasileirão round, and
  postponements make counting unreliable, so the chart does not invent one.
