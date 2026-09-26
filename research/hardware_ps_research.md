# Research trail: hardware + software problem statements, SIH 2026 Internal (MIT Bengaluru)

**Written:** 2026-08-25
**Scope of this pass:** Part B of `assets/SIH_2026_Master_PS_Bank.pdf` (PS-SH01 to PS-SH22, "Software + Hardware"), with a short note on Part C (PS-H01 to PS-H20, "Hardware").
**Why this pass exists:** the earlier pick, PS-S36 (Trustworthy Agentic AI for Engineering Education), was a pure-software statement. It is deprioritised on Vinay's direction: he wants the Software + Hardware category so the project does not read as "another AI recommendation system for student courses." This file is the auditable trail behind the new pick in `DECISION.md`.

**Verification honesty note.** Every source below was found by live web search on 2026-08-25. Entries marked **[full text checked]** were fetched and read at the abstract or article level. Entries marked **[search-result level]** were surfaced by search and the title, venue, and claim shown here come from the search result or the abstract snippet, not a full read. Nothing here is invented, and nothing is upgraded past what was actually verified. Before any of this is quoted on a slide, the **[search-result level]** items get a full read first.

---

## Part 0: the filter used

Two tests were applied before any paper was searched for.

**Test 1, load-bearing hardware.** If you delete the physical device and replace it with a CSV file, does the project still demo? If yes, it is a software project wearing an IoT costume and it is out. Many Part B statements fail this: they say "IoT sensors" but the deliverable named in EXPECTED OUTCOME is a dashboard, and a dashboard runs fine on replayed data.

**Test 2, 9-day physical feasibility.** Registration closes 29 Aug, demo is 5 Sep. That is roughly 9 calendar days and closer to 6 or 7 honest working days across 6 students with coursework. Any bill of materials that needs international shipping, custom PCB fabrication, machining, a biosafety or ethics clearance, or a single component costing more than about 10k INR is out. Bengaluru advantage: SP Road plus Robu.in and Robocraze next-day delivery covers most hobby-grade sensing. That advantage only applies to parts those channels actually stock.

Only statements passing both tests got a literature search.

---

## Part 1: triage of all 22 Software + Hardware statements

| PS | Hardware load-bearing? | 9-day sourcing | Verdict |
|---|---|---|---|
| SH01 Intelligent Waste Segregation | Yes (bin, camera, servo) | Easy | **Cut on crowding.** The single most-picked hardware idea in Indian internal hackathons. |
| SH02 Smart Energy Consumption & Optimization | Depends entirely on framing. Smart-plug version fails Test 1. Single-point disaggregation version passes hard. | Easy, all local | **Survivor.** See Part 2. |
| SH03 Intelligent Public Safety & Emergency Response | No. Statement is integration and alerting. | n/a | Cut. Becomes a CCTV demo plus a notification. |
| SH04 AI-Based Water Quality Monitoring | Yes (pH, turbidity probes) | Easy | Weak survivor. See Part 2, downgraded. |
| SH05 Smart Flood & Urban Disaster Prediction | No. The prediction runs on weather and terrain data; the ultrasonic level sensor is decoration. | n/a | Cut on Test 1. |
| SH06 Smart Assistive System for PwD | Yes, but the statement is open-ended | Depends on what you choose | Cut as framed. See note in Part 3. |
| SH07 Intelligent Healthcare Monitoring | Yes (MAX30102, DS18B20) | Easy | **Cut on crowding.** The default "vitals to a dashboard" build. |
| SH08 IoT-Based Smart Irrigation | Yes (moisture probe, solenoid) | Easy | **Cut on crowding.** Most saturated IoT statement in the country. |
| SH09 Smart Renewable Energy Management | Partial. Needs a panel and a charge controller; the AI is forecasting on logs. | Medium | Cut. Demo collapses to a chart. |
| SH10 Smart Food Waste Reduction | No. Inventory and expiry tracking is software. | n/a | Cut on Test 1. |
| SH11 Smart Infrastructure Monitoring | Yes (accelerometers on a real structure) | Medium (sensor choice matters) | **Survivor.** See Part 2. |
| SH12 NeuroWave RT, Live EEG Brain Analytics | Yes, maximally | **Hard.** Needs a real EEG headset in hand. | Conditional survivor, gated. See Part 2. |
| SH13 Gestureless Gaming using EEG-VR | Yes | Harder than SH12 (EEG + VR headset) | Cut on sourcing. |
| SH14 VR + BCI Human-Computer Interaction | Yes | Same as SH13 | Cut on sourcing. |
| SH15 Accessibility Training & Simulation | No. It is a simulator. | n/a | Cut on Test 1. Miscategorised as hardware. |
| SH16 Precision Farming Digital Twin | Barely. Twin runs on models; sensors feed it. | Easy | Cut on Test 1 (weak) plus crowding with SH08. |
| SH17 Muscle Strength Assessment Device | Yes (sEMG + load cell) | Easy to medium | **Survivor.** See Part 2. |
| SH18 Smart Spinal Cord / Pressure-Injury Monitoring | Yes (pressure sensing array, fabricated by us) | Easy, DIY fabrication | **Survivor.** See Part 2. |
| SH19 Bio-Inspired Impact-Resistant Vehicle Material | Yes, but it is mechanical engineering | Needs a UTM or drop tower plus print time | Cut. Outside our stack, and the test rig is the project. |
| SH20 AI-Optimized 3D Bioprinting | Yes | Needs a bioprinter or a converted extruder plus bioink | Cut on sourcing and on unverifiable claims in a 10-minute demo. |
| SH21 Neuron Magnetic Field Measurement | Yes | **Impossible.** OPM or SQUID magnetometers, lakhs of rupees, shielded room. | Cut hard. Anyone who picks this is presenting a slide deck. |
| SH22 AI-Based Air Quality Prediction | Yes (SDS011, MQ-series) | Easy | **Cut on crowding.** Second-most-picked after irrigation. |

**Part C note.** Part C was struck wholesale in the previous pass on procurement grounds and that reasoning still mostly holds for the mechanical statements (H02 exoskeleton, H04 CubeSat hinge, H11 Braille embosser, H12 cold storage, H17 hand-crank generator, H19 prosthetic hand: all need fabrication time we do not have). Two Part C statements are cheap enough to be real, PS-H01 (passive acoustic/RF drone detection) and PS-H10 (retrofit predictive-maintenance kit for MSME motors), but Vinay's direction was the Software + Hardware category specifically, so they are noted and not pursued. PS-H10 in particular shares most of its sensing stack with the SH02 survivor, which is a useful fallback fact.

---

## Part 2: literature search per surviving candidate

### Candidate A. PS-SH02, Smart Energy Consumption & Optimization

**The reframe that makes hardware load-bearing.** Read literally, this statement invites a smart-plug build: one plug per appliance, each reporting kWh, a dashboard on top. That fails Test 1 (delete the plugs, replay a CSV, same demo) and it fails the organiser's own "genuinely strengthens" filter, because nothing about it needs a model. The version that passes both is **Non-Intrusive Load Monitoring (NILM)**: one current clamp at a single point, and software that infers which individual appliances are running from the aggregate waveform. The sensor is then the whole point, because the entire technical claim is "one sensor instead of twenty."

**Papers found.**

1. **Gerasimov, Kamyshev, Moghimian Hoosh, Gryazina, Ouerdane. "Toward Explainable NILM: Real-Time Event-Based NILM Framework for High-Frequency Data." arXiv:2501.16841, submitted 28 January 2025.** https://arxiv.org/abs/2501.16841 **[full text checked at abstract level]**
   *Relevance:* This is the closest single match to the whole pitch. It is event-based (a z-score detector fires on appliance state changes rather than running a model continuously), it is high-frequency (trained and evaluated on PLAID), it reports 90 percent classification accuracy at under one second latency with low computational requirements, and it is explicitly explainable via post-hoc SHAP attributing each decision to specific features such as the cosine of individual harmonic phases. Three things matter for us. First, the low-compute and sub-second-latency claim means this is a real-time demo, not a batch job, which is what a live hardware demo needs. Second, "which harmonic drove this decision" is a per-event provenance story, which is exactly the verification pattern Vinay already ships elsewhere. Third, event-based framing means the demo has a natural beat: someone flips a switch, the system names the appliance within a second and shows why.

2. **Petralia, Charpentier, Kadhi, Palpanas. "NILMFormer: Non-Intrusive Load Monitoring that Accounts for Non-Stationarity." arXiv:2506.05880, submitted 6 June 2025, published at KDD 2025.** https://arxiv.org/abs/2506.05880 **[full text checked at abstract level]**
   *Relevance:* The current strong published baseline for the low-frequency side of NILM. Its contribution is a subsequence stationarisation and de-stationarisation scheme that cancels distribution drift inside each window, plus a positional encoding built from the subsequence timestamp rather than an index. Evaluated on 4 real-world datasets. This is useful to us as the named state of the art we compare against and as a well-motivated reason to prefer event-based high-frequency features when we only have hours of our own data. Honest assessment: reproducing NILMFormer end to end in 9 days is not realistic and we should not pretend otherwise. Its role is as a cited baseline and as the source of the non-stationarity argument, not as something we reimplement.

3. **Zhao, Liu, Li, Wei, Han. "Unknown appliances detection for non-intrusive load monitoring based on vision transformer with an additional detection head." Heliyon 10(9):e30666, 7 May 2024.** https://pmc.ncbi.nlm.nih.gov/articles/PMC11101768/ **[full text checked at abstract and results level]**
   *Relevance:* This is the differentiator paper. Almost every NILM student build is closed-set: it is trained on N appliances and, shown an unseen one, confidently mislabels it. This paper does open-set NILM. A Vision Transformer over V-I trajectory images plus an extra detection head that clusters known-appliance features around class centres, then classifies a test sample as known or unknown by distance to those centres. Reported: AUROC above 0.85 for most appliances on PLAID (11 types, 1,793 records at 30 kHz), above 0.95 for most on WHITED (54 types at 44.1 kHz, 12 tested), and honestly a much weaker F1 of 0.56 on kettle versus toaster, which are physically near-identical resistive loads. That last number is the useful one, because it is the failure mode we should report ourselves rather than hide. Building a distance-to-class-centre rejection head on top of an embedding is genuinely a one-day job, not a research programme, which is what makes this the right kind of borrowed idea.

4. **Wang, Tang, Xue, Keshav, Li, Ding. "DualNILM: Energy Injection Identification enabled Disaggregation with Deep Multi-Task Learning." arXiv:2508.14600, submitted 20 August 2025 (revised June 2026).** https://arxiv.org/abs/2508.14600 **[full text checked at abstract level]**
   *Relevance:* Behind-the-meter solar or battery injects power that masks appliance signatures and collapses conventional NILM accuracy. DualNILM is a Transformer multi-task model that jointly does appliance state recognition and injected-energy identification, with open-sourced synthetic PV-augmented datasets. *Honest assessment: do not build this in 9 days.* Its value to us is exclusively as the future-scope slide, and it is a good one, because Indian rooftop solar makes this the obvious next failure mode and having a named 2025 paper for it shows the panel we know where the work goes next. Citing it as our future direction is honest. Claiming it as a feature would not be.

5. **Batra, Kelly, Parson, Dutta, Knottenbelt, Rogers, Singh, Srivastava. "NILMTK: An Open Source Toolkit for Non-intrusive Load Monitoring." arXiv:1404.3878; code at https://github.com/nilmtk/nilmtk** **[search-result level]**
   *Relevance:* Not novel, and that is the point. NILMTK gives standard dataset parsers (REDD, UK-DALE, iAWE, AMPds and others), a standard data format, reference disaggregation baselines, and an accuracy metric suite. Using it means our numbers are comparable to published numbers instead of being self-defined, which is the difference between honest measurement and a made-up score. iAWE is Indian data, which is a small extra credibility point for an Indian panel.

6. **"Towards trustworthy Energy Disaggregation: A review of challenges, methods and perspectives for Non-Intrusive Load Monitoring." arXiv:2207.02009 (also PMC9371074).** **[search-result level]**
   *Relevance:* Establishes, with a citable review rather than our own assertion, that transferability to unseen buildings is the standing open problem in NILM and that most state-of-the-art techniques have not succeeded in unseen houses. This matters because it converts our honest negative into a known-hard result. When we report that accuracy drops on an appliance the model never saw, we are describing the field's open problem, not our incompetence, and we can cite it.

7. **"Prompting Large Language Models for Training-Free Non-Intrusive Load Monitoring." arXiv:2505.06330, 2025.** https://arxiv.org/html/2505.06330 **[search-result level]**
   *Relevance:* Interesting as a contrast, not as an approach. It argues LLMs generalise across unseen environments without retraining. Worth one line in the deck as the alternative we considered and rejected, because a 30 kHz waveform is exactly the kind of signal an LLM should not be in the loop for, and saying so out loud to a panel that warned against buzzword AI is a positive, not a negative.

**Hardware feasibility, checked.**

- ESP-IDF documents that the ESP32 built-in ADC in I2S mode supports fully continuous DMA sampling at up to **150 kHz**. https://docs.espressif.com/projects/esp-idf/en/v4.2.3/esp32/api-reference/peripherals/i2s.html **[search-result level, doc page]** PLAID is 30 kHz and WHITED is 44.1 kHz, so a 150 kHz ceiling means a single ESP32 can natively capture in the same regime the published high-frequency work uses. This is the fact that makes the whole plan feasible on a 400 INR board. Honest caveat: the ESP32 internal ADC is 12-bit and known to be noisy and non-linear, so we must measure and publish our own noise floor and effective bits rather than assume 12 clean bits.
- ADS1115 is the usual hobby ADC upgrade and it is the wrong choice here: 860 samples per second is three orders of magnitude too slow for V-I trajectories. Noted so nobody on the team wastes a day on it.
- Sensors are stocked domestically with next-day delivery. SCT-013-000 100A split-core clamp: https://robu.in/product/sct-013-000-100a-non-invasive-ac-current-sensor-split-core-type-clamp-sensor/ , also on Amazon.in. Lower range SCT-013-005 (5A) exists on Robu and is the better choice for a single power strip. ZMPT101B single-phase AC voltage sensor module: https://robu.in/product/ac-voltage-sensor-module-zmpt101b-single-phase/ **[search-result level, product pages]**
- Safety, stated plainly because it is a 230V mains project: the current clamp is non-contact and safe. The voltage channel is the risk. Two acceptable routes, both isolated: a ZMPT101B module (transformer-isolated by design) or the OpenEnergyMonitor-standard approach of a plug-in AC-AC step-down adapter feeding a divider. No exposed mains, no probing a live board by hand, all work on a switched extension board behind an RCD, and a faculty mentor sighting the wiring before it is energised. If the mentor is not comfortable, we fall back to a current-only build, which loses the true V-I trajectory and keeps current-harmonic features. That fallback costs accuracy and we would report it.

**Policy context (for the impact and national-SIH slides).** India's RDSS smart-meter programme targets roughly 250 million prepaid smart meters; reporting in 2026 puts installations at roughly 60 million to 150 million depending on the source and counting method, with the completion deadline extended from March 2026 to March 2028. Sources: https://genuspower.com/rollout-strategy-for-250-million-smart-meters-in-india/ , https://energy.prayaspune.org/power-perspectives/smart-metering-in-india-a-work-in-progress , https://kimbal.io/blog/rdss-scheme-state-wise-update/ **[search-result level, mixed industry and think-tank sources, figures disagree between them]**. *Honest handling:* the figures conflict across sources, so on the slide we say "tens of millions of smart meters already installed under RDSS, target 250 million, deadline now 2028" and cite the range rather than picking the flattering number. The load-bearing point does not depend on the exact count: those meters report aggregate kWh only, so appliance-level insight is a missing software layer on hardware that is already in the wall, and that is a real national-scale gap rather than a hypothetical one.

---

### Candidate B. PS-SH11, Smart Infrastructure Monitoring

**Papers found.**

1. **"Structural vibration measurement based on improved phase-based motion magnification and deep learning." Mechanical Systems and Signal Processing, 2024.** https://www.sciencedirect.com/science/article/abs/pii/S0888327024008434 **[search-result level]**
2. **"Motion magnification for video-based vibration measurement of civil structures: A review." Mechanical Systems and Signal Processing, June 2024.** https://www.sciencedirect.com/science/article/abs/pii/S088832702400579X **[search-result level]**
3. **Sarrafi, Mao, Niezrecki, Poozesh. "Vibration-Based Damage Detection in Wind Turbine Blades using Phase-Based Motion Estimation and Motion Magnification." arXiv:1804.00558.** https://arxiv.org/pdf/1804.00558 **[search-result level]**
4. **Emadi et al. "Application of Intelligent Low-Cost Accelerometers for Bridge Monitoring With a Deep Learning Approach." Structural Control and Health Monitoring, 2025.** https://onlinelibrary.wiley.com/doi/full/10.1155/stc/9835353 **[search-result level]**
5. **"Physics-Informed Neural Network based Damage Identification for Truss Railroad Bridges." arXiv:2502.00194, February 2025.** https://arxiv.org/pdf/2502.00194 **[search-result level]**

*Relevance assessment.* The genuinely separating idea here is not the accelerometer, it is **phase-based motion magnification**: process ordinary video through a complex steerable pyramid, amplify sub-pixel phase changes, and you get full-field vibration measurement from a smartphone with no contact and no instrumented points. The review literature reports optical measurement of displacements down to around three microns with high correlation against contact sensors. Pairing that with a cheap MEMS accelerometer gives something rare in a hackathon: two independent instruments measuring the same modal frequencies, so each one verifies the other. That is Vinay's "every generator gets a checker" expressed in physical instrumentation, and it is the single best thing about this candidate. The Emadi 2025 paper adds a second good idea, temporarily co-locating a reference sensor to train a low-cost one and then removing the reference, which is a clean story for why cheap hardware can be trusted.
*Downgrade reasons, honestly.* Three. First, the demo needs a physical test structure with a credible, reversible damage mode (a bolted lab-scale truss or a cantilever with an added mass or a loosened joint), and building and characterising that structure is itself a multi-day physical workstream in a category where we have no machine-shop slack. Second, cheap MEMS parts have a noise floor problem: an MPU6050 or ADXL345 is fine for a lab beam that moves visibly, and not fine for anything resembling a real structure, so the honest framing is strictly lab-scale and we have to say so. Third, and most important for this panel, faculty judges cannot sanity-check operational modal analysis, so a correct result and a plausible-looking wrong result score the same. That is a bad property when the thing being scored is confidence in the team.

---

### Candidate C. PS-SH12, NeuroWave RT (Live EEG Brain Analytics)

**Papers found.**

1. **LaBraM, the first large-scale EEG foundation model, pretrained on roughly 2,000 hours of EEG using patch-based transformers with vector-quantised neural tokenisation (ICLR 2024).** Overview: https://www.emergentmind.com/topics/labram **[search-result level]**
2. **"FEMBA: Efficient and Scalable EEG Analysis with a Bidirectional Mamba Foundation Model." arXiv:2502.06438, February 2025.** https://arxiv.org/pdf/2502.06438 **[search-result level]**
3. **"LEAD: An EEG Foundation Model for Alzheimer's Disease Detection." arXiv:2502.01678, February 2025.** https://arxiv.org/pdf/2502.01678 **[search-result level]**
4. **"Advancing Brainwave Modeling with a Codebook-Based Foundation Model." arXiv:2505.16724, May 2025.** https://arxiv.org/pdf/2505.16724 **[search-result level]**
5. Curated list of EEG foundation models with code: https://github.com/gayalkuruppu/eeg-foundation-models **[search-result level]**

*Relevance assessment.* On paper this is the highest-ceiling candidate in the bank. Real hardware that nobody can fake, a genuinely 2024-to-2026 technique (EEG foundation models did not exist before 2024), and a demo that stops a room. If it worked, nothing else on this list competes for spectacle.
*Why it is cut to conditional.* Two independent problems, and either one alone is disqualifying inside 9 days. **Sourcing:** we need an EEG headset physically in hand. OpenBCI ships from the US on multi-week lead times. A Muse S is roughly 25,000 to 30,000 INR with import and delivery risk inside our window. A DIY ADS1299 front end is weeks of work plus board bring-up. The only version of this that is real is if MIT Bengaluru's biomedical or ECE department already owns a working headset and will lend it, confirmed by 27 Aug, with the person who knows how to run it available. **Technical:** the foundation models above are pretrained on clinical montages with many channels, and adapting them to 4 dry consumer electrodes is a domain-shift research problem, not a fine-tune. The realistic 9-day EEG build is therefore ordinary bandpower features plus a classical classifier, which is a 2015-level project dressed in 2026 citations, and that is exactly the paper-that-does-not-cash-out failure we are trying to avoid. **Conclusion: only revisit if a headset is confirmed in hand before registration closes, and even then expect to drop the foundation-model angle.**

---

### Candidate D. PS-SH17, Muscle Strength Assessment Device

**Papers found.**

1. **"Physics-informed Deep Learning for Musculoskeletal Modelling: Predicting Muscle Forces and Joint Kinematics from Surface EMG." arXiv:2207.01435.** https://arxiv.org/abs/2207.01435 **[search-result level]**
2. **"Deep Muscle EMG construction using A Physics-Integrated Deep Learning approach." arXiv:2503.05201, March 2025** (also in Expert Systems with Applications). https://arxiv.org/abs/2503.05201 **[search-result level]**
3. **"Pareto-Optimal Model Selection for Low-Cost, Single-Lead EMG Control in Embedded Systems." arXiv:2601.06516, January 2026.** https://arxiv.org/pdf/2601.06516 **[search-result level]**
4. **"Physiologically Constrained Musculoskeletal Neural Network for Multi-DoF Joint Kinematics Estimation from Partially Observed sEMG." arXiv:2606.07476, June 2026.** https://arxiv.org/pdf/2606.07476 **[search-result level]**

*Relevance assessment.* The structurally elegant thing about this candidate is that ground truth is buyable. Put an sEMG electrode on the forearm and a 20 kg load cell with an HX711 in the grip, and the load cell measures the true force while the model estimates force from the muscle signal. The verifier is a physical object, which is unusually strong for a hackathon: you are not asserting accuracy, you are showing the residual live on screen. The 2026 Pareto paper is directly on-point for our constraints, using a roughly 12 dollar single-lead sensor on an ESP32 under real latency limits, which is exactly our budget and platform. The physics-informed line of work (2207.01435, 2503.05201, 2606.07476) supplies the differentiator: constrain the network with a Hill-type muscle model rather than regressing blind, so the estimate stays physiologically plausible and the parameters mean something.
*Downgrade reasons.* The "why didn't we have this before" test is where it loses. Hand dynamometers exist, cost about 2,000 INR, and measure grip strength directly and accurately, so a judge can reasonably ask why we inferred a number we could have measured. The honest answer (sEMG gives per-muscle contribution, fatigue onset, and works where a patient cannot grip a device at all) is a real answer but it is a rehabilitation-specialist answer, not a room-stopping one. Also: MyoWare-class sEMG is notoriously noisy with wet electrodes, skin prep, and cable motion artefacts, so demo-day reliability is a genuine risk on a body that is nervous and sweating.

---

### Candidate E. PS-SH18, Smart Spinal Cord and Pressure-Injury Monitoring

**Sources found.**

1. **"Smart Pressure e-Mat for Human Sleeping Posture and Dynamic Activity Recognition." arXiv:2305.11367.** https://arxiv.org/pdf/2305.11367 **[search-result level]**
2. **"Intelligent Medical Velostat Pressure Sensor Mat Based on Artificial Neural Network and Arduino Embedded System" (2023).** **[search-result level]**
3. **"Velostat-Based Pressure Sensor Matrix for a Low-Cost Monitoring System Applied to Prevent Decubitus Ulcers."** **[search-result level]**
4. **"Development of Low-Cost Fabric-Integrated Capacitive Pressure Sensors for Real-Time Pressure Monitoring and Ulcer Prevention." Sensing and Imaging, 2025.** https://link.springer.com/article/10.1007/s11220-025-00642-1 **[search-result level]**
5. **"Fabrication of Soft and Comfortable Pressure-Sensing Shoe Sole for Intuitive Monitoring of Human Quality Gaits." arXiv:2501.14193, January 2025.** **[search-result level]**

*Relevance assessment.* The strongest feasibility story of all five survivors, because we fabricate the sensor ourselves. A Velostat sheet between orthogonal strips of conductive copper tape gives an N by N piezoresistive matrix for roughly 1,500 to 2,500 INR, scanned by a multiplexer into any microcontroller. A 16 by 16 mat is a real afternoon of building, and "we made the sensor" is a genuinely differentiating sentence in a room of people who bought modules. The literature supports both the fabrication and the downstream ML (posture classification from pressure images).
*Downgrade reasons.* The clinical claim is the problem, and it is the same structural objection that killed the mental-health statements in the earlier pass: preventing a pressure injury is a claim you cannot demonstrate in a 10-minute demo and cannot measure in 9 days. What you can demonstrate is pressure-map visualisation and posture classification, which is honest but is a smaller claim than the PS title promises, and the gap between the two will be visible to the panel. Velostat also drifts and creeps under sustained load, which is well documented and would have to be disclosed.

---

### Candidate F (weak). PS-SH04, AI-Based Water Quality Monitoring

Not researched further. Probes are cheap and available (analog pH around 1,200 INR, turbidity around 700 INR), and hardware is genuinely load-bearing, but the "AI" reduces to threshold-plus-anomaly-detection on three slow-moving scalars, the demo is dipping a probe into dirty water and watching a number change, and the statement sits close enough to SH22 and SH01 in the environmental-IoT cluster to attract a crowd. Cut without a literature pass.

---

## Part 3: things deliberately not pursued, recorded so we do not rediscover them

- **PS-SH06 (assistive system)** is open-ended enough to allow almost anything, which sounds like freedom and functions as a trap: with no framing given by the statement, the default output is a smart cane or a gesture glove, both of which are heavily built and easily dismissed. If pursued at all it would need a specific, defensible device chosen first, and we do not have the days to converge on one.
- **PS-H01 and PS-H10 (Part C)** are the only two Part C statements that pass the sourcing test. H10 in particular overlaps SH02's sensing stack almost completely (vibration and current on a motor, edge anomaly detection), so if the category rule turns out to be looser than assumed, H10 is a near-zero-cost pivot from the SH02 build. Recorded as a fallback fact, not a recommendation.
- **PS-SH21** deserves one explicit sentence because it will attract someone: measuring neuronal magnetic fields requires SQUID or optically-pumped magnetometers and magnetic shielding. It is not buildable by anyone in this hackathon at any budget available to a student team, and any team presenting it will be presenting slides.

---

## Part 4: what the trail concludes

PS-SH02, framed as single-point NILM rather than as smart plugs, is the only candidate that is simultaneously: hardware-load-bearing under Test 1, sourceable inside 9 days from Bengaluru stock, aligned with the stack Vinay already works in (Python and PyTorch, edge firmware, FastAPI, Next.js), supported by 2024 to 2026 literature that a normal team will not know exists (event-based explainable high-frequency NILM, open-set unknown-appliance rejection), measurable against public benchmarks rather than self-defined scores (NILMTK, PLAID, WHITED), and attached to a live national policy gap (tens of millions of RDSS smart meters that report only aggregate kWh).

PS-SH11 is the strongest alternate on novelty and visual impact, and loses on physical build time and on the panel's inability to verify the result. PS-SH17 is the strongest alternate on verifiability, since the load cell is a physical ground truth, and loses on the "why didn't we have this before" test.

Full reasoning, scope, kill criteria and the build plan are in `../DECISION.md` and `../PLAN.md`.

---

## Part 5: awe-factor addendum (added 2026-08-25, after Vinay's pushback)

Vinay rejected the Kirchhoff pick as technically sharp but not dashing enough: a clamp reporting "fridge: on" does not make a judge sit up. **Awe factor** was added as an explicit fifth criterion alongside feasibility, differentiation, judge alignment and the crowd-magnet discount. No paper search was re-run; this is the awe lens applied on top of Parts 1 to 4, plus one new feasibility verification that turned out to decide the pick.

### The definition used

> A **visible, visceral, real-time moment a non-technical judge understands in under ten seconds with no explanation.** It must SHOW, not tell. Qualifying: live physical reaction, before-and-after reveal, invisible thing made visible, real human interacting on stage. **Disqualifying: a screen displaying a number or a classification label.**

Worth noting: the organiser wrote this criterion themselves before we did. "Build something that makes people ask, why didn't we have this before?" is the awe bar in their own words, which is the strongest evidence that revision 2 under-weighted it.

### The new verification that decided everything

The pivotal question was whether phase-based motion magnification can genuinely run **live on stage**, or only as a pre-recorded processed clip. If the latter, the awe is fake and PS-SH11 is dead. Checked before anything else. **It is real**, on three independent confirmations:

1. **Wadhwa, Rubinstein, Durand, Freeman. *Riesz Pyramids for Fast Phase-Based Video Magnification.* IEEE ICCP 2014.** https://ieeexplore.ieee.org/document/6831820/ **[search-result level, plus patent text US9338331B2]** The Riesz pyramid is 4 times overcomplete versus more than 21 times for the eight-orientation complex steerable pyramid it replaces, uses compact spatial-domain linear filters, and the Riesz transform is approximable by **two three-tap finite difference filters**. Stated purpose is real-time phase-based magnification, with output quality reported comparable to the steerable pyramid. The three-tap detail is what makes our own implementation realistic in the time available rather than a research project.
2. **`tschnz/Live-Video-Magnification`.** https://github.com/tschnz/Live-Video-Magnification **[full text checked, README read]** An OpenCV and Qt application running **from live cameras**, with three real-time modes: Motion (Laplace), **Motion (Phase) via Riesz pyramid**, and Color. Exposes adjustable processing resolution 1/1 to 1/8 specifically to trade live rate against quality; OpenGL 3.3 for display; C++20, Qt 6, OpenCV, FFmpeg. README states it drops camera frames under computational load and stops camera recording at 8 GB RAM. This is a working existence proof and our validation reference.
3. **`chrdiller/VideoMagnification`** (webcam streams, heartbeat detection) https://github.com/chrdiller/VideoMagnification and ***Real-time motion amplification on mobile devices*, arXiv:2206.08422** https://arxiv.org/pdf/2206.08422 **[search-result level]**

**Caveats found, all load-bearing for the plan rather than footnotes.** Phase-based Eulerian methods **assume stabilised capture and fail on handheld video**, since hand shake at 2 to 10 Hz sits inside the passband and gets amplified with the signal (stated in *Event-Based Motion Magnification*, arXiv:2402.11957, https://arxiv.org/html/2402.11957v2 **[search-result level]**). Tripod is mandatory. Live also means reduced processing resolution, so the honest claim is a measured framerate at a stated resolution, never a target. The temporal bandpass needs a buffered window, giving roughly a second of lag that must be in the demo script. Lighting matters and the passband must be tuned, which turned into the project's best idea rather than its worst problem (see Resonance Lock in `../DECISION.md`).

Future-scope references found in the same pass: *3D Motion Magnification: Visualizing Subtle Motions with Time-Varying Neural Fields* https://3d-motion-magnification.github.io/ and the event-camera paper above. Neither is built.

### Awe scoring of the survivors

| Candidate | Moment | Time to get it | Shows or tells | Human on stage | Verdict |
|---|---|---|---|---|---|
| **SH11** | Beam visibly motionless on the table, visibly swaying on screen; then one bolt loosened and the motion changes | ~2s, silent | **Shows.** Invisible made visible | Judge taps it themselves | **Highest** |
| **SH18** | Judge leans on a fabric mat, live body-pressure heatmap of their own body blooms | ~3s, silent | **Shows** | Their own body | **High** |
| **SH17** | Judge squeezes, force bar reacts; hidden gem is activation preceding force | ~5s, subtle part needs a sentence | Shows, but grip force is already visible | Their own hand | Medium-high |
| **SH02** | Judge plugs in their own charger, system says "unknown load, 4.8 W, signature recorded", learns it in 30s | ~25s with narration | **Tells.** A label on a screen | Their own object | Medium |
| **SH12** | Judge thinks, thing moves | ~2s | Shows | Yes | Highest in theory, no headset in hand |

### The honest Kirchhoff re-look (requested explicitly, and not forced)

Best available staging: hand the judge the clamp so they attach it themselves (no hidden switch), then "plug in anything you brought." Their charger. The system refuses to name it, reports the real power draw, learns it in thirty seconds, and names it on replug. A machine admitting ignorance in front of a room and then learning is a genuine moment.

Measured against the definition, it still fails. The judge is watching a screen print a label, and appreciating why "unknown" is impressive requires knowing that most systems would have confidently guessed wrong. That is a twenty-five second insight with narration, not a two second visceral hit. Two upgrades were tried and rejected: sonifying the current waveform adds a novelty a judge cannot interpret, and showing the raw waveform with the kettle spike arriving is still a screen showing a trace. **Awe is medium and cannot honestly be raised.** Kirchhoff keeps its wins on differentiation, rigour, feasibility certainty and policy path, and becomes the revert target.

### Two things the awe lens changed beyond the top pick

- **SH11's original "why not first" objection dissolved.** Revision 2 said faculty cannot sanity-check operational modal analysis, so a correct result and a plausible wrong one score the same. Under the awe lens the judge does not need to verify the modal analysis: they watch the beam move, watch a bolt loosen, watch the motion change. The video verifies for the non-specialist, the accelerometer agreement verifies for the specialist. One demo, two audiences, two independent paths.
- **SH18 was under-weighted and is promoted to Alternate 2.** A live full-body pressure map of a judge's own body is legitimately high awe, the sensor is fabricated by us for under 2,500 INR, there is no mains hazard and no lead time. It stays third only because the defensible claim (pressure visualisation and posture classification) is visibly smaller than the PS title promises, and Velostat drift and creep would have to be disclosed.

### Residual risk on the new pick, stated plainly

The "camera trick" objection is real: a judge may notice that motion magnification is an off-the-shelf effect with public implementations. The answer must be given before it is asked, and it is **Resonance Lock**, the closed loop where the accelerometer's identified modal frequency automatically sets the camera's magnification passband, plus the **full-field mode shape** that a single-point sensor physically cannot produce. We also state openly which parts of the pipeline are ours and which come from the reference implementation. Claiming we invented motion magnification would be exactly the dishonesty this whole method exists to prevent.
