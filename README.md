# ⚡ 3-Phase AC Induction Motor Simulator

A high-fidelity, interactive 3D and 2D visualizer built to demonstrate the electromechanical physics of a 3-Phase AC Induction Motor (Squirrel Cage). 

Designed for electrical engineering students, academics, and industry professionals, this simulator runs entirely in the browser using pure JavaScript, HTML5 Canvas, and Three.js—requiring no backend or frameworks.

---

## 🌟 Key Features

### 🔧 Realistic Physics Engine
- **Accurate Telemetry:** Live calculations of Synchronous Speed ($N_s$), Rotor Speed ($N_r$), Slip, Developed Torque, Power Factor, Stator Input Power, and Efficiency.
- **Variable Frequency Drive (VFD):** Activate "V/f Mode" to dynamically scale stator voltage linearly with frequency to prevent magnetic saturation.
- **Dynamic Load Profiles:** Choose between realistic industrial load types:
  - *Linear* (Standard friction)
  - *Quadratic* (Fan/Pump fluid dynamics)
  - *Constant Torque* (Conveyors, Hoists)
- **Inertial Mass:** Adjust the rotor's mechanical inertia to observe realistic flywheel spool-up and coast-down times.

### 🎮 Interactive 3D Visualizations
- **Detailed Geometry:** A mathematically generated 3D model featuring finite squirrel-cage conductor bars, end rings, laminated stator/rotor cores, and isolated phase windings.
- **Cutaways & Inspections:** Toggle Exploded, X-Ray, Cross-Sectional, and Mag-Field views. Click any 3D component to cast a visual ray and read out its material properties and governing electrical formulas.
- **High-End Effects:** 
  - **Induced Currents:** Floating arrows speed along rotor bars visualizing induced $I_r$.
  - **Thermal Layer:** Visual color-grading mapping the motor's operating temperature to its physical mesh.
  - **Heat Distortion Haze:** A dynamic shader projects a refractive heat-wave mirage when temperatures exceed 80°C.
  - **Fault Sparks:** A particle system erupts with physics-based glowing sparks if extreme overload or temperature limits are exceeded.

### 📈 Live Telemetry Dashboards
- **Oscilloscope:** A 3-Phase instantaneous voltage and current waveform canvas featuring a reactive mouse-hover crosshair to decode exact instantaneous values.
- **Torque-Speed Characteristic:** Real-time plotting of the motor's operating point along the theoretical Kloss curve.
- **Phasor Diagram:** Live tracking of phase voltages ($V_a, V_b, V_c$) and lagging stator currents based on the real-time Power Factor ($\cos \phi$).
- **Current Vector Locus:** A Circle Diagram plotting the theoretical and instantaneous stator current magnitude and phase angle.

---

## 🚀 Getting Started

Since the entire application is bundled into a single file with CDN resources, there's no complex build process!

1. Clone or download this repository.
2. Ensure you have an active internet connection (to fetch `Three.js` from the CDN).
3. Double-click **`simulation .html`** to open it in any modern web browser (Chrome, Edge, Firefox, or Safari).

> **Note:** For the best visual experience and 60FPS simulation, running on a machine with hardware acceleration (a modern GPU) is highly recommended.

---

## 🛠️ Tech Stack & Dependencies

- **HTML5 & CSS3** (Custom glassmorphism UI, grid layouts, custom variables)
- **Vanilla JavaScript (ES6)** (Physics modeling, state-machine, event propagation)
- **[Three.js (r128)](https://threejs.org/)** (WebGL 3D engine, custom `ShaderMaterial`s, OrbitControls)
- **HTML5 Canvas API** (2D graphing logic and geometric data plotting)

---

## 📚 Technical & Mathematical Basis

The physics updates at 60Hz inside the main `requestAnimationFrame` loop, processing deterministic calculations:
1. $N_s = \frac{120 \times f}{P}$
2. $T_{dev} = \frac{3 \times V^2 \times R_2' / s}{\omega_s \left[ (R_1 + R_2'/s)^2 + (X_1 + X_2')^2 \right]}$ *(Approximated in-engine)*
3. $Slip = \frac{N_s - N_r}{N_s}$

### Exporting Data
If you need raw data for an assignment or lab report, click the **"Export CSV"** button in the header. The app will immediately compile the last 60 seconds of telemetry (storing at 10Hz) into a `.csv` file detailing Timestamp, Speeds, Slip, Torque, Efficiency, and Temperature!

---

## ⚖️ License
Feel free to fork, expand upon, or use this specifically for educational or personal projects!!
