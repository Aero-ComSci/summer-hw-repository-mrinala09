# Selection Sort
-------
A sorting algorithm is an algorithm in which you find the smallest element in any list (unsorted) and replace it at the "beginning" of the list, and this repeats till the whole list is sorted in the correct order. 
## Brief Rundown

1. Set the first element (index 0) as the smallest element
   
   <img width="739" alt="Screen Shot 2024-08-12 at 1 59 41 PM" src="https://github.com/user-attachments/assets/a94dcdcc-5501-4bae-9c71-c310d2fa0654">

2. Then check if the first element is smaller than the second element, if it isn't then assign the second element as the smallest element
   * Now compare it to the third element, if its smaller than assign the third element as the smallest element, otherwise do nothing.
   * This keeps repeating till you've reached the last element
     
     <img width="735" alt="Screen Shot 2024-08-12 at 2 01 57 PM" src="https://github.com/user-attachments/assets/59d46824-c5e6-4960-9e36-1cf4f8554200">
     
3. After each iteration we place the smallest element that we have gotten at the start of the list (index 0) or in front of the unsorted list

   <img width="735" alt="Screen Shot 2024-08-12 at 2 14 41 PM" src="https://github.com/user-attachments/assets/1aed1c42-cb49-41e5-9d04-ee63bbe2335a">

4. Now for every next iteration the index starts from the next element (the first element of the unsorted list), this creates continuous subarrays after each iteration

   <img width="739" alt="Screen Shot 2024-08-12 at 2 15 17 PM" src="https://github.com/user-attachments/assets/13ef7d99-92d7-4fb8-a5b0-a31ceda3b609">

   ^^ similar pattern for each iteration

   Last iteration example below
   
   <img width="738" alt="Screen Shot 2024-08-12 at 2 18 09 PM" src="https://github.com/user-attachments/assets/456a3524-24ee-4296-ab5e-3cafbb93d617">

5. Now go code
6. You're still here...
7. ...
8. ...

In short, the [Sorting Algorithm]([https://website-name.com](https://website-name.com)) arranges an unsorted list in an ascending order in such a way that it checks and compares each element in said list

CODE 

```python 

def swap(array, x, y):
  temp = array[x]
  array[x] = array[y]
  array[y] = temp

  return array

def index_smallest(array, start):
  smallest = array[start]
  index_smallest = start
  for i in range(start + 1, len(array)):
    if array[i] < smallest:
      smallest = array[i]
      index_smallest = i
  return index_smallest

def sort(array):
  for i in range(len(array)):
    smallest_num_index = index_smallest(array, i)
    if smallest_num_index != i:
      swap(array, smallest_num_index, i)
  return array

array = [-1,0, 17, -3, 4, 9, 18, 31, 29, 91, 1]
sort(array)
print(array)


