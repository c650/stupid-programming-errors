# Stupid Programming Errors
A list of stupid programming errors. Fork and PR [to contribute](/CONTRIBUTING.md).

## Incrementing `i` in the `j` loop.
```
for (int i = 0; i < n; ++i) {
	for (int j = i+1; j < n; ++i) {
		/* do you see it? */
	}
}
```

## Forgetting to read in the first part of input
This most frequently occurs when doing ICPC type stuff.

```
int n;
/* forget to read in n. */

std::vector<int> vec(n);
for (auto& e : vec)
	std::cin >> e;  /* vec[0] holds what should be in n, if n even happens to be non-zero (declare w/o define is UB) */
```

## [C++] Calling the default constructor with parenthesis, essentially declaring some sort of function

```
std::vector<int> vec(); /* can't do this */
vec.push_back(5);
```

Yields this compile error:

> request for member ‘push_back’ in ‘vec’, which is of non-class type ‘std::vector<int>()’

At first glance, it's an odd error.
