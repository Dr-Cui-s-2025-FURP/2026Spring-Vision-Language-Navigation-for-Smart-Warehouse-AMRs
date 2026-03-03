# Vision-Language Navigation for Smart Warehouse AMRs


---

## 📖 1. Project Background & Overview (Start Here)

### 1.1 What are AMRs and How Do They Move?

Imagine a massive modern warehouse (like those operated by Amazon or Alibaba). Inside, there are hundreds of **Autonomous Mobile Robots (AMRs)** moving goods around. Traditionally, these robots are "blindly obedient." They navigate using fixed, pre-calculated coordinate points ($X, Y$) or virtual "tracks" encoded into their systems. If you want a traditional AMR to move to a shelf, you cannot tell it, *"Go to the second shelf on the left near the blue forklift."* Instead, a central computer must translate that location into absolute map coordinates (e.g., `Goal: [15.2, -4.5]`). This is rigid, struggles with dynamic environments (things moving around), and is very unfriendly to human-robot interaction.

### 1.2 Entering Vision-Language Navigation (VLN)

To make robots truly intelligent collaborative partners, they need to understand human language and connect it to what they "see." This is called **Vision-Language Navigation (VLN)**.
VLN is a cutting-edge AI paradigm. It gives the robot a "Brain" (Large Language/Vision Models) to process a natural language instruction from a human, use its "Eyes" (cameras/sensors) to look at the environment, and figure out exactly *where* it needs to go and *how* to get there without needing exact coordinates.

### 1.3 The Simulation-First Approach (Why ROS 2, Nav2, and Isaac Sim?)

Testing untested AI models on real, heavy, moving robots is dangerous and expensive. Therefore, modern robotics relies on **High-Fidelity Simulation**—essentially putting the robot in "The Matrix" before bringing it into the real world.
In this project, you will build a complete digital-twin workflow using industry-standard tools:

- **ROS 2 (Robot Operating System 2):** Think of this as the "nervous system." It handles communication between the robot's sensors, motors, and brain.
- **Nav2:** This is the "GPS and Steering Wheel." Once given a destination, it calculates the best path and avoids obstacles.
- **NVIDIA Isaac Sim:** This is the "Virtual World." It provides photorealistic physics and environment simulation so the robot thinks it is in a real warehouse.

### 1.4 Your Mission

Your ultimate goal is to build an end-to-end simulated navigation pipeline. First, you will build the baseline navigation system (ROS 2 + Nav2 + Isaac Sim). Then, you will integrate a powerful VLN Large Model to act as the "translator"—turning human text into navigation goal points for Nav2. Finally, for those who master the simulation, you will have the rare opportunity to deploy your code onto a **physical laboratory robot**!

---

## 🎯 2. Research Objectives

| Priority           | Objective                                                                                                            |
| ------------------ | -------------------------------------------------------------------------------------------------------------------- |
| **Primary**  | Build a reproducible, simulation-based navigation pipeline using ROS 2, Nav2, and NVIDIA Isaac Sim.                  |
| **Primary**  | Integrate a pre-trained VLN model to generate navigation goal points dynamically from natural-language commands.     |
| **Primary**  | Quantitatively evaluate navigation success rate, path efficiency, and language grounding accuracy in the simulation. |
| **Extended** | Transfer and validate the VLN-augmented navigation system on a real laboratory AMR platform.                         |

---

## 🗺️ 3. Project Milestones (9 Nodes)

This project is meticulously divided into three phases: Introduction, Reproduction, and Innovation.

### Phase 1: Onboarding & Foundations (Introduction 1/3)

*Objective: Build foundational knowledge and set up the computational environment.*

- [ ] **Node 1: Simulation Environment Setup**
  - Install and configure ROS 2, Nav2, and Isaac Sim on your development machine.
  - Spawn a warehouse-like scene in Isaac Sim.
  - *Deliverable:* A short screen-capture video demonstrating a live ROS 2 topic stream from the simulated robot.
- [ ] **Node 2: Literature Review & Model Selection**
  - Conduct a structured survey of VLN research (minimum 4-5 peer-reviewed papers).
  - *Deliverable:* A written literature review (≥ 800 words, academic English) justifying the choice of the VLN backbone model.
- [ ] **Node 3: Baseline Navigation (Coordinate-based)**
  - Implement a traditional point-goal navigation task (using specific coordinates) in simulation using Nav2 to ensure the physics and path-planning work.
  - *Deliverable:* Experiment log calculating success rate over 10 trials.

### Phase 2: Reproduction & Integration (The Core Work 1/3)

*Objective: Connect the AI model with the Robotic constraints to reproduce baseline autonomous behaviors.*

- [ ] **Node 4: VLN Model Deployment & Testing**
  - Download the selected VLN backbone model; test inference on standard benchmark data (bypassing the robot for now).
  - *Deliverable:* Inference demo script in Python.
- [ ] **Node 5: VLN–Nav2 Interface Bridge Designer**
  - Design a ROS 2 node that specifically accepts text input, sends it to your VLN model, converts the model's output into a spatial coordinate, and feeds it to Nav2.
  - *Deliverable:* Software architecture diagram and working ROS 2 package script.
- [ ] **Node 6: Integrated Simulation Evaluation**
  - Construct a suite of ≥ 15 language-conditioned navigation trials (e.g., "Go to the shelf with red boxes"). Let the robot run autonomously.
  - *Deliverable:* Middle-term evaluation report analyzing success rates and failure cases.

### Phase 3: Innovation & Deployment (The Research Frontier 1/3)

*Objective: Develop new ideas, implement optimizations, and deploy to physical hardware.*

- [ ] **Node 7: System Optimization Proposal**
  - Identify a limitation in Node 6 (e.g., the robot gets confused by synonymous words or complex obstacles). Propose and code a targeted improvement.
  - *Deliverable:* Ablation study report.
- [ ] **Node 8: Final Simulation Result Compilation**
  - Consolidate all experiments, trajectory plots, and data into a clean, academic format.
  - *Deliverable:* Final Simulation Report (ready for poster conversion).
- [ ] **Node 9: Real-Robot Deployment (Ultimate Boss)**
  - Transfer the VLN-augmented navigation stack to the physical lab robot. Address the "sim-to-real gap" (sensor noise, network latency).
  - *Deliverable:* Live demonstration video and a deployment guide markdown file.

---

## 🎓 4. Evaluation & Certificate Requirements

To successfully complete this FURP project and receive the official participation certificate, students **must** meet the strictly enforced criteria below:

1. **Milestone Completion**: Successfully complete, push code for, and pass at least **50% of the project milestones (5 out of 9 Nodes)**.
2. **Poster Submission**: Submit a formal academic poster summarizing your methodology and simulation results to the annual **FURP Showcase event** at the end of the academic year.
3. **Repository Standard**: All evaluations are strictly based on your GitHub repository. Commit history is proof of work.

---

## 🗂️ 5. Repository Structure Requirements

Students must create a personal repository within the designated GitHub Organization named strictly as `FirstnameLastname-VLN`. Keep the structure exactly as follows:

```text
FirstnameLastname-VLN/
├── README.md                    # Project introduction 
├── docs/                        # Literature reviews, interface designs, reports
├── logs/                        # Weekly work logs (e.g., logs/2026-03-10.md)
├── src/                         # All source code (ROS 2 workspaces, VLN inference)
├── data/                        # Experiment metrics, bag files, datasets
├── assets/                      # Evaluation figures, diagrams, and videos
└── poster/                      # Final FURP Showcase poster (PDF + Source)
```
