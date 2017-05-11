# Graphs

## Graph Traversal

- Depth First Search: DFS involves searching a node and all its children before proceeding to its siblings.

- Breadth First Search: BFS involves searching a node and its siblings before going on to any children.

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
}

```