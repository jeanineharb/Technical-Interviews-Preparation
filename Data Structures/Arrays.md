# Arrays

An array is a type of data structure that stores elements of the same type in a contiguous block of memory. In an array A, of size N, each memory location has some unique index, i (where 0 ≤ i ≤ N), that can be referenced as A\[i\] (you may also see it written as A_i).

- Fixed-length arrays
- Resizable arrays

## Resizable Array

```java
public class ResizableArray {
	final private int _intialCapacity = 8;
	private int[] items;
	private int size;

	public ResizableArray(){
		items = new int[_intialCapacity];
		size = 0;
	}

	public int size() {
		return size;
	}

	public void append(int item) {
		ensureExtraCapacity();
		items[size] = item;
		size++;
	}

	private void ensureExtraCapacity() {
		if(size == items.length){
			int[] copy = new int[size * 2];
			System.arraycopy(items, 0, copy, 0, size);
			items = copy;
		}
	}

	public void set(int index, int item) {
		checkBounds(index);
		items[index] = item;
	}

	public int get(int index) {
		checkBounds(index);
		return items[index];
	}

	private void checkBounds(int index) {
		if (index < 0 || index >= size) {
			throw new ArrayIndexOutOfBoundsException(index);
		}
	}
}

```

Performance considerations: An resizable array hits capacity (i.e., has to copy the contents of its underlying array over to a new array of double size) infrequently enough that storing values in a resizable array (ArrayList in Java) still averages out to constant time (as opposed to linear time).

## Left Rotation

```java
public int[] arrayLeftRotation(int[] array, int size, int shift) {
    int[] rotatedArray = new int[size];
    
    for(int i = 0; i < size; i++) {
        int newIndex = (size + i - shift) % size; 
        rotatedArray[newIndex] = array[i];
    }
    
    return rotatedArray;
}
```