# Rubik’s Cube Solver Using IDA* Algorithm

**Language:** C++  
**Build System:** CMake  
**Platform:** Windows (MinGW/GCC)

## 1. Project Overview

The Rubik’s Cube Solver is a C++ project designed to solve a scrambled Rubik’s Cube using search algorithms and heuristic optimization.

The project represents a Rubik’s Cube using different data structures and implements search techniques such as Depth-First Search (DFS), Breadth-First Search (BFS), Iterative Deepening Depth-First Search (IDDFS), and Iterative Deepening A* (IDA*).

The main program generates a scramble from a solved cube, displays the scrambled state, searches for a solution, and displays the resulting solution moves.

## 2. Objectives

- Implement a Rubik’s Cube model using C++.
- Explore different cube representations and data structures.
- Implement search algorithms to explore possible cube states.
- Use heuristic search to improve solving efficiency.
- Use pattern databases to guide the search.
- Understand the practical application of artificial intelligence search algorithms.

## 3. Technologies Used

- **C++:** Core programming language.
- **GCC/MinGW:** C++ compiler on Windows.
- **CMake:** Build-system configuration and compilation.
- **IDA\* Search:** Heuristic-guided search algorithm.
- **Pattern Databases:** Precomputed information used to guide the search.

## 4. Project Structure

```text
rubiks-cube-solver-main/
├── CMakeLists.txt
├── main.cpp
├── Model/
├── Solver/
├── PatternDatabases/
├── Databases/
│   └── cornerDepth5V1.txt
└── README.md
```

- **main.cpp:** Entry point of the application.
- **CMakeLists.txt:** Defines how the project is configured and built.
- **Model/:** Contains Rubik’s Cube representations and operations.
- **Solver/:** Contains search algorithm implementations.
- **PatternDatabases/:** Contains pattern-database functionality.
- **Databases/:** Stores precomputed database files used by the solver.

## 5. How the Project Works

### Step 1: Initialize the Cube

The program creates a solved Rubik’s Cube in which each face contains a single color.

### Step 2: Scramble the Cube

The program applies a sequence of random legal cube moves to generate a scrambled state.

### Step 3: Display the Scrambled State

The scrambled cube and the moves used to generate the scramble are printed in the terminal.

### Step 4: Search for a Solution

The IDA* algorithm explores possible move sequences. It uses a heuristic to guide the search and a pattern database when configured to do so.

### Step 5: Display the Solution

The program prints the solution move sequence and the solved cube representation.

The solution sequence does not necessarily have to be the exact reverse of the scramble sequence. The solver can find a different valid sequence that reaches the solved state.

## 6. Search Algorithms

### Depth-First Search (DFS)

DFS explores one path deeply before backtracking. It is simple to implement but can explore many unnecessary states.

### Breadth-First Search (BFS)

BFS explores states level by level. With equal-cost moves, it can find a shortest solution, but its memory requirements grow rapidly for large search spaces.

### Iterative Deepening Depth-First Search (IDDFS)

IDDFS repeatedly performs depth-limited DFS with increasing depth limits. It combines the low memory usage of DFS with the completeness of iterative deepening.

### Iterative Deepening A* (IDA*)

IDA* combines iterative deepening with a heuristic evaluation function. It repeatedly searches within a threshold based on the estimated total cost:

**f(n) = g(n) + h(n)**

Where:

- **g(n):** Cost of the path from the initial state to the current state.
- **h(n):** Heuristic estimate of the remaining cost.
- **f(n):** Estimated total cost through the current state.

IDA* is useful for large search spaces because it generally requires less memory than conventional A* search.

## 7. Pattern Databases

A pattern database stores precomputed information about selected aspects of a Rubik’s Cube state.

The solver can use this information as a heuristic to estimate the remaining work needed to reach the goal state.

A suitable heuristic can reduce the number of states explored during search. Its effectiveness depends on the database construction, the heuristic implementation, and how the database is used by the solver.

The project includes a database file named `cornerDepth5V1.txt`.

## 8. Requirements

Before building the project, install:

1. A C++ compiler such as GCC/MinGW.
2. CMake version 3.20 or newer.
3. MinGW Make, if using the `MinGW Makefiles` CMake generator.
4. Visual Studio Code or another code editor (optional).

Verify the installations using:

```powershell
g++ --version
cmake --version
```

## 9. Build and Run on Windows

### Step 1: Extract the Repository

Extract the project ZIP file and open the root project folder in a terminal.

Ensure that the terminal is in the directory containing `CMakeLists.txt`.

### Step 2: Check the Database Path

Open `main.cpp` and locate the database filename assignment.

If the source code contains an absolute path from another computer, change it to:

```cpp
string fileName = "Databases/cornerDepth5V1.txt";
```

Save the file.

This relative path assumes that the program is run from the project root directory.

### Step 3: Remove the Previous Build Directory

In PowerShell, run:

```powershell
Remove-Item -Recurse -Force build -ErrorAction SilentlyContinue
```

This removes the old CMake build configuration so a new one can be generated.

### Step 4: Configure CMake

Run:

```powershell
cmake -S . -B build -G "MinGW Makefiles"
```

This configures the project using the MinGW Makefiles generator.

### Step 5: Compile the Project

Run:

```powershell
cmake --build build --parallel
```

If the build succeeds, the executable should be created at:

```text
build/rubiks_cube_solver.exe
```

### Step 6: Execute the Solver

From the project root directory, run:

```powershell
.\build\rubiks_cube_solver.exe
```

The application should display the scrambled cube, scramble moves, solution moves, and the solved cube, depending on the program's configured output.

## 10. Understanding the Output

The program's terminal output can be understood in four sections:

1. **Scrambled Cube:** The cube state after applying scramble moves.
2. **Scramble Moves:** The moves used to scramble the initially solved cube.
3. **Solved Cube:** The solved cube representation printed by the program.
4. **Solution
