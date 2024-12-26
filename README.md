# Minesweeper Game

Welcome to the Minesweeper Game! Test your logic and luck as you uncover cells on a board while avoiding hidden mines. The game becomes progressively more challenging as you advance through the levels.

---

## Game Rules

1. The game is played on a square board.
2. Click on cells to uncover them. Avoid the ones hiding mines.
3. If you click on a cell with a mine, you lose.
4. If you uncover all cells without mines, you win.

---

## Game Levels

The game has three levels of difficulty:

- **Beginner**: 
  - Board: 9 x 9
  - Mines: 10
  - Probability of a mine: 10/81 (0.12)

- **Intermediate**: 
  - Board: 16 x 16
  - Mines: 40
  - Probability of a mine: 40/256 (0.15)

- **Advanced**: 
  - Board: 24 x 24
  - Mines: 99
  - Probability of a mine: 99/576 (0.17)

The difficulty increases with the number of tiles and mines, making the game more challenging as you progress.

---

## Winning Tips

1. **Use Clues**:
   - Clicking on a cell adjacent to one or more mines reveals the count of adjacent cells containing mines.
   - Use this information to logically deduce the locations of mines.

2. **Chain Reactions**:
   - Clicking on a cell with no adjacent mines automatically clears all surrounding cells, saving you time and effort.

3. **Strategic Clicking**:
   - You don’t have to uncover all non-mine cells to win. Prioritize cells with no adjacent mines for quick progress.

---

## Game Implementation

Two versions of the game are provided:

1. **User-Input Version**:
   - The user selects their moves manually using input prompts.

2. **Automated Version**:
   - The user’s moves are selected randomly by the program.

---

## Flow of the Game

1. **Boards**:
   - Two boards are used:
     - `realBoard`: Stores the location of the mines.
     - `myBoard`: The board on which the game is played.

2. **Initialization**:
   - Choose a difficulty level using the `chooseDifficultyLevel()` function.
   - Initialize `realBoard` and `myBoard` based on the selected level.
   - Mines are placed randomly on `realBoard`.

3. **Game Mechanics**:
   - Assign moves using the `assignMoves()` function.
   - In the user-input version, moves are entered during gameplay.
   

4. **Game Progression**:
   - The game continues until the user either wins (by uncovering all non-mine cells) or loses (by clicking on a mine-containing cell). This is implemented using a `while()` loop that runs until the game is won or lost.

5. **Move Execution**:
   - The `makeMove()` function inside the `while` loop gets a move randomly from the pre-assigned moves. 
   - In the user-input version, this function prompts the user to enter their own move.
   - To ensure fairness, the first move is always safe. If the `currentMoveIndex == 0`, the `replaceMine()` function guarantees the user does not lose on the first move.

6. **Recursive Gameplay**:
   - The core gameplay relies on the recursive function `playMinesweeperUtil()`. This function:
     - Returns `true` if the user clicks on a mine (loss).
     - Otherwise, it calculates the count of adjacent mines using `countAdjacentMines()`.
     - If there are no adjacent mines, it recursively clears all safe adjacent cells, speeding up gameplay.
     - If adjacent mines are present, the count is displayed as a hint for logical deduction.

7. **Efficient Clicking**:
   - Clicking on a cell with no adjacent mines clears all its neighboring cells automatically.
   - Winning doesn’t require uncovering all non-mine cells, as luck and strategic clicking can lead to quick victories.

8. **End Conditions**:
   - The game ends when:
     - The user clicks on a mine (loss).
     - The user uncovers all safe cells (win).

---

Enjoy the game and good luck!
