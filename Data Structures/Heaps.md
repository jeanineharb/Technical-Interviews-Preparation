# Heaps

Heaps are tree-like structures that come in two types:
- Min Heaps
- Max Heaps

A Min Heap is a structure where the root node is always the minimum.

```java
// Easier to implement using an array.
// Binary tree structure, that we fill from left to right. 
// Easy to compute the index for left child, right child, and parent.

class MinIntHeap {
	private int capacity = 10;
	private int size = 0;

	int[] items = new int[capacity];

	private int getLeftChildIndex(int parentIndex) { return 2 * parentIndex + 1; }
	private int getRightChildIndex(int parentIndex) { return 2 * parentIndex + 2; }
	private int getParentIndex(int childIndex) { return (childIndex - 1) / 2; }

	private boolean hasLeftChild(int index) { return getLeftChildIndex(index) < size; }
	private boolean hasRightChild(int index) { return getRightChildIndex(index) < size; }
	private boolean hasParent(int index) { return getParentIndex(index) >= 0; }

	private int leftChild(int index) { return items[getLeftChildIndex(index)]; }
	private int rightChild(int index) { return items[getRightChildIndex(index)]; }
	private int parent(int index) { return items[getParentIndex(index)]; }

	private void swap(int index1, int index2) {
		int tmp = items[index1];
		items[index1] = items[index2];
		items[index2] = tmp;
	}

	private void ensureExtraCapacity() {
		if(size == capacity) {
			items = Arrays.copyOf(items, capacity * 2);
			capacity *= 2;
		}
	}

	public int peek() {
		if(size == 0) throw new IllegalStateException();
		return items[0];
	}

	// Remove minimum item from the heap (root).
	public int poll() {
		if(size == 0) throw new IllegalStateException();

		int item = items[0];
		items[0] = items[size-1];
		size--;

		// Sort the heap to have the min element as root.
		heapifyDown();

		return item;
	}

	public void add(int item) {
		ensureExtraCapacity();
		items[size] = item;
		size++;

		// Sort the heap to ensure that the min element is still the root.
		heapifyUp();
	}

	// Sort the heap to ensure that the min element is still the root.
	public void heapifyUp() {
		int index = size - 1;

		while(hasParent(index) && parent(index) > items[index]){
			swap(getParentIndex(index), index);
			index = getParentIndex(index);
		}
	}

	// Sort the heap to have the min element as root.
	public void heapifyDown() {
		int index = 0;

		while(hasLeftChild(index)) {
			int smallerChildIndex = getLeftChildIndex(index);
			
			if(hasRightChild(index) && rightChild(index) < leftChild(index))
				smallerChildIndex = getRightChildIndex(index);
			
			if(items[index] < items[smallerChildIndex])
				break;
			else 
				swap(index, smallerChildIndex);
			
			index = smallerChildIndex;
		}
	}
}
```