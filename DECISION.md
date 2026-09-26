# DECISION: SIH 2026 Internal Hackathon, MIT Bengaluru

**Date:** 2026-08-25 (revision 3)
**Event:** Smart India Hackathon 2026, Internal Hackathon, MIT Bengaluru (IIC)
**Registration closes:** Sat 29 Aug 2026, 11:45 PM IST. Stated final, no further extension.
**Internal Hackathon (build + demo):** Fri 5 Sep 2026.
**Real build window:** 11 calendar days, roughly 6 to 7 honest build days across 6 people after coursework and surprise tests. This is a hardware build, so one full day is physically spent on parts and assembly and cannot be parallelised away.
**Hard constraints:** 6 students, minimum 1 girl student, 1 faculty mentor, all from MIT Bengaluru. All 6 must present. Working PoC expected, plus a professional PPT covering problem understanding, existing challenges, proposed solution, innovation, architecture, tech stack, PoC, impact, future scope.
**PS source:** `assets/SIH_2026_Master_PS_Bank.pdf`, 84 statements (41 Software, 22 Software + Hardware, 20 Hardware, 1 Open).
**Full research trail:** `research/hardware_ps_research.md`.

---

## Revision history, and what changed this time

- **Revision 1** picked PS-S36 (Trustworthy Agentic AI for Engineering Education). **Deprioritised on Vinay's direction:** pure software, and the visible surface reads as another AI recommendation system for student courses.
- **Revision 2** rescoped to the Software + Hardware category and picked PS-SH02 (single-point NILM, build name Kirchhoff) on feasibility, differentiation and technical rigour.
- **Revision 3 (this one)** adds **awe factor** as an explicit, named, first-class criterion alongside the existing four, on Vinay's pushback: Kirchhoff is technically sharp but a clamp reporting "fridge: on" does not make a judge sit up. Awe was scored, all survivors were re-ranked, and **the top pick changed.** Kirchhoff is not discarded. It is fully specced below as Alternate 1 so that reverting to it costs nothing if the new pick fails its dated gate before registration closes.

---

## The five criteria, now stated explicitly

Every candidate is scored on all five. Awe was added; nothing was removed.

1. **Feasibility.** Parts in hand and working inside 9 days, with real sourcing and assembly time counted, not hand-waved.
2. **Differentiation.** A recent technique or angle that most teams do not know exists and could not casually replicate.
3. **Judge alignment.** Overlap with what this specific panel personally understands and cares about.
4. **Crowd-magnet discount.** Anything a large fraction of the room will also pick is struck before merit is considered.
5. **Awe factor (new).** Defined precisely below, because a vague version of this criterion is worthless.

### Awe factor, defined before scoring

> Does the demo contain a **visible, visceral, real-time moment that a non-technical judge understands in under ten seconds with no explanation**? It must **show** rather than tell. Qualifying forms: a live physical reaction, a before-and-after reveal, an invisible thing made visible, or a real human interacting with it on stage. **Disqualifying form: a screen displaying a number or a classification label.**

This is deliberately harsh, and it has to be, or every project claims it. A dashboard that updates quickly is not awe. A chart that goes up is not awe. "The system correctly identified the appliance" is not awe, no matter how hard the identification was.

---

## Step 1: reverse-engineer the judges (carried forward)

The panel is MIT Bengaluru faculty plus the Institution's Innovation Council, convened by Dr. Satyanarayana Mathur (School of Computer Engineering, Assistant Director IIC, AICTE Innovation Ambassador). Four things from the organiser emails set the scoring function.

1. **They pre-registered "feasible, not moonshot":** "your team should have a meaningful PoC that demonstrates the feasibility of your idea and gives the evaluators confidence that your solution can be taken forward." Confidence in the team is what is actually being scored. *Hardware consequence:* the device must physically work in the room, on the day. A photo of a breadboard on a slide is worse than no hardware, because it advertises that the hardware did not work.
2. **They explicitly warned against buzzword AI:** "wherever they genuinely strengthen your solution." *Hardware consequence:* the test applies twice. Delete the model, does it still work? Delete the sensor, does it still demo? Half the Software + Hardware entries in that room will be software projects wearing an IoT costume.
3. **They named the win condition themselves:** "Build something that makes people ask, why didn't we have this before?" **This sentence is the awe criterion in the organiser's own words**, which is the strongest possible argument that revision 2 under-weighted it. It is not a slogan we imposed. It is theirs, and it is a filter.
4. **This is a selection round, not a prize round.** The winner represents MIT Bengaluru at national SIH. A solution with a visible next six months beats one that peaks at the demo.

---

## Step 2 and 3: hardware filter and crowd discount (unchanged from revision 2)

Two tests were applied to all 22 Software + Hardware statements before merit. Full table in `research/hardware_ps_research.md`.

**Test 1, load-bearing hardware.** Replace the device with a CSV of recorded data. Does the demo still run? If yes, cut. Kills SH03, SH05, SH10, SH15, SH16.

**Test 2, 9-day physical feasibility.** No international shipping, no custom PCB, no machining, no ethics clearance, nothing over about 10,000 INR. Kills SH13, SH14, SH19, SH20, and SH21 outright (neuronal magnetic fields need SQUID or OPM magnetometers and a shielded room; anyone who picks it will be presenting slides).

**Crowd-magnet discount.** Struck before merit: **SH08** (irrigation, the most saturated hardware student project in India), **SH22** (air quality, second most saturated), **SH01** (waste segregation, the default hardware pick), **SH07** (vitals to a dashboard, the default health pick), **SH04** (same environmental-IoT cluster, and the AI reduces to thresholds on three slow scalars), **SH06** (open-ended, so the default output is a smart cane or a gesture glove, both heavily built and easily dismissed), **SH09** and **SH16** (hardware weakly load-bearing, demo collapses to a chart). **Part C** is out of category by direction, with PS-H01 and PS-H10 noted as the only two that would have survived on merit.

**Survivors carried into the awe re-scoring:** SH02 (reframed as NILM), SH11, SH12 (conditional), SH17, SH18.

---

## Step 4: the awe re-scoring

Honest scoring against the definition above. "Time to get it" is how long a non-technical judge needs, with no narration, before the point lands.

| Candidate | The moment | Time to get it | Shows or tells | Human on stage | Awe verdict |
|---|---|---|---|---|---|
| **SH11** Structural monitoring | A steel beam sitting apparently perfectly still on the table appears on the screen swaying like a branch in wind. Then one bolt is loosened and the motion visibly changes shape in front of you. | ~2 seconds, silent | **Shows.** Invisible thing made visible, textbook case. | Yes, a judge taps the structure and the screen erupts | **Highest** |
| **SH18** Pressure mat | A judge leans a hand or sits on a fabric mat and a live body-pressure heatmap blooms on screen, their own body, in real time. | ~3 seconds, silent | **Shows.** Invisible made visible. | Yes, their own body | **High** |
| **SH17** Muscle strength | A judge squeezes the grip and the force bar reacts instantly. The genuine hidden moment is that muscle activation appears slightly before force does. | ~5 seconds for the squeeze, longer for the interesting part | Shows, but grip force is already visible to the naked eye. The subtle part needs a sentence. | Yes, their own hand | **Medium-high** |
| **SH02** Kirchhoff (NILM) | A judge plugs in their own charger and the system announces "unknown load, 4.8 W, signature recorded," then learns it in thirty seconds. | ~25 seconds, needs narration | **Tells.** It is a label on a screen. The wow is intellectual, not visceral. | Yes, their own object | **Medium** |
| **SH12** EEG (gated) | A judge wears a headset, thinks, and something moves. | ~2 seconds | Shows | Yes | Highest in theory, **but no headset in hand.** Still cut. |

### The honest re-look at Kirchhoff, since it was asked for specifically

The instruction was to check whether SH02's Evidence Gate moment can be staged for real awe, and not to force it if it is not there. It was checked properly and the answer is: **it is genuinely good theatre and it still does not clear the bar.**

The best available staging is strong. Hand the clamp to a judge and let them clamp it themselves, so nobody suspects a hidden switch. Then say "plug in anything you brought." They plug in their own charger. The system refuses to name it, reports the unknown load with its real power draw, and learns it in thirty seconds so that on the replug it names it correctly. A machine that admits ignorance in front of a room and then learns is a real moment, and it is the single best thing about the project.

But measure it against the definition honestly. The judge is looking at a screen that prints a label. The impressive part is that the label says "unknown," and understanding why that is impressive requires knowing that most systems would have confidently guessed wrong. That is a **twenty-five second insight with narration**, not a two second visceral hit. Two upgrades were considered and both fail: sonifying the current waveform is a novelty that adds nothing a judge can interpret, and showing the raw waveform with the kettle's spike arriving is still a screen showing a trace.

**Verdict: Kirchhoff's awe is medium and cannot honestly be raised.** It remains the strongest candidate on differentiation, technical rigour, feasibility certainty and national-policy path. It loses on the new criterion, and the new criterion is the organiser's own stated win condition. It moves to Alternate 1, fully specced, ready to revert to.

### The verification that decided the pick

Everything above depends on one question: **can phase-based motion magnification actually run live on stage in real time, or is it only a pre-recorded processed clip?** If it is only pre-recorded, the awe is fake, the pick is fraudulent, and SH11 is dead. This was checked before anything else.

**It is real.** Three independent confirmations:

1. **The algorithm was purpose-built for real time.** Wadhwa, Rubinstein, Durand and Freeman, *Riesz Pyramids for Fast Phase-Based Video Magnification*, IEEE International Conference on Computational Photography 2014. The Riesz pyramid is 4 times overcomplete against more than 21 times for the eight-orientation complex steerable pyramid it replaces, it uses compact spatial-domain linear filters, and the Riesz transform itself can be approximated by **two three-tap finite difference filters**. The paper's stated purpose is real-time phase-based motion magnification, and the reported output quality is comparable to the steerable pyramid. https://ieeexplore.ieee.org/document/6831820/
2. **A working open-source real-time implementation exists today.** `tschnz/Live-Video-Magnification`, an OpenCV and Qt application that runs **from live cameras**, offering three real-time modes including **Motion (Phase), which is Riesz pyramid based**, alongside Motion (Laplace) and Color. It exposes an adjustable processing resolution from 1/1 down to 1/8 precisely so live rate can be traded against quality, and renders through OpenGL 3.3. https://github.com/tschnz/Live-Video-Magnification . A second implementation, `chrdiller/VideoMagnification`, does webcam streams and heartbeat detection. This is the reference we validate our own implementation against.
3. **Real-time on mobile is published.** *Real-time motion amplification on mobile devices*, arXiv:2206.08422. https://arxiv.org/pdf/2206.08422

**And the honest caveats, which are load-bearing for the plan, not footnotes.**

- **The camera must be on a tripod. This is not optional.** Phase-based Eulerian methods assume stabilised capture and fail on handheld video, since hand shake at 2 to 10 Hz sits inside the passband and gets amplified along with the signal. (Stated explicitly in *Event-Based Motion Magnification*, arXiv:2402.11957.) A handheld demo produces garbage on stage. Tripod, locked, framed before the slot.
- **Live means reduced processing resolution.** The reference app drops camera frames under computational load and provides the 1/1 to 1/8 control for exactly this reason. Our honest claim will be "live at 1/2 or 1/4 processing resolution at N fps measured," with N being whatever we actually sustain on the demo machine. We publish the measured number, not a target.
- **There is a temporal filter lag.** The bandpass needs a buffered window, so there is roughly a second of delay between the real tap and the screen reaction. Irrelevant on stage, but it must be in the demo script so nobody panics and taps again.
- **Lighting matters and the passband must be tuned.** Amplifying the wrong band amplifies noise. This turns out to be the project's best idea rather than its worst problem. See below.

---

## The pick

### **PS-SH11 | Smart Infrastructure Monitoring**

> "Build a sensor-based system to monitor structural health of bridges, buildings, or roads by detecting stress, vibration, or wear indicators. The platform should flag maintenance needs before critical failures occur."
> Expected outcome: "Structural-health monitoring prototype flagging maintenance needs ahead of critical failure."

Working name for the build: **Chladni**. See the vibration, find the crack.

Named for Ernst Chladni, who in 1787 made vibration visible for the first time by scattering sand on a bowed metal plate and letting the nodal lines draw themselves. That is literally what this project does with a camera instead of sand, and an engineering faculty panel will get the reference instantly. It is the same naming instinct as Kirchhoff and a better fit.

### Why this one wins, with awe as a first-class criterion

**1. It is the only candidate whose awe moment and whose technical rigour are the same mechanism.**

This is the argument that flips the decision, and it is worth stating carefully because it is not the obvious one.

In most projects, the wow is bolted onto the engineering. You build the real thing, then you build a flashy surface for it. Kirchhoff is like that: the Evidence Gate is the rigour and the demo staging is separate theatre wrapped around it.

In Chladni they are one object. The camera is simultaneously (a) the thing that makes a judge gasp, because a beam that is visibly motionless on the table is visibly swaying on the screen, and (b) **a second, independent measuring instrument** that cross-checks the accelerometer. Two instruments, different physics, no shared failure mode, measuring the same modal frequencies and agreeing. That is "every generator gets a checker" expressed in physical instrumentation rather than in code, and it means the spectacle cannot be dismissed as decoration, because the spectacle **is** the second measurement.

**2. It resolves revision 2's own objection to itself.**

Revision 2 ranked SH11 second and gave this reason: faculty judges cannot sanity-check operational modal analysis, so a correct result and a plausible-looking wrong result score identically. That was a real objection and the awe lens dissolves it.

The judge does not need to verify the modal analysis. They **watch the beam move on screen, watch one bolt come loose, and watch the motion visibly change**. The video is the verification for a non-specialist. The accelerometer agreement and the frequency shift are the verification for a specialist. One demo, two audiences, two independent verification paths, and neither requires trusting us. That is a much stronger position than revision 2 credited.

**3. The differentiating technique is recent, specific, and almost nobody in that room knows it exists.**

Phase-based motion magnification is not in any standard undergraduate curriculum. The relevant structural-engineering literature is 2024:

- *Motion magnification for video-based vibration measurement of civil structures: A review*, Mechanical Systems and Signal Processing, June 2024. https://www.sciencedirect.com/science/article/abs/pii/S088832702400579X
- *Structural vibration measurement based on improved phase-based motion magnification and deep learning*, MSSP 2024, which suppresses background noise and illumination change and is validated on simply supported and cantilever beams, which is exactly our test article. https://www.sciencedirect.com/science/article/abs/pii/S0888327024008434
- Sarrafi, Mao, Niezrecki, Poozesh, *Vibration-Based Damage Detection in Wind Turbine Blades using Phase-Based Motion Estimation and Motion Magnification*, arXiv:1804.00558. https://arxiv.org/pdf/1804.00558
- Emadi et al., *Application of Intelligent Low-Cost Accelerometers for Bridge Monitoring With a Deep Learning Approach*, Structural Control and Health Monitoring 2025, which supplies the second good idea: temporarily co-locate a reference sensor to calibrate a cheap one, then remove the reference. https://onlinelibrary.wiley.com/doi/full/10.1155/stc/9835353

The review literature reports optical measurement of displacements down to roughly three microns with high correlation against contact sensors. A camera measuring microns is a sentence that lands.

**4. The one genuinely novel thing we contribute: Resonance Lock.**

The honest risk with this project is the "camera trick" objection: a judge notices that motion magnification is an off-the-shelf visual effect with public implementations and asks where the engineering is. We must answer that before it is asked, and we have a real answer.

**The accelerometer tells the camera what to amplify.** The Probe identifies the structure's actual modal frequencies from its spectrum, and those frequencies automatically set the magnification passband for the Witness. Amplify the right band and you see the mode. Amplify a wrong band and you see noise. Nobody in that room is doing a closed sensor-to-camera loop, and it converts the magnification from a filter you eyeball into an instrument that is aimed by a measurement. It also produces the thing a single-point accelerometer physically cannot give you: **the full-field mode shape**, meaning where on the structure the motion actually concentrates, which is what tells you where the damage is rather than merely that damage exists.

That is the defensible core, it is ours, and it is one paragraph a judge can repeat afterwards.

**5. Awe compounds for free, twice.**

The same tripod-mounted camera running the same open-source-validated pipeline in colour mode shows a person's pulse in the skin of their face or hand. It costs zero extra build time because it is a mode switch. Point it at a judge for three seconds as the opening beat, let the room see a heartbeat that is invisible to the naked eye, then say "now we point it at a structure." The judges have felt the capability on their own body before they are asked to care about a bridge. That is the cheapest awe in this entire document.

Second freebie: hand the structure to a judge and let them tap it. Their own tap, their own eyes, the screen erupting. No trust required.

**6. Feasibility is real, and the cost of being wrong is bounded by a dated gate.**

Total bill of materials under 4,000 INR, everything from a Bengaluru hardware store and Robu.in or SP Road, no lead time. And the entire pick rests on one testable claim (live magnification visibly works), which is a **two-hour test we run on 26 Aug, three days before registration closes**, on a laptop webcam pointed at a clamped steel ruler. If it does not visibly work, we revert to Kirchhoff, which is fully specced below and whose parts we are buying anyway. This is the "verify claimed state against reality before building on it" rule applied to a decision rather than to code.

**7. It generalises past the first use case.**

The method is "measure a structure's vibration with no contact and no instrumented points." Bridges, building columns, rotating machinery, a transformer humming at the wrong frequency, a wind turbine blade. Nothing about it is specific to our test article. The national path is real too: India's bridge and building stock is inspected visually by eye, and a technique that turns any phone on a tripod into a vibration instrument is a genuine inspection-cost argument, not a hypothetical one.

### What the PoC concretely is by 5 Sep

Four named parts. Nothing else exists before demo day.

- **The Probe.** An ESP32 with an ADXL345-class MEMS accelerometer mounted on the test structure, streaming sampled acceleration, with a spectrum and identified peak modal frequencies. This is the contact instrument and the numeric ground truth.
- **The Witness.** Our own Riesz-pyramid phase-based magnification running live from a tripod-mounted camera, at whatever processing resolution sustains a usable framerate on the demo machine. We implement it ourselves in Python with OpenCV and numpy, following the 2014 paper (the Riesz transform approximated by two three-tap finite difference filters), and we **validate our output against `tschnz/Live-Video-Magnification` as a reference implementation**. We say openly which parts are ours and which are the reference. Claiming we invented motion magnification would be the exact dishonesty we refuse.
- **Resonance Lock.** The coupling. The Probe's identified modal frequency sets the Witness's temporal passband automatically, live, on screen. Change the structure and watch the band retune itself. This is the part that is ours and it is the part Vinay builds.
- **Damage Ledger.** Before-and-after: baseline modal frequencies and full-field mode shape recorded, damage introduced, both instruments re-measured, and the shift reported by each independently with their agreement stated. Every entry carries which instrument measured it, when, and how far the two disagreed. Same provenance discipline as the memory vault, applied to physical measurements.

**The live demo, in order.** Camera on a judge's hand for three seconds: their pulse, visible, on screen. Swing the tripod to the steel structure sitting motionless on the table: on screen it is swaying like a branch. Hand it to a judge and let them tap it. Then show the Probe's spectrum and Resonance Lock retuning the passband to the measured peak. Then the payoff: loosen one bolt, re-measure, and both the frequency **and** the visible mode shape change, with the accelerometer and the camera independently agreeing on the shift. Total elapsed under four minutes, entirely live.

The bolt is the moment. A judge watches a single bolt come loose and sees a machine detect it two ways at once.

### Honest numbers we will actually have (pre-registered, no vibes)

- **Modal frequency agreement between instruments:** camera-derived versus accelerometer-derived natural frequencies for the first two or three modes, reported as absolute Hz difference and percent, per mode. This is the headline number and it is a cross-check, not a self-assessment.
- **Damage detection:** measured frequency shift for the added-mass case and for the bolt-loosening case, baseline versus damaged, from both instruments, with the run-to-run repeatability spread across at least five repeats. If the shift is inside the noise spread we say so.
- **Measured live framerate and processing resolution** of the Witness on the actual demo machine. Published as measured, never as a target.
- **Measured accelerometer noise floor** on our own board, because MEMS datasheet numbers are not our numbers.
- **Bill of materials, actual receipts, in rupees.**
- **The honest scale limitation, stated out loud:** this is a lab-scale structure with motion amplitudes far larger than a real bridge, and low-cost MEMS noise floors are not adequate for real civil structures without better sensors. We say this before a judge finds it, and it becomes the future-scope slide rather than a hole.

### Hardware sourcing and assembly, stated realistically

| Item | Approx cost (INR) | Source | Lead time |
|---|---|---|---|
| ESP32 DevKit (buy 3, one will die) | 400 each | SP Road / Robocraze / Robu.in | Same day at SP Road |
| ADXL345 or ADXL355 breakout accelerometer (buy 2) | 200 to 3,000 each depending on part | Robu.in / SP Road | Same or next day |
| Aluminium or mild steel flat bar for the cantilever, plus a small two-bay bolted frame (angle stock, nuts, bolts, washers) | ~1,500 | any Bengaluru hardware store | Same day |
| Heavy C-clamps and a rigid base (a table edge counts) | ~500 | hardware store | Same day |
| Tripod (phone or camera), plus a phone or a USB webcam | mostly already owned | team | Same day |
| Work lamp for consistent lighting | ~400 | hardware store | Same day |
| **Total** | **under 4,000 INR** | | |

**Assembly is one honest day, and it is the real schedule risk in this pick.** Not the electronics, the *structure*. It must be rigid enough that the boundary conditions do not wander between the baseline run and the damaged run, or the whole before-and-after collapses. Clamp it hard, mark every position, photograph the setup, and never move it after the baseline is recorded. Budget 28 Aug for building and characterising it, with 29 Aug as slack.

**Two damage modes, deliberately, because one of them is guaranteed to work.** Adding a small known mass produces a predictable, perfectly reversible, perfectly repeatable frequency shift and is our insurance. Loosening a bolt is the realistic and more impressive one, and it is the standard laboratory demonstration of stiffness loss, but on a small frame the shift can be smaller than we would like. **Both are built. If the bolt shift turns out to sit inside our measurement noise by 31 Aug, the added mass becomes the demo and we report honestly why.** No safety concerns in this project beyond ordinary workshop care, which is a genuine advantage over Kirchhoff's mains work.

### Evidence trail

All found by live web search on 2026-08-25. Fuller assessments, including which sources were read in full versus seen at search-result level, are in `research/hardware_ps_research.md`.

1. Wadhwa, Rubinstein, Durand, Freeman. *Riesz Pyramids for Fast Phase-Based Video Magnification.* IEEE ICCP 2014. https://ieeexplore.ieee.org/document/6831820/
2. `tschnz/Live-Video-Magnification`, real-time OpenCV and Qt application, live camera, Motion (Phase) via Riesz pyramid. https://github.com/tschnz/Live-Video-Magnification
3. `chrdiller/VideoMagnification`, webcam streams and heartbeat detection. https://github.com/chrdiller/VideoMagnification
4. *Real-time motion amplification on mobile devices.* arXiv:2206.08422. https://arxiv.org/pdf/2206.08422
5. *Motion magnification for video-based vibration measurement of civil structures: A review.* MSSP, June 2024. https://www.sciencedirect.com/science/article/abs/pii/S088832702400579X
6. *Structural vibration measurement based on improved phase-based motion magnification and deep learning.* MSSP 2024. https://www.sciencedirect.com/science/article/abs/pii/S0888327024008434
7. Sarrafi, Mao, Niezrecki, Poozesh. *Vibration-Based Damage Detection in Wind Turbine Blades using Phase-Based Motion Estimation and Motion Magnification.* arXiv:1804.00558. https://arxiv.org/pdf/1804.00558
8. Emadi et al. *Application of Intelligent Low-Cost Accelerometers for Bridge Monitoring With a Deep Learning Approach.* Structural Control and Health Monitoring, 2025. https://onlinelibrary.wiley.com/doi/full/10.1155/stc/9835353
9. *Physics-Informed Neural Network based Damage Identification for Truss Railroad Bridges.* arXiv:2502.00194, Feb 2025. https://arxiv.org/pdf/2502.00194
10. *Event-Based Motion Magnification.* arXiv:2402.11957 (source for the handheld-capture failure mode; cited as future scope). https://arxiv.org/html/2402.11957v2
11. *3D Motion Magnification: Visualizing Subtle Motions with Time-Varying Neural Fields.* https://3d-motion-magnification.github.io/ (future scope)

### Kill criteria

Kill approaches, not the project. Each is a checkpoint with a date.

- **By 26 Aug, and this is the one that matters.** **Live magnification smoke test, two hours, before registration.** Laptop webcam on a tripod, pointed at a steel ruler clamped to a desk and flicked. Either run `tschnz/Live-Video-Magnification` or write a fifty-line numpy prototype. **If the amplified motion is not visibly obvious on screen, live, to someone who is not told what to look for, revert to Kirchhoff immediately and register PS-SH02.** The entire pick rests on this claim and it is cheap to test, so it gets tested before the door closes rather than after.
- **By 27 Aug.** Crowding check. Nobody is expected on SH11, but ask. If another MIT team is genuinely doing camera-based vibration measurement, switch to Kirchhoff.
- **By 28 Aug, end of day.** Test structure built, clamped, photographed, and producing a repeatable baseline spectrum across five runs. If the baseline wanders between runs, the boundary conditions are loose and that is a structure problem, not a software problem. Fix the clamping, do not start filtering.
- **By 31 Aug.** Damage mode locked. If the bolt-loosening shift sits inside the run-to-run noise spread, the added mass becomes the demo damage mode. Decided that day, written down, not revisited on 4 Sep.
- **By 31 Aug.** Sustained live framerate measured at a chosen processing resolution. If our own implementation cannot hold a usable live rate, we drop resolution in stages (1/2, then 1/4, then 1/8) and publish whichever holds. If none of them holds, we ship the reference implementation for the live view and our own implementation for the offline analysis, and we say exactly that on the slide. **We do not pre-record a clip and present it as live under any circumstances.** That single dishonesty would be worse than losing.
- **By 2 Sep.** If the two instruments do not agree on modal frequency to within a defensible margin, that is the finding, and we report the disagreement with an explanation rather than tuning until they match. A cross-check we tuned to agree is not a cross-check.
- **Any time.** If the project starts needing a better camera or a bigger model rather than better clamping, better lighting, and a better-aimed passband, that is the signal we built the wrong thing.
- **Scope tripwire.** Anything beyond the four named parts goes to `GAPS.md` on sight. Multi-camera, 3D magnification, neural field methods, event cameras, a deployed bridge, a mobile app, cloud, automated alerting to a municipality: all parked, all future scope, none built before 5 Sep.

---

## Alternates

### Alternate 1: **PS-SH02 | Smart Energy Consumption & Optimization** (build name Kirchhoff)

**Kept fully specced because it is the 26 Aug revert target, and the reversion must cost nothing.** It was revision 2's top pick and it is still the strongest candidate on differentiation, technical rigour, feasibility certainty and national-policy path. It lost only on awe.

- **The reframe:** not smart plugs. **One** non-contact current clamp at a single point, sampling mains at tens of kHz, with software inferring which individual appliances are running from the aggregate waveform alone. The sensor is load-bearing by construction (the claim is one sensor instead of twenty) and so is the model (without it a clamp is an ammeter). It is the only survivor that passes both deletion tests that cleanly.
- **The techniques:** Gerasimov et al., *Toward Explainable NILM: Real-Time Event-Based NILM Framework for High-Frequency Data*, arXiv:2501.16841, 28 Jan 2025, which reaches 90 percent on PLAID at sub-one-second latency with SHAP attribution per event (https://arxiv.org/abs/2501.16841). And Zhao et al., *Unknown appliances detection for NILM based on vision transformer with an additional detection head*, Heliyon 10(9):e30666, 7 May 2024, which adds open-set rejection, AUROC above 0.85 on PLAID and above 0.95 on most of WHITED, and honestly reports F1 of only 0.56 separating a kettle from a toaster (https://pmc.ncbi.nlm.nih.gov/articles/PMC11101768/).
- **The four parts:** **The Probe** (ESP32 sampling an SCT-013 clamp via built-in ADC in I2S DMA continuous mode, documented to 150 kHz, which puts a 400 INR board in PLAID's 30 kHz regime), **Signature Bank** (each demo appliance switched fifty times, the 200 ms around each switch captured and labelled), **Evidence Gate** (z-score event detection, harmonic and V-I features, classification, open-set rejection, and per-event provenance so the system says "unknown load, 1.8 kW, signature recorded" rather than guessing), and **The Wall** (live waveform, per-appliance kWh and rupees, wastage callout, forecast).
- **Numbers:** closed-set accuracy and macro F1 on our rig and on PLAID via NILMTK, open-set AUROC per appliance, p95 switch-to-screen latency, concurrent-load accuracy at 2 and 3 appliances reported separately, measured ADC noise floor and effective bits, and the actual BOM under 3,000 INR.
- **Policy path:** India's RDSS programme targets roughly 250 million prepaid smart meters, tens of millions already installed, deadline extended from March 2026 to March 2028. Those meters report aggregate kWh only. Appliance-level insight is a missing software layer on hardware already in the wall. (Source figures conflict across industry and think-tank reporting, so quote the range, never the flattering number.)
- **Safety, if we revert:** clamp is non-contact and safe; the voltage channel is the only risk and both acceptable routes are galvanically isolated (ZMPT101B, or an AC-AC step-down adapter into a divider). RCD-protected extension board, mentor sights the wiring before first energising, and a current-only fallback decided by 30 Aug.
- **Why not first:** awe is medium and cannot honestly be raised. The best staging is a judge plugging in their own charger and the system admitting it does not know, which is a twenty-five second insight with narration rather than a two second visceral hit at a screen printing a label.

### Alternate 2: **PS-SH18 | Smart Spinal Cord and Pressure-Injury Monitoring**

**Promoted from a downgraded survivor to a real alternate on the strength of the awe re-scoring, which revision 2 under-weighted.** A judge leans on a fabric mat and a live pressure map of their own body blooms on screen. Invisible made visible, their own body, under three seconds, no narration. That is genuine awe and the earlier pass did not credit it.

- **The build:** we fabricate the sensor ourselves. A Velostat sheet between orthogonal strips of conductive copper tape gives an N by N piezoresistive matrix for roughly 1,500 to 2,500 INR, scanned by a multiplexer into any microcontroller. A 16 by 16 mat is a real afternoon of building, and "we made the sensor" is a differentiating sentence in a room of people who bought modules. Cheapest BOM of every candidate, no mains, no fabrication lead time, no safety gate.
- **Sources:** *Smart Pressure e-Mat for Human Sleeping Posture and Dynamic Activity Recognition*, arXiv:2305.11367 (https://arxiv.org/pdf/2305.11367); *Velostat-Based Pressure Sensor Matrix for a Low-Cost Monitoring System Applied to Prevent Decubitus Ulcers*; *Intelligent Medical Velostat Pressure Sensor Mat Based on Artificial Neural Network and Arduino Embedded System*, 2023; *Development of Low-Cost Fabric-Integrated Capacitive Pressure Sensors for Real-Time Pressure Monitoring and Ulcer Prevention*, Sensing and Imaging 2025 (https://link.springer.com/article/10.1007/s11220-025-00642-1).
- **Why not first:** the defensible claim is smaller than the PS title promises, and that gap is visible. Preventing a pressure injury cannot be demonstrated in ten minutes or measured in nine days. What we can honestly show is pressure-map visualisation and posture classification, which is a real but modest claim, and it is the same structural objection that killed the mental-health statements. Velostat also drifts and creeps under sustained load, which is well documented and would have to be disclosed. Awe is high, defensibility is the lowest of the three.

### Still noted, still not an alternate: **PS-SH12 | NeuroWave RT (Live EEG)**

Highest theoretical awe in the entire bank (a judge thinks and something moves) and genuinely 2024-to-2026 in technique (LaBraM; FEMBA arXiv:2502.06438; LEAD arXiv:2502.01678). Still cut, for the same two independent reasons, either of which alone is disqualifying. **Sourcing:** we need a working headset physically in hand; OpenBCI is multi-week from the US, a Muse S is 25,000 to 30,000 INR with import and delivery risk, a DIY ADS1299 front end is weeks. **Technical:** those foundation models are pretrained on many-channel clinical montages and adapting them to 4 dry consumer electrodes is a domain-shift research problem, not a fine-tune, so the realistic 9-day build is bandpower plus a classical classifier, which is a 2015-level project wearing 2026 citations. Awe cannot rescue hardware that is not in the room. **Revisit only if MIT Bengaluru's biomedical or ECE department confirms a working headset in hand before 27 Aug, with someone who knows how to run it, and even then drop the foundation-model angle.**

---

## Final ranked verdict

| Rank | PS | Feasibility | Differentiation | Judge alignment | Crowd discount | **Awe** | Net |
|---|---|---|---|---|---|---|---|
| **1** | **SH11 Chladni** | Good, structure build is the risk | High, and the coupling is ours | High, they see it with their own eyes | Very low crowding | **Highest, verified live-feasible** | **Pick** |
| 2 | SH02 Kirchhoff | Highest certainty | Highest | High, plus a real policy path | Low once reframed | Medium, honestly capped | Alternate 1, revert target |
| 3 | SH18 Pressure mat | Highest, we make the sensor | Medium | Medium | Low | High | Alternate 2 |
| 4 | SH17 Muscle strength | Good | Medium-high | Medium | Low | Medium-high | Cut, dynamometer objection |
| 5 | SH12 EEG | **Fails**, no headset | Highest | High | Very low | Highest in theory | Cut, gated |

**Chladni wins because its awe moment and its verification mechanism are the same camera.** Every other candidate would have to bolt spectacle onto engineering; this one gets both from one instrument, which is why it survives the "what is the AI actually doing" question and the "why didn't we have this before" question with the same answer.

---

## Open items (Vinay owns these, not the build track)

- [ ] **Run the 26 Aug live-magnification smoke test personally, before anything else.** Two hours. The whole pick rests on it and it is the cheapest de-risking available.
- [ ] **Order parts on 26 Aug, before registration and before the crowding check.** Under 4,000 INR, and the ESP32s are useful under all three candidates, so ordering early is free insurance and ordering late is the largest avoidable schedule risk in this plan.
- [ ] Team of 6, minimum 1 girl student, all MIT Bengaluru. Mix must cover firmware, signal processing and CV, frontend, documentation and presentation, because all 6 must present.
- [ ] Faculty mentor confirmed. Preference now shifts: someone from Mechanical or Civil who has run a modal analysis lab and can sanity-check our frequencies and lend a proper clamp or a shaker if one exists.
- [ ] Crowding check before 27 Aug.
- [ ] Register at https://tinyurl.com/MIT-SIH2026 with PS-SH11 locked, well before 29 Aug 11:45 PM. Not on the last evening.
- [ ] Confirm whether the internal submission is scored against the SIH portal PS text or this master bank text, since the 21 Aug email points to sih.gov.in/sih2026PS while the attached bank is what was circulated. Match the wording of whichever governs the registration form.
