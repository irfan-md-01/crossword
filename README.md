# CS50 AI Crossword Generator

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

## Implementation Details

### Core Functions Implemented

1. **`enforce_node_consistency()`**
   - Removes values from variable domains that don't match length constraints
   - Ensures unary constraint satisfaction

2. **`revise(x, y)`**
   - Makes variable x arc-consistent with variable y
   - Removes values from x's domain that have no compatible values in y's domain

3. **`ac3(arcs=None)`**
   - Implements the AC-3 algorithm for arc consistency
   - Maintains a queue of arcs and processes them until consistency is achieved

4. **`assignment_complete(assignment)`**
   - Checks if all variables have been assigned values

5. **`consistent(assignment)`**
   - Verifies that an assignment satisfies all constraints:
     - All words are unique
     - All words have correct lengths
     - No conflicts in overlapping positions

6. **`order_domain_values(var, assignment)`**
   - Orders domain values using least-constraining values heuristic
   - Prioritizes values that eliminate fewer options for neighbors

7. **`select_unassigned_variable(assignment)`**
   - Chooses next variable using MRV and degree heuristics
   - Optimizes search efficiency

8. **`backtrack(assignment)`**
   - Implements backtracking search with constraint propagation
   - Returns complete assignment or None if unsolvable

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
- One word per line
- Words should match the language/theme of your puzzle
- Example:
```
CAT
DOG
RAT
BAT
```

## Requirements

- Python 3.x
- Pillow (for image generation): `pip install Pillow`

## Testing

The implementation can be tested using CS50's check50 tool:
```bash
check50 ai50/projects/2024/x/crossword
```

Style checking:
```bash
style50 generate.py
```

## Performance Optimizations

- **Early Termination**: Stops search when domains become empty
- **Constraint Propagation**: Maintains arc consistency throughout search
- **Intelligent Ordering**: Uses heuristics to minimize search space
- **Efficient Data Structures**: Uses sets and dictionaries for fast operations

## Example Puzzles

The project includes three example puzzles of varying complexity:
- `structure1.txt` + `words1.txt`: Simple 4-variable puzzle
- `structure2.txt` + `words2.txt`: Medium complexity
- `structure3.txt` + `words3.txt`: More challenging layout

## Key Concepts Demonstrated

- **Constraint Satisfaction Problems (CSP)**
- **Arc Consistency and Node Consistency**
- **Backtracking Search with Heuristics**
- **Constraint Propagation**
- **Search Space Optimization**

## Limitations

- Requires pre-defined puzzle structure
- Limited to rectangular grids
- Word list must contain sufficient vocabulary for the given structure
- No automatic difficulty adjustment

## Future Enhancements

- Automatic puzzle structure generation
- Difficulty scoring system
- Theme-based word filtering
- Interactive puzzle solving interface
- Multi-language support

---

This project demonstrates fundamental AI concepts in constraint satisfaction and search algorithms, providing a practical application of theoretical computer science principles.