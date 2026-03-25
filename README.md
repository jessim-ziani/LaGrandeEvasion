# La Grande Évasion - 3D Multiplayer Escape Game

## 📖 Project Context

**La Grande Évasion** is a first-year engineering project developed at EPITA. It is a 3D cooperative escape room game designed for 1 to 4 players. Players are trapped in a medical prison and must collaborate to solve puzzles, gather items, and evade an AI-controlled guard ("The Plague") to escape. 

**My Role:**
- Designed the game’s visual identity (logo, menus, overall UI)
- Created and textured selected 3D assets, and assembled the game map
- Implemented core gameplay systems: inventory, digicode, and in-game puzzles
- Implemented sound and music systems
- Assisted with character movement and controller logic

## 🏗️ Technical Architecture & Features

### 1. Multiplayer Network Engine (Photon PUN 2)
The game relies on a real-time online multiplayer architecture using Photon Engine.
* **Local Authority & Synchronization:** Networked objects (Players, AI, interactable doors/puzzles) are synchronized using `PhotonView` and `PhotonTransformView`. The `IsMine` property ensures that input processing and camera controls are strictly handled by the local client, preventing input overlap between players.
* **Remote Procedure Calls (RPCs):** Global game states, such as player death, inventory updates, and puzzle solving, are broadcasted across the network using `[PunRPC]`. For instance, if a player's health drops to zero, an RPC triggers the "Game Over" canvas and disables audio for all connected clients simultaneously.

### 2. Custom Character Controller
Developed a robust, physics-safe C# character controller from scratch.
* **Collision Management:** Replaced native Rigidbody forces with `transform.Translate` coupled with continuous Raycasting (`IsPathClear` function) to detect obstacles and prevent clipping or residual force accumulation when walking into walls.
* **Dynamic Animation Blending:** Player animations are driven by an Animator State Machine using float variables (e.g., walking, sprinting, strafing) calculated directly from the input axes, ensuring seamless transitions via Blend Trees.

### 3. Artificial Intelligence (NavMesh & State Machine)
The antagonist is driven by an autonomous AI that reacts to player presence.
* **Pathfinding:** Utilizes Unity's `NavMeshAgent` combined with `NavMeshModifiers` and `NavMeshLinks` to allow the AI to navigate complex geometry, including stairs and obstacles.
* **Sensory State Machine:** The AI operates on a `GuardState` enumeration (Patrol, Chase). It autonomously patrols waypoints (`UpdatePatrol()`) and switches to pursuit mode (`UpdateChase()`) if a player enters its red-light Field of View or generates noise (e.g., sprinting).

### 4. Synchronized Inventory & Puzzles
* **Networked Inventory:** Items picked up by a player trigger a raycast detection. An RPC is sent to allocate the item to the local player's UI slot and globally deactivate the item's GameObject across all clients (`DesactivateItem`), preventing item duplication.
* **Cooperative Puzzles:** Features complex, state-driven puzzles (e.g., rotating paintings, color-coded sequences) that require multiple players to interact simultaneously.

## 🎯 Installation & Demonstration

A pre-compiled Windows installer and its instruction manual are available for testing.

1. Go to the **[Releases](../../releases)** tab of this repository.
2. Download `La Grande Evasion 1.1 Setup (x64).exe` and the installation manual.
3. Run the setup and follow the manual's instructions to connect to the multiplayer server and play.

### Gameplay Overview

https://github.com/user-attachments/assets/8685f126-00c0-49c2-bbe8-20ad76577cee

## 👥 Contributors

This project was developed by a team of 4 EPITA engineering students.

<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="https://github.com/jessim-ziani">
          <img src="https://github.com/jessim-ziani.png" width="60px" style="border-radius: 50%;" alt="Jessim Ziani"/><br />
          <sub><b>Jessim Ziani</b></sub>
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/Wael-Akhdar">
          <img src="https://github.com/Wael-Akhdar.png" width="60px" style="border-radius: 50%;" alt="Wael Akhdar"/><br />
          <sub><b>Wael Akhdar</b></sub>
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/youcefzahra">
          <img src="https://github.com/youcefzahra.png" width="60px" style="border-radius: 50%;" alt="Youcef Zahra"/><br />
          <sub><b>Youcef Zahra</b></sub>
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/skylegend31">
          <img src="https://github.com/skylegend31.png" width="60px" style="border-radius: 50%;" alt="Ilann Oller"/><br />
          <sub><b>Ilann Oller</b></sub>
        </a>
      </td>
    </tr>
  </table>
</div>

---
**🛠️ Technologies:** C#, Unity, Photon PUN 2, Blender, Photoshop, Git.

