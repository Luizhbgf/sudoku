def f(puzzle):

    for r in range(9):
        for c in range(9):
            if puzzle[r][c] == -1:
                return r,c
    return None, None

def iv(puzzle,adivinhe,fila,col):
    rv = puzzle[fila]                    
    if adivinhe in rv:
        return False
    c_valts=[]    
    for i in range(9):
        c_valts.append(puzzle[i][col])
    c_valts = [puzzle[i][col] for i in range(9)]
    if adivinhe in c_valts:
        return False
    rs = (fila // 3) * 3
    cs = (col // 3) * 3
    for r in range(rs,rs +3):
        for c in range(cs,cs+3):
            if puzzle[r][c] == adivinhe:
                return False

    return True

def r_suduku(puzzle): 
    fila, col = f(puzzle)
    if fila is None:
        return True

    for adivinhe in range(1,10):
        if iv(puzzle,adivinhe,fila,col):
            puzzle[fila][col] = adivinhe
            if r_suduku(puzzle):
                return True
    puzzle[fila][col] = -1
                
