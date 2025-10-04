# 🎮 Tic-Tac-Toe Game (AI + 2P)

A modern web-based **Tic-Tac-Toe** game built using **HTML, CSS, and JavaScript**, featuring:
- Player vs Player  
- AI with three difficulty levels (Easy, Medium, Hard using Minimax)  
- Intelligent decision-making  
- Dark/Light mode toggle and responsive UI  

---

## Overview

This project demonstrates **core Computer Science concepts** and **Data Structures & Algorithms (DSA)** principles in a fun, interactive setting.  
It simulates both **human and computer gameplay**, integrating **game trees, recursion, arrays, and decision optimization**.

---

## Features

| Feature           | Description                                                       |
|-------------------|-------------------------------------------------------------------|
| Game Modes        | 2-Player, Vs Computer (Easy, Medium, Hard)                        |
| Hard Mode         | Uses **Minimax Algorithm** (with recursion) for “Hard” difficulty |
| Medium Mode       | Mix of **heuristic move prediction** and fallback randomness      |
| Easy Mode         | Random valid moves (demonstrating uniform random selection)       |
| Score Tracking    | Maintains wins, draws, and streaks                                |
| Turn Timer        | Each player gets a countdown timer to make their move             |
| Theme Switch      | Dark/Light mode with CSS transitions                              |

---

## DSA & CS Fundamentals Demonstrated

### 1. **Array Representation of Game State**
The `board` is implemented as:
```js
board = Array(9).fill(null);
```
- Represents a **1D array** abstraction of a **3×3 matrix**.
- Demonstrates **mapping between 2D coordinates and 1D indices**.
- Enables **O(1)** access for cell updates and checks.

---

### 2. **Pattern Matching with Predefined Winning States**
```js
const winPatterns = [
  [0,1,2],[3,4,5],[6,7,8],
  [0,3,6],[1,4,7],[2,5,8],
  [0,4,8],[2,4,6]
];
```
- Encodes **winning combinations** using a **list of arrays (array of tuples)**.  
- Demonstrates **pattern checking algorithms** with constant-time lookups.  
- Used in `checkWinner()` and `isWinner()` functions for **pattern recognition**.

---

### 3. **Recursion and Game Tree Search (Minimax Algorithm)**

The **Minimax algorithm** recursively explores possible game states:
```js
function minimax(newBoard, player) {
  const avail = newBoard.map((v,i)=>v?null:i).filter(v=>v!==null);
  if (isWinner('X')) return {score: -10};
  if (isWinner('O')) return {score: 10};
  if (avail.length === 0) return {score: 0};

  const moves = [];
  for (let i of avail) {
    const move = { index: i };
    newBoard[i] = player;
    const result = minimax(newBoard, player === 'O' ? 'X' : 'O');
    move.score = result.score;
    newBoard[i] = null;
    moves.push(move);
  }
  ...
}
```
#### Concepts Illustrated:
- **Recursion:** explores all future game states.
- **Backtracking:** resets board state after each simulation.
- **Game Tree Traversal:** decision-making through depth-first exploration.
- **Optimization:** selects maximum or minimum score depending on the player.

This models **AI decision-making** using **deterministic minimax search**, a cornerstone of **Artificial Intelligence** and **Game Theory**.

---

### 4. **Heuristic Evaluation and Greedy Selection (Medium Mode)**

```js
move = findWinningMove('O') || findWinningMove('X') || randomMove();
```
- Demonstrates a **greedy heuristic approach**.
- Prioritizes **winning move**, then **blocking move**, else **random**.  
- Mirrors **real-world AI heuristics**: efficient but not exhaustive.

---

### 5. **Event-Driven Programming**
Each cell dynamically registers an event listener:
```js
cell.addEventListener('click', handleCellClick);
```
- Demonstrates **event-driven architecture**.  
- Uses **callback functions** — a key concept in **asynchronous programming**.

---

### 6. **Time-Based Control Flow (Countdown Timer)**
```js
countdown = setInterval(() => {
  time--;
  if (time === 0) { ... }
}, 1000);
```
- Illustrates **stateful timing logic** using **closures and intervals**.
- Demonstrates **temporal event handling**, simulating real-time constraints.

---

### 7. **Dynamic DOM Manipulation**
- Uses **JavaScript DOM APIs** (`document.createElement`, `querySelector`) for:
  - Dynamic grid generation
  - Scoreboard updates
  - Visual highlights for winning combinations  
- Reflects **data-to-UI synchronization**, akin to how **state management frameworks** (React/Vue) work internally.

---

### 8. **Object-Like State Tracking**
State variables like `scores`, `streaks`, and `board` mimic object-based design:
```js
scores = { X: 0, O: 0, Draw: 0 };
streaks = { X: 0, O: 0 };
```
- Demonstrates **encapsulation** of related data.
- Reflects **struct-like modeling**, essential in software design and data management.

---

## Algorithmic Complexity

| Function            | Purpose                     | Complexity                          |
|---------------------|-----------------------------|-------------------------------------|
| `checkWinner()`     | Validate win condition      | O(1) (fixed patterns)               |
| `findWinningMove()` | Heuristic simulation        | O(9)                                |
| `minimax()`         | Full game tree exploration  | O(b^d) where b = 9, d = depth (≈9!) |
| `randomMove()`      | Random valid move           | O(9)                                |
| `resetTimer()`      | Event loop                  | O(1)                                |

---

## Tech Stack

- **HTML5** - Structure  
- **CSS3** - Design, animations, theme switching  
- **Vanilla JavaScript (ES6)** - Game logic and AI   

---

## Future Enhancements
- Implement **alpha-beta pruning** to optimize minimax.  
- Add **localStorage** to persist scores across sessions.  
- Integrate **performance metrics** (time per AI move).  
- Multiplayer over WebSocket for online play.  

---

## How to Run
1. Download or clone this repository.  
2. Open `game.html` in any browser.  
3. Choose a mode and start playing!  

---

## Core CS Concepts Reinforced
- Arrays & Searching  
- Recursion & Backtracking  
- Heuristics & Greedy Algorithms  
- Game Trees & Decision Making  
- Event-driven Programming  
- State Management  
- Time Complexity & Optimization  
