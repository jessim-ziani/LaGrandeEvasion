# La Grande Evasion
*A 3D Puzzle & Horror Game developed in Unity.*


https://github.com/user-attachments/assets/62590c32-d57e-4676-9f93-a0a87d0314cc


---

> **Disclaimer:** This game was developed by a team of four students during our first year at EPITA. In accordance with the school's strict academic integrity and anti-plagiarism policies, the source code (C#) for this project is kept private. This repository serves as a technical and visual showcase. Code architecture and implementation choices can be discussed in detail during an interview.

## About the Project
"La Grande Evasion" is a 3D horror and puzzle game. The player must escape a medical prison patrolled by an artificial intelligence. The main objective is to explore the environment, solve mathematical equations, and decipher visual clues to unlock the final exit.

## Technical Features
To meet the academic requirements (developed in Unity using C#), several interactive systems were implemented:

* **Artificial Intelligence:** Pathfinding via NavMesh and a patrol system (State Machine) including player detection mechanics.
* **Interactive Environment:** Modular scripts (Raycasting) for inventory management (collecting keys) and environment manipulation (e.g., rotating paintings).
* **Dynamic Puzzles:** Puzzle logic coupled with an Event-driven system controlling dynamic lighting sequences.
* **Level Design & Atmosphere: Custom construction of the prison environment by assembling and texturing various 3D assets, combined with dynamic lighting configuration to build an oppressive atmosphere.

## Controls
```text
[Z] [Q] [S] [D] - Movement (AZERTY)
[SHIFT]         - Sprint
[E]             - Interact
