# Sorting

## Bubble Sort

Start at the beginning of an array and swap the first two elements if the first is bigger than the second. Go to the next pair, etc, continuously making sweeps of the array until sorted. 

Complexity: O(n^2).

```java
public void bubbleSort(int[] array) {
	for(int i=0; i < array.length-1; i++) {
		for(int j=i+1; j < array.length; j++) {
			if(array[i] > array[j]) {
				int tmp = array[i];
				array[i] = array[j];
				array[j] = tmp;
			}
		}
	}
}
```

## Selection Sort

Find the smallest element using a linear scan and move it to the front. Then, find the second smallest and move it, again doing a linear scan. Continue doing this until all the elements are in place. 

Complexity: O(n^2).

```java
public void selectionSort(int[] a) {
	for(int i=0; i < a.length; i++){
		int min = a[i];
		int min_index = i;

		for(int j=i+1; j < a.length; j++) {
			if(a[j] < min){
				min = a[j];
				min_index = j; 
			}
		}
	
		a[min_index] = a[i];
		a[i] = min;
	}
}
```

## Merge Sort

Sort each pair of elements. Then, sort every four elements by merging every two pairs. Then, sort every 8 elements, etc. 

Complexity: O(n log n) expected and worst case.

```java
public void mergeSort(int[] a){
	mergeSort(a, new int[a.length], 0, a.length - 1);
}

private void mergeSort(int[] a, int[] tmp, int leftStart, int rightEnd) {
	if(leftStart >= rightEnd) return;
	
	int middle = (leftStart + rightEnd) / 2;
	mergeSort(a, tmp, leftStart, middle);
	mergeSort(a, tmp, middle + 1, rightEnd);
	mergeHalves(a, tmp, leftStart, rightEnd);
}

private void mergeHalves(int[] a, int[] tmp, int leftStart, int rightEnd) {
    int leftEnd = (leftStart + rightEnd) / 2;
    int rightStart = leftEnd + 1;
    int size = rightEnd - leftStart + 1;

    int leftIndex = leftStart;
    int rightIndex = rightStart;
    int index = leftStart;

    while(leftIndex <= leftEnd && rightIndex <= rightEnd) {
        if(a[leftIndex] <= a[rightIndex]){
            tmp[index] = a[leftIndex];
            leftIndex++;
        }
        else{
            tmp[index] = a[rightIndex];
            rightIndex++;
        }
        index++;
	}

    System.arraycopy(a, leftIndex, tmp, index, leftEnd - leftIndex + 1);	
    System.arraycopy(a, rightIndex, tmp, index, rightEnd - rightIndex + 1);
    System.arraycopy(tmp, leftStart, a, leftStart, size);
}
```

## Quick Sort

Pick a random element and partition the array, such that all numbers that are less than it come before all elements that are greater than it. Then do that for each half, then each quarter, etc. 

Complexity: O(n log n) expected, O(n^2) worst case.

```java
public void quickSort(int[] a) {
	quickSort(a, 0, a.length - 1);
}

private void quickSort(int[] a, int left, int right) {
	if(left >= right) return;
	
	int pivot = a[(left + right) / 2];
	int index = partition(a, left, right, pivot);
	quickSort(a, left, index - 1);
	quickSort(a, index, right);
}

private int partition(int[] a, int left, int right, int pivot) {
	while(left <= right){
		while(a[left] < pivot) left++;
		while(a[right] > pivot) right--;

		if(left <= right){
			// Swap items
			int tmp = a[left];
			a[left] = a[right];
			a[right] = tmp;

			left++;
			right--;
		}
	}
	return left;
}
```

## Bucket Sort

Partition the array into a finite number of buckets, and then sort each bucket individually. 

Complexity: O(n + m), where n is the number of items and m is the number of distinct items.

```java
```