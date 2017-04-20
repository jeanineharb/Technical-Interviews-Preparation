# Linked Lists

```java
class Node {
	Node next = null;
	int data;

	public Node(int d){
		data = d;
	}

	public void appendToTail(Node head, int d){
		if(head == null){
	        head = new Node(d);
	    }
    	else{
	        Node n = head;
	        while(n.next != null){
	            n = n.next;
	        }
	        n.next = new Node(d);
	    }
	    return head;
	}

	public Node insertAtBeginning(Node head, int x) {
    	if(head == null) {
        	head = new Node(x);
    	}
    	else{
        	Node n = head; 
	        head = new Node(x);
	        head.next = n;
	    }
    	return head;
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