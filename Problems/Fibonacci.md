# Fibonacci Series

## Iterative Solution

```java
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

## Recursive Solution

```java
int fibonacci(int n) {
    if(n == 0) return 0;
    if(n == 1) return 1;
    return fibonacci(n-1) + fibonacci(n-2);
}
```