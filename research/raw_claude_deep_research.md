# Raw deep research output (Claude), 2026-08-25

Pasted verbatim from Vinay's deep research session, run against `deep_research_prompt.md`. Kept for provenance; the adjudicated, cite-safe version is in `deep_research_findings.md`.

---

## 1. State of the art in vision-based SHM (2024–2026)

**Field-proven at real scale — yes, and further along than a hackathon framing usually assumes.**

- Computer-vision displacement monitoring has been demonstrated on three landmark suspension bridges in Turkey (First and Second Bosphorus, Osman Gazi), at standoff distances of 600 m, 755 m and 1350 m, with both displacements and dynamic frequencies agreeing with conventional monitoring and finite-element analysis. That's not a lab demo.
- A 2022 field test used hybrid motion magnification on a large-scale truss bridge, with a commercial camera over 400 m away, recovering four full-field mode shapes of the bridge while a train crossed.
- A 2025/26 study achieved UAV-based multi-point displacement measurement across a full span of a real highway bridge in Guangdong with RMSE under 0.3 mm.

**Commercial deployment:** the dominant player is RDI Technologies (Knoxville, TN), whose patented Motion Amplification Iris platform has been selling since 2016.

- The Iris M already automatically determines frequencies of interest and creates multiple filtered data sets with a single click, i.e. automatic passband selection is a shipped product feature, not a research gap.
- The Iris CM connects traditional vibration inputs and RDI's video-based vibration measurements in a continuous monitoring configuration, i.e. accelerometer-plus-camera fusion is a commercial product.

No published price found for any Iris model; distributors quote custom pricing. Anecdotal $50k-$100k figures circulate but are not sourceable.

**The honest gap:** camera-based SHM in public infrastructure is still overwhelmingly campaign-based or industrial condition monitoring. No evidence found of a national programme using continuous camera-based modal monitoring as a primary modality. That's a gap in continuous deployment, not in the technique.

---

## 2. Stress-testing "Resonance Lock"

The coupling is not novel, and a structural-dynamics faculty judge is reasonably likely to know the prior art.

Closest prior art: Cufar, Slavic & Boltezar, "Mode-shape magnification in high-speed camera measurements," Mechanical Systems and Signal Processing, Vol. 213, art. 111336 (2024). https://www.sciencedirect.com/science/article/pii/S0888327024002346 . They measure structural response with a gradient-based optical flow method and perform a hybrid modal analysis in conjunction with a reference accelerometer measurement, identifying dynamics into the sub-pixel range and below the image noise floor, magnification factors around 40,000x.

Earlier lineage: "Camera-based experimental modal analysis with impact excitation: Reaching high frequencies thanks to one accelerometer and random sampling in time," MSSP Vol. 170, art. 108879 (2022).

Automatic passband selection is already solved without an accelerometer: Shang, Shen et al., arXiv:1712.06566, automatic band-selection method deriving bands from per-pixel vibration frequency measurements within regions of interest, explicitly motivated by manual band selection being ineffective for large bridges.

Two-instrument agreement as damage validation is standard practice in this literature (Chen, Wadhwa, Cha, Durand, Freeman, Buyukozturk, Journal of Sound and Vibration 345, 2015, and recurring since).

| Claim | Verdict |
|---|---|
| Accelerometer-derived modal frequency drives video magnification | Not novel. Cufar et al. 2024; commercially in Iris CM. |
| Automatic passband tuning | Not novel. Shipped product feature plus published auto-band-selection. |
| Two-modality agreement as damage validation | Standard practice, not a contribution. |
| Doing all of it live, closed-loop, on ~4,000 INR of hardware | Defensible. No published low-cost real-time closed-loop implementation found. |

Recommendation: stop calling it novel method, call it novel accessibility. "We reproduced, on 4,000 INR of commodity hardware and in real time, a sensor-to-camera modal coupling that currently exists only in research code and in commercial systems priced for industrial customers."

Additional honest point: accelerometer and camera observing the same excitation is not independent validation in the statistical sense; both see the same physical event. The genuinely complementary argument is spatial: accelerometer gives frequency at one point, camera gives full-field mode shape.

---

## 3. The India use case

**Collapse data:**
- Newslaundry analysis (29 July 2025) of media reports: 170 bridge collapses 2021-2025, 202 deaths, 441 injuries, while MoRTH officially reported only 42 collapses 2019-2024. Bihar (26), Uttarakhand (25), Himachal Pradesh (17), Gujarat (16). https://www.newslaundry.com/2025/07/29/4-years-170-collapses-202-deaths-whats-ailing-indias-bridges
- Gambhira bridge (Vadodara, Gujarat, 9 July 2025): span collapse, 20 deaths, preliminary probe cited crushing of pedestal and articulation joints, bridge built 1985.
- Morbi, October 2022: suspension bridge collapse, at least 132 deaths.
- Older study cited in reporting: 2,130 bridge collapses in India 1977-2017, 80.3% natural disasters, 10.1% material deterioration, 3.28% overloading. Not independently verified, second-hand.

**Inspection practice:**
- MoRTH's Indian Bridge Management System: 172,517 bridges/structures inventoried, condition data collected twice yearly (pre/post-monsoon) via Mobile Bridge Inspection Units, ~147 critically distressed bridges identified, ~200 bridges over 75 years old in inventory.
- 2026: nationwide digital survey of ~1.7 lakh NH structures via IBMS mobile app, field engineers on smartphones/tablets, drones for hard-to-access sections, September deadline.

**The mandate that changes the pitch:** 4 March 2024, MoRTH directive mandating sensor installation on bridges for real-time health monitoring on national highways, DPR consultants required to specify sensor types/quantities/locations and include in cost estimates. Mandated parameters: strain, deflection, vibration, tilt, displacement, temperature, corrosion, scour.

**Surviving gap:** state and district maintained bridges, where collapses concentrate (Bihar, Uttarakhand, Himachal). Bihar State Bridge Maintenance Policy 2025 (India's first state-level systematic bridge upkeep framework), 3,968 bridges targeted including 532 mega structures, IIT Delhi and IIT Patna auditing 85 of them.

**Defensible slide claim:** "India's national-highway bridges are now covered by a 2024 MoRTH sensor mandate, but the ~170 collapses recorded 2021-2025 concentrate in state- and district-maintained structures, where per-bridge instrumented SHM is economically infeasible and inspection remains twice-yearly and largely visual. A portable sub-5,000 INR rig that yields a repeatable quantitative modal signature during those existing inspection visits converts a subjective condition rating into a comparable number over time." Positioned as screening/triage, not continuous monitoring.

Could not source: per-bridge cost figures for Indian SHM installations, or cost of a single IBMS/MBIU inspection.

---

## 4. Limitations to disclose proactively

**4a. Environmental confounding (the most dangerous one).**
- Sohn et al.: Alamosa Canyon Bridge natural frequencies changed ~6% per day with temperature.
- Farrar et al.: I-40 Bridge, severe artificial damage produced little change in natural frequencies.
- Z24 Bridge (Switzerland): damage-induced frequency change smaller than temperature-induced variation; temperature swings produced up to 10% eigenfrequency change.
- Simply supported RC beam: natural frequency decreases ~0.148% per 1C; temperature-induced changes may exceed structural-damage impact.
In Indian field conditions with large diurnal/seasonal swings this is not a footnote. Mitigations: temperature-regression baselines, cointegration, PCA/kernel-PCA EOV removal.

**4b. Global modal methods miss local failure modes.** Gambhira failed via crushing of pedestal/articulation joints in one of 23 spans; a localised failure may produce a global modal change below detection floor (consistent with the I-40 result). Disclose: method targets global stiffness loss, not local component failure.

**4c. Camera-specific failure modes.**
- Heat haze: Kong et al., Sensors 24(16):5151, Aug 2024, doi:10.3390/s24165151. Their correction fixed 61.05% of static and 95.31% of dynamic heat-haze-induced errors, implying uncorrected error is significant.
- Atmospheric turbulence at range: 2025 MSSP paper on anisotropic turbulence from uneven heating over long remote monitoring paths.
- Amplitude floor on large structures: stated directly in PBMM-for-SHM literature, phase-based motion estimation cannot extract subtle movements from a large structure.
- Civera et al., Shock and Vibration 2021: PBMM values consistent with attached sensors on a cracking structure, but signal amplitude decay made PBMM less robust over time versus strain gauges.
- Plus: camera ego-motion/tripod vibration, illumination change, occlusion, out-of-plane motion, pixel-to-mm calibration, and Nyquist limits from frame rate.

**4d. Hardware risk specific to this build.** Research-grade SHM MEMS: 25 microg/rtHz standard, 0.7 microg/rtHz ultra-low-noise, comparable to force-balance accelerometers; ADXL355 spec ~25 microg/rtHz, <0.15 mg/C offset drift. Consumer parts far above this; a review of low-cost SHM DAQ found tested low-cost devices had low sensitivity and high noise density, suitable only for near-field M5+ earthquakes. An MPU6050 on a real bridge under ambient excitation will likely show nothing; fine on a lab beam excited by hand. Recommend ADXL355 (~2,000-3,000 INR) if budget allows, disclose noise floor explicitly otherwise. ESP32 sampling jitter corrupts FFT bin accuracy; use hardware-timer ISR with fixed sample clock, log real timestamps.

**4e. Scope: motion, not stress.** PS asks about "stress, vibration, or wear indicators." This system measures motion/frequency, infers global stiffness change. Strain gauges/fibre optics measure strain directly and locally. State plainly: measuring the vibration indicator, stress and wear out of scope.

**4f. Cheap-competitor preempt.** Matarazzo et al., Communications Engineering 1:29 (2022), doi:10.1038/s44172-022-00025-4: recovered modal frequencies of Golden Gate Bridge and a short-span Italian highway bridge from ordinary smartphone data during vehicle trips (including uncontrolled Uber rides); projected crowdsourced data could add 14+ years of service life (~30% increase) to a maintenance plan. Hardware cost: zero. Our answer to "why not just phones": mode shape, phones give frequency only, camera gives full-field spatial shape for localisation.

---

## 5. Three recent works ahead of typical team findings

1. Cufar, Slavic & Boltezar (2024), MSSP 213:111336. Cite as prior art ourselves; state what we add (real-time, closed-loop, commodity hardware).
2. Genuine sensor fusion: "Prior-free vision-acceleration fusion with self-calibrated scaling for high-accuracy bridge displacement monitoring," Measurement (2025), adaptive Kalman filter with Sage-Husa estimator fusing asynchronous visual displacement and acceleration; also a 2025 Intelligent Transportation Infrastructure (Oxford Academic) review of multi-modal sensing fusion, multi-rate Kalman filtering, backward smoothing, up to 200 Hz dynamic displacement. Implementing even a basic multi-rate Kalman filter fusing low-rate camera displacement with high-rate accelerometer data would convert "Resonance Lock" from two instruments in a room into actual fusion; highest-value technical upgrade available in the build window.
3. Outdoor robustness: Kong et al., Sensors 2024 (heat haze, doi:10.3390/s24165151); Zhang, Tao, Zhou & Chen, MSSP (2025), turbulence-tilt elimination plus deblurring network plus displacement extraction for long-span bridges; 2025 Engineering Structures paper, Phase-ECC frame matching maintaining sub-pixel tracking under adverse lighting, validated in low-light and vehicle-bridge interaction experiments.

Also: hybrid motion magnification truss-bridge field test (Sensors, 2022, PMC9739241), four full-field modal shapes of a real truss bridge from a commercial camera over 400 m away. "Here's what this scales to" slide.

---

## 6. Verdict

**(a) Sound and novel?** Sound: yes. Novel as method: no. Accelerometer-informed magnification is published (Cufar 2024) and commercially productised (RDI Iris CM). Automatic band selection is both published and shipped. Present as novel cost point and form factor for a known technique, not a novel technique.

**(b) Real, citable unmet use case?** Yes, narrower than the obvious pitch. Not "India's bridges are uninstrumented" (false for national highways post-March-2024 mandate). Real gap: state/district/rural bridges, where collapses concentrate and even a leading state framework covers 85 of 3,968 bridges. Positioned as low-cost repeatable screening within existing inspection visits, holds up. Positioned as continuous monitoring, doesn't.

**(c) Strongest defensible claim:**
"On our test structure, a contact accelerometer and a markerless camera pipeline independently register the same modal frequency shift under a known stiffness perturbation, and the camera additionally recovers the spatial mode shape that a single-point sensor cannot, on under 4,000 INR of commodity hardware, in real time. Everything beyond our test structure is future scope, and here are the specific things that would have to be solved first."
Every clause is something actually demonstrated; no extrapolation to real bridges.

**(d) Weakest point:** Environmental confounding of modal frequency (Z24, I-40, Alamosa Canyon results). Cannot be fixed in the build window. Disclose first, cite Z24/I-40, log temperature (DS18B20, ~100 INR) alongside every modal measurement, name the mitigation literature (temperature-regression baselines, cointegration, PCA-based EOV removal) as stated future work. Secondary, fixable: consumer MEMS noise floor and ESP32 sampling jitter, upgrade to ADXL355 if budget allows, hardware-timer-driven sampling with logged timestamps either way.
