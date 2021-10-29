## Quick Sort

-   퀵 정렬은 병합 정렬과 마찬가지로 '분할 정복(divide and conquer')에 근거하여 만들어진 정렬 방법이다.
    -   정렬의 대상이 되는 배열에서 하나의 원소를 고른다. 이 원소를 pivot이라고 한다.
    -   피벗을 기준으로 앞에는 피벗보다 작은 원소를 뒤에는 큰 원소들이 오도록 피벗을 기준으로 배열을 둘로 나눈다.
    -   둘로 나누어진 배열에 대해서 재귀(recursion)적으로 반복한다. 배열의 원소의 개수가 1이 될때 까지 반복한다.
-   퀵 정렬 세부 동작 과정
-   left가 가리키는 값이 pivot이 가리키는 값보다 클 때까지 반복
    -   pivot이 가리키는 값과 left가 가리키는 값을 비교하여 left가 가리키는 값이 작기 때문에 left 우측으로 한칸 이동,
        -   4(pivot)와 3을 비교해서 3이 4보다 작기 때문에 left 우측으로 한 칸 이동
        -   4(pivot)과 2를 비교해서 2가 4보다 작기 때문에 left 우측으로 한 칸 이동

-   다시 left가 가리키는 값과 pivot이 가리키는 값을 비교
-   퀵정렬 알고리즘 C코드 구현


```C++
#include <cstdio>
#include <cstdlib>
void Swap(int& a, int& b) {
	int t = a;
	a = b;
	b = t;
}
void _Sort(int list[], int left, int right) {

	if (left <= right) { 
		int pivot = left;
		int i = left + 1;
		int j = right;
		while (i <= j)
		{
			while (list[pivot] > list[i])
				++i;
			while (list[pivot] < list[j])
				--j;

			if (i <= j) {
				Swap(list[i], list[j]);
				++i;
				--j;

			}
			else
				break;
		}
		Swap(list[pivot], list[j]);
		_Sort(list, left, j - 1);
		_Sort(list, j + 1, right);
	}

}
//Sort는 퀵소트의 재귀적인 구현을 위한 매개변수를 모두 갖고 있지 않으므로
//위임함수를 만들어서 동작 시킴
void Sort(int list[], int size) {

	_Sort(list, 0, size - 1);
}
void PrintList(int list[], int size) {

	for (int i = 0; i < size; ++i) {
		printf("%5d", list[i]);
	}
	printf("\n");
}

int main() {
	//int list[10] = { 40,30,10,70,50,80,90,60 };
	int list[10] = { 40,30,70,90,50,80,10,60 };


	PrintList(list, 8);
	Sort(list, 8);
	PrintList(list, 8);

	system("pause");

}
```

## Sort 인터페이스

-   배열의 주소와 배열의 크기만으로 quicksort 위임함수를 호출 하도록 구현

## \_Sort 인터페이스

-   재귀적으로 동작할 '배열의 주소, 시작 값, 끝 값'을 매개변수로 하는 함수
-   재귀 함수 동작을 멈출 조건은 피벗을 기준으로 배열을 점점 둘로 나눌 때 배열의 원소의 개수가 1개에서 한번 더 동작 하면 left값과 right값이 교차하게 된다. 이때 재귀함수 종료조건 즉, 반대의 경우는 계속 함수가 동작하도록 if문 구성
-   코드 가독성을 위해 do while 문으로 실행 일단 1~1 사이의 코드를 먼저 동작하고 i와 j가 교차 하지 않을 경우 값 교환
-   do while 문으로 루프문 조건에 부합해 확인하고 교체하고 확인하고 교체하다가 해당 조건이 끝나면 이제 피벗함수를 옮기고 분할 한다는 내용으로 이해하기 좋음
-   While 문이 아니라 do while 문으로 하는 이유는 j 값을 먼저 변화 시키고 pivot보다 큰값들만 있는 곳 바로 왼쪽에서 j를 위치시키고 do while이 빠져 나온 후 j위칭와 pivot을 교체 하기 위해서이다.
-   do 내부 코드를 반복하는데 i와 l이 교차 하지 않을 때까지
-   여기서 swap조건 if와 while의 조건이 같음 하지만 목적은 다름
-   while의 조건은 루프문을 빠져나갈 조건이고 if문은 Swap을 위한 조건이다.\\

## 시간복잡도

-   pivot과 left, right에서 찾은 원소들을 비교하는 횟수는 자료의 개수(N)에 비례한다.
-   그리고 위에서 한 행위가 배열의 범위가 분할 되면서 재귀 호출이 되는데 이것은 logN에 비례한다.
-   그래서 시간복잡도를 계산하면 O(NlogN)이 나온다.