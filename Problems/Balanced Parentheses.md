# Balanced Parentheses

Given an expression string `exp`, write a program to examine whether the pairs and the orders of “{“,”}”,”(“,”)”,”[“,”]” are correct in `exp`.

```python
# python
def isBalanced(s):
	stack = []

	for c in s:
		if c in ["{", "[", "("]:
			stack.append(c)
		else:
			p = stack.pop()
			if (c == "}" and p == "{") or (c == "]" and p == "[") or (c == ")" and p == "("):
				continue
			else:
				return False

	return len(stack) == 0


if __name__ == "__main__":
	s = "[()]{}{[("

	if isBalanced(s):
		print("Balanced")
	else:
		print("Not Balanced")
```