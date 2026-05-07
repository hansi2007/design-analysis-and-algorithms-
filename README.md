# design-analysis-and-algorithms-
learning codes of data structures 




def quicksort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[0]

    left = []
    right = []

    for i in arr[1:]:
        if i < pivot:
            left.append(i)
        else:
            right.append(i)

    return quicksort(left) + [pivot] + quicksort(right)


# Example
numbers = [5, 3, 8, 4, 2, 7, 1}

print("Before sorting:", numbers)

sorted_numbers = quicksort(numbers)

print("After sorting:", sorted_numbers)

Before sorting: [5, 3, 8, 4, 2, 7, 1]
After sorting: [1, 2, 3, 4, 5, 7, 8]
