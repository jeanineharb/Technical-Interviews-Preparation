# Stacks

LIFO: Last-In, First-Out

```java
public class Stack {

	private class Node {
		Node next;
		int data;
		public Node(int d) {
			data = d;
		}
	}

	Node top;

	public Boolean isEmpty() {
		return top == null;
	}

	public int peek() {
		// Handle null values
		return top.data;
	}

	public void push(int d) {
		Node n = new Node(d);
		n.next = top;
		top = n;
	}

	public int pop() {
		if(top == null)
			// Handle null values

		else{
			int i = top.data;
			top = top.next;
			return i;
		}
	}
}
```