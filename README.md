# Crossword – AI-Powered Crossword Puzzle Solver and Creator

An AI-powered crossword puzzle generator that uses constraint satisfaction algorithms to create complete crossword puzzles from given structures and word lists.

## Overview

This project implements a constraint satisfaction problem (CSP) solver to generate crossword puzzles. Given a crossword structure (blank grid) and a vocabulary list, the AI determines which words should be placed in each position while satisfying all constraints.

## Features

- **Constraint Satisfaction**: Implements node consistency, arc consistency (AC-3), and backtracking search
- **Smart Heuristics**: Uses minimum remaining values and degree heuristics for variable selection
- **Optimization**: Implements least-constraining values heuristic for value ordering
- **Visual Output**: Generates both text and PNG image representations of solved puzzles
- **Flexible Input**: Supports custom crossword structures and word lists

## Algorithm Components

### 1. Node Consistency
Ensures each variable's domain contains only values that satisfy unary constraints (correct word length).

### 2. Arc Consistency (AC-3)
Maintains binary constraints between overlapping variables, ensuring consistent character overlaps.

### 3. Backtracking Search
Systematically explores possible assignments with intelligent variable and value ordering.

### 4. Heuristics
- **Minimum Remaining Values (MRV)**: Selects variables with fewest possible values first
- **Degree Heuristic**: Breaks ties by choosing variables with most neighbors
- **Least Constraining Values**: Orders values to minimize impact on neighboring variables

## Project Structure

```
crossword/
├── crossword.py          # Crossword and Variable classes (provided)
├── generate.py          # Main CSP solver implementation
├── data/
│   ├── structure1.txt   # Example crossword structure
│   ├── structure2.txt   # Example crossword structure
│   ├── structure3.txt   # Example crossword structure
│   ├── words1.txt       # Example word list
│   ├── words2.txt       # Example word list
│   └── words3.txt       # Example word list
└── README.md           # This file
```

## Usage

### Basic Usage
```bash
python generate.py data/structure1.txt data/words1.txt
```

### Generate with Image Output
```bash
python generate.py data/structure1.txt data/words1.txt output.png
```

### Example Output
```
██████████████
███████M████R█
█INTELLIGENCE█
█N█████N████S█
█F██LOGIC███O█
█E█████M████L█
█R███SEARCH█V█
███████X████E█
██████████████
```

## Input File Formats

### Structure Files
- Use `_` for blank cells (to be filled)
- Use any other character for blocked cells
- Example:
```
___
_█_
___
```

### Word Files
- Words should match the language/theme of your puzzle
- Example:
```
CAT
DOG
RAT
BAT
```

## Requirements

- Python
- Pillow 

## How to Run

1. Clone the repository
2. python generate.py data/structure1.txt data/words1.txt
3. python generate.py data/structure1.txt data/words1.txt output.png 

This project is part of CS50's coursework.
