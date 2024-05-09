# Recursive
- 자기 자신을 호출 하는 함수를 재귀라고 부른다. 재귀적 방법은 자신의 복사본을 호출하여 더 작은 문제를 풀게하여 문제를 해결한다.
- 주의할 점은 재귀함수 작성시 반드시 종료시점이 존재해야 한다는 것이다.


# 피보나치수열을 구하는 함수를 재귀적 방법으로 구현
```c
#include <stdio.h>
#include <stdlib.h>

void Fibonacci(int n, int& result) {

	if (n == 1)
		result = 1;
	else if (n == 2)
		result = 2;
	else {
		int f1, f2;
		Fibonacci(n - 1, f1);
		Fibonacci(n - 2, f2);
		result = f1 + f2;

	}

}

int main() {

	int fibo;

	Fibonacci(4, fibo);
	printf("%d\n", fibo);

	system("pause");

	return 0;
}
```