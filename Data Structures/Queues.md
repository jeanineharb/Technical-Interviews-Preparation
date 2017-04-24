# Queues

FIFO: First-In, First-Out

```java
public class Queue {

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

## Implementing a queue using two stacks

```java
public class QueueWithTwoStacks<T> {

	Stack<T> stackNewestOnTop = new Stack<T>();
    Stack<T> stackOldestOnTop = new Stack<T>();

    public void enqueue(T value) {
        stackNewestOnTop.push(value); 
    }

    public T peek() {
        prepOld();
        return stackOldestOnTop.peek();
    }

    public T dequeue() {
        prepOld();
        return stackOldestOnTop.pop();
    }
    
    private void prepOld(){
        if(stackOldestOnTop.isEmpty()){
            while(!stackNewestOnTop.isEmpty()){
                stackOldestOnTop.push(stackNewestOnTop.pop());
            }
        }
    }
}
```