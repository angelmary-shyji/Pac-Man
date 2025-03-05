# PacMan Game

This Java-based project is a simple implementation of the classic **PacMan** game using **Swing** for graphical user interface (GUI) components. The game features a **PacMan** character navigating a maze, avoiding ghosts, and eating food pellets, with the goal of achieving the highest possible score.

## Features:
- **PacMan** can move in four directions: up, down, left, and right.
- **Ghosts** move around the maze in random directions and can collide with **PacMan** to decrease lives.
- **Walls** block movement, and **PacMan** cannot pass through them.
- **Food** is collected by **PacMan** to increase the score. Each food item is worth 10 points.
- **Game Over** is triggered when **PacMan** runs out of lives, and the game resets.
- **Score** and **Lives** are displayed at the top of the screen.
- **Multiple Ghosts** with different images chase **PacMan** through the maze.

## Game Components:

### 1. **Main Game Class (`App.java`)**
- Initializes the game window using **JFrame**.
- Creates an instance of the `PacMan` panel and adds it to the frame.
- Sets the game window size, visibility, and other properties like no resizing.

### 2. **PacMan Class (`PacMan.java`)**
This class handles the main logic and graphical rendering of the game.

#### Key Components:
- **Block Class**: Represents individual entities in the game, such as walls, ghosts, food, and PacMan. It includes:
  - `x`, `y` coordinates for positioning.
  - `width`, `height` for size.
  - `image` for graphical representation.
  - Methods to update the direction of movement, handle velocity, and detect collisions.

- **Game Variables**:
  - **Walls**: A collection of obstacles PacMan cannot pass.
  - **Ghosts**: A collection of ghost objects that move randomly and chase PacMan.
  - **Foods**: Items PacMan collects to earn points.
  - **PacMan**: The player's character that can move around the maze.

- **Game Loop (`Timer gameLoop`)**:
  - Continuously updates the game state (positioning of objects) at a rate of 50 milliseconds per frame (roughly 20 frames per second).
  - Stops the game loop once the game is over.

- **Movement & Collision Detection**:
  - **PacMan** and **Ghosts** have movement logic to handle user input (arrow keys) and random movement, respectively.
  - Collisions are detected between **PacMan**, **Ghosts**, and **Walls** to handle interactions like bumping into walls or losing lives upon ghost collisions.
  - **Food** is collected when **PacMan** collides with it, increasing the score.

#### Key Methods:
- `loadMap()`: Initializes the game board by placing walls, food, and ghosts according to a predefined tile map.
- `move()`: Handles the movement of **PacMan** and **Ghosts**, checks for collisions, and updates the score.
- `collision()`: Checks if two blocks (e.g., **PacMan** and **Ghosts**) are colliding.
- `paintComponent(Graphics g)`: Draws the current state of the game on the screen (including PacMan, ghosts, walls, and food).
- `resetPositions()`: Resets the positions of **PacMan** and the **Ghosts** when PacMan loses a life.

### 3. **Game Controls (KeyListener)**:
- The user controls **PacMan** with the arrow keys.
- **KeyEvent** listeners capture the arrow key presses to update **PacMan**'s direction.

### 4. **Graphics & Images**:
- Multiple images for walls, ghosts, and **PacMan**'s movement directions are used to visually represent the game.
- Images are loaded using `ImageIcon` and drawn onto the screen using `g.drawImage()`.

## Game Tile Map:
The maze is represented by a 2D array (`tileMap`) where each character in the string corresponds to a type of game element:
- `X` = Wall
- `P` = **PacMan**'s initial position
- `b`, `o`, `p`, `r` = Ghosts (blue, orange, pink, red)
- `' '` = Food

## How the Game Works:
1. The game window is initialized, displaying a 19x21 grid of tiles representing the game maze.
2. **PacMan** and **Ghosts** are positioned based on the `tileMap` and can move based on user input or random behavior.
3. The game starts and continuously updates based on the timer, moving the objects and checking for collisions.
4. If **PacMan** eats food, the score increases.
5. If **PacMan** collides with a ghost, the player loses a life.
6. The game resets if the player runs out of lives.

## Technical Requirements:
- **Java Development Kit (JDK)**: Version 8 or higher required to run the game.
- **Graphics**: Game relies on **Swing** for GUI components (`JPanel`, `JFrame`), and images for game entities are stored in the resources directory.

## How to Run:
1. Compile both `App.java` and `PacMan.java`.
2. Ensure all image files (`wall.png`, `blueGhost.png`, `orangeGhost.png`, `pinkGhost.png`, `redGhost.png`, `pacmanUp.png`, `pacmanDown.png`, `pacmanLeft.png`, `pacmanRight.png`) are placed in the appropriate directory (e.g., `resources`).
3. Run `App.java` to start the game.

## Game Over:
- The game ends when **PacMan** runs out of lives.
- The score is displayed on the screen, and the game resets when the user presses any key.
