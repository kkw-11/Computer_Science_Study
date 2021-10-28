# Stack
- 먼저 들어간 데이터가 나중에 나오는 자료구조

## Stack code
```c
#include <stdio.h>
#include <stdlib.h>
struct Stack {
	int* stack; 
	int top; 
};
void Push(Stack* st, int data) {

	st->stack[st->top] = data;
	++st->top;
}
int Pop(Stack* st) {
	--st->top; //*top = *top-1;
	return st->stack[st->top];
}
void InitStack(Stack* st, int cap) {
	st->stack = (int*)malloc(sizeof(int) * cap);
	st->top = 0;
}
void UninitStack(Stack* st) {
	free(st->stack);
	st->top = 0;
}

/////////////////////////////////
int main() {
	Stack st;
	Stack st2;

	InitStack(&st,500);
	Push(&st, 10);
	Push(&st, 20);
	Push(&st, 30);
	printf("%d\n", Pop(&st));
	printf("%d\n", Pop(&st));
	printf("%d\n", Pop(&st));
	UninitStack(&st);

	InitStack(&st2,10);
	Push(&st2, 100);
	Push(&st2, 200);
	printf("%d\n", Pop(&st2));
	printf("%d\n", Pop(&st2));
	UninitStack(&st2);

	return 0;
}
```