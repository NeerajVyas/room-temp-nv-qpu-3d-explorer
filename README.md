# Portable Room-Temperature NV-Diamond Quantum Computer: 3D Explorer
An interactive 3D model, built with Three.js, of a portable quantum computer that uses nitrogen-vacancy (NV) centres in diamond as qubits and runs at room temperature (293 K).
Interactive 3D portable room-temperature NV-diamond quantum computer: hardware view, X-ray laser-beam view, atomic NV lattice, and a Qiskit program journey. Illustrative model.


> **Illustrative model.** This shows a *typical* NV-diamond machine. It is not the design of any specific company or product, and it is not affiliated with any hardware vendor.

## What you can do

- **Two view modes**
  - *Real-World Hardware View:* black steel rack, stainless breadboard with M6 holes, kinematic mirror mounts, brass lens barrel, copper/gold microwave loop, coax cables, cooling fans, and an external monitor, keyboard and mouse.
  - *X-Ray / Laser Beam View:* semi-transparent chassis with the 532 nm laser beam, 45° mirror reflections, microwave pulses and red fluorescence photons lit up.
- **Click any component** (laser, 45° mirrors / dichroic, optical switch, convex lens, quantum core, red filter + detector, electronics + control PC, PSU + fans). The camera flies to it and opens a 7-point card: Info, Before / During / After a program run, Why, Fault tolerance, Life.
- **Click the diamond** (or use the dive button) to enter the atomic lattice: carbon lattice, nitrogen atom, vacancy, trapped electron spin and carbon-13 nuclear spins, plus a toggle for 2 cores × 4–5 qubits vs a 4 cores × 30 qubits roadmap.
- **Mode 2, program journey:** a Qiskit Bell-state program (`h`, `cx`, `measure_all`, 1024 shots) is followed through the machine: typing and submitting, laser initialisation, microwave gate pulses, readout, and the final histogram.

## Run it

Open `index.html` in a modern browser. No build step is needed.
Three.js (r128) and OrbitControls load from the jsDelivr CDN, so an internet connection is required.

Controls: drag to rotate, scroll or pinch to zoom, right-drag to pan, `Esc` to go back.

## Data and accuracy notes

- **Simulated values:** photon rate, shot counter, and the Bell-state histogram (00: 50.4%, 11: 49.6%) are simulated for illustration. Nothing is read from real hardware.
- **Figures from the author's brief, not independently verified:** 1-qubit fidelity 99.995%, 2-qubit fidelity 99.93%, 8–10 qubits (2 cores × 4–5), the 120-qubit roadmap figure, laser lifetime of about 10,000–20,000 hours, "effectively infinite" NV lifetime, and 50,000+ hour electronics lifetime.
- **Materials:** items marked *Confirmed* were stated as confirmed in the brief; items marked *Probable* are typical NV-diamond practice, not a published parts list.
- **Layout:** the position of every part, including the detector behind the dichroic mirror, is a plausible teaching layout, not a known design.

## Tech
Three.js r128 · OrbitControls · plain HTML/CSS/JS in a single file
