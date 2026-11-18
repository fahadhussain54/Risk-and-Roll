# 🎲 Risk and Roll — Advanced C Console Dice Game

Welcome to **Risk and Roll**, a feature-rich, two-player turn-based tactical dice game developed in C as a Programming Fundamentals final project[cite: 4, 6].

---

## 🌟 Key Features

- **Modular Multi-File Architecture**: Cleanly separated into a header file (`game.h`), core game flow (`main.c`), and utility/logic modules (`functions.c`)[cite: 4, 5, 6].
- **Player Career Profiles & Lifetime Stats**: Automatically tracks and updates individual player profiles (`profiles.txt`) across matches—recording **Total Games Played**, **Total Wins**, and **All-Time High Scores** using structured file searching and updating.
- **Sorted Leaderboard System**: Reads match records from `leaderboard.txt` into structures and ranks players in descending order by score[cite: 4, 6].
- **Tactical Item Shop & Inventory**: Earn coins with every roll and spend them on **Shields**, **Reroll Tokens**, and **Double Points** multipliers[cite: 4, 6].
- **Real-Time Timed Turn Mode**: Uses non-blocking keyboard input (`kbhit()`) and real-time clock tracking (`time.h`) to force quick decisions under a ticking countdown[cite: 4, 6].
- **Enhanced Console UI/UX & Audio**: Features ANSI escape color codes, animated rolling indicators, ASCII art dice faces, dynamic rule loading (`rules.txt`), and Windows audio triggers (`Beep()`)[cite: 4, 6].

---

## 📂 Project File Structure

```text
├── main.c          # Entry point, main menu flow, and core game loop
├── functions.c     # UI rendering, shop logic, timers, sorting, and file I/O
├── game.h          # Shared header file containing structs, prototypes, and libraries
└── rules.txt       # External text file containing game instructions
```
