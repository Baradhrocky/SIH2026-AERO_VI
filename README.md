<div align="center">
  <h1>🚁 AEROCUE: Autonomous SAR Drone</h1>
  <p><strong>Offline, zero-network Edge AI delivering real-time survivor detection and aerial reconnaissance directly to the disaster zone.</strong></p>
  <p><i>Smart India Hackathon 2026</i></p>
</div>

---

## 🚀 Quick Links for Evaluators
> **Note to Evaluators:** Click the links below to view our project demonstration, live web dashboard, and technical documentation.
- [🌐 **Live Rescue Headquarters Dashboard**](#) *(Insert Vercel/Website link here)*
- [🎥 **Video Demonstration**](#) *(Insert YouTube/Drive link here)*
- [📄 **Technical Project Report (PDF)**](#) *(Insert file link here)*
- [📊 **SIH Presentation Deck**](#) *(Insert file link here)*

---

## ⚠️ The Problem: The Golden 72 Hours
During the critical **Golden 72 Hours** of a disaster, response teams suffer severe operational delays due to dangerously slow manual foot sweeps, total communication blackouts, and visual blindness in GPS-denied ruins, resulting in a high rate of preventable casualties.

* **The 72-Hour Bottleneck:** Ground rescue squads lose critical operational time conducting hazardous sweeps across unstable perimeters before victims succumb to injuries.
* **Total Sensor & Telemetry Failure:** Heavy smoke and darkness render optical cameras blind, while the collapse of cellular towers and GPS satellites causes drones to drift uncontrollably.
* **Prohibitive Cost Barrier:** Existing enterprise SAR drones cost upwards of ₹8,00,000, making rapid-response fleets impossible for local disaster units to deploy at scale.

---

## 💡 Our Solution: Key Features
AEROCUE is an indigenous, field-ready autonomous rescue drone that bypasses infrastructure failures using on-device processing and multi-spectral sensors, linked directly to a local web command center.

1. **Edge-Based Multi-Spectral Triage:** Detects and localizes human survivors through dense smoke and complete darkness by running quantized INT8 neural networks directly on the companion computer, within 150 milliseconds.
2. **Sub-Surface Acoustic Distress Detection:** Directional MEMS microphones employ real-time noise-cancellation filters to isolate human screams and structural pipe-tapping beneath rubble from drone propeller wash.
3. **GPS-Denied Autonomous Navigation:** Visual Inertial Odometry combines downward optical flow and micro-LiDAR data to automate centimeter-level station keeping and prevent drift inside collapsed concrete ruins.
4. **Live Command Center Web Dashboard:** Encrypted, lightweight MAVLink telemetry is broadcast over a 10 km radius via Sub-GHz LoRa directly to our custom web application. Ground medics can use this interface offline to view mapped survivor coordinates, emergency signals, and P1-P3 triage tags in real time.

---

## ⚙️ System Architecture Flow

```mermaid
graph TD
    classDef main fill:#1e3a8a,stroke:#fff,stroke-width:2px,color:#fff;
    classDef sub fill:#3b82f6,stroke:#fff,stroke-width:1px,color:#fff;
    classDef output fill:#10b981,stroke:#fff,stroke-width:1px,color:#fff;

    A[Multi-Spectral Aerial Sensing]:::main --> B{Parallel Onboard Edge Processing}:::main
    
    B --> C(Navigation Stack: ArduPilot & VIO):::sub
    B --> D(Vision Engine: Quantized INT8):::sub
    B --> E(Acoustic DSP: Rotor Noise Filter):::sub
    
    C --> F[Casualty Triage & Coordination Logic]:::main
    D --> F
    E --> F
    
    F -->|Assigns P1-P3 Priority Tags| G{Zero-Bandwidth Tactical Output}:::main
    
    G --> H[10 km Sub-GHz LoRa Broadcast]:::output
    G --> I[React/Node.js Rescue Dashboard]:::output
    G --> J[Autonomous Return-to-Safe-Hover]:::output
