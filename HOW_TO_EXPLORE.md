# How to Explore the 3D Model

A step-by-step guide to using the Portable Room-Temperature NV-Diamond Quantum Computer explorer. Open `index.html` in a browser and follow along.

## 1. Moving around (works everywhere)

| Action | Mouse | Touch |
|---|---|---|
| Rotate | Left-drag | One-finger drag |
| Zoom in / out | Scroll wheel | Pinch |
| Pan | Right-drag | Two-finger drag |
| Go back to the full system | **⬅ BACK TO FULL SYSTEM** button, or `Esc` | Button |

Tips:
- Zoom in close to a part to see its detail. Floating name tags fade out when you get close, so they do not cover the hardware.
- Hover over a part (mouse) and it glows with its name. Click it to fly to it.
- You can rotate and zoom at every stage, including inside the diamond.

## 2. The top bar

The bar at the very top always shows the machine summary: dual-core NV-diamond QPU, 2 cores × 4–5 qubits (8–10 physical qubits), 293 K room temperature, 600 W AC power.

Below it are two switches:

- **Mode 1: Hardware & Atomic Explorer** (default): click parts, read the cards, dive into the crystal.
- **Mode 2: Journey with Program Execution (Python Qiskit)**: watch one program run through the machine.

## 3. The two views

Switch with the toggle at the top right.

**📷 Real-World Hardware View**
How the hardware would look: black steel rack with the front and top open, stainless breadboard with mounting holes, mirror mounts, brass lens barrel, copper and gold microwave loop, coax cables, fans, and the monitor, keyboard and mouse on the desk. Beams are hidden here.

**🔬 X-Ray / Laser Beam View**
The chassis turns almost transparent so you can see what light and signals do:
- green 532 nm laser beam through the optical switch, two 45° mirrors and the lens onto the diamond
- microwave pulses travelling along the cable to the gold antenna
- red fluorescence photons (637–750 nm) returning through the lens, the dichroic mirror and the red filter to the detector
- magnetic field lines around the diamond

Try the same part in both views: for example, fly to the quantum core in Real-World view, then switch to X-Ray view and watch the beams appear.

## 4. Clicking components (Mode 1)

Click any of these: laser, 45° mirrors / dichroic, optical switch (AOM), convex lens, quantum core, red filter + detector, electronics + control PC (with monitor, keyboard, mouse), 600 W PSU + fans.

The camera flies to the part and a 7-point card opens:

1. **Info:** what it is, with Confirmed vs Probable materials
2. **Status before** program execution
3. **Status during** program execution
4. **Status after** program completion
5. **Why** it is needed
6. **Fault tolerance**
7. **Life** (expected lifetime)

Close the card with **✕ Close**. Use **⬅ BACK TO FULL SYSTEM** to return to the full view.

## 5. Diving into the diamond (atomic view)

Click the diamond chip, press **🔬 DIVE INTO ATOMIC NV LATTICE**, or use the dive button in the Quantum Core card. The screen flashes and you are inside the crystal:

- **Grey-blue lattice:** carbon atoms and bonds
- **Purple sphere:** the nitrogen atom
- **Wireframe sphere next to it:** the vacancy (empty carbon site) with dashed dangling bonds and a small electron spin cloud
- **Amber and cyan spheres:** carbon-13 nuclear spins, linked to the nitrogen by faint lines. These act as extra memory qubits.

Use the toggle at the top right of the screen:
- **Gen 3 Dual-Core (2026):** 2 cores × 4–5 qubits = 8–10 qubits
- **Roadmap scaling:** 4 cores × 30 qubits = 120 qubits

Press **⬅ BACK TO FULL SYSTEM** to fly back out to the cabinet.

## 6. Program journey (Mode 2)

Switch to **Mode 2**. The view changes to X-Ray automatically. A Qiskit console appears on the left with this program:

```python
from qiskit import QuantumCircuit
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
qc.measure_all()
result = backend.run(qc, shots=1024).result()
```

Press **▶ RUN QISKIT PROGRAM (AUTOPLAY)**. The camera tours the machine by itself (about 70 seconds). The current code line is highlighted, and the three Journey boxes light up as you go. A status line and a caption explain each step.

**Journey 1: Before execution (STATUS: INITIALIZING)**
1. Desk: the script is typed on the keyboard and shown on the monitor.
2. The script goes over USB into the control PC in the electronics bay.
3. The green laser passes the open switch, the two 45° mirrors and the lens.
4. The lens focuses the beam onto the diamond.
5. Inside the lattice, the electron spin is pumped into |0⟩.

**Journey 2: While executing (STATUS: GATE PULSES ACTIVE)**
6. The optical switch blocks the laser (its tag turns red). The AWG and microwave amplifier fire pulses. The shot counter starts.
7. Pulses travel the cable into the gold loop antenna.
8. Inside the lattice, superposition forms and the electron entangles with the carbon-13 spins. The counter runs up to 1024 shots.

**Journey 3: After completion (STATUS: READOUT & RESULT CHECK)**
9. The readout laser turns on and hits the diamond.
10. Red photons return through the lens, the dichroic mirror and the red filter to the single-photon detector.
11. The monitor shows the Bell-state histogram (00 about 50.4%, 11 about 49.6%) and a Before / During / After summary table appears.

Press **BACK TO FULL SYSTEM** at any time to stop the tour. Press **▶ RUN AGAIN** to replay it. You can still rotate and zoom with the mouse, but the tour will keep moving the camera to the next step.

## 7. Suggested exploring order

1. Mode 1, Real-World view: rotate around the whole rack.
2. Switch to X-Ray view: see the beams.
3. Click the two mirrors and read why two are needed.
4. Click the quantum core, then dive into the diamond.
5. Back out, switch to Mode 2 and run the Qiskit journey.

## 8. Good to know

- The histogram, shot counter and photon rate are simulated. Nothing comes from real hardware.
- Some figures (fidelities, qubit counts, lifetimes) come from the author's brief and are not independently verified.
- The layout is an illustrative typical design, not a specific company's.
- An internet connection is needed because Three.js loads from a CDN.
