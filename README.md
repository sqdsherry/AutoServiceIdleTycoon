# 🚗 Auto Service Tycoon — 3D Idle & Management Architecture Showcase

![Unity Version](https://img.shields.io/badge/Unity-6000.3.17f1%20URP-black?style=flat&logo=unity)
![Tests](https://img.shields.io/badge/EditMode%20Tests-325%20Passed-emerald?style=flat)
![Architecture](https://img.shields.io/badge/Architecture-Asmdef%20Layered%20%2B%20Pure%20DI-blue?style=flat)
![Dataflow](https://img.shields.io/badge/Dataflow-Zero--Alloc%20Struct%20EventBus-purple?style=flat)
![Assets](https://img.shields.io/badge/Assets-Kenney%20CC0%201.0-orange?style=flat)

<p align="center">
  <a href="https://youtu.be/9n1WJOhTLrE" target="_blank">
    <img src="https://img.youtube.com/vi/9n1WJOhTLrE/maxresdefault.jpg" alt="Watch Auto Service Tycoon Gameplay" width="100%">
  </a>
</p>
<p align="center">
  <b><a href="https://youtu.be/9n1WJOhTLrE">▶️ Watch Full Gameplay & Architecture Demo on YouTube (1:35)</a></b>
</p>
A production-ready 3D Idle / Management Tycoon prototype built in **Unity 6 (URP)**. Designed with enterprise-grade clean architecture, assembly-level decoupling (`.asmdef`), zero-allocation dataflows, pure C# dependency injection (Composition Root), and comprehensive automated test coverage (**325 EditMode unit tests**).

---

## 🎮 Core Gameplay Loop




* **Autonomous Traffic Flow**: Vehicles dynamically navigate a road graph, queue up at barriers, park, and enter assigned service bays.
* **Service & Station Operations**: Players and hired staff process vehicles across multiple stations (Wash Bays, Oil Change).
* **Logistics & Supplies**: Stations consume consumable crates. Players and hired warehouse workers restock stations based on prioritized demand.
* **Expansion & Upgrades**: Expand parking slots, unlock new service bays, hire workers, and unlock **Location 2 (Tuning Center)**.
* **Dynamic Customization**: Vehicles moving through the Tuning Center visibly alter their appearance (sports body kits, custom racing rims, dynamic paint jobs).

---

## ⚡ Quick Evaluation Guide (F1 In-Game Cheat Console)

To evaluate the entire progression and architecture in **under 2 minutes**, a custom Debug Console is built-in:

1. Hit **Play** (starts via `Boot` scene setup). Select **New Game** $\to$ Press **`F1`** (or the on-screen `F1` button).
2. Click **`+$10,000`**, then click **`+1 Level`** three times to instantly unlock progression gates.
3. Build new bays on Location 1, step onto the blue interaction pads to hire automated staff and buy station upgrades.
4. Click **`Teleport: Location 2`** to immediately transition to the Tuning & Customization Center.
5. Construct **Tires, Tuning, and Paint bays** to observe real-time vehicle mesh and material modifications.
6. Press **`Esc` $\to$ Main Menu $\to$ Continue**: Verify that persistence properly restores wallet balances, level progression, active staff, and constructed plots.
7. *(Optional)* Click **`Reset Progress`** in the F1 console to wipe save data and restart clean.

---

## 🏗️ Architecture & Engineering Design

The codebase (`Assets/_Project/Scripts`) enforces strict **Assembly Definition (`.asmdef`) boundaries**:

```text
Presentation ────► Services ────► Domain (No UnityEngine)
Infrastructure ──► Services, Domain (Implements service contracts)
Bootstrap ───────► All (Composition Root)
