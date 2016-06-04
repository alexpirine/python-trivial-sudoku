# python-trivial-sudoku

Simple Python implementation of a sudoku solver

## Example

Download or clone the repository, go to your terminal, and try to execute a few  examples:

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
```

## Heuristics

The algorithm simply recursively tries different values until it reaches a valid solution.

But before making recursive guesses, the algorithm tries to find logical moves through two algorithms:

### Algorithm 1

The algorithm computes all possible values at a specific square. If there is only one possible value, the square is solved.

### Algorithm 2

The algorithm successively takes values from 1 to 9, and checks for possible locations in a region (a region being a set of 9 squares in a cell, a row or a column). If only one location is available in the region, it's filled with the value.
