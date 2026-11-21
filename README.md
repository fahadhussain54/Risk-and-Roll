# 🎲 Risk and Roll — Advanced C Console Dice Game



> A feature-rich, two-player turn-based tactical dice game developed in C as a **Programming Fundamentals** final project.



---



## 🌟 Key Features



- **Modular Multi-File Architecture**: Cleanly separated into a header file (`game.h`), core game flow (`main.c`), and utility/logic modules (`functions.c`).

- **Player Career Profiles & Lifetime Stats**: Automatically tracks and updates individual player profiles (`profiles.txt`) across matches—recording **Total Games Played**, **Total Wins**, and **All-Time High Scores** using structured file parsing (`fscanf`) and updating (`fprintf`).

- **Persistent Leaderboard System**: Logs match winners and final scores in `leaderboard.txt` for historical match tracking.

- **Tactical Item Shop & Inventory**: Earn coins (`+2` per roll) and spend them mid-turn on **Shields**, **Reroll Tokens**, and **Double Points** multipliers using pointer-based pass-by-reference updates.

- **Real-Time Timed Turn Mode**: Uses non-blocking keyboard input (`kbhit()`) and real-time clock tracking (`time.h`) to enforce timed decisions under a ticking countdown.

- **Enhanced Console UI/UX & Audio**: Features ANSI escape color codes, animated rolling indicators, ASCII art dice faces, dynamic rule loading (`rules.txt`), and Windows audio triggers (`Beep()`).



---



## 📂 Project File Structure



```text

├── main.c          # Entry point, main menu switch-case, and core game loop

├── functions.c     # UI rendering, item shop, countdown timers, and file I/O

├── game.h          # Shared header file with PlayerProfile struct, prototypes, and headers

└── rules.txt       # External text file containing game instructions

```



> **Note:** `leaderboard.txt` and `profiles.txt` are generated and updated automatically by the executable at runtime.



---



## 🚀 How to Compile and Run



Because this is a multi-file C project, you must compile and link all `.c` source files together using a compiler such as **GCC** before running the executable.



### Step 1: Compile the Code



Open your terminal or command prompt inside the project folder and run:



```bash

gcc main.c functions.c -o dice_game.exe

```



### Step 2: Run the Executable



Once the compilation finishes without errors, execute the generated binary:



- **Windows (PowerShell / Command Prompt):**

  ```bash

  ./dice_game.exe

  ```



- **Linux / macOS:**

  ```bash

  ./dice_game

  ```



---



## 🛒 Tactical Item Shop Reference



| Item Name | Cost (Coins) | Effect |

| :--- | :---: | :--- |

| **Shield** | `5` | Automatically blocks a `1` roll and prevents your score from resetting to `0` |

| **Reroll Token** | `4` | Allows you to discard your current dice roll and roll again |

| **Double Points** | `6` | Multiplies your current roll value by `2x` |



---



## 🧪 Sample Run Cases



Below are representative execution scenarios demonstrating core gameplay mechanics, power-ups, shop interactions, and file persistence.



### Run Case 1: Normal Roll, Double Points Activation & Holding Score



**Scenario:** Player 1 (`Fahad`) rolls a `5`, declines the Reroll token, activates a Double Points token to earn `10` points, and chooses to hold the score safely.



```text

========================================

         WELCOME TO THE DICE GAME       

========================================

1. Play Game

2. View Leaderboard

3. View Players Profile

4. View Rules

5. Exit

========================================

Enter your choice: 1



------- PLAYERS REGISTRATION -------

Enter player 1 name: Fahad

Enter player 2 name: Mareeha



======= GAME START =======

----------------------------------------

>>> Fahad's TURN <<<

Fahad's current score is: 0

Fahad's Inventory -> Shields: 1 | Rerolls: 1 | Double Points: 1

[S] Open Shop | [Any Other Key] Roll Dice (Timeout in 10 seconds): R

Rolling the dice...

Fahad rolled a: 5

+-------+

| O   O |

|   O   |

| O   O |

+-------+

Do you want to use your Reroll token? (Y/N) (Timeout in 5 seconds): N

Do you want to use your Double Point token? (Y/N) (Timeout in 5 seconds): Y

Double point token used! Roll value doubled.



Do you want to hold score and switch turn [Y] or continue rolling [N]?: Y

Fahad holds. Score 10 is safely stored. Switching turn.

```



### Run Case 2: Visiting the Item Shop & Shield Protection Against Rolling a `1`



**Scenario:** Player 2 (`Mareeha`) opens the Item Shop before rolling, buys a Shield, rolls a `1`, and uses her Shield to block the score reset penalty.



```text

----------------------------------------

>>> Mareeha's TURN <<<

Mareeha's current score is: 24

Mareeha's Inventory -> Shields: 0 | Rerolls: 1 | Double Points: 1

[S] Open Shop | [Any Other Key] Roll Dice (Timeout in 10 seconds): S



========================================

         WELCOME TO THE ITEM SHOP       

========================================

Player: Mareeha | Available Coins: 6 

1. Buy Shield (+1)        - Cost: 5 coins

2. Buy Reroll Token (+1)  - Cost: 4 coins

3. Buy Double Points (+1) - Cost: 6 coins

4. Exit Shop & Roll

========================================

Enter your choice (1-4): 1

Successfully bought a Shield!

Enter your choice (1-4): 4



----------------------------------------

>>> Mareeha's TURN (Resuming) <<<

Mareeha's score: 24 | Coins: 1 

Rolling the dice...

Mareeha rolled a: 1

+-------+

|       |

|   O   |

|       |

+-------+

Do you want to use your Reroll token? (Y/N) (Timeout in 5 seconds): N

Do you want to use your Double Point token? (Y/N) (Timeout in 5 seconds): N

Oh no! You rolled a 1, but your Shield blocked the penalty!



Do you want to hold score and switch turn [Y] or continue rolling [N]?: Y

Mareeha holds. Score 24 is safely stored. Switching turn.

```



### Run Case 3: Rolling a `1` Without a Shield & Decision Timeout



**Scenario:** A player lets the shop timer expire (defaulting to rolling), rolls a `1` with `0` Shields remaining, triggers the warning beep, and resets their score to `0`.



```text

----------------------------------------

>>> Fahad's TURN <<<

Fahad's current score is: 42

Fahad's Inventory -> Shields: 0 | Rerolls: 0 | Double Points: 0

[S] Open Shop | [Any Other Key] Roll Dice (Timeout in 10 seconds): 

[ Time's up! Defaulting choice]

Rolling the dice...

Fahad rolled a: 1

+-------+

|       |

|   O   |

|       |

+-------+

Oh no! Fahad rolled a 1! Score resets to 0.

Switching turn to the next player...

```



### Run Case 4: Winning the Match & Updating Persistent Files



**Scenario:** Player 1 reaches `100` or more points, triggering victory audio and automatically updating `leaderboard.txt` and `profiles.txt`.



```text

----------------------------------------

>>> Fahad's TURN <<<

Fahad's current score is: 96

Fahad's Inventory -> Shields: 0 | Rerolls: 0 | Double Points: 0

[S] Open Shop | [Any Other Key] Roll Dice (Timeout in 10 seconds): R

Rolling the dice...

Fahad rolled a: 6

+-------+

| O   O |

| O   O |

| O   O |

+-------+

CONGRATULATIONS! Player Fahad WINS the game with a score of 102!

Game result successfully saved to 'leaderboard.txt' !



Press any key to return to the main menu...

```



#### Viewing Career Profiles (`Option 3` from Main Menu)



```text

========================================

         PLAYER CAREER PROFILES         

========================================

Name            | Played | Wins  | High Score

----------------------------------------

Fahad           | 3      | 2     | 102       

Mareeha         | 3      | 1     | 100       

========================================

Press any key to return to the main menu...

```



---



## 👥 Authors



- **Fahad Hussain** (`26K-2033`)

- **Mareeha Tahir** (`26K-2032`)

- **Course:** Programming Fundamentals (Fall 2026)

- **Institution:** National University of Computer and Emerging Sciences (FAST-NUCES)
