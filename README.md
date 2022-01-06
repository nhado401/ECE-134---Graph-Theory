# ECE-134---Graph-Theory
This is the project in which I was provided a list of sensor locations in a 300x300 map. My task was to design an algorithm to find a shortest route for a drone starting at the central node (150,150), where the receiver/sink will be, visit all other nodes and return to the same point. Moreover, because it is a large drone, as it flies above a square x, it can simultaneously drop sensors not only on the square x but also on all neighboring squares inside a 5 x 5 square with center x.

My algorithm is as follow:
1) Create a minimum spanning tree represented by an adjacency matrix.
2) Choose the path that has the smallest distance from the sink and traverse it to find the last leaf node in this path. For each visited node, we will replace it with 0 in the adjacency matrix and remove it from the nodes list.
3) For each node we visit, we will also search in its 5x5 area. If there exist any nodes inside that area, we will count them as visited nodes, and remove them from the list of nodes. We will not consider them in the final trajectory because according to our assumption, we do not need to visit these nodes.
4) When we are at the end of the path, we will create a new minimum spanning tree between the last leaf node and other existence nodes.
5) Repeat steps 2-4 until there is only one node left in the spanning tree.
6) Calculate the distance from the last node to the sink.

However, the run time was very terrible and I was not able to run the program for the entire map (with 1269 sensors). For the convenience, I only ran it with the first 400 sensors, but by observing the trajectory, the algorithm is not too bad.

You can create any arbitrary list of node to test the program, it works well for all cases.
