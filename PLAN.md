# PLAN: SIH 2026 Internal Hackathon, PS-SH11 (Chladni)

**Decision:** see `DECISION.md` (revision 3). PS-SH11, Smart Infrastructure Monitoring, built as camera-plus-accelerometer structural health monitoring with live phase-based motion magnification. Build name **Chladni**. See the vibration, find the crack.
**Research trail:** `research/hardware_ps_research.md`.
**Written:** 2026-08-25 (supersedes the PS-SH02 / Kirchhoff plan, which is retained in `DECISION.md` as Alternate 1 and as the 26 Aug revert target)
**Registration hard stop:** 29 Aug 2026, 11:45 PM IST.
**Demo day:** 5 Sep 2026.
**Calendar reality:** 11 calendar days. Surprise tests and placement activity are running (the IIC said so in writing when they extended). Plan against roughly 6 to 7 honest build days across 6 people, not 11. One full day goes to building and characterising the physical test structure and cannot be parallelised away.

## The four parts, and nothing else

1. **The Probe**: ESP32 plus an ADXL345-class MEMS accelerometer on the test structure, streaming acceleration, producing a spectrum and identified modal frequencies. The contact instrument and the numeric ground truth.
2. **The Witness**: our own Riesz-pyramid phase-based motion magnification running live from a tripod-mounted camera, validated against `tschnz/Live-Video-Magnification` as a reference implementation.
3. **Resonance Lock**: the coupling. The Probe's identified modal frequency automatically sets the Witness's temporal passband, live, on screen. This is the part that is ours and it is the defensible core.
4. **Damage Ledger**: baseline modal frequencies and full-field mode shape recorded, damage introduced, both instruments re-measured, and the shift reported by each independently with their disagreement stated. Every entry carries which instrument measured it, when, and how far the two differed.

If a task does not serve one of those four, it is not in scope before 5 Sep. It goes to `GAPS.md`.

## Three things that make this plan different from a software plan

**One: the pick is gated on a two-hour test that runs before registration.** Phase 0 contains a smoke test on 26 Aug that either confirms live magnification visibly works or sends us to Kirchhoff. Nothing else starts until that answer exists. This is not caution, it is the "verify claimed state against reality before building on it" rule applied to a decision instead of to code.

**Two: the physical structure is the schedule risk, not the electronics.** The boundary conditions must not wander between the baseline run and the damaged run or the entire before-and-after collapses. Clamping, marking and photographing the setup is real engineering work with a real failure mode, and it gets its own day.

**Three: two damage modes are built, deliberately.** Added mass is predictable, reversible and guaranteed to produce a measurable shift. Bolt loosening is the realistic and more impressive one but the shift can hide inside the noise on a small frame. Both are built, the choice is made on 31 Aug on measured evidence, and it is not revisited on 4 Sep.

## Standing rules for every phase

- Commit at every milestone, named. Never any AI attribution in a commit message.
- `PROGRESS.md` updated at the end of every phase so any session or teammate can resume cold.
- Numbers are measured, never estimated, and the same number appears in every artifact.
- Every capture is saved. Raw accelerometer traces and raw video are never overwritten, never regenerated in place, and every capture session gets a run ID plus a photo of the physical setup.
- **Once the baseline is recorded, nobody moves the structure or the tripod.** If either moves, the baseline is void and gets re-recorded. Say so out loud, do not quietly reuse it.
- **We never pre-record a magnified clip and present it as live.** Under any schedule pressure, at any point. That single dishonesty would be worse than losing.
- We state openly which parts of the magnification pipeline are ours and which come from the reference implementation.
- Secrets to `.env` on arrival, secrets grep before any push.
- No em dashes in anything a judge will read.

---

## Phase 0: Smoke test, lock, order, register
**Window:** 25 Aug to 28 Aug (registration finished by the 28th evening, never the 29th)
**Owner:** Vinay

**Done state**
- **The 26 Aug smoke test is run and the answer is written down.** Two hours. Laptop webcam on a tripod, a steel ruler clamped to a desk and flicked. Run `tschnz/Live-Video-Magnification` or a fifty-line numpy prototype. The pass condition is deliberately blunt: **the amplified motion must be visibly obvious, live, to a teammate who was not told what to look for.** If it is not, revert to Kirchhoff and register PS-SH02. `DECISION.md` Alternate 1 has the full spec so the reversion costs nothing.
- **Parts ordered on 26 Aug**, before the crowding check completes and before the PS is locked. 3x ESP32, 2x accelerometer breakout, flat bar and angle stock and fasteners, heavy C-clamps, work lamp, tripod if nobody owns one. Under 4,000 INR total. The ESP32s are useful under all three candidates, so ordering early is free insurance.
- Crowding check run by 27 Aug and the answer written down. Nobody is expected on SH11; ask anyway. If another MIT team is genuinely doing camera-based vibration measurement, switch to Kirchhoff.
- Team of 6 confirmed, minimum 1 girl student, all MIT Bengaluru, roles assigned per the split at the bottom of this file.
- Faculty mentor confirmed. Preference is Mechanical or Civil, someone who has run a modal analysis lab, can sanity-check our frequencies and may have a proper clamp or a small shaker.
- Registration submitted at https://tinyurl.com/MIT-SIH2026 with PS-SH11, before 28 Aug end of day.
- Repo initialised, `PROGRESS.md` and `GAPS.md` created, first commit.

**Negative scope**
- NO building anything before the smoke test answers. The entire pick rests on it.
- NO waiting for the crowding check before ordering parts.
- NO writing our own Riesz implementation yet. The smoke test may use the reference app entirely; that is what it is for.
- NO registering on the final evening.
- NO buying anything not on the bill of materials in `DECISION.md`. Scope creep starts at the hardware store.

---

## Phase 1A (structure track): the test article
**Window:** 28 Aug, with 29 Aug as slack
**Owner:** structure and hardware pair
**Runs in parallel with Phase 1B. Neither blocks the other.**

**Done state**
- Cantilever flat bar clamped to a rigid base, plus a small two-bay bolted frame, both built.
- Every clamp position marked and the whole setup photographed from three angles, so it can be rebuilt exactly if something is knocked.
- Accelerometer mounted, ESP32 streaming, and a spectrum visible.
- **Repeatable baseline: five runs, and the identified modal frequencies agree run to run within a spread we write down.** This is the hard gate. If the baseline wanders, the boundary conditions are loose. **Fix the clamping. Do not start filtering.**
- Measured accelerometer noise floor on our own board, recorded in `PROGRESS.md`. The datasheet number is not our number.
- Both damage modes physically prepared: a known small mass with a repeatable mounting point, and a designated bolt with a marked torque reference.
- Milestone commit: `structure-baseline`.

**Negative scope**
- NO software fixes for a mechanical problem. A wandering baseline is a clamping problem every time.
- NO moving the structure after the baseline is recorded.
- NO shaker, NO instrumented hammer, NO lab equipment we do not own. A finger flick and a small pendulum tap are the excitation.
- NO second structure. One cantilever and one frame is the whole test article.
- NO more than one day here. If the baseline is not repeatable by end of 29 Aug, simplify to the cantilever alone and drop the frame.

---

## Phase 1B (vision track): the Witness
**Window:** 28 Aug to 30 Aug
**Owner:** Vinay plus the CV pair
**Runs in parallel with Phase 1A.**

**Done state**
- Our own Riesz-pyramid phase-based magnification implemented in Python with OpenCV and numpy, following Wadhwa et al. 2014, with the Riesz transform approximated by two three-tap finite difference filters.
- **Validated against `tschnz/Live-Video-Magnification` on the same input clip.** Same amplification band, comparable visible output. Where ours differs, we record how and why.
- Live path running from a tripod-mounted camera, with **measured framerate at each processing resolution** (1/1, 1/2, 1/4, 1/8) on the actual demo machine. We pick the highest that holds a usable live rate and publish the measured number.
- Temporal filter lag measured and written into the demo script, so nobody panics on stage and taps twice.
- Colour mode working for the pulse opener. It is a mode switch, not a build.
- Milestone commit: `witness-live`.

**Negative scope**
- NO handheld capture, ever. Phase-based methods assume stabilised capture and hand shake at 2 to 10 Hz sits inside the passband. Tripod or nothing.
- NO GPU rewrite, NO CUDA, NO Rust port. Drop processing resolution instead. Optimising here is a time sink with a cheap alternative.
- NO neural motion magnification, NO event cameras, NO 3D methods. All future scope.
- NO claiming we invented motion magnification. Lineage is stated on the slide.
- NO UI polish in this phase.

---

## Phase 2: Resonance Lock and the Damage Ledger
**Window:** 30 Aug to 2 Sep
**Owner:** Vinay, both pairs supporting captures

**Done state**
- **Resonance Lock working:** the Probe's identified peak modal frequency automatically sets the Witness's temporal passband, live, visible on screen as it retunes. Change the structure and watch the band follow.
- **Two-instrument agreement measured:** camera-derived versus accelerometer-derived natural frequencies for the first two or three modes, reported as absolute Hz and percent difference, per mode. This is the headline number.
- Full-field mode shape extracted from the magnified video, which is the thing a single-point accelerometer physically cannot give and the reason the camera is not decoration.
- **Damage runs done for both modes**, added mass and bolt loosening, baseline versus damaged, both instruments, at least five repeats each, with the run-to-run spread recorded.
- Damage Ledger storing every measurement with its instrument, timestamp, run ID, setup photo, and the cross-instrument disagreement.
- Milestone commit: `resonance-lock`.

**Negative scope**
- NO tuning the two instruments until they agree. A cross-check we tuned to agree is not a cross-check. If they disagree, that is the finding and it gets reported with an explanation.
- NO discarding a run because it looked bad. Every run stays in the ledger.
- NO deep learning anywhere in this phase. The damage indicator is a measured frequency shift with a stated noise spread. Adding a model here would weaken the claim, not strengthen it.
- NO third damage mode.
- NO frontend polish yet.

---

## Phase 3: The demo surface
**Window:** 2 Sep to 3 Sep
**Owner:** frontend pair, design input from the whole team

**Done state**
- One screen, laid out for a room watching from a distance: live magnified video large and central, the Probe spectrum with the locked passband marked, and the Damage Ledger's baseline-versus-current comparison.
- **The bolt moment is a built, deliberate feature:** when damage is introduced, the surface visibly calls out the shift from both instruments side by side, with their agreement stated. It must not require the presenter to explain what changed.
- Pulse opener wired to a one-key mode switch so the camera can be swung at a judge's hand and back in three seconds without fumbling.
- Measurement protocol frozen. No edits after this point.
- Milestone commit: `demo-surface`.

**Negative scope**
- NO mobile app, NO cloud, NO multi-camera, NO alerting to a municipality. All parked in `GAPS.md`.
- NO emoji in the product UI. SVG icons only.
- NO new measurement features. The pipeline froze at the end of Phase 2 except for bug fixes.
- NO redesigning the layout after the fallback video is recorded in Phase 5.

---

## Phase 4: Measure, honestly
**Window:** 3 Sep to 4 Sep morning
**Owner:** Vinay

**Done state**
- Full scored run on the frozen protocol: per-mode cross-instrument frequency agreement in Hz and percent; measured damage shift for both damage modes from both instruments with run-to-run spread; measured live framerate and processing resolution on the demo machine; measured accelerometer noise floor; actual bill of materials with receipts.
- **The scale limitation written down and put on a slide:** this is a lab-scale structure with amplitudes far larger than a real bridge, and low-cost MEMS noise floors are not adequate for real civil structures without better sensors. We say it before a judge finds it, and it becomes the future-scope slide instead of a hole.
- If the bolt shift sits inside the noise spread, added mass is the demo damage mode and the reason is stated.
- One numbers file becomes the single source of truth. Nothing quotes a number from anywhere else.
- Milestone commit: `measured-v1`.

**Negative scope**
- NO editing the protocol after seeing a result.
- NO rerunning until a number looks better. One pre-registered protocol, one reported result.
- NO rounding up, NO "approximately", NO number on any slide that does not exist in the numbers file.
- NO quoting the camera-measures-microns figure from the literature as if it were our own measurement. It is theirs, cited as theirs.
- NO new features. Anything broken today gets a one-line fix or gets cut from the demo script.

---

## Phase 5: PPT, demo script, rehearsal
**Window:** 4 Sep
**Owner:** whole team

**Done state**
- PPT complete against the required sections: problem statement and understanding, existing challenges, proposed solution, innovation and uniqueness, system architecture and workflow, technology stack, PoC, expected impact and benefits, future scope. Resonance Lock is the innovation slide and lineage is stated honestly on the tech-stack slide.
- Demo script written beat by beat with timings, matching `DECISION.md`: pulse on a judge's hand, swing to the motionless structure now swaying on screen, hand it to a judge to tap, show Resonance Lock retuning, then loosen the bolt and watch both instruments agree on the shift. Under four minutes, entirely live.
- **Recorded fallback video of the full working demo**, made on 4 Sep while the rig definitely works, and **clearly labelled as a recording** if it ever has to be played. Hardware demos fail in strange rooms and this is the cheapest insurance available.
- **Physical demo kit packed and checklisted:** structure, clamps, tripod, camera, laptop, ESP32 rig, spare ESP32, spare accelerometer, spare cables, the damage mass, the marked bolt and spanner, work lamp, extension cord. A missing extension cord loses a hackathon.
- All 6 members have an assigned section and have spoken it out loud at least twice. Graded requirement, not a courtesy.
- Cross-artifact numbers sweep: PPT equals README equals on-screen equals what is said aloud. Line by line, run by someone who did not write the numbers.
- Em dash sweep and slop sweep across every outward artifact.
- Milestone commit: `submission-freeze`.

**Negative scope**
- NO code changes after the freeze except a demo-breaking crash fix, re-verified against the demo script before it lands.
- NO new numbers, NO new claims.
- NO re-clamping the structure after the fallback video is recorded. The video and the rig must be the same system.
- NO one person presenting for the group in rehearsal. Rehearse the real distribution.

---

## Phase 6: Demo day
**Window:** 5 Sep
**Owner:** whole team

**Done state**
- Arrive early enough to set up the tripod, frame the shot, set the work lamp and run one full live pass in the actual room. **Lighting and camera framing are room-dependent and this setup is not optional.** Budget thirty minutes.
- Fallback video loaded locally and ready in one click.
- Demo delivered inside the time limit, all 6 presenting.
- Q and A pre-rehearsed for the five questions this panel will certainly ask: what breaks if you delete the camera, what breaks if you delete the accelerometer, is the magnification just a visual effect (answer: Resonance Lock, and the full-field mode shape a point sensor cannot give), how do you know the two instruments are not both wrong, and does this work on a real bridge (answer: honestly, not with these sensors, and here is what it would take).
- Post-event: `PROGRESS.md` closed out with what held and what did not, and the national-SIH next steps written while it is fresh.

**Negative scope**
- NO live edits on demo day. NO re-tuning the passband by hand in the room.
- NO claiming anything the numbers file does not contain, under any question, including a friendly one.
- NO improvising a feature that does not exist in response to a judge's suggestion. Write it down as future scope and say so.
- NO playing the fallback video without saying it is a recording.

---

## Role split across the 6

Assign on 28 Aug, at the same time as registration, so nobody is idle while parts arrive.

- **Structure and probe**: procurement, building and clamping the test article, marking and photographing the setup, accelerometer mounting, ESP32 firmware, baseline repeatability, noise floor measurement.
- **Vision**: the Witness. Riesz pyramid implementation, validation against the reference app, live framerate measurement at each processing resolution, colour mode for the pulse opener.
- **Coupling**: Vinay. Resonance Lock, modal identification from both instruments, full-field mode shape extraction, the Damage Ledger and its provenance.
- **Frontend**: the demo surface, live video panel, spectrum with locked passband, baseline-versus-damaged comparison, the pulse mode switch.
- **Deck and narrative**: PPT, architecture diagrams, the Chladni framing, honest lineage statement, impact and future-scope sections.
- **Demo and QA**: the script, the fallback recording, the physical kit checklist, rehearsal discipline, the cross-artifact sweep.

Everyone presents regardless of role. The sweep in Phase 5 is run by someone who did not write the numbers.
