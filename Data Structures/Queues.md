# Queues

FIFO: First-In, First-Out

```java
class Queue {

	private class Node {
		Node next;
		int data;
		public Node(int d) {
			data = d;
		}
	}

	Node head; // out
	Node tail; // in

	public Boolean isEmpty(){
		return head == null;
	}
	
	public int peek(){
		// Handle null values
		return head.data;
	}

	public void enqueue(int d){
		Node n = new Node(d);

		if(tail != null)
			tail.next = n;
		
		tail = n;

		if(head == null)
			head = tail;
	}

	public int dequeue(){
		if(head == null)
			// Handle null values

		else{
			int d = head.data;
			head = head.next;
			return d;
		}
	}
}
```