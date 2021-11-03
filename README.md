def isPositionAvailable(row, col, maze): 
    if row < 0 or col < 0: 
        return False
    if maze[row][col] == '1':
        return False
    elif maze[row][col] == '0': 
        return True
    else:
        return True

def generateMaze(textMaze):
    textMaze = textMaze.split('\n')

    maze = []

    for row in textMaze:
        rowOfMaze = row.split(' ')
        maze.append(rowOfMaze)

    return maze

def printMaze(maze, currRow, currCol):
    rowCount = -1

    for row in maze:
        rowCount += 1
        for stuff in range(3):
            colCount = -1
            for column in row:
                colCount += 1


                if rowCount == currRow and colCount == currCol:
                    for i in range(3):
                        print('v', end = '')

                elif column == '1':
                    for i in range(3):
                        print('*', end = '')

                elif column == '0':
                    for i in range(3):
                        print(' ', end = '')

                elif column == 'S':
                    for i in range(3):
                        print('S', end = '')

                elif column == 'X':
                    for i in range(3):
                        print('X', end = '')
            print()
def playGame(maze, row, col):
    commands= input("Enter a string of commands: ")

    for command in commands:

        if command == 'R':
            if isPositionAvailable(row,col + 1,maze):
                col = col + 1
            else:
                return False

        if command == 'L':
            if isPositionAvailable(row,col - 1,maze):
                col = col - 1
            else:
                return False
        if command == 'U':
            if isPositionAvailable(row - 1,col,maze):
                row = row - 1
            else:
                return False

        if command == 'D':
            if isPositionAvailable(row + 1,col,maze):
                row = row + 1
            else:
                return False

        if (maze[row][col]) == 'X':
            return True
