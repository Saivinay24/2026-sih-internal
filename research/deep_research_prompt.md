# Deep research prompt: Chladni (PS-SH11, camera-based structural health monitoring)

Paste everything below into Claude's deep research mode.

---

I'm building a structural health monitoring system for a national-level student hackathon (Smart India Hackathon 2026, India). The problem statement asks for a sensor-based system that monitors structural health of bridges, buildings, or roads by detecting stress, vibration, or wear indicators, and flags maintenance needs before critical failure. I have 6 to 7 real build days and a hardware budget under 4,000 INR (roughly 50 USD).

## What I've already decided, so you don't need to re-derive it

The core idea: a contact accelerometer (ESP32 + MEMS accelerometer) on the structure identifies its actual modal (resonant) frequencies. Those frequencies then automatically tune the passband of a live, camera-based phase-based video motion magnification pipeline (Eulerian/Riesz-pyramid style), which visualises the structure's vibration mode shape in real time from a tripod-mounted camera with no contact and no markers. I'm calling the sensor-to-camera coupling "Resonance Lock." The two instruments (accelerometer and camera) independently measure the same modal frequency shift when damage (a loosened bolt, or added mass) is introduced, and their agreement is the validation.

I already know phase-based motion magnification is real and has working real-time open-source implementations (Wadhwa et al. 2014 Riesz Pyramids paper; `tschnz/Live-Video-Magnification`), and that recent (2024-2025) structural-engineering literature applies it to vibration measurement of beams and bridges. I don't need you to re-find those basics.

## What I actually need from you, and why

I need to be certain this is a real engineering contribution with a genuine deployment path, not a demo trick dressed up as one. The panel judging this will include engineering faculty, and the project needs to survive the question "what is this actually good for, beyond looking cool on stage." Please do the following, and be skeptical and honest throughout, not encouraging by default. I would much rather hear "this doesn't hold up" now than find out on stage.

1. **Find the actual state of the art (2024-2026) in vision-based / non-contact structural health monitoring**, beyond phase-based motion magnification specifically. Who is doing this in real deployed infrastructure right now (not lab demos)? Companies, government infrastructure programs, published field studies. Is there prior art that already does exactly what I'm describing, and if so, how is it deployed and what does it cost?

2. **Stress-test the "sensor-to-camera coupling" idea specifically.** Is closing the loop from an accelerometer's identified modal frequency to a camera's magnification passband a genuinely novel combination, or is this a known technique under a different name (e.g. in operational modal analysis, video-based OMA, or multi-sensor fusion for SHM)? I want to know if I'm about to present something as novel that a judge with domain knowledge will recognize as standard practice. Find the closest prior art and tell me honestly how much daylight is actually between it and what I'm proposing.

3. **Validate or kill the real-world use case.** India specifically has a large stock of ageing bridges and buildings that are currently inspected primarily by visual/manual methods rather than instrumented monitoring. Find real data or reporting on: how structural inspection is actually done in India today, what it costs, what the failure/collapse incident rate looks like, and whether there is a real, currently-unmet gap that a low-cost non-contact vibration-monitoring method could plausibly address. I don't want a vague "infrastructure monitoring is important" framing, I want a specific, defensible claim I can put on a slide with a citation, or an honest "this gap doesn't actually exist / is already well served" if that's what you find.

4. **Find the real limitations and failure modes I need to disclose proactively**, not have exposed by a judge's question: measurement range and sensitivity limits of camera-based methods versus direct contact sensors on large real structures (not lab-scale beams), lighting/environmental robustness, what happens outdoors or in wind, how this compares in accuracy and cost to existing structural health monitoring hardware (strain gauges, fiber optic sensors, wireless accelerometer networks like those used in real bridge monitoring deployments), and where camera-based methods are known to fail or mislead.

5. **Find the strongest 2-3 pieces of very recent (last 12 months if possible) research** that would let me push past what a typical hackathon team would find, specifically anything that: improves robustness of phase-based magnification outdoors or under real structural (not lab) conditions, combines vision-based and contact-sensor SHM in a genuinely fused (not just side-by-side) way, or applies this to real bridge/building monitoring rather than lab specimens.

6. **Give me an honest verdict**, structured as: (a) is the core technical idea sound and at least somewhat novel, or derivative of known work, (b) is there a real, citable, currently-unmet use case in structural inspection this could plausibly address, even at a "future scope beyond this hackathon" level, (c) what is the single strongest true claim I can defend under hostile questioning from an engineering faculty judge, and (d) what is the single weakest point I should either fix or openly disclose before someone else finds it.

Cite everything with real, checkable sources (papers, links, dates). If a claim can't be sourced, say so explicitly rather than stating it as fact. I would rather have three honestly-verified findings than ten unverified ones.
