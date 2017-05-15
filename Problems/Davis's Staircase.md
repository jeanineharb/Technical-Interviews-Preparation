# Davis's Staircase

Davis has a staircase in his house and he likes to climb it 1, 2, or 3 steps at a time. How many ways are there to reach the top of the staircase ?

```java
public int staircase(int n) {
    if(n == 0) return 1;
    if(n < 0) return 0;
    return staircase(n-1) + staircase(n-2) + staircase(n-3); 
}
```