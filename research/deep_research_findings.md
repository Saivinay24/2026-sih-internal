# Deep research: two independent passes, reconciled

Two deep-research runs were done against the prompt in `deep_research_prompt.md`: one on Claude, one on ChatGPT. Full raw output of both is kept below for audit. This file's job is to say which claims are safe to put in front of a judge and which are not, and why.

Verified by both independently, or well-linked by at least one and not contradicted: **usable, stage-safe.**
Claimed by only one report, without a working link: **do not cite on a slide, treat as a lead to verify, not a fact.**
Directly contradicted between the two reports: **flagged below, resolved in favour of the linked, checkable version.**

---

## Resolved conflicts

### 1. "Does a commercial product already do this?"

- **Claude:** names RDI Technologies (Knoxville, TN) and their Motion Amplification Iris platform by name. States the Iris M auto-selects frequency bands (shipped feature, not a research gap) and the Iris CM fuses traditional vibration sensor inputs with video-based measurement in a continuous configuration. Could not source a price and says so explicitly rather than guessing.
- **ChatGPT:** states "No major company sells an off-the-shelf 'video SHM' box today."
- **Resolution: Claude is right, ChatGPT is wrong.** This is the single most consequential fact in either report, because it's the exact claim a judge would catch you on if you overclaimed novelty. Go verify RDI Technologies exists before final slides (a two-minute web check), but do not repeat ChatGPT's "no such product exists" line anywhere.

### 2. Citation rigor

ChatGPT's report contains dangling reference markers ("[18]", "[60]", "[67]") with no attached bibliography, and gives precision numbers with no link: 92% correlation for a "2026 study" on the Great Belt bridge hangers, 0.96 correlation for a "Zhang et al. 2025" aqueduct study. Neither could be checked. Claude's report links nearly every claim and explicitly refuses to state a number it couldn't source (RDI pricing, per-bridge Indian SHM installation cost).

**Rule for the deck: any number without a working link from either report does not go on a slide.** That kills ChatGPT's 92%, 0.96, and "129 collapses/year (2007-2017)" as citable figures. Use Claude's Newslaundry-linked 170 collapses (2021-2025) instead, and mention the gap between that count and MoRTH's own lower official figure as a finding in its own right.

### 3. The India instrumentation mandate

ChatGPT's report never surfaces this. Claude's does: **MoRTH directive, 4 March 2024**, mandating sensor installation (strain, deflection, vibration, tilt, displacement, temperature, corrosion, scour) on national-highway bridges, with DPR consultants required to specify sensor plans and cost estimates.

This is the fact that reshapes the whole pitch. Without it, "Indian bridges are uninstrumented" sounds true and is an easy, generic claim. With it, the honest and more defensible claim is narrower and better: **national highways are being addressed top-down, state and district bridges are not**, and that's exactly where the collapse concentration sits (Bihar 26, Uttarakhand 25, Himachal 17, 2021-2025) and exactly where a state framework audits 85 of 3,968 bridges. Verify the MoRTH circular independently before quoting a date on a slide, since this is load-bearing.

---

## Corroborated, safe to use

- **Not a novel method, novel packaging.** Both reports independently land here. Claude's version has the sharper citation: Cufar, Slavic & Boltezar, MSSP 213:111336 (2024), accelerometer-anchored mode-shape magnification, peer-reviewed, University of Ljubljana. Use this exact paper as the "prior art we're building past" citation. Say novelty is in the closed-loop real-time implementation on commodity hardware, not the underlying technique.
- **Environmental sensitivity is the real weak point.** Both reports converge here independently, which is a stronger signal than either alone. Specific mechanisms from Claude's pass (heat haze, Kong et al. 2024, Sensors, DOI given; atmospheric turbulence at range; Z24/I-40/Alamosa temperature-confounding results) are the ones with citations attached, use those. ChatGPT's version of the same point (lighting, wind, texture) is directionally correct but uncited, treat as confirming, not as the citation source.
- **Frame rate / Nyquist limit.** ChatGPT's addition, and it's correct and Claude's report didn't spell it out as plainly: consumer cameras cap under 100 fps, high modes above roughly half that rate alias or vanish. At whatever fps we actually sustain live, state the Nyquist limit explicitly on the numbers slide. This is free credibility.
- **Mode shape is the actual differentiator over "just use a phone."** Both reports converge on this independently: a single point sensor (accelerometer, or a phone in your pocket per the MIT smartphone-bridge paper Claude found) gives frequency only. The camera gives spatial mode shape, which is what actually localises where the damage is. This is the answer to "why not just use an accelerometer" and to "why not just use a phone."

---

## What changes in the plan because of this

1. **Pitch language locked to Claude's most defensible sentence** (now in DECISION.md): demonstrated agreement between two independent instruments plus a mode shape a single sensor can't give, on under 4,000 INR, in real time. No claim about bridges, no claim about deployment, no claim about novelty of method.
2. **Temperature confounding gets disclosed before it's asked**, per Claude's Z24/I-40 findings (this is the single scariest hole either report found, and neither ChatGPT nor a first-pass slide would have caught it). A DS18B20 temperature log alongside every modal reading is now a build item, not optional.
3. **Consumer MEMS noise floor and ESP32 sampling jitter is now a named risk**, not assumed away. Upgrade path to ADXL355 if budget allows; hardware-timer-driven sampling either way, with logged timestamps so the spectrum is provable, not asserted.
4. **RDI Technologies gets name-checked in our own deck as prior art**, the same move as citing Cufar et al., because pre-empting "this already exists as a product" is stronger than hoping nobody in the room knows it.

---

## Raw reports, kept in full for audit

- Report 1 (Claude): `raw_claude_deep_research.md`
- Report 2 (ChatGPT): `raw_chatgpt_deep_research.md` (copied verbatim from `~/Downloads/deep-research-report (3).md`, saved 2026-08-25)
