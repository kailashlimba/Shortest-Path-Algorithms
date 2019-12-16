# Shortest-Path-Algorithms


# Bellman Ford's algorithm

It is used to find the shortest paths from the source vertex to all other vertices in a weighted graph. It depends on the following concept: Shortest path contains at most n-1 edges, because the shortest path couldn't have a cycle.

So why shortest path shouldn't have a cycle ?
There is no need to pass a vertex again, because the shortest path to all other vertices could be found without the need for a second visit for any vertices.

Algorithm Steps:

1. The outer loop traverses from 0 to n-1.
2. Loop over all edges, check if the next node distance > current node distance + edge weight, in this case update the next node distance to "current node distance + edge weight".

This algorithm depends on the relaxation principle where the shortest distance for all vertices is gradually replaced by more accurate values until eventually reaching the optimum solution. In the beginning all vertices have a distance of "Infinity", but only the distance of the source vertex = , then update all the connected vertices with the new distances (source vertex distance + edge weights), then apply the same concept for the new vertices with new distances and so on.
Time Complexity of Bellman Ford algorithm is relatively high O(V.E). In case V=E2, it is O(E3).



# Dijkstra's algorithm

It has many variants but the most common one is to find the shortest paths from the source vertex to all other vertices in the graph.

Algorithm Steps:

1. Set all vertices distances = infinity except for the source vertex, set the source distance = 0.
2. Push the source vertex in a min-priority queue in the form (distance , vertex), as the comparison in the min-priority queue will be according to vertices distances.
3. Pop the vertex with the minimum distance from the priority queue (at first the popped vertex = source).
4. Update the distances of the connected vertices to the popped vertex in case of "current vertex distance + edge weight < next vertex distance", then push the vertex with the new distance to the priority queue.
5. If the popped vertex is visited before, just continue without using it.
6. Apply the same algorithm again until the priority queue is empty.

Time Complexity of Dijkstra's Algorithm is O(V2) but with min-priority queue it drops down to O(V+ElogV) .

# Floyd–Warshall's Algorithm

It is used to find the shortest paths between between all pairs of vertices in a graph, where each edge in the graph has a weight which is positive or negative. The biggest advantage of using this algorithm is that all the shortest distances between any  vertices could be calculated in O(V3) , where V is the number of vertices in a graph.

The Algorithm Steps:

For a graph with N vertices:

1. Initialize the shortest paths between any 2 vertices with Infinity.
2. Find all pair shortest paths that use 0 intermediate vertices, then find the shortest paths that use  intermediate vertex and so on.. until using all N vertices as intermediate nodes.
3. Minimize the shortest paths between any 2 pairs in the previous operation.
4. For any 2 vertices (i,j), one should actually minimize the distances between this pair using the first  nodes, so the shortest path will be: min(dist[i][j],dist[i][k]+dist[k][j]).
dist[i][k] represents the shortest path that only uses the first K vertices, dist[k][j] represents the shortest path between the pair k,j. As the shortest path will be a concatenation of the shortest path from i to k, then from k to j.



