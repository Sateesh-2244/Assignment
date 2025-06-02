# Assignment
def solveNQueens(n: int):
    def backtrack(row, cols, diag1, diag2, path):
        if row == n:
            res.append(path)
            return
        for col in range(n):
            d1 = row + col
            d2 = row - col + n - 1
            if cols[col] or diag1[d1] or diag2[d2]:
                continue
            cols[col] = diag1[d1] = diag2[d2] = True
            backtrack(row + 1, cols, diag1, diag2, path + [col])
            cols[col] = diag1[d1] = diag2[d2] = False

    res = []
    backtrack(0, [False] * n, [False] * (2 * n - 1), [False] * (2 * n - 1), [])
    
    # Convert column positions to board configurations
    boards = []
    for solution in res:
        board = []
        for col in solution:
            row_str = ['.'] * n
            row_str[col] = 'Q'
            board.append(''.join(row_str))
        boards.append(board)
    return boards
