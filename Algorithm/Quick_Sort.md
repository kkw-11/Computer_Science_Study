# Quick Sort

- 퀵 정렬은 병합 정렬과 마찬가지로 '분할 정복(divide and conquer')에 근거하여 만들어진 정렬 방법이다.
  - 정렬의 대상이 되는 배열에서 하나의 원소를 고른다. 이 원소를 pivot이라고 한다.
  - 피벗을 기준으로 앞에는 피벗보다 작은 원소를 뒤에는 큰 원소들이 오도록 피벗을 기준으로 배열을 둘로 나눈다.(오름차순 정렬 기준)
  - 둘로 나누어진 배열에 대해서 재귀(recursion)적으로 반복한다. 배열의 원소의 개수가 1이 될때 까지 반복한다.

## 시간복잡도

- pivot과 원소들을 비교하는 횟수는 자료의 개수(N)에 비례한다.
- 그리고 위에서 한 행위가 배열의 범위가 분할 되면서 재귀 호출이 되는데 이것은 logN에 비례한다.
- 그래서 시간복잡도를 계산하면 O(NlogN)이 나온다.


```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    lesser_arr, equal_arr, greater_arr = [], [], []
    for num in arr:
        if num < pivot:
            lesser_arr.append(num)
        elif num > pivot:
            greater_arr.append(num)
        else:
            equal_arr.append(num)
    return quick_sort(lesser_arr) + equal_arr + quick_sort(greater_arr)
```
