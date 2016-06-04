# python-trivial-sudoku

Simple Python implementation of a Sudoku solver

## Example

```console
$ ./example.py 
EXAMPLE:
+---+---+---+
|13 |  6|   |
| 74|  2|58 |
|   | 5 |3  |
+---+---+---+
| 8 | 1 |   |
|   | 6 | 29|
|   |   |43 |
+---+---+---+
|   | 3 | 5 |
|9 3|   |7 4|
|   | 75|8  |
+---+---+---+
Solution:
+---+---+---+
|135|846|297|
|674|392|581|
|892|157|346|
+---+---+---+
|289|413|675|
|347|568|129|
|561|729|438|
+---+---+---+
|718|634|952|
|953|281|764|
|426|975|813|
+---+---+---+
...
```

## Installation

### From PyPi

```bash
pip install trivial-sudoku
```

### From source

```bash
git clone https://github.com/alexpirine/python-trivial-sudoku.git
cd python-trivial-sudoku
make install
```

## Usage

Once installed, the Sudoku solver is available in the `sudoku` module:

```pycon
>>> from sudoku import SudokuProblem
>>> 
>>> puzzle = SudokuProblem([
...   [8,5,0, 0,0,2, 4,0,0],
...   [7,2,0, 0,0,0, 0,0,9],
...   [0,0,4, 0,0,0, 0,0,0],
... 
...   [0,0,0, 1,0,7, 0,0,2],
...   [3,0,5, 0,0,0, 9,0,0],
...   [0,4,0, 0,0,0, 0,0,0],
... 
...   [0,0,0, 0,8,0, 0,7,0],
...   [0,1,7, 0,0,0, 0,0,0],
...   [0,0,0, 0,3,6, 0,4,0],
... ])
>>> 
>>> print "Sudoku puzzle:"
Sudoku puzzle:
>>> puzzle.print_matrix()
+---+---+---+
|85 |  2|4  |
|72 |   |  9|
|  4|   |   |
+---+---+---+
|   |1 7|  2|
|3 5|   |9  |
| 4 |   |   |
+---+---+---+
|   | 8 | 7 |
| 17|   |   |
|   | 36| 4 |
+---+---+---+
>>> solution = puzzle.solve()
>>> print "Solution:"
Solution:
>>> solution.print_matrix()
+---+---+---+
|859|612|437|
|723|854|169|
|164|379|528|
+---+---+---+
|986|147|352|
|375|268|914|
|241|593|786|
+---+---+---+
|432|981|675|
|617|425|893|
|598|736|241|
+---+---+---+
>>> 
```

## Heuristics

The algorithm simply recursively tries different values until it reaches a valid solution.

But before making recursive guesses, the algorithm tries to find logical moves through two algorithms:

### Algorithm 1

The algorithm computes all possible values at a specific location. If there is only one possible value, the location is filled with that value.

### Algorithm 2

The algorithm successively takes values from 1 to 9, and checks for possible locations in a region (a region being a set of 9 squares in a cell, a row or a column). If only one single location is available in the region for that specific value, the location is filled with that value.
