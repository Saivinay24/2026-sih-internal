# SIH 2026 — fresh shortlist from the official SIH26xxx bank (revision 5 candidate)

**Date:** 2026-08-29
**Status:** proposal. Does NOT overwrite `DECISION.md` (rev 3, Chladni/SH11). rev 3 is void anyway: it came from the old master PS bank the faculty told us not to use.
**Source of truth:** the three portal exports in `~/Downloads` (`Smart India Hackathon.pdf`, `Smart India2.pdf`, `sih 3.pdf`), parsed to 229 unique statements = 54 Hardware + 175 Software. Matches the portal's own counters, so the list is complete.
**Known gap, stated up front:** the exports carry title + org + theme + category only. Full PS descriptions and "Expected Solution" text live on the portal detail pages and have NOT been read yet. Every pick below must be re-read against its full description before it is locked.

---

## Part 1 — the context, with me deliberately left out

### The rounds this has to survive, and what each one actually scores

| Round | Format | What is really being scored |
|---|---|---|
| College internal (MIT Bengaluru, ~5 Sep) | live PoC + PPT, faculty/IIC panel | "Do we trust this team to represent us." Working PoC, not slides. Organiser's own words: *"makes people ask, why didn't we have this before?"* |
| Idea submission (portal, deadline 20 Sep 2026) | PPT only, no demo, up to 500 ideas per PS | Novelty, complexity, clarity, feasibility, impact. **Read off a document by someone who has never met you.** |
| Grand Finale | 36-hour build, judged by the sponsoring organisation | The org's own engineers asking "could we deploy this." Domain depth, honesty of numbers, deployment path. |

Three consequences that drive everything below.

1. **The finale judge is the sponsor, not a generalist.** ISRO's PS is judged by ISRO. MRPL's is judged by refinery digital engineers. This is the single most exploitable fact in SIH: pick a PS whose sponsor has a real, specific, unglamorous pain, and depth gets rewarded instead of being invisible.
2. **The idea round is won on paper, by a stranger.** Anything whose value needs a live demo to land loses marks here. The pick must read as novel and complex *in a PPT*.
3. **Crowd density is the hidden filter.** 500 ideas per PS is the cap. ISRO, MoD, MHA and the 17 AICTE "Student Innovation" open statements (SIH26193 to SIH26209) will cap out. Obscure sponsors (MRPL, Oil India, MoSPI, Ministry of Cooperation, Egreen Quanta, NTRO) will not. Same effort, an order of magnitude better odds.

### What has actually won SIH, historically

Looking at recent grand-finale winners (NALCO wire-rod property optimisation by IIIT Bhopal, the Telegram/WhatsApp drug-trafficking detection build, the solar tracking team that paired MATLAB simulation with a working hardware prototype, real-time analytics on a government PS): the pattern is not "most impressive AI." It is:

- **A narrow, real, boring-sounding operational pain of the sponsoring body**, not a broad societal theme.
- **A working end-to-end system**, including the ugly parts (ingestion, integration with what the org already runs), not a model in a notebook.
- **Honest, checkable numbers against a baseline the sponsor already uses.**
- **A visible deployment path.** Winners answer "what happens Monday."

What consistently loses: dashboards, "AI-powered portals," another RAG chatbot, crop disease on camera, waste segregation, irrigation, air quality, generic ANPR. Those are the saturated clusters.

### The filter applied to all 174 software statements

1. **Sponsor-depth test.** Is the finale judge a domain expert with this exact pain? (Favours MRPL, Oil India, NTRO, MoSPI, MoD, Legal Metrology. Penalises AICTE open statements, where the judge is a generalist and the crowd is enormous.)
2. **Paper test.** Does it read as novel and technically complex in a PPT, with no demo?
3. **Crowd discount.** Struck before merit regardless of quality: all 17 AICTE Student Innovation statements, WeatherGPT (SIH26068), crop disease and onion grading (SIH26031, SIH26131), waste and sanitation, generic ANPR (SIH26127), "AI chat with satellite images" (SIH26167, the single most attractive-looking ISRO statement in the list and therefore the most crowded).
4. **Moat test.** Is there a resource or skill barrier that most student teams physically cannot cross? (GPU compute, ability to actually run open-weight models on-prem, real systems engineering.)
5. **Awe test, unchanged from rev 3.** A visible, visceral, real-time moment a non-technical judge gets in under ten seconds with no narration. A screen printing a label does not count.
6. **7-day PoC feasibility.** The binding constraint is the internal hackathon, not 20 Sep.

---

## Part 2 — the top five, with me in the picture

Ranked. Every one of these is a system-with-a-checker shaped problem, which is the shape I actually build well.

### 1. SIH26117 — MRPL, "Sovereign On-Premise Agentic AI Workbench using Open-Weight Multimodal LLMs for Confidential Industrial Work"
*Software | Smart Automation | Mangalore Refinery and Petrochemicals Limited*

**Why it wins.** This is the closest thing in 174 statements to what I already build: decompose, ground, generate, verify, correct, assemble, with every generator getting a checker. The word "sovereign" is doing enormous work here. It means no API calls. Any team that wraps GPT or Gemini fails the problem statement on its face, and most of the room will do exactly that because they have never run a multimodal open-weight model themselves. I have rented A100/H100 capacity and have actually done this.

**The moat.** Running Qwen2.5-VL or similar locally on refinery documents (P&IDs, SOPs, incident reports, MSDS sheets, handwritten shift logs) with citation-grounded outputs and a refusal path when grounding fails. The hard, unglamorous, winning part is the verifier layer: every answer carries provenance to a page and a bounding box, and the system says "I cannot ground this" instead of guessing. That is exactly the discipline I already enforce in the memory vault, ported to a refinery.

**The awe beat.** Pull the ethernet cable and turn off wifi on stage, in full view. Hand a judge a confidential-looking engineering drawing. It still reads it, answers about it, and cites the exact region of the page it read the answer from. Under ten seconds, no narration, and for a PSU judge it is not a trick, it is the entire reason the PS exists.

**Risks, honestly.** "Workbench" is vague, so the PPT has to define a sharp scope for us or the idea round reads it as unfocused. Model quality on Indian industrial documents (rotated, scanned, handwritten) is a real unknown and must be measured, not claimed. 16GB M4 will not run this; the demo depends on the rented GPU box or a quantised model, and that dependency must be tested before the internal round, not on the day.

---

### 2. SIH26158 — NTRO, "Single-Pass Drone Video to Accurate 3D Model Generation System"
*Software | Robotics and Drones | National Technical Research Organisation*

**Why it wins.** Highest awe-per-rupee in the entire list, and I have already worked in this exact area (`quantum-inrs-nerfs`, `barf-4d`). Play a short video, and a navigable 3D model of the building assembles itself on screen while the judges watch. Then a judge flies through it. There is nothing to explain.

**Where the real engineering is, and it is not the splatting.** "Single-pass" is the whole problem. Standard photogrammetry and standard 3D Gaussian Splatting want overlapping multi-pass coverage. One pass means sparse views, weak parallax, and unobserved geometry, so the contribution is sparse-view reconstruction plus an honest **confidence surface**: the model must colour which parts of the mesh are actually observed versus hallucinated. That coverage-and-confidence layer is the checker, it is ours, and it is what turns a party trick into an instrument NTRO could use.

**The moat.** Compute. Most teams do not have a GPU that can train a splat in minutes. I do.

**Risks, honestly.** No drone is needed for the software (a phone walked around a building produces the same input), but a real drone clip presents much better and that should be sourced or shot early. Accuracy claims need a measured baseline (compare against a COLMAP multi-pass reconstruction and report error in metres, not adjectives). Category is tagged Robotics and Drones, so read the full PS text to confirm they are not expecting an actual airframe.

---

### 3. SIH26228 — MoD, "Trustworthy Computer Vision Integrity Assurance for Data, Models and Inference Outputs in Multi-Contributor Pipelines"
*Software | Blockchain & Cybersecurity | Ministry of Defence*

**Why it wins.** This is provenance engineering, which is the thing I care about most and the thing almost no undergraduate team has even heard of. Multi-contributor CV pipelines have a supply-chain problem: who supplied which images, was the training set poisoned, is this model the one that was signed off, is this inference output the real one. Novelty and complexity marks in the idea round are close to free here, because the problem itself sounds unfamiliar and serious.

**The awe beat.** Poison half a percent of a training set on stage. Show that the resulting model looks perfectly healthy on every normal metric, then show it obeying the backdoor trigger. Then run our integrity layer and watch it name the contributor who supplied the poisoned batch. A judge does not need to understand anything to feel that.

**The moat.** It is intimidating and abstract, which is precisely why the room will avoid it. MoD sponsorship means the finale judges are exactly the people who will recognise the depth.

**Risks, honestly.** Lowest immediate visual polish of the five, so the PPT has to carry more weight. There is a real temptation to solve it with "blockchain" as decoration; the answer must be signed manifests, content-addressed datasets and reproducible builds, with the ledger only where it genuinely earns its place. Poison-attribution accuracy has to be a pre-registered number.

---

### 4. SIH26034 — Ministry of Consumer Affairs, "Software System to check compliance of Packaged Commodities under Legal Metrology (Packaged Commodities) Rules, 2011 by scanning products, images and labels"
*Software | Miscellaneous | Ministry of Consumer Affairs, Food & Public Distribution*

**Why it is the sleeper of the whole list.** Nobody will pick it because the title is dull, the ministry is unglamorous and the theme is "Miscellaneous". That is the opportunity. It has the strongest "why didn't this exist before" reaction per unit of effort of anything in 174 statements, because enforcement of these rules in India is genuinely done by hand today.

**The awe beat.** Ask a judge for whatever is in their bag. Point a phone at it. The system instantly flags "net quantity declaration below the prescribed font height, MRP not in the prescribed format, country of origin missing," each verdict citing the specific sub-rule. Their own object, their own eyes, under five seconds. This is the single most demo-durable pick in the list: it works identically in a classroom, on a portal PPT with a photo sequence, and in a 36-hour finale.

**Where the complexity has to come from, or this loses.** OCR plus if-statements is a C-grade project. The defensible core is a **formal, machine-readable encoding of the Rules themselves** as a versioned rule set that produces citation-grounded verdicts, plus the genuinely hard vision work: curved and reflective packaging, multilingual labels, measuring declared font height in millimetres from an image with no reference scale. That last one alone is a real computer vision problem and it is what the rules actually require.

**Risks, honestly.** The complexity marks are the exposure. If the PPT does not lead with the rules-as-code layer and the metric font-height measurement, an idea-round reviewer files it as a barcode scanner app and moves on.

---

### 5. SIH26102 — MoSPI, "AI-powered system to detect anomalies, fraud, and inefficiencies in MPLAD Scheme implementation"
*Software | Smart Automation | Ministry of Statistics and Programme Implementation*

**Why it wins.** MPLADS data is publicly published. That means the idea-round PPT can contain a slide no competing team can produce: **findings from the real data**, not a mock-up. "We ran this on the actual published MPLADS records and here are the anomalous vendor clusters we surfaced" ends the argument about feasibility before it starts. I already have the graph-based financial anomaly work (`smurfing-hunter`) to build from, so the head start is real.

**The technique.** Entity resolution across messy government records, then graph analytics for the patterns that matter: the same vendor under slightly different names across constituencies, works split just under approval thresholds, implausible cost-per-unit outliers, temporal bunching before deadlines. Structured, checkable, and it produces a ranked case file for a human investigator rather than a verdict, which is both more honest and more deployable.

**Risks, honestly.** Awe is the weakest of the five, since findings arrive as a ranked list. The compensating move is that the findings are real, and real findings on real public money is its own kind of moment. Also: anything flagged is an allegation about identifiable people, so the output must be framed as "requires review" throughout, in the PPT as well as the UI. Data quality in the published records may be worse than expected and that has to be checked in the first two days, not assumed.

---

## Alternates, ranked, with the honest reason each is not in the five

| PS | What it is | Why not top five |
|---|---|---|
| **SIH26119** | MRPL, indigenous GPU-accelerated optimisation solver, sovereign alternative to CPLEX/Xpress | Highest ceiling in the entire list and the most defensible thing I could possibly build (benchmark against CPLEX on public instances, publish the honest numbers). Cut only on 7-day risk. A realistic scope is a GPU first-order LP solver, not a competitive MIP solver, and that scoping conversation has to happen before it is picked, not after. Revisit if the internal round timeline moves. |
| **SIH26142** | NTRO, deep-learning super resolution mapping from medium-resolution satellite imagery | Excellent awe (a slider, blurry to sharp, on real Indian imagery) and squarely in my generative work. Held back because super resolution invites the hallucination objection, and answering it properly costs build days. |
| **SIH26104** | AICTE, real-time voice cloning impersonation detection | The awe beat is outstanding, cloning a consenting judge's voice live and catching it. Demoted purely on sponsor and crowd: AICTE means a generalist judge and a very large field, and voice deepfakes are the most fashionable pick in the list. |
| **SIH26227** | MoD, semantic retrieval and multi-temporal change analysis of satellite imagery | Strong and well matched. Slightly behind SIH26228 on novelty because "search satellite images with text" is close to the crowded ISRO cluster. |
| **SIH26166** | ISRO, sun-angle and scale invariant multi-modal correspondence on Chandrayaan-2 imagery | The genuine research problem in the list, and Chandrayaan data is public. Cut on crowd (ISRO) and on 7-day risk, not on merit. Wildcard if the goal shifts from winning to publishing. |

---

## What I would actually do

Lock **SIH26117 (MRPL agentic workbench)** as the primary and **SIH26158 (single-pass drone to 3D)** as the alternate, then run a 2-hour gate on each before committing:

- **26117 gate:** get a quantised open-weight VLM answering questions about a scanned, rotated Indian engineering document, fully offline, with a page-region citation. If grounding is garbage on real scans, fall to 26158.
- **26158 gate:** shoot one single-pass phone walkaround of a building, train a splat, and check whether an unobserved face of the building is visibly hallucinated. If the confidence surface is not separable, fall to 26034, which has the lowest technical risk of the five.

Same rule as rev 3: the pick rests on one testable claim, and the claim gets tested before the pick is locked.

## Open items before anything is locked
- [ ] Read the full portal description and Expected Solution for 26117, 26158, 26228, 26034, 26102. The exports only carry titles.
- [ ] Confirm the current MIT internal hackathon date and the registration deadline (rev 3 had 29 Aug 11:45 PM registration, 5 Sep internal). Portal idea-submission deadline reads 20 September 2026.
- [ ] Confirm team of 6 with at least 1 girl student and a faculty mentor, unchanged.
- [ ] Check how many other MIT Bengaluru teams are converging on the same PS, since same-PS collisions inside one college cost nothing but goodwill and everything in odds.
