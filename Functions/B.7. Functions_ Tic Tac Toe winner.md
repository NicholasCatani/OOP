_**Tic Tac Toe winner**_


Assume that the configurations in the game of Tic Tac Toe are represented by a tuple conf of length 3, where conf[0] stores the top row of game board, conf[1] stores the middle row, and conf[2] stores the bottom row. Each conf[i] is a tuple of length 3, where conf[i][0] is represents the left column of the row corresponding to i, conf[i][1] represents the middle column, and conf[i][2] the right column.
The value of each conf[i][j] is one of "X", "O", "-", which indicate that the corresponding position of the board has, respectively, a cross, a circle, or it empty. A valid configuration is a configuration, where the number of "X"’s and "O"’s is either the same or differs by 1. A valid configuration is a win configuration for "X" if there are three "X" in one line in conf, horizontally (in one row), vertically (in one column) or diagonally. A valid configuration is a win configuration for "O" if the same properties hold for "O".
Implement a function winner that, given a valid configuration conf as an argument, returns "X", if this is a win configuration for "X" and not for "O", "O" if this is a win configuration for "O" and not for "X", and "-" otherwise.


Example:
winner((("X", "-", "O"), ("-", "O", "-"), ("O", "-", "X"))) is "O"



Python Code:
    
    def winner(conf):
    # Define lines to check: 3 rows, 3 columns, and 2 diagonals
      lines = [
        # Rows
          conf[0], conf[1], conf[2],
        # Columns
          (conf[0][0], conf[1][0], conf[2][0]),
          (conf[0][1], conf[1][1], conf[2][1]),
          (conf[0][2], conf[1][2], conf[2][2]),
        # Diagonals
          (conf[0][0], conf[1][1], conf[2][2]),
          (conf[0][2], conf[1][1], conf[2][0])
      ]
    
    # Check if there is a winning line for "X" or "O"
      x_wins = any(line == ("X", "X", "X") for line in lines)
      o_wins = any(line == ("O", "O", "O") for line in lines)
    
    # Determine the result based on win conditions
      if x_wins and not o_wins:
          return "X"
      elif o_wins and not x_wins:
          return "O"
      else:
          return "-"
