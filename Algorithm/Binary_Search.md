# Binary Search

- 정렬된 데이터 집합에서 사용할 수 있는 탐색 알고리즘

## Binary Search Algorithm process

- 정렬된 데이터의 집합이 중앙에 있는 요소를 고릅니다.
- 중앙 요쇼의 값과 찾고자 하는 목표 값(target)을 비교합니다.
- 목표 값이 중앙 요소의 값보다 작다면 데이터 집합의 왼편에 대해 새로 검색을 수행하고 크다면 오른편에 대해 이진 탐색을 새롭게 수행합니다.
- 찾고자 하는 값을 찾을 때 까지 위 과정을 반복합니다.

```c
#include <stdio.h>
#include <stdlib.h>
void PrintList(int list[], int size)
{
	for (int i = 0; i < size; ++i)
		printf("%5d", list[i]);
	printf("\n");
}
int BSearch(int data, int list[], int size, int (*cmp)(int, int))
{
	int left = 0;
	int right = size - 1;
	while (left <= right)
	{
		int middle = (left + right) / 2;
		switch (cmp(data, list[middle]))
		{
		case 1:
			right = middle - 1;
			break;
		case -1:
			left = middle + 1;
			break;
		case 0:
			return middle;
		}
	}

	return -1;
}
/////////////////////
int cmp(int data1, int data2)
{
	if (data2 < data1)
		return -1;
	else if (data2 > data1)
		return 1;
	else
		return 0;
}

int main()
{
	int list[10] = { 20, 23, 25, 35, 42, 51, 56, 65, 70, 89 };

	PrintList(list, 10);
	int idx = BSearch(100, list, 10, cmp);
	if (idx != -1)
		printf("list[%d]:%d\n", idx, list[idx]);
}

```

## 시간 복잡도
- 중간 값과 비교할 때마다 데이터 집합의 범위가 1/2 씩 줄어 들기 때문에 최악의 경우 데이터 집합이 1이 될때 까지 알고리즘이 수행되는 것이다.
- 전체 데이터가 N개 있을 때 최악의 비교 수행 횟수를 계산하면 아래와 같다.
  <a href="https://www.codecogs.com/eqnedit.php?latex=log_{2}N" target="_blank"><img src="https://latex.codecogs.com/gif.latex?log_{2}N" title="log_{2}N" /></a>이 된다.
