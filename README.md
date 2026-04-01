<div align="center">

# Farming Simulator 🌾

<img src="https://img.shields.io/badge/Unity-2019.4-000000?style=for-the-badge&logo=unity&logoColor=white" />
<img src="https://img.shields.io/badge/C%23-5%20Scripts-239120?style=for-the-badge&logo=csharp&logoColor=white" />
<img src="https://img.shields.io/badge/Platform-Desktop-lightgrey?style=for-the-badge" />
<img src="https://img.shields.io/badge/Genre-Simulation-22c55e?style=for-the-badge" />
<img src="https://img.shields.io/badge/Collab-Multi--Developer-f59e0b?style=for-the-badge" />

<br/>

*A 3D farming simulation game built in Unity — grow crops, manage inventory, and explore a handcrafted farm world with dynamic terrain, weather, and an inventory system.*

</div>

---

## Overview

A collaborative Unity farming simulation game where players manage a virtual farm. The game features a handcrafted 3D terrain, crop growth stages (saplings → medium → full corn), an item-based inventory system, weather effects (rain), and multiple game scenes including an intro, main farm, UI overlay, and the **Polam Purugu (Farm Worm)** terrain scene.

Built as a team project using **Unity Collaborate** for version control across multiple developers.

---

## My Contribution — Polam Purugu (పొలం పురుగు)

**"Polam Purugu"** (Telugu: *Farm Worm*) — I designed and built the `farmworm` scene, a dedicated terrain environment within the farming world:

- **Custom terrain sculpting** with road walls, tree barriers, and landscape boundaries
- **Camera system** for the farmworm exploration area
- **Environmental layout** — directional lighting, subtree placement, ground planes
- **Integration** with the main game's scene system alongside `MainGame`, `IntroScene`, and `GameViewUI`

---

## Architecture

```mermaid
graph TD
    A[IntroScene] -->|IntroScript.PlayGame| B[MainGame]
    B --> C[GameViewUI Overlay]
    B --> D[farmworm Scene]

    subgraph MainGame
        E[Farmer + Camera] --> F[Farm Terrain]
        F --> G[Crop Stages]
        G --> G1[plantstage-1 🌱]
        G --> G2[plantstage-2 🌿]
        G --> G3[Plantstage3 🌽]
        F --> H[MiniFarm Plots]
    end

    subgraph Inventory System
        I[ItemContainer] -->|ScriptableObject| J[ItemSlot]
        J --> K[ItemsScript]
        K -->|icon, stackable| L[InventoryButton]
        L --> M[InventoryPanel]
    end

    subgraph "Polam Purugu (farmworm)"
        D --> N[Custom Terrain]
        N --> O[Road Walls]
        N --> P[Tree Barriers]
        N --> Q[Ground Plane]
        N --> R[Camera + Lighting]
    end
```

---

## Game Flow

```mermaid
sequenceDiagram
    participant Player
    participant Intro as IntroScene
    participant Main as MainGame
    participant UI as GameViewUI
    participant Inv as Inventory

    Player->>Intro: Launch game
    Intro->>Main: PlayGame() → LoadScene
    Main->>UI: Overlay HUD (menu, user profile)
    Player->>Main: Explore farm terrain
    Player->>Main: Interact with crops
    Main->>Inv: Collect items → Add to ItemContainer
    Inv->>UI: Update InventoryPanel display
```

---

## Scripts

| Script | Responsibility |
|--------|---------------|
| `IntroScript.cs` | Loads the MainGame scene from the intro screen |
| `ItemsScript.cs` | ScriptableObject defining item properties (name, icon, stackable) |
| `ItemContainer.cs` | ScriptableObject managing a list of ItemSlots with add/remove logic |
| `InventoryButton.cs` | UI button for each inventory slot — displays icon and count |
| `InventoryPanel.cs` | Renders the full inventory grid from the ItemContainer data |

---

## Scenes

| Scene | Description |
|-------|-------------|
| `IntroScene` | Title screen with Play button |
| `MainGame` | Primary gameplay — farm terrain, crop stages, farmer movement |
| `GameViewUI` | HUD overlay — inventory, menu button, user profile |
| `farmworm` | **Polam Purugu** — custom terrain environment with roads and barriers |
| `test` | Development testing scene |

---

## 3D Assets

The project includes a rich set of 3D models and environmental assets:

- **Terrain** — Custom Unity terrain with mountain ranges and ground textures
- **Vegetation** — Corn crops, saplings (small/medium), trees (laxer tree package)
- **Structures** — House, walls, well, wooden props
- **Weather** — RainMaker particle system
- **Character** — Farmer character model
- **Tools** — Sickle for harvesting
- **Environment** — Skybox, ground texture packs

---

## Getting Started

1. Clone the repo
2. Open in **Unity 2019.4.x** (LTS)
3. Open `Assets/Scenes/IntroScene.unity`
4. Hit **Play** — click the play button on the intro screen to enter the farm

---

<div align="center">

Built collaboratively · Polam Purugu scene by [Akhila Susarla](https://github.com/Akhila-Susarla)

</div>
