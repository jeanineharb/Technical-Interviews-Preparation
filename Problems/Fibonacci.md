# Fibonacci Series

```java
public class Fibonacci {

	public long computeFibonacciSeries(int n) {
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
	
	public static void main(String[] args) {
		Fibonacci f = new Fibonacci();
		int n = Integer.parseInt(args[0]);

		System.out.println("Fibonacci number at position " + n + ": " + f.computeFibonacciSeries(n));
	}
}
```