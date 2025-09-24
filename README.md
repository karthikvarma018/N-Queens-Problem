# N-Queens-Problem
Creating a N-Queens Problem
def solveNQueens(n):
    def is_safe(board, row, col):
        # Check column, main diagonal, and anti-diagonal for conflicts
        for i in range(row):
            if board[i] == col or \
               board[i] - i == col - row or \
               board[i] + i == col + row:
                return False
        return True
    
    def backtrack(board, row):
        if row == n:  # If we've placed queens in all rows, it's a valid solution
            solution = []
            for i in range(n):
                row_str = '.' * board[i] + 'Q' + '.' * (n - board[i] - 1)
                solution.append(row_str)
            result.append(solution)
            return
        
        for col in range(n):  # Try each column for the current row
            if is_safe(board, row, col):
                board[row] = col  # Place the queen
                backtrack(board, row + 1)  # Move to the next row
    
    result = []  # Store all valid solutions
    board = [-1] * n  # Initialize board to keep track of queen positions
    backtrack(board, 0)  # Start placing queens from row 0
    return result
solutions = solveNQueens(4)
print(f"Number of solutions for n=4: {len(solutions)}")
if len(solutions) > 0:
    # Display solutions in a readable horizontal format
    for solution in solutions:
        for row in solution:
            print(row)
        print()  # Print a newline to separate different solutions
else:
    print("No solutions found.")
