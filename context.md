# Repository Context

## What this project does

This repository contains a small, self-contained Memory (Concentration) card game. Players flip cards to find matching emoji pairs. The game offers 4x4 and 6x6 boards, tracks moves and elapsed time, assigns a star rating based on moves, and shows a completion screen when all pairs are found. Best scores are stored in the browser's local storage.

## What it stands for

The project is a lightweight browser game for fun and for practicing memory and concentration. It also demonstrates how to build an interactive web experience with standard web technologies, without requiring a framework, external library, build step, or server.

## How it is built

- `memory-game.html` contains the complete game: structure, styling, and JavaScript behavior.
- HTML, CSS, and vanilla JavaScript are used; there are no external dependencies.
- The layout adapts to smaller screens, and cards can be played with a mouse or keyboard.
- Scores are saved in the browser on the device where the game is played.

## How to run it

Open `memory-game.html` in a modern web browser. Alternatively, start a local server from the repository folder with `python3 -m http.server 8000` and open `http://localhost:8000/memory-game.html`.
