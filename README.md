# Merge Sort Using Divide-and-Conquer

## 1. Aim

To implement the Merge Sort algorithm using the Divide-and-Conquer technique to sort product prices in ascending order and count the number of comparisons.

## 2. What is Merge Sort?

Merge Sort is a sorting algorithm based on the Divide-and-Conquer technique. It divides an array into smaller subarrays, recursively sorts them, and merges the sorted subarrays to produce the final sorted array.

### Main Steps

1. Divide the array into two halves.
2. Recursively sort both halves.
3. Merge the sorted halves.
4. Continue until the complete array is sorted.

## 3. Uses

- Sorting large amounts of data.
- Sorting product prices, marks, and records.
- Useful when stable sorting is required.
- Used in external sorting.
- Provides consistent `O(N log N)` performance.

## 4. Program

```python
def merge_sort(arr):
    global comparisons

    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2

    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)


def merge(left, right):
    global comparisons

    result = []
    i = j = 0

    while i < len(left) and j < len(right):
        comparisons += 1

        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])

    return result


n = int(input("Enter number of product prices: "))

prices = list(map(int, input(f"Enter {n} product prices : ").split()))

if len(prices) != n:
    print(f"Please enter exactly {n} prices.")
else:
    comparisons = 0

    sorted_prices = merge_sort(prices)

    print("Sorted product prices:")
    print(sorted_prices)

    print("Number of comparisons:", comparisons)
```

## 5. Input

```text
Enter number of product prices: 10
Enter 10 product prices : 50 20 80 10 40 70 30 90 60 100
```

## 6. Output

```text
Sorted product prices:
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

Number of comparisons: 21
```

## 7. Time Complexity

| Case | Complexity |
|---|---|
| Best Case | O(N log N) |
| Average Case | O(N log N) |
| Worst Case | O(N log N) |
| Space Complexity | O(N) |

## 8. Analysis

Merge Sort divides the array into smaller subarrays and merges them in sorted order. The array is divided into `log N` levels, and each level requires `O(N)` work for merging. Therefore, the overall time complexity is `O(N log N)`.

## 9. Result

The product prices were successfully sorted in ascending order using the Merge Sort algorithm, and the number of comparisons was calculated.


