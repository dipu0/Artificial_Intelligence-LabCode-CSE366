# Astar


```python
import math
from simpleai.search import SearchProblem, astar

# Class containing the methods to solve the maze
class MazeSolver(SearchProblem):
    # Initialize the class 
    def __init__(self, board):
        self.board = board
        self.goal = (0, 0)

        for y in range(len(self.board)):
            for x in range(len(self.board[y])):
                if self.board[y][x].lower() == "o":
                    self.initial = (x, y)
                elif self.board[y][x].lower() == "x":
                    self.goal = (x, y)

        super(MazeSolver, self).__init__(initial_state=self.initial)

    # Define the method that takes actions
    # to arrive at the solution
    def actions(self, state):
        actions = []
        for action in COSTS.keys():
            newx, newy = self.result(state, action)
            if self.board[newy][newx] != "#":
                actions.append(action)

        return actions

    # Update the state based on the action
    def result(self, state, action):
        x, y = state

        if action.count("up"):
            y -= 1
        if action.count("down"):
            y += 1
        if action.count("left"):
            x -= 1
        if action.count("right"):
            x += 1

        new_state = (x, y)

        return new_state

    # Check if we have reached the goal
    def is_goal(self, state):
        return state == self.goal

    # Compute the cost of taking an action
    def cost(self, state, action, state2):
        return COSTS[action]

    # Heuristic that we use to arrive at the solution
    def heuristic(self, state):
        x, y = state
        gx, gy = self.goal

        return math.sqrt((x - gx) ** 2 + (y - gy) ** 2)

if __name__ == "__main__":
    # Define the map
    MAP = """
    ##############################
    #         #              #   #
    # ####    ########       #   #
    #  o #    #              #   #
    #    ###     #####  ######   #
    #      #   ###   #           #
    #      #     #   #  #  #   ###
    #     #####    #    #  # x   #
    #              #       #     #
    ##############################
    """

    # Convert map to a list
    print(MAP)
    MAP = [list(x) for x in MAP.split("\n") if x]

    # Define cost of moving around the map
    cost_regular = 1.0
    cost_diagonal = 1.7

    # Create the cost dictionary
    COSTS = {
        "up": cost_regular,
        "down": cost_regular,
        "left": cost_regular,
        "right": cost_regular,
        "up left": cost_diagonal,
        "up right": cost_diagonal,
        "down left": cost_diagonal,
        "down right": cost_diagonal,
    }

    # Create maze solver object
    problem = MazeSolver(MAP)

    # Run the solver
    result = astar(problem, graph_search=True)

    # Extract the path
    path = [x[1] for x in result.path()]

    # Print the result
    print()
    for y in range(len(MAP)):
        for x in range(len(MAP[y])):
            if (x, y) == problem.initial:
                print('o', end='')
            elif (x, y) == problem.goal:
                print('x', end='')
            elif (x, y) in path:
                print('·', end='')
            else:
                print(MAP[y][x], end='')

        print()
```

    
        ##############################
        #         #              #   #
        # ####    ########       #   #
        #  o #    #              #   #
        #    ###     #####  ######   #
        #      #   ###   #           #
        #      #     #   #  #  #   ###
        #     #####    #    #  # x   #
        #              #       #     #
        ##############################
        
    
        ##############################
        #         #              #   #
        # ####    ########       #   #
        #  o #    #              #   #
        #   ·###     #####  ######   #
        #    · #   ###   #  ····     #
        #    · #     # ··# ·#  #·  ###
        #    ·#####   ·# ·· #  # x   #
        #     ········ #       #     #
        ##############################
        
    

# BFS


```python
class Node:
    def __init__(self, i, j, parent=None):
        self.i = i
        self.j = j
        self.parent = parent

    def __eq__(self, obj):
        return self.i == obj.i and self.j == obj.j

class Problem:
    def __init__(self):
        self.actions = ['R', 'L', 'U', 'D']
        MAP = """
            ##############################
            #         #              #   #
            # ####    ########       #   #
            #  o #    #              #   #
            #    ###     #####  ######   #
            #      #   ###   #           #
            #      #     #   #  #  #   ###
            #     #####    #    #  # x   #
            #              #       #     #
            ##############################
            """
        self.maze = [list(x) for x in MAP.split("\n") if x]
        self.initial_state, self.goal_state = self.get_init()

    def get_init(self):
        for idx, row in enumerate(self.maze):
            if "o" in row:
                c_node = Node(idx, row.index("o")) # Inital state
            if "x" in row:
                g_node = Node(idx, row.index("x"))  # Goal state
        
        return c_node, g_node


    def goal_test(self, node):
        return node == self.goal_state

    def print_maze(self, path):
        if isinstance(path, str): print(path)
        else:
        
            for i, row in enumerate(self.maze):
                for j, cell in enumerate(row):
                    if (i, j) in path:
                        print('+ ', end="")
                    else:
                        print(cell + " ", end="")
                print()

            print("Steps taken: ", len(path))

def BFS(problem):
    c_node = problem.initial_state

    if problem.goal_test(c_node):
        return solution(c_node)

    frontier = []  # FIFO queue/ frontier
    explored_set = []

    frontier.append(c_node)

    while True:
        if len(frontier) == 0:
            faliure = 'There is no availble path'
            return faliure

        c_node = frontier.pop(0)  # First in First out
        explored_set.append(c_node)

        for action in problem.actions:
            child = child_node(problem, c_node, action)
            if not child: continue

            if child not in explored_set and child not in frontier:
                if problem.goal_test(child):
                    return solution(child)
                frontier.append(child)


def solution(child):
    # Backtracking
    path = []
    while child:
        path.append((child.i, child.j))
        child = child.parent

    return path[::-1]


def child_node(problem, c_node, action):
    child = None
    i, j = c_node.i, c_node.j

    if action == 'R':
        j = j + 1
        if j < len(problem.maze[i]) and problem.maze[i][j] != '#':
            child = Node(i, j, c_node)

    elif action == 'L':
        j = j - 1
        if j >= 0 and problem.maze[i][j] != '#':
            child = Node(i, j, c_node)

    elif action == 'U':
        i = i - 1
        if i >= 0 and problem.maze[i][j] != '#':
            child = Node(i, j, c_node)

    elif action == 'D':
        i = i + 1
        if i < len(problem.maze) and problem.maze[i][j] != '#':
            child = Node(i, j, c_node)

    return child


problem = Problem()
path = BFS(problem)
problem.print_maze(path)

```

                            # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # 
                            #                   #                             #       # 
                            #   # # # #         # # # # # # # #               #       # 
                            #     + + #         #                             #       # 
                            #       + # # #           # # # # #     # # # # # #       # 
                            #       + +   #       # # #       #   + + + + + + +       # 
                            #         +   #           # + + + #   + #     #   +   # # # 
                            #         + # # # # #       + # + + + + #     #   +       # 
                            #         + + + + + + + + + + #               #           # 
                            # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # 
                            
    Steps taken:  35
    

# DFS


```python
import sys

class Node():
    def __init__(self, state, parent, action):
        self.state = state
        self.parent = parent
        self.action = action


class StackFrontier():
    def __init__(self):
        self.frontier = []

    def add(self, node):
        self.frontier.append(node)

    def contains_state(self, state):
        return any(node.state == state for node in self.frontier)

    def empty(self):
        return len(self.frontier) == 0

    def remove(self):
        if self.empty():
            raise Exception("empty frontier")

        else:
            node = self.frontier[-1]
            self.frontier = self.frontier[:-1]
            return node

class QueueFrontier(StackFrontier):

    def remove(self):
        if self.empty():
            raise Exception("empty frontier")
        else:
            node = self.frontier[0]
            self.frontier = self.frontier[1:]
            return node


class Maze():

    def __init__(self,filename):
        # Read file and set height and width of maze
        with open(filename) as f:
            contents = f.read()

        # Validate start and goal
        if contents.count("o") !=1:
            raise Exception("maze must have exactly one start point")
        if contents.count("x") != 1:
            raise Exception("maze must have exactly one goal")

        # Determine height and width of maze
        contents = contents.splitlines()
        self.height = len(contents)
        self.width = max(len(line) for line in contents)

        # Keep track of walls
        self.walls = []
        for i in range(self.height):
            row = []
            for j in range(self.width):
                try:
                    if contents[i][j] == "o":
                        self.start = (i, j)
                        row.append(False)

                    elif contents[i][j] == "x":
                        self.goal = (i, j)
                        row.append(False)
                    elif contents[i][j] == " ":
                        row.append(False)
                    else:
                        row.append(True)
                except IndexError:
                    row.append(False)
            self.walls.append(row)

        self.solution = None


    def printt(self):
        solution = self.solution[1] if self.solution is not None else None 
        for i, row in enumerate(self.walls):
            for j, col in enumerate(row):
                if col:
                    print("#", end="")
                elif (i, j) == self.start:
                    print("o", end="")
                elif (i,j) == self.goal:
                    print("x", end="")
                elif solution is not None and (i, j) in solution:
                    print("+", end="")
                else:
                    print(" ", end="")
            print()
        print()

    def neighbors(self, state):
        row, col = state
        # All possible actions
        candidates = [
            ("up", (row-1, col)),
            ("down", (row + 1, col)),
            ("left", (row, col - 1)),
            ("right", (row, col + 1))
        ]

        # Ensure action are valid
        result = []
        for action, (r, c) in candidates:
            try:
                if not self.walls[r][c]:
                    result.append((action, (r,c)))
            except IndexError:
                continue
        return result


    def solve(self):
        """Finds a solution to maze, if one exists."""

        # keep track of number of states explored
        self.num_explored = 0

        # Initialize frontier to just the starting position
        start = Node(state=self.start, parent=None, action=None)
        frontier = StackFrontier() #DFS
        frontier.add(start)

        # Initialize an empty explored set
        self.explored = set()

        #Keep looping until solution is found
        while True:
            # If nothing left in frontier, then no path
            if frontier.empty():
                raise Exception("No solution")

            # Choose a node from the frontier
            node = frontier.remove()
            self.num_explored += 1

            #If node is the goal, then is solution
            if node.state == self.goal:
                actions = []
                cells = []

                # Follow parent nodes to find solutions
                while node.parent is not None:
                    actions.append(node.action)
                    cells.append(node.state)
                    node = node.parent
                # Reverse the solution so it is readable
                actions.reverse()
                cells. reverse()
                self.solution = (actions, cells)
                return

            # Not the goal
            self.explored.add(node.state)

            # Add neighbors to frontier
            for action, state in self.neighbors((node.state)):
                if not frontier.contains_state((state)) and state not in self.explored:
                    child = Node(state=state, parent=node, action=action)
                    frontier.add(child)


print("Maze Solve")
maze = Maze("maze1.txt")
##print('MAP:')
##maze.printt()
print('Goal Node', maze.goal)
maze.solve()
maze.printt()
path= maze.solution
print("States Explored:",maze.num_explored)
print('Path: ',path[0],'\n')
print('Path points: ',path[1])
```

    Maze Solve
    Goal Node (7, 25)
    ##############################
    #+++++++++#              #   #
    #+####   +########       #   #
    #+ o+#  ++#              #   #
    #+  +###+    #####  ######   #
    #+  ++ #+++###   #    +++++  #
    #+   + #  +++#+++#  # +#  +###
    #+++++##### +++#++++# +# x+  #
    #              #   ++++#     #
    ##############################
    
    States Explored: 128
    Path:  ['right', 'down', 'down', 'right', 'down', 'down', 'left', 'left', 'left', 'left', 'up', 'up', 'up', 'up', 'up', 'up', 'right', 'right', 'right', 'right', 'right', 'right', 'right', 'right', 'down', 'down', 'left', 'down', 'down', 'right', 'right', 'down', 'right', 'right', 'down', 'right', 'right', 'up', 'right', 'right', 'down', 'right', 'right', 'right', 'down', 'right', 'right', 'right', 'up', 'up', 'up', 'right', 'right', 'right', 'right', 'down', 'down', 'left'] 
    
    Path points:  [(3, 4), (4, 4), (5, 4), (5, 5), (6, 5), (7, 5), (7, 4), (7, 3), (7, 2), (7, 1), (6, 1), (5, 1), (4, 1), (3, 1), (2, 1), (1, 1), (1, 2), (1, 3), (1, 4), (1, 5), (1, 6), (1, 7), (1, 8), (1, 9), (2, 9), (3, 9), (3, 8), (4, 8), (5, 8), (5, 9), (5, 10), (6, 10), (6, 11), (6, 12), (7, 12), (7, 13), (7, 14), (6, 14), (6, 15), (6, 16), (7, 16), (7, 17), (7, 18), (7, 19), (8, 19), (8, 20), (8, 21), (8, 22), (7, 22), (6, 22), (5, 22), (5, 23), (5, 24), (5, 25), (5, 26), (6, 26), (7, 26), (7, 25)]
    


```python

```
