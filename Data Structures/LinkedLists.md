# Linked Lists

```java
class Node {
	Node next = null;
	int data;

	public Node(int d){
		data = d;
	}

	public void appendToTail(int d){
		Node end = new Node(d);
		Node n = this;

		while (n.next != null) {
			n = n.next;
		}

		n.next = end;
	}

	public Node deleteNode(Node head, int d){
		if (head.data == d) return head.next;

		Node n = head.next;

		while (n != null) {
			if (n.data == d) {
				n = n.next;
				return head;
			}
			n = n.next;
		}
	}
}
```