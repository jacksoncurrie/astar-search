# A* Search Algorithm

A searching algorithm to find the best path to a goal.

## Terms Defined

### `start_node`

The position on the map that the algorithm starts at denoted with a tuple, e.g. `(0,0)`.

### `end_node`

The position on the map that the algorithm finishes at denoted with a tuple, e.g. `(0,0)`.

### `heuristic`

The estimated distance from the current node to the final node. Used to see if the next move is better than another move. It is also known as the *h* value which is used in the calculation for A* search algorithms.

### `child.g, child.f, child.h`

The values used in the equation `f(n) = g(n) + h(n)`. `child.g` is used to work out the distance from the start, `child.h` is the heuristic (explained above), and `child.f` is worked out from the equation, and is used as the calculation to prioritize the next nodes to check.

### `open_list`

The A* algorithm uses a priority queue to try the best estimated moves first. The `open_list` is the priority queue, and the next best nodes to try (worked out from the equation above) will be at the top.

### `closed_list`

The `closed_list` is the moves that have already been moved to, which are stored so that the algorithm doesn't have to re-check a node that has already been moved to. These are the nodes that shouldn't be tried again.

### `current_node`

The current position on the map that the algorithm is at, it checks the nodes around this node to find next node to move to and change the `current_node` to that one.

### `open_list.append(start_node)`

Add the start node to the open list which is where the algorithm will start and begin searching for the path the the final node, adding the next best nodes to this `open_list`.

### `tuples`

A tuple is an ordered an unchangeable list used in the Python programming language (which is being used for this algorithm). It is used in this algorithm to display the coordinates of nodes, such as where to start (`start = (0, 0)`).

### `visited_nodes`

The nodes that have already been visited by the algorithm, and make up the path to the goal. They get placed into the `closed_list` as these should not be evaluated by the algorithm as they don't want to be moved to twice.

### `goal_found`

When the end node is found by the algorithm so the path is complete. This variable is used to stop the algorithm when the `current_node` is the same as the `end_node`.

### `walkable`

Whether there is a wall that doesn't allow the algorithm to move to. This is when the algorithm is checking neighbouring nodes and the node gives back a *1* which is a wall, and is not `walkable`.

## How does the program recognise the difference between a valid move and an invalid move?

The algoritms iterates through the lsit of tuples that the algorithm can move to from its current location. When the algorithm checks all these positions from the current node, if the location is not a `0` (must be a `1`) then the algorthm skips checking this position as it is a wall and connot move here. The algorithm also checks to make sure the move is within the bounds of the map (2d array) specified; it will also skip this position if it finds it there. These are the invalid moves of the prgram which are checked at the top of the position check loop.

## How does the program find and test its neighbour nodes?

As explained above we specify a list of tuples that are the coordinate directions of the neighbour nodes from the current node. For example, the tuple `(-1, 1)` would mean that the cell 1 above and 1 right (diagonal) should be checked as a valid place to move. All 8 cell directions are vaild moves for this program, so they should all be added to the list to be checked. The prgram loops over this list, and adds the direction to the current node to check the actual new position on the map.

## How and why values from the open-list will interact with the closed-list?

The `open_list` holds the best estimates for the algorithm to check first. The `closed_list` holds the nodes that should not be re-evaluated by the program as they have already been moved to. This means that the current node being evaluated, that will be in the `open_list`, will be moved to the `closed_list` and removed from the top of `open_list` as it should not be moved to again, as retracing a node will not be the shortest route.

## What is the role of the Pythagoras Theorum used in the code?

It is used to work out the heuristic value. The heuristic value is explained above, and its estimate for this algorithm is the direct distance from the current node to the goal node. It uses the Pythagoras Theorum to work out the direct distance from the horizontal and vertical distance supplied by the coordinates on the map. It estimates the distance cost to the final node and is used to prioritize the nodes in `open_list`.

## What is the Manhattan distance and how does it relate to an A* search?

The Manhattan distance is the distance over only the x and y axes (only horizontal and vertical distance). For example the distance from point (0,0) to (2,5) would be 7 (2 + 5). the Manhattan distance doesn't work out diagonals, and is used in algorithms like this one when diagonals are not permitted (the only directions to go are left, right, up or down). In this algorithm diagonals are allowed, so the Manhattan distance is not used, but should be considered if diagonals are not allowed.
