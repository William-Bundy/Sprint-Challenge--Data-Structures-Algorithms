# Analysis of Algorithms
**Exercise I**: _Give an analysis of the running time of each snippet of pseudocode with respect to the input size n of each of the following:_
```
a)  a = 0
    while (a < n * n * n) 
      a = a + n * n
```
"Take steps of n^2 until you reach n^3"
`O(n ^ (3/2))`

```
b)  sum = 0
    for (i = 0; i < n; i++)
      for (j = i + 1; j < n; j++)
        for (k = j + 1; k < n; k++)
          for (l = k + 1; l < 10 + k; l++)
            sum++
```

"Do an operation 10 times for every combination of 3 objects"

`O(5(n^3)))`


```
c)  bunnyEars = function(bunnies) {
      if (bunnies == 0) return 0
      return 2 + bunnyEars(bunnies-1)
    }
```
`O(bunnies)`


**Exercise II**:
Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.

Binary search uses `O(log(eggs dropped)))` steps

```
typedef int32_t i32;
typedef ptrdiff_t isize;

i32 eggFloor(i32 secretEggFloor, i32 height)
{
	isize min = 0, max = height - 1, mid = 0;
	while(min <= max) {
		mid = (min + max) / 2;
		// mid is the floor
		if(mid == secretEggFloor) {
			return mid;
		} else if(mid < secretEggFloor) { // egg didn't break
			min = mid + 1;
		} else { // egg broke
			max = mid - 1;
		}
	}

	// eggs don't break in this universe
	return -1;
}

```
