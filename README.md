This project is part of Freecodecamp's [Scientific Computing with Python](https://www.freecodecamp.org/learn/scientific-computing-with-python/) curriculum

```py
'''
The merge sort algorithm mainly performs three actions:

1. Divide an unsorted sequence of items into sub-parts
2. Sort the items in the sub-parts
3. Merge the sorted sub-parts

The above happens recursively until the sub-parts are merged into the complete sorted sequence. Let's start by dividing the sequence.
'''
def merge_sort(array):
    if len(array) <= 1: # Base case. If the array length is 1, there is no need to go down
        return

    middle_point = len(array) // 2 # Find the mid index of the array.
    left_part = array[:middle_point] # Making a copy of the `array` upto mid index
    right_part = array[middle_point:] # Making a copy of the `array` from mid index to last index

    merge_sort(left_part) # Recursively calling
    merge_sort(right_part) # Recursively calling

    left_array_index = 0
    right_array_index = 0
    sorted_index = 0

    while left_array_index < len(left_part) and right_array_index < len(right_part):
        if left_part[left_array_index] < right_part[right_array_index]:

            array[sorted_index] = left_part[left_array_index]
            # Assign the value at the specified index to the array where it is being sorted

            left_array_index += 1 # To move to the next index, increase the value of index by 1
        else:
            array[sorted_index] = right_part[right_array_index]
            # Assign the value at the specified index to the array where it is being sorted

            right_array_index += 1 # To move to the next index, increase the value of index by 1

        sorted_index += 1 # To move to the next index for sorting, increase the value of index by 1

    # The while loop compares one element from left_part with another in right_part, then adds the smaller element to the main array list. The process will continue until there are no elements left to be compared.

    # But left_part may still have elements left while right_part has none, and vice versa. To solve this issue following while loops are created.

    while left_array_index < len(left_part):
        array[sorted_index] = left_part[left_array_index]
        left_array_index += 1
        sorted_index += 1

    while right_array_index < len(right_part):
        array[sorted_index] = right_part[right_array_index]
        right_array_index += 1
        sorted_index += 1




# The following codes are modified

numbers = input('Enter numbers: ')

numbersArray = [int(num) for num in numbers.split()]

print(f'Unsorted array : {' '.join(map(str,numbersArray))}')

if __name__ == '__main__':

    merge_sort(numbersArray)

    print(f'Sorted array: {' '.join(map(str,numbersArray))}')
```
