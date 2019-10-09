# Fibonacci Series

## Iterative Solution

```java
// java
public long fibonacci(int n) {
	if(n == 0) return 0;
	if(n < 3) return 1;

	long u1 = 1;
	long u2 = 1;
	long un = 0;

	for(int i = 3; i <= n; i++) {
		un = u2 + u1;
		u1 = u2;
		u2 = un;
	}
	return un;
}
```

```python
# python
def fibonacci_generator(n):
	if n < 1 :
		return [0]

	arr = [0, 1]
	for i in range(2, n+1):
		arr.append(arr[i-1] + arr[i-2])

	return arr
```

## Recursive Solution

```java
// java
int fibonacci(int n) {
    if(n == 0) return 0;
    if(n == 1) return 1;
    return fibonacci(n-1) + fibonacci(n-2);
}
```