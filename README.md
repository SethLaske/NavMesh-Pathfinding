# NavMesh-Pathfinding
Use Processing to create a simulation that allows for an AI to pathfind using automatically generated NavMeshes

Project for CS 4990
Due 11/9/2022
Baseline code and structure provided by Professor Eger
Group Project with Alec

Lab created to learn about steering behaviors for making smooth and natural game AI agents with linear and rotational accelerations
as well as pathfinding using A* and NavMeshes
Processing was used for its easy to learn graphic system

Steering Behavior
The steering behavior prioritizes making the turn to its target first, before accelerating to its given maximum speed
It slows down based on a ratio of how tight the turn is and also double checks the following distance between points to avoid hitting a turn at high speed

NavMesh Generation
To create a NavMesh without an convex polygons, the border walls are ordered moving counter clockwise. Using this a new wall is created by moving along the
order until a point is found that is both reachable and will create a non reflex point. Then a pair of walls is created to form two new ordered polygons
and the split function is called recursively. After that each wall object will contain a list of adjacent walls and the edged, stored individually as well
as together in a Hashmap.

Pathfinding
Finding a path between the agents initial position and the target is done using A*, using the center point of each convex polygon. Once the optimal path is
found, the agent will follow a list of targets that use the center points of each connecting wall for the path rather than the center points to avoid 
crashing. A list of followpoints can be provided at once to the agent, and a path will be found from one point to the next.

Further changes/improvements that can be made:
Simplifying the process for matching a node to their neighbors and edges. The HashMap is efficient, but the code is a bit difficult to understand and should be made more intuitive
Reducing additional code that was created for various stages of trouble shooting, or as various progress checkpoints
Adding compatibility with obstacles, whether randomly generated or manually placed
Potential for adding more agents with flocking, allowing them to follow the central agent without colliding with each other or the walls as they follow the path to the destination
