# Sequential Search (Linear Search)

**Step to perform binary search:**
1. Sequentially walk through the array, starting with the first element
2. Compares each element with the element we are looking for, stops when
  * The element looking for is same as the element *OR*
  * Reach the end of the array
3. The index of the element at the stopping position is the result

## Code Sample

C++:
```C++
int sequentialSearch(int arr[], int first, int last, int key) {
  for(int index = first; index <= last; index++) {
    if(key == arr[index]) {
      return index; // found! return index
    }
  }
  return -1; // key is not found
}
```

## Complexity Analysis

* Time complexity : $${O}(n)$$
