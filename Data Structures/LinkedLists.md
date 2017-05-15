# Linked Lists

```java
public class Node {
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

## Cycle Detection

Algorithm based on [Floyd's cycle-finding algorithm](https://en.wikipedia.org/wiki/Cycle_detection#Tortoise_and_hare), also known as Tortoise and Hare algorithm.

```java
boolean hasCycle(Node head) {   
    if(head == null)
        return false;
    
    else {
        Node slow, fast; // create two references.
        slow = fast = head; // make both refer to the start of the list.

        while(true) {
            slow = slow.next;          // 1 hop.

            if(fast.next != null)
                fast = fast.next.next; // 2 hops.
            else    
                return false;   // next node null => no loop.

            if(slow == null || fast == null) // if either hits null..no loop.
                return false; 
            
            if(slow == fast) // if the two ever meet...we must have a loop.
                return true;
        }
    }
}
```

## Merge Lists

```java
Node mergeLists(Node headA, Node headB) {
    if(headA == null) return headB;
    if(headB == null) return headA;

    if(headA.data > headB.data) {
        Node tmp = headB; 
        headB = headB.next;
        tmp.next = headA;
        headA = tmp; 
    }
    
    headA.next = mergeLists(headA.next, headB);
    return headA;
}
```