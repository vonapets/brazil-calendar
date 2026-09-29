# Brazil's popular sports on Polymarket and Kalshi

*Research date: 29 Sep 2026. All market data pulled from the Polymarket Gamma API and the Kalshi trade API on 29 Sep 2026; popularity figures from the surveys cited. Raw pulls, scripts and `out/summary.json` are in `~/brazil-calendar/research/sports_markets/` on the machine that built this — local only, not committed (≈250 MB).*

> **Units:** these volume figures aren't directly comparable, so read this first.
> - **Polymarket "vol"** is Gamma `volume`, the sum of taker fill sizes in $1-notional shares. Polymarket shows it with a "$" sign, but it is not premium paid.
> - **Kalshi contracts** (`volume_fp`) use the same $1-notional unit, so they are the closest like-for-like comparison. They are inflated by losing legs that get dumped at $0.001 after settlement.
> - **Kalshi premium $** is rebuilt from daily candles (contracts × mean price). It is the money actually paid.
> - *Checked 29 Sep 2026:* on a settled Série A market, Gamma volume 36,067 equals the summed size of its 128 taker trades (36,067 shares), while the dollars paid were $29,572.
> - Never compare Polymarket vol with Kalshi premium $ as if both were dollars. On Série A, Kalshi's contract count is 1.5× Polymarket's volume, but its premium $ is smaller than Polymarket's volume.

## Headline

- **Football is both the most popular sport and the one with real Brazil-specific markets on both venues.** Série A, B and C, Copa do Brasil, Libertadores and Sudamericana all list match markets on Polymarket and Kalshi. Settled matches involving Brazilian clubs: Polymarket 959 matches / 181.6M vol. Kalshi 782 matches / 361.7M contracts / ~$147.4M premium.
- **Both venues are new to Brazilian football.** First Kalshi match date: Série A 2025-11-01, Série B 2026-06-30, Série C 2026-06-30, Copa do Brasil 2026-04-22, Libertadores 2026-04-08, Sudamericana 2026-04-08. First Polymarket match date: Série A 2025-10-08, Série B 2026-03-21, Série C 2026-07-25, Copa do Brasil 2026-04-21, Libertadores 2025-09-16, Sudamericana 2025-09-16. On Série A, Kalshi's contract count is 1.5× Polymarket's volume. Outrights (Série A winner, Libertadores winner) are dead on both venues: under $40k each.
- **Brazil-linked events outside club football trade heavily, inside global products.** Brazil's 5 World Cup games did Polymarket 275.4M vol and Kalshi 196.0M contracts. João Fonseca's matches did Polymarket 27.9M and Kalshi 134.7M contracts. UFC fights with Brazilian fighters did Kalshi 273.8M contracts, and FURIA/MIBR esports matches also trade. Events staged in Brazil have their own history on both venues: the NFL São Paulo 2025 and Rio 2026 games, UFC Rio, the São Paulo F1 GP, the Rio Open, and IEM Rio (Polymarket only).
- **Several sports that Brazilians love are missing or negligible.** Superliga volleyball, futsal, skateboarding, NBB (Polymarket) and the state championships (Paulista/Carioca/Mineiro) are **never listed**. Indoor volleyball on Polymarket is tiny and all closed: the Nations League (60 games, 61k vol), EuroVolley (123 games, 119k vol) and German 2. Bundesliga (13 games, 691 vol). Kalshi's only sizeable volleyball is **US college** (NCAA women's: 696 matches, 1.4M contracts, open in season) plus the Pan American Cup (14 matches, 2.6k contracts). *Corrected 29 Sep: the first pass counted only the Nations League and the Pan American Cup.* Volleyball is the biggest popularity-vs-supply gap.

## Ranked table: popularity in Brazil vs what trades

Ranked by Brazil popularity. The sources use different definitions and years (see Caveats), so the order below football is approximate. Polymarket figures are settled volume unless marked "open". Kalshi figures cover every status (live and historical tiers).

| # | Sport | Brazil popularity (figure + source) | Polymarket | Kalshi | Brazil-specific markets found | Evidence class |
|---|---|---|---|---|---|---|
| 1 | **Football: Brazilian clubs** | **Datafolha, Jul 2026** (n=2,004, 16+): 64% have much/some interest in football (28% "muito"), down from 72% in 2023 [D]. Competitions followed (Opinion Box 2024): Brasileirão 83%, Copa do Brasil 77%, Libertadores 69%, Sudamericana 57%, state championships 48% [O] | **Yes.** Match winner (3-way), spreads, totals, BTTS, exact score, halves, corners, team totals; small outrights. Série A: 395 matches, 99.4M; Série B: 298 matches, 21.9M; Série C: 66 matches, 1.5M; Copa do Brasil: 56 matches, 12.2M; Libertadores†: 71 matches, 24.3M; Sudamericana†: 73 matches, 22.3M | **Yes.** Match winner, spread, totals, BTTS, 1st-half, correct score, team totals, first to score, to-advance, outrights. Série A: 369 matches, 148.6M c / $62.7M; Série B: 157 matches, 85.0M c / $34.9M; Série C: 89 matches, 17.3M c / $7.5M; Copa do Brasil: 51 matches, 28.3M c / $11.1M; Libertadores†: 52 matches, 40.8M c / $15.3M; Sudamericana†: 64 matches, 41.7M c / $16.0M | All six competitions, both venues (†=ties involving a Brazilian club). State leagues: none | **Own history** |
| 2 | **Football: Seleção** | Opinion Box 2024: World Cup 74%, WC qualifiers 60% of sports followers [O]; football interest fell to 64% after Brazil's R16 exit to Norway (Datafolha 2026) [D] | **Yes.** WC 2026 Brazil games: 5 games + 35 side events, 275.4M; Brazil-to-win-WC leg 81.9M; friendlies 11 games, 6.1M; CONMEBOL qualifiers 2 (Sep 2025), 176k | **Yes.** WC games: 5 games, 196.0M contracts · $71.5M premium; Brazil-to-win leg 26.7M contracts · $1.8M premium; friendlies 7 games, 11.2M contracts · $4.7M premium | Brazil's own fixtures (WC 2026: Morocco, Haiti, Scotland, Japan, Norway) | **Own history** (team-specific fixtures inside global tournaments) |
| 3 | Volleyball (indoor) | IBOPE Repucom Sponsorlink, Jun 2022 wave: 87% of connected adults show some interest (96M) [I-vb]; Opinion Box 2024: 38% [O] | **Barely, all closed.** Nations League 60 games (26 Jun–1 Aug 2026), 61k; EuroVolley 123 games (19 Aug–26 Sep 2026), 119k; German 2. Bundesliga 13 games, 691. Brazil's Nations League games 8 games, 5k. Superliga and World Championship series defined in `/sports` but **0 events** | **US college only, in size.** KXNCAAWVMATCH (NCAA women's): 696 matches from 9 Sep 2026, 1.4M contracts, open in season; KXNCAAWV 2026 champion outright (49 teams). International: KXVOLLEYBALLMATCH 14 Pan American Cup matches (14–17 Aug 2026), 2.6k contracts. No Brazil match | Brazil VNL games (Polymarket, ~$5k) | **Sport only** (Superliga never listed) |
| 4 | Formula 1 | IBOPE Sponsorlink, Jun 2022: 47% of connected adults are fans (52.2M) [I-f1]; Opinion Box 2024: 36% (F1/F2/F3 GPs followed: 29%) [O] | **Yes.** Race winner, podium, pole, fastest lap, H2H, championships: 400 events (2023-11→2027-04), 281.2M settled + 232.7M open | **Yes.** KXF1RACE 40 races (2025-03→2026-10), 66.1M contracts, plus podium/pole/H2H series (not pulled) | São Paulo/Brazilian GP: Polymarket 14 events (2024–25), 2.5M. Kalshi 2025 winner market 1.0M contracts · $313k premium. Bortoleto legs: Polymarket 7.8M, Kalshi 3k contracts. 2026 GP (8 Nov) not yet listed | **Own history** (the GP itself) |
| 5 | Esports (CS2, LoL, Valorant, Free Fire) | IBOPE Sponsorlink, Nov 2021 wave: 46% of connected adults are fans (50.5M) [I-es] | **Yes, large.** CS2 11,148 events (2025-09→2026-11) / 1.74B; LoL 3,462 / 2.64B; Valorant 2,591 / 244.4M. Free Fire: one EWC-winner market, $435 | **Yes.** CS2 6,385 games (2026-01→2026-10) / 532.1M c; LoL 2,789 / 361.0M c; Valorant 1,591 / 175.0M c. No Free Fire game markets (only an EWC-winner series, not pulled) | **CBLOL** (Polymarket 119 events, 49.6M). **IEM Rio 2026** (Polymarket 83 matches, 72.0M). Gamers Club Liga (153 matches, 1.3M). FURIA all titles: Polymarket 186 events / 183.3M. MIBR: 236 / 71.0M. Kalshi Brazilian-team games: CS2 616 (102.0M contracts · $52.5M premium, 89% candle-priced), LoL 219 (17.9M contracts · $9.1M premium, 70% candle-priced), Valorant 92 (24.5M contracts · $12.1M premium, 92% candle-priced) | **Own history** (CBLOL, IEM Rio, Gamers Club Liga) |
| 6 | Surfing | IBOPE Sponsorlink, Nov 2021 wave: 41% fans (45.3M) [I-sf] | **No** (public-search "surf": no surfing markets) | **Tiny.** KXSURF/KXSURFCOMPETITION: 6 events (2025-12→2026-09), 134k contracts total | Brazilian-surfer legs (Yago Dora etc.): 19k contracts · $2k premium | **Sport only** |
| 7 | American football (NFL) | IBOPE Sponsorlink, Jun 2024 wave: 35% of connected adults are American-football fans (41M) [I-nfl] | **Yes.** 2026-season series: 157 games (2026-08→2026-10), 299.5M settled so far | **Yes.** KXNFLGAME 461 games since Jul 2025, 6.68B contracts | **NFL São Paulo 2025** (KC–LAC, 5 Sep 2025): Polymarket 3.3M, Kalshi 27.3M contracts · $13.6M premium. **NFL Rio 2026** (BAL–DAL, 27 Sep 2026): Polymarket 8.2M, Kalshi 36.2M contracts · $17.5M premium | **Own history** (the Brazil games) |
| 8 | Basketball (NBA + NBB) | Opinion Box 2024: basketball 32%, NBA followed by 29% [O]. No NBB figure found | **NBA yes** (1,421 games (2025-10→2026-10), 4.36B). **NBB: series defined, 0 events** | **NBA yes** (1,452 games (2025-04→2026-10), 11.68B contracts). **NBB yes**: KXNBBGAME 10 playoff games (21 May–7 Jun 2026), 1.6M contracts · $855k premium | NBB playoffs (Kalshi only) | **Own history** (Kalshi NBB) |
| 9 | Tennis | Opinion Box 2024: 31% [O]; IBOPE 2019: 27M fans [I-tn]; female tennis fans +33% since 2020 (IBOPE, Jun 2024 wave) [I-w]. No Fonseca-specific audience figure found | **Yes.** ATP 9,670 (2025-10→2026-10) / 1.89B; WTA 5,117 / 982.9M (moneyline, set handicap, totals, first set) | **Yes.** ATP 4,765 (2025-06→2026-09) / 7.10B c; WTA 4,714 / 4.68B c | João Fonseca: Polymarket 42 matches, 27.9M; Kalshi 55 matches, 134.7M contracts · $68.2M premium, plus a 'Fonseca wins a 2026 major' market (29k c). Haddad Maia: Polymarket 23 / 2.7M; Kalshi 33 / 9.2M contracts · $4.9M premium. **Tournaments in Brazil**, Polymarket: Rio Open, Qualification 12 matches/614k, Rio Open 34 matches/7.1M, Sao Paulo 31 matches/1.0M, Sao Paulo Open, Qualification 13 matches/1.3M, Sao Paulo Open 34 matches/10.3M. Kalshi (matched to Polymarket fixtures by player names): Rio Open, Qualification 11/3.9M c, Rio Open 34/48.4M c; no São Paulo Open match found | **Own history** (Rio Open, São Paulo Open) |
| 10 | MMA / UFC | Opinion Box 2024: UFC followed by 29% [O]; IBOPE 2019: 30M MMA fans [I-mma] | **Yes.** 654 UFC events (2021-01→2026-10), 352.1M (moneyline, method, distance, rounds) | **Yes.** KXUFCFIGHT 731 fights (2025-05→2026-10), 1.37B contracts | **UFC Rio (11 Oct 2025, Oliveira vs Gamrot)**: Polymarket card 3.9M; Kalshi 6 fights, 979k contracts · $461k premium, 95% candle-priced. Fights with a Brazilian (name list): Polymarket 107 events, 49.3M; Kalshi 129 fights, 273.8M contracts · $129.0M premium | **Own history** (UFC Rio card) |
| 11 | Beach volleyball | IBOPE Women & Sports 2025 (Jun 2024 wave, n=2,000): 61% of **women** are fans [I-w] (no all-adult figure found) | **Barely.** 3 outright events ever: 2025 Worlds M and W (~130k vol each), 2024 Olympics W (11k) | **No** | None | **Sport only** |
| 12 | Futsal | IBOPE Women & Sports 2025: female futsal fans +27% since 2020 [I-w] (growth only, no level) | **No** (search: 0) | **No** series | None | **Never listed** |
| 13 | Skateboarding | IBOPE Women & Sports 2025: female skate fans +48% since 2020 [I-w] (growth only, no level) | **No** (search: 0) | **No** series | None | **Never listed** |
| 14 | Boxing | No figure found (not searched further — lean run) | **Yes, small.** Boxing series 41 events (2026-08→2026-09) / 256k; Zuffa Boxing 102 / 1.1M | **Yes.** KXBOXING 375 fights (2025-05→2026-12), 226.2M contracts | None checked | **Sport only** |
| 15 | Handball | No figure found (not searched further — lean run) | **Yes, European leagues only** (Bundesliga, Håndboldligaen, LNH…; search: 244 hits, ~$1.9M incl. non-handball noise) | **No** series | None | **Sport only** |

Sources for the popularity column: [D] Datafolha via Exame, 1 Aug 2026 — https://exame.com/esporte/datafolha-interesse-dos-brasileiros-por-futebol-cai-apos-a-copa-de-2026/ · [O] Opinion Box for Aposta Legal Brasil (n=525 online) via Esporte Press Brasil — https://www.esportepressbrasil.com.br/noticia/2166/pesquisa-mostra-campeonatos-e-esportes-mais-vistos-pelos-brasileiros/ · [I-vb] https://www.iboperepucom.com/br/noticias/volei-e-o-esporte-que-mais-desperta-algum-interesse-entre-brasileiros-conectados/ · [I-f1] https://www.iboperepucom.com/br/noticias/formula1-52-milhoes-de-brasileiros-conectados-se-declaram-fas-da-competicao/ · [I-es] https://www.iboperepucom.com/br/noticias/e-sports-volume-fas-modalidade-dobra-ultimos-anos/ · [I-sf] https://www.iboperepucom.com/br/noticias/surfe-atinge-nivel-historico-de-popularidade-entre-os-brasileiros/ · [I-nfl] https://www.iboperepucom.com/br/noticias/fidelidade-em-jogo-os-fas-de-nfl-sao-mais-fieis-as-marcas-patrocinadoras-que-a-media-dos-brasileiros/ · [I-tn] https://www.iboperepucom.com/br/noticias/rio-open-e-brasil-open-estao-entre-os-eventos-com-maior-interesse-da-populacao-conectada/ · [I-mma] https://www.iboperepucom.com/br/noticias/brasil-30-milhoes-de-fas-de-mma/ · [I-w] IBOPE Repucom *Women and Sports 2025* — https://www.iboperepucom.com/br/noticias/o-interesse-medio-feminino-por-esporte-cresce-desde-2020/ and PDF https://www.iboperepucom.com/media/2025/03/Estudo-IBOPE-REPUCOM-WOMEN-AND-SPORTS-2025-2.pdf. Every figure was read on the source page itself (saved under `research/sports_markets/web/`); none is snippet-only.

## Brazilian football competitions in detail

Only settled matches count toward volume. "Per match" figures are the settled total divided by settled matches. Polymarket totals include each match's side events ("More Markets", halftime, exact score, corners). Kalshi totals add every market series for the match (GAME, SPREAD, TOTAL, BTTS, 1H*, SCORE, TEAMTOTAL, FTTS, ADVANCE). Kalshi premium $ is rebuilt from daily candles; 96% of Brazil-football contracts are priced from their own candles, and the rest are extrapolated at their market type's average price (see Caveats).

| Competition | Venue | Matches listed (settled / open) | Match dates | Settled volume | Avg per settled match | Median | Outrights |
|---|---|---|---|---|---|---|---|
| Série A | Polymarket | 415 (395 / 20) | 2025-10-08→2026-10-12 | 99.4M vol (match-winner 65.4M, side 34.0M) | 252k vol | 157k | 7 events, all still open |
| Série A | Kalshi | 391 (369 / 22) | 2025-11-01→2026-10-12 | 148.6M contracts · $62.7M premium (92% candle-priced) | 397k contracts · $154k premium (candle-priced part) | — | 39,216 contracts |
| Série B | Polymarket | 324 (298 / 26) | 2026-03-21→2026-10-11 | 21.9M vol (match-winner 13.7M, side 8.2M) | 73k vol | 42k | none |
| Série B | Kalshi | 170 (157 / 13) | 2026-06-30→2026-10-06 | 85.0M contracts · $34.9M premium (98% candle-priced) | 541k contracts · $217k premium (candle-priced part) | — | 0 contracts |
| Série C | Polymarket | 66 (66 / 0) | 2026-07-25→2026-09-27 | 1.5M vol (match-winner 767k, side 755k) | 23k vol | 14k | 2 events, all still open |
| Série C | Kalshi | 93 (89 / 4) | 2026-06-30→2026-10-03 | 17.3M contracts · $7.5M premium (97% candle-priced) | 194k contracts · $82k premium (candle-priced part) | — | 0 contracts |
| Copa do Brasil | Polymarket | 56 (56 / 0) | 2026-04-21→2026-09-03 | 12.2M vol (match-winner 6.7M, side 5.5M) | 217k vol | 113k | none |
| Copa do Brasil | Kalshi | 51 (51 / 0) | 2026-04-22→2026-09-03 | 28.3M contracts · $11.1M premium (95% candle-priced) | 554k contracts · $206k premium (candle-priced part) | — | 3,709 contracts |
| Libertadores | Polymarket | 163 (163 / 0) | 2025-09-16→2026-09-17 | 40.5M vol (match-winner 24.2M, side 16.3M) | 249k vol | 174k | 2 events, all still open |
| Libertadores | Kalshi | 114 (114 / 0) | 2026-04-08→2026-09-17 | 59.2M contracts · $22.3M premium (99% candle-priced) | 519k contracts · $194k premium (candle-priced part) | — | 14,503 contracts |
| Libertadores (Brazilian clubs only) | Polymarket | 71 (71 / 0) | 2025-09-17→2026-09-17 | 24.3M vol (match-winner 14.6M, side 9.7M) | 342k vol | 314k | none |
| Libertadores (Brazilian clubs only) | Kalshi | 52 (52 / 0) | 2026-04-08→2026-09-17 | 40.8M contracts · $15.3M premium (100% candle-priced) | 784k contracts · $293k premium (candle-priced part) | — | 14,503 contracts |
| Sudamericana | Polymarket | 165 (165 / 0) | 2025-09-16→2026-09-17 | 36.8M vol (match-winner 20.9M, side 15.9M) | 223k vol | 167k | 1 events, all still open |
| Sudamericana | Kalshi | 131 (131 / 0) | 2026-04-08→2026-09-17 | 69.2M contracts · $26.2M premium (97% candle-priced) | 528k contracts · $195k premium (candle-priced part) | — | 21 contracts |
| Sudamericana (Brazilian clubs only) | Polymarket | 73 (73 / 0) | 2025-09-16→2026-09-16 | 22.3M vol (match-winner 13.2M, side 9.1M) | 306k vol | 219k | none |
| Sudamericana (Brazilian clubs only) | Kalshi | 64 (64 / 0) | 2026-04-08→2026-09-16 | 41.7M contracts · $16.0M premium (98% candle-priced) | 652k contracts · $243k premium (candle-priced part) | — | 21 contracts |
| Campeonato Mineiro / Paulista / Carioca / Gaúcho | Both | 0 | — | — | — | — | Polymarket has a `brcm` (Mineiro) series with 0 events. Search hits for "Paulista"/"Mineiro" are club names (Corinthians Paulista, CA Mineiro), and "Carioca"/"Gaúcho" hits are unrelated. Kalshi has no series |

**Market-type mix (share of volume).** Polymarket Série A: moneyline dominates, then totals (O/U 2.5), exact score, spreads and BTTS. Kalshi Série A by contracts:
match winner 75%; totals 14%; spread 3%; 1st-half totals 2%; 1st-half result 1%; BTTS 1%; correct score 1%; team totals 0%.

### Top 5 settled matches by volume

**Série A**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-07-29 SC Internacional vs. CR Flamengo — 1.6M | 2026-07-26 Flamengo vs Sao Paulo — $1.3M · 3.2M c |
| 2 | 2026-07-16 Botafogo FR vs. Santos FC — 1.4M | 2026-07-29 Vitoria vs Palmeiras — $1.3M · 2.6M c |
| 3 | 2026-07-29 EC Vitória vs. SE Palmeiras — 1.4M | 2026-07-26 Palmeiras vs Atletico Mineiro — $1.2M · 3.0M c |
| 4 | 2026-02-12 Fluminense FC vs. Botafogo FR — 1.2M | 2026-07-29 Internacional vs Flamengo — $1.0M · 2.8M c |
| 5 | 2026-05-31 Red Bull Bragantino vs. SC Internacional — 1.2M | 2026-09-16 Botafogo vs Gremio — $928k · 1.9M c |

**Série B**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-07-28 AA Ponte Preta vs. Athletic Club — 910k | 2026-07-23 Botafogo vs Juventude RS — $1.1M · 2.2M c |
| 2 | 2026-07-28 EC Juventude vs. Avaí FC — 566k | 2026-09-21 Criciuma vs Ferroviario — $965k · 2.3M c |
| 3 | 2026-07-13 América FC vs. Londrina EC — 556k | 2026-07-12 CR Brasil vs Goias — $793k · 1.6M c |
| 4 | 2026-07-27 AC Goianiense vs. Operário Ferroviário EC — 543k | 2026-09-10 Vila Nova vs Goias — $701k · 1.6M c |
| 5 | 2026-08-25 EC Juventude vs. CR Brasil — 438k | 2026-07-13 America FC vs Londrina — $652k · 1.5M c |

**Série C**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-08-29 AO Itabaiana SE vs. Botafogo FC PB — 121k | 2026-09-07 Paysandu vs Brusque — $447k · 959k c |
| 2 | 2026-08-10 Anapolis FC GO vs. Guarani FC SP — 120k | 2026-07-27 Guarani vs Internacional — $429k · 1.2M c |
| 3 | 2026-08-10 Paysandu SC PA vs. AD Confianca SE — 117k | 2026-08-10 Paysandu vs Confianca — $323k · 819k c |
| 4 | 2026-08-17 Guarani FC SP vs. Ypiranga FC RS — 84k | 2026-08-10 Anapolis vs Guarani — $265k · 655k c |
| 5 | 2026-07-27 Guarani FC SP vs. AA Internacional Limeira SP — 84k | 2026-07-13 Itabaiana vs Brusque — $257k · 635k c |

**Copa do Brasil**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-08-26 CR Vasco da Gama vs. EC Vitória — 825k | 2026-09-01 Atletico Mineiro vs Cruzeiro — $792k · 1.7M c |
| 2 | 2026-08-04 Clube do Remo vs. Santos FC — 668k | 2026-08-25 Cruzeiro vs Atletico Mineiro — $562k · 1.6M c |
| 3 | 2026-08-26 SE Palmeiras vs. Santos FC — 630k | 2026-08-26 Palmeiras vs Santos — $537k · 1.4M c |
| 4 | 2026-08-05 Cruzeiro EC vs. Associação Chapecoense de Futebol — 567k | 2026-09-03 Gremio vs Internacional — $487k · 922k c |
| 5 | 2026-08-05 Grêmio FBPA vs. Mirassol FC — 563k | 2026-08-27 Internacional vs Gremio — $479k · 1.5M c |

**Libertadores**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-08-12 SE Palmeiras vs. Club Cerro Porteño — 1.5M | 2026-09-16 LDU Quito vs Palmeiras — $1.2M · 2.6M c |
| 2 | 2026-08-19 Club Cerro Porteño vs. SE Palmeiras — 1.1M | 2026-09-17 Flamengo vs Ind. del Valle — $1.1M · 3.0M c |
| 3 | 2026-08-12 Cruzeiro EC vs. CR Flamengo — 870k | 2026-09-10 Ind. del Valle vs Flamengo — $961k · 2.5M c |
| 4 | 2026-04-28 CA Lanús vs. LDU de Quito — 770k | 2026-09-16 Corinthians vs Estudiantes La Plata — $852k · 1.9M c |
| 5 | 2026-09-17 CR Flamengo vs. Independiente del Valle — 745k | 2026-08-18 Rivadavia vs Fluminense — $826k · 1.8M c |

**Sudamericana**

| # | Polymarket (vol incl. side events) | Kalshi (premium $ · contracts, all series) |
|---|---|---|
| 1 | 2026-08-13 Santos FC vs. CSyD Macará — 1.1M | 2026-09-16 Atletico Mineiro vs Santos — $1.2M · 2.6M c |
| 2 | 2026-08-11 CA Boca Juniors vs. Recoleta FC — 1.1M | 2026-09-08 Boca Juniors vs Sao Paulo — $1.0M · 2.6M c |
| 3 | 2026-07-23 Club Bolívar vs. Grêmio FBPA — 822k | 2026-08-13 Santos vs Macara — $981k · 2.7M c |
| 4 | 2026-04-28 CA San Lorenzo de Almagro vs. Santos FC — 790k | 2026-09-15 Sao Paulo vs Boca Juniors — $854k · 2.0M c |
| 5 | 2026-08-26 CA River Plate vs. Independiente Santa Fe — 789k | 2026-07-23 Boca Juniors vs O´Higgins — $853k · 2.2M c |

### The calendar's other competitions (checked 29 Sep 2026)

| Competition | Polymarket | Kalshi |
|---|---|---|
| Supercopa do Brasil (Flamengo v Corinthians, 1 Feb 2026) | **Never listed.** Public search returns only Spain's Supercopa | **Never listed.** No series; no event on that date |
| Recopa Sudamericana (Lanús v Flamengo, 20 and 27 Feb 2026) | **Never listed** | **Never listed.** No series |
| FIFA Intercontinental Cup | **Once:** the Dec 2025 final PSG v Flamengo. 90-minute result 268k vol + winner 53k vol. The Derby of the Americas (v Cruz Azul) and Challenger Cup (v Pyramids) not found | **Once:** the same final. `KXINTERCONCUPGAME` 3 markets, 372k contracts; `KXINTERCUPADVANCE` 2 markets, 58k contracts. The 2026 edition is not listed yet |

### Jiu-jitsu / grappling (checked 29 Sep 2026)

- **Kalshi: never listed.** The full series list (14,468 series) has nothing matching jiu-jitsu, BJJ, IBJJF, ADCC or grappling.
- **Polymarket: IBJJF never listed**, and neither are ADCC, the Craig Jones Invitational or the CBJJ Brasileiro. Public search found only two "Grappling:" events, both Hype Fighting Championship matches with UFC fighter Arman Tsarukyan:
  - v Shara Magomedov, Armenia, 30 Dec 2025: 247,624 vol.
  - v Muhammad Mokaev, Farmasi Arena, Rio de Janeiro, 11 Mar 2026: listed, **0 volume**. Not checked whether the match took place.
- **Popularity: no survey figure found.** IBOPE Repucom releases, Datafolha and the Opinion Box survey don't measure jiu-jitsu. The nearest proxy is MMA: 30M fans (IBOPE Repucom, 2019); UFC followed by 29% (Opinion Box 2024).

## Caveats

- **The units differ, as the note at the top explains.** Polymarket vol is $1-notional shares. Kalshi contracts are the same unit, but inflated by losers dumped at $0.001. Kalshi premium $ is what was actually paid. Neither pairing is clean, so this doc never adds the two venues together.
- **Some Kalshi premium $ is extrapolated.** Daily candles price 96% of Brazil-football contracts; the rest (historical-tier markets not yet pulled when this was written) are priced at their market type's average covered price. The candle pull runs in descending volume order, so the uncovered markets are the small ones. The estimate can still drift if small markets trade at different prices.
- **Kalshi has a new historical-data trap.** `/markets?series_ticker=X` only serves markets settled after the moving `/historical/cutoff` (`market_settled_ts` = 2026-07-31 on 29 Sep 2026). Anything older sits only at `/historical/markets`, and its candles at `/historical/markets/{ticker}/candlesticks` (one market per call; the batch endpoint returns nothing for these). Without it, KXNBAGAME shows 6 markets and Brazilian football appears to start in July 2026.
- **The two venues' sport-level totals aren't comparable.** Kalshi's are match-winner series only (no props or futures series pulled). Polymarket's sport totals are `/sports` series events and include props nested in each event. Most Polymarket `/sports` series (and the Brazilian-football tags) only reach back to Sep/Oct 2025; UFC and F1 go further back. The NFL series covers the 2026 season only, so the São Paulo 2025 game was found by slug.
- **Eliminated outright legs vanish on Kalshi.** Lifetime outright totals are understated (World Cup winner: only a few legs remain). Brazilian-competition outrights are tiny on both venues anyway.
- **The Brazil filters are heuristics.** Libertadores and Sudamericana "Brazilian clubs only" means a Brazilian club (from the Série A/B/C and Copa do Brasil team lists) is in the tie. UFC uses a hand-made list of ~75 Brazilian fighters, so it undercounts. Esports uses Brazilian org names (FURIA, MIBR, paiN, LOUD, Imperial, Legacy, ODDIK, Fluxo, RED Canids, Sharks, Keyd, Bounty Hunters…) and includes their academy teams.
- **The popularity sources aren't like-for-like.** Only Datafolha 2026 is a general-population poll (football only). IBOPE Repucom Sponsorlink covers online adults 18+, and its figures come from different waves (2019, Nov 2021, Jun 2022, Jun 2024). "Fans" means interested plus very interested; volleyball's 87% also counts 'a little interested'. Opinion Box (n=525, commissioned by a betting-affiliate site, sample = people who follow teams, athletes and competitions, including foreign ones) reports shares of that sample. Its publication date (Jan 2024) comes from a WebFetch reading of the page and wasn't re-confirmed in the raw HTML. The ranking below football is therefore indicative.
- **The F1 2026 São Paulo GP (8 Nov) isn't listed on either venue yet.** Only the 2024 and 2025 races have settled.
- **Sport-level Polymarket totals weren't spot-checked.** They are sums of Gamma event `volume` as returned; for example, LoL shows 2.64B vol across 3,462 events.
- **Event venues come from search snippets and the APIs, not source pages.** UFC Rio = the 11 Oct 2025 *UFC Fight Night: Oliveira vs. Gamrot* card, placed in Rio (Farmasi Arena) by the ufc.com result pages titled "UFC Rio" (search snippet only). The NFL Rio game is Ravens–Cowboys on 27 Sep 2026 at Maracanã, per a search snippet of NFL.com ("Ravens to face Cowboys in 2026 NFL Rio Game"). The APIs confirm a BAL–DAL game on that date. The NFL São Paulo game (Chiefs–Chargers, 5 Sep 2025) was identified from general knowledge plus the API fixture, not re-verified on a source page.
- **Tennis tournament matching.** Polymarket titles name the tournament ("Rio Open: …"), but Kalshi titles don't. Kalshi Rio Open matches were found by matching both surnames within ±3 days of the Polymarket fixture, so Kalshi figures for Brazilian tournaments are a floor, and are given in contracts only.

## Files (local only — `research/` is not in the repo)

- `research/sports_markets/pm_pull.py`, `pm_tags.py` and `pm_search.py` pull Polymarket (keyset paging by series and tag, plus public-search).
- `research/sports_markets/kalshi_pull.py` runs `markets`, `hist`, `candles` and `hcandles` against Kalshi (live and historical tiers, daily candles).
- `research/sports_markets/analyze.py` writes `out/summary.json`, and `build_doc.py` writes this doc.
- `research/sports_markets/raw/` holds every raw pull. `web/` holds the survey pages as fetched.
