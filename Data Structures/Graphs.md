# Graphs

Graph is a data structure that consists of following two components:
- A finite set of vertices also called as nodes.
- A finite set of ordered pair of the form (u, v) called as edge. The pair is ordered because (u, v) is not same as (v, u) in case of directed graph(di-graph). The pair of form (u, v) indicates that there is an edge from vertex u to vertex v. The edges may contain weight/value/cost.

## Graph Representation

The most commonly used representations of a graph are:
- Adjacency Matrix
- Adjacency List
- Edge List

### Adjacency Matrix

Adjacency Matrix is a 2D array of size V x V where V is the number of vertices in a graph. 

Let the 2D array be adj[][], a slot adj[i][j] = 1 indicates that there is an edge from vertex i to vertex j. 

Adjacency matrix for undirected graph is always symmetric. 

Adjacency Matrix is also used to represent weighted graphs. If adj[i][j] = w, then there is an edge from vertex i to vertex j with weight w.

**Pros**: Representation is easier to implement and follow. Removing an edge takes O(1) time. Queries like whether there is an edge from vertex ‘u’ to vertex ‘v’ are efficient and can be done O(1).

**Cons**: Consumes more space O(V^2). Even if the graph is sparse(contains less number of edges), it consumes the same space. Adding a vertex is O(V^2) time.

### Adjacency List

An array of linked lists is used. Size of the array is equal to number of vertices. 

Let the array be array[]. An entry array[i] represents the linked list of vertices adjacent to the ith vertex. 

This representation can also be used to represent a weighted graph. The weights of edges can be stored in nodes of linked lists.

**Pros**: Saves space O(|V|+|E|) . In the worst case, there can be C(V, 2) number of edges in a graph thus consuming O(V^2) space. Adding a vertex is easier.

**Cons**: Queries like whether there is an edge from vertex u to vertex v are not efficient and can be done O(V).

## Graph Traversal

- Depth First Search: DFS involves searching a node and all its children before proceeding to its siblings.

- Breadth First Search: BFS involves searching a node and its siblings before going on to any children.

### Edge List

One simple way to represent a graph is just a list, or array of |E| edges, which we call an edge list. 

To represent an edge, we just have an array of two vertex numbers, or an array of objects containing the vertex numbers of the vertices that the edges are incident on. 

If edges have weights, add either a third element to the array or more information to the object, giving the edge's weight.

**Pros**: Saves space, simple to implement.

**Cons**: If we want to find whether the graph contains a particular edge, we have to search through the edge list. 

```java
public class Graph {
	private HashMap<Integer, Node> nodeLookup = new HashMap<>();

	public static class Node {
		private int id;
		LinkedList<Node> adjacent = new LinkedList<>();

		private Node(int id) {
			this.id = id;
		}
	}

	private Node getNode(int id) {
		return nodeLookup.get(id);
	}

	public void addEdge(int source, int destination) {
		Node s = getNode(source);
		Node d = getNode(destination);
		s.adjacent.add(d);
	}

	// DFS
	public boolean hasPathDFS(int source, int destination) {
		Node s = getNode(source);
		Node d = getNode(destination);
		HashSet<Integer> visited = new HashSet<>();
		return hasPathDFS(s, d, visited);
	}

	private boolean hasPathDFS(Node s, Node d, HashSet<Integer> visited) {
		if(visited.contains(s.id)) return false;

		visited.add(s.id);
		if(s == d) return true;

		for(Node child : s.adjacent){
			if(hasPathDFS(child, d, visited)) return true;
		}
		
		return false;
	}

	// BFS
	public boolean hasPathBFS(int source, int destination) {
		LinkedList<Node> nextToVisit = new LinkedList<>();
		HashSet<Integer> visited = new HashSet<>();

		nextToVisit.add(source);

		while(!nextToVisit.isEmpty()) {
			Node node = nextToVisit.remove();

			if(node == destination) return true;

			if(visited.contains(node.id)) continue;
			visited.add(node.id);

			for(Node child : node.adjacent) {
				nextToVisit.add(child);
			}
		}
		
		return false;
	}
}

```