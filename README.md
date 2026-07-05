# 6PPD Ban & Fee — Campaign Model (WA Legislature 2027)

An interactive war-gaming tool for the 2027 Washington State 6PPD ban-and-fee campaign. Single-file HTML — no build, no dependencies, no server. Open `index.html` in a browser.

**Current version: v8** (engine v9 — correlated voting + tornado sensitivity)

## What it does

Models the bill's path from coalition alignment to regulatory rulemaking and answers three questions live, as you adjust assumptions:

1. **P(becomes law)** — six sequential stage gates (EET scheduling, committee vote, Ways & Means, Rules/calendar, Senate floor, House path), multiplied to a single-session probability.
2. **The Senate floor** — a 20,000-trial Monte Carlo whip count over 19 in-play senators, each with a heuristic base lean, confidence band, coalition pull, and opposition pressure.
3. **The landing point** — a BDM weighted-median bargaining model projecting where the bill's substance ends up (from "dies again" to "ban by 2035 + full fee").

## The engine

- **Correlated voting (new in v8).** Senators don't vote independently — budget news, caucus mood, and leadership pressure move them together. Each Monte Carlo trial draws a shared session shock through a one-factor Gaussian copula; per-senator marginal probabilities are preserved exactly. Correlation ρ is adjustable on the whip tab (default 0.35; ρ = 0 reproduces the old independent model, which was overconfident — too-narrow a vote distribution when the count sits at the 25-vote threshold).
- **Tornado sensitivity (new in v8).** The Forecast tab re-runs the engine one input at a time — each external force to its worst/best state, every gate ±15 pts, the EPC slate toggled, opposition mobilization ±25%, ρ perturbed — and ranks inputs by their swing in P(law). Read it as a ranking of where to spend effort, not a set of independent promises: real inputs correlate.
- **Stage-gate pathway.** Live gates pull from sliders; a binding-constraint readout flags the lowest gate.
- **Deployment recommendations.** Tests every untried org→senator relationship and ranks by floor-passage gain × pivot probability.

## Tabs

| Tab | Contents |
|---|---|
| Overview | Gauntlet status, top-ranked moves, current blockers |
| Path to Passage | The full 12-step legislative roadmap with live gate percentages |
| Senate | Whip count, committees, 19 senator profiles, org→senator relationship map |
| House | ENVI/Appropriations/floor-calendar gates, key member profiles |
| Players & Forces | Coalition orgs, opposition, external forces, named individuals |
| Forecast | Actor position map, bargaining landing point, tornado chart |
| Method | What's real vs. estimated, engine documentation, sources |

## Data honesty

Real: committee rosters, sponsors, 2026 procedural history (SB 6119 died without an exec session; HB 2421 cleared two committees and died at the floor calendar), testimony, retirements, litigation, and every named organization. Estimated: base leans (labeled heuristics with ±5/±12/±18-pt confidence bands), relationship depths (editable in the UI), opposition mobilization, and engine constants. Donor fields are empty pending a PDC pull.

## Usage notes

- Scenario buttons (2026 reality check / Opposition surge / Path to win) set coherent assumption bundles; any manual change switches to Custom.
- The Relationships grid is the highest-value input — map what you actually know before trusting the deployment recommendations.
- State is in-memory only; a page reload resets to defaults.

## Caveats

Internal strategy tool. Real people are named from public records; leans and relationships are labeled estimates, not facts. Stage gates are modeled as independent but correlate in reality (correlating the gates the way v8 correlated the votes is the next known improvement). Verify rosters and identities before acting. Not for external distribution.
