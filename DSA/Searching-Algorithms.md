# Searching Algorithms

<hline>
  
## Linear Search

### Theory :

- Linear Search is the search which checks every value in a given array whether it matches the given key or not.
- In Linear Search, we provide a key to check the elements in the array
- If the key matches with the value, it prints the position of the value in the array
- If the array is having unique values, we can break the loop, or it continues until the end of the array to check more values.
- Else if the key is not present we return -1

### Pseudo Code :
```
int linearSearch (int array[], int size, int key){
  int i=0;
  while(i<size){
    if(key==array[i]){
      return i    \\return i+1 if indexing wrt to 1
     }
    i++;
  }
  if(i==size)
    return -1
}
```
