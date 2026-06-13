# 6PPD Campaign Model — WA Legislature, 2027

Probabilistic, network-aware decision-support tool for the 6PPD tire-chemical ban and fee campaign (HB 2421 / SB 6119). Built for internal strategy use.

## What it does

- **Whip count + Monte Carlo** (20,000 simulated floor votes) — P(Senate floor passage) and expected YES votes across 19 real swing senators
- **Stage-gate gauntlet** — P(becomes law) = product of Senate EET scheduling → committee vote → Ways & Means → Rules → floor → House path
- **House tab** — full House Environment & Energy Committee roster (21 members, 12D–9R), with 4-gate House path breakdown (ENVI scheduling, ENVI vote, Appropriations, floor calendar)
- **External forces** — budget crisis, alternative readiness, CA litigation, fee design — each modifying base leans, opposition pressure, and the W&M gate
- **Coalition & opposition** — real orgs (EPC, TFF, WCA, TU, AWC, tribal nations, CBOs), real opposition (USTMA, ACC, Les Schwab, WA Trucking), lobbyist firm webs
- **People tab** — named individuals with LinkedIn search links and strategic notes
- **BDM-style policy forecast** — actor position map, bargaining rounds, landing point gauge

## Data integrity rules

- Base leans are **heuristic estimates** from public signals — not facts
- Donor/employer fields say "→ PDC pull pending" until loaded from the [WA PDC SODA API](https://www.pdc.wa.gov/political-disclosure-reporting-data/browse-search-data)
- Relationship depths labeled "(est.)" — correct them and recommendations correct themselves
- No fabricated data for real people

## How to host on GitHub Pages

1. Create a new GitHub repository (can be private or public)
2. Upload `index.html` to the repo root
3. Go to **Settings → Pages → Source**: set branch to `main`, folder to `/ (root)`
4. Save — GitHub will publish the site at `https://[yourorg].github.io/[repo]`
5. Share the URL with colleagues (private repos require GitHub login to access Pages)

## Calibration (June 2026)

| Scenario | P(floor) | P(law) |
|---|---|---|
| 2026 reality (defaults) | ~55% | ~1.2% |
| Opposition surge | ~36% | ~0.3% |
| 2027 path-to-win | ~94% | ~27% |

The 2026 retrodict is correct: SB 6119 received a hearing in Senate EET (Jan 20) and never got an executive session. HB 2421 cleared ENVI and Appropriations and died at the floor calendar. The model reproduces this via the scheduling gate (45% default), not the floor vote.

## Key sources

- Senate EET roster: [leg.wa.gov](https://leg.wa.gov/about-the-legislature/committees/senate/enet/)
- House ENVI roster: [leg.wa.gov](https://leg.wa.gov/about-the-legislature/committees/house-of-representatives/envi/) (pulled June 2026)
- HB 2421 / SB 6119 history: [LegiScan](https://legiscan.com/WA/bill/HB2421/2025)
- Hearing testimony: [Puget Sound Institute](https://www.pugetsoundinstitute.org/) / TVW
- PDC lobbying registrations: [PDC SODA API](https://www.pdc.wa.gov/political-disclosure-reporting-data)

---
*Internal strategy tool. Real people named from public records. Leans and relationships are labeled estimates. Verify roster before acting. Not for external distribution.*
