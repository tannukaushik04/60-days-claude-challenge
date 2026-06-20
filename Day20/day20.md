# Day 20 – FaceBlocks AI Face Puzzle Game


Build and test **FaceBlocks**, an AI-generated browser-based face puzzle game that uses webcam capture, image processing, puzzle generation, drag-and-drop interactions, timers, move tracking, and local leaderboard storage.

---

## Project Overview

FaceBlocks converts a captured photo into a sliding puzzle game.

### Features

* Webcam photo capture
* Camera switching support
* Image-to-puzzle conversion
* Multiple difficulty levels

  * 3×3
  * 4×4
  * 5×5
* Drag-and-drop gameplay
* Touch support for mobile devices
* Timer tracking
* Move counter
* Local leaderboard
* Best-time records
* Responsive UI

---

## Screenshots

### 1. Camera Capture Stage

<img width="1082" height="1658" alt="face-puzzle1" src="https://github.com/user-attachments/assets/4153f628-9943-4fb4-a829-4433b615ad47" />


**Observations**

* Webcam permission requested successfully.
* Camera frame displayed.
* Photo capture button available.
* Privacy-friendly implementation as photos remain inside browser storage.

---

### 2. Difficulty Selection

<img width="1082" height="2508" alt="face-puzzle2" src="https://github.com/user-attachments/assets/7585b05a-3d83-43f1-bdb7-57dbe44b47e9" />


**Available Levels**

| Difficulty | Grid Size | Tiles |
| ---------- | --------- | ----- |
| Easy       | 3×3       | 9     |
| Medium     | 4×4       | 16    |
| Hard       | 5×5       | 25    |

**Selected Mode**

* Easy (3×3)

---

### 3. Puzzle Gameplay

<img width="1082" height="2284" alt="face-puzzle3" src="https://github.com/user-attachments/assets/a795ef62-5505-452a-b8b8-7c3c162453a5" />


### Performance

| Metric     | Result       |
| ---------- | ------------ |
| Time       | 26.0 seconds |
| Moves      | 6            |
| Grid       | 3×3          |
| Completion | Successful   |

---

## Game Mechanics Tested

### Camera Integration

Successfully tested:

* Webcam access
* Photo capture
* Camera switching

### Puzzle Generation

Successfully tested:

* Image slicing
* Tile generation
* Tile placement

### Interactions

Successfully tested:

* Drag and Drop
* Touch interactions
* Tile movement
* Puzzle validation

### Tracking System

Successfully tested:

* Timer
* Move counter
* Completion detection
* Best time recording


---

## Technical Concepts Learned

### Browser APIs

* MediaDevices API
* Camera access
* Image capture
* Canvas processing

### Game Development

* Puzzle generation
* Tile management
* Win condition detection
* State management

### Frontend Development

* Responsive design
* Event handling
* Drag-and-drop interactions
* Mobile touch support

### Local Storage

* Score persistence
* Leaderboard storage
* Session management

---

## Key Learnings

### 1. AI-Assisted Development

AI can generate complete browser applications including:

* UI design
* Business logic
* Browser integrations
* Game mechanics

### 2. Camera APIs

Learned how modern browsers allow:

* Webcam access
* Photo capture
* Device switching

### 3. Image Processing

Learned how images can be:

* Captured
* Split into tiles
* Rearranged dynamically

### 4. Game Logic

Implemented:

* Difficulty selection
* Move counting
* Time tracking
* Completion validation

### 5. Local Data Persistence

Used browser storage to:

* Save best scores
* Maintain leaderboards
* Track performance history

---

## Outcome

Successfully generated and tested the **FaceBlocks AI Face Puzzle Game**.

### Final Result

* Webcam Integration Tested
* Puzzle Generation Tested
* Drag-and-Drop Functionality Tested
* Timer & Move Counter Tested
* Leaderboard Working
* Puzzle Completed Successfully
* Responsive UI Verified
