# Queue
- 가장 먼저 넣은 데이터를 가장 먼저 꺼내는 선입선출 자료구조(FIFO, First In First Out)
- 큐의 응용 분야 : 컴퓨터의 운영체제에서 여러 작업들의 스케줄링


```C
#include <stdio.h>
#include <stdlib.h>

typedef struct q_ {
	int* queue;
	int front, rear;
	int capacity;
}Queue;
//서버(Queue)
void Push(Queue* q, int data) {
	if ((q->rear + 1) % q->capacity == q->front)
		return;

	//rear가 0,1,2,3,4 가 되는 코드
	/*rear = rear + 1;
	if (rear == 5)
		rear = 0;*/

	q->rear = (q->rear + 1) % q->capacity; //위 주석 처리 코드와 같음(rear가 0,1,2,4가 되는 코드)
	q->queue[q->rear] = data;
}
int Pop(Queue* q) {
	if (q->front == q->rear)
		return 0xfffffff; //오류값으로 임의의 큰 값 지정

	//Push에서 대입전 rear를 증가시키고 대입시켰으므로 
	//Pop에서도 증가시키고 값을 빼야 해당 위치의 값을 정확히 값의 위치로 가리키게됨 
	q->front = (q->front + 1) % q->capacity;
	return q->queue[q->front];
}
void InitQueue(Queue* q, int cap) {
	q->queue = (int*)malloc(sizeof(int) * cap);
	q->capacity = cap;
	q->front = q->rear = 0; //front 와 rear를 같게만 해주면 됨 0,1,2,3,4 어느것으로 초기화 하든 상관없음

}
void UninitQueue(Queue* q) {
	free(q->queue);
	q->front = q->rear = 0; //여기서는 Uninit 할거 없지만해줌
}

//////////////////////
//클라이언트
int main() {

	Queue q1;
	Queue q2;

	InitQueue(&q1, 100);
	Push(&q1, 10);
	Push(&q1, 20);
	Push(&q1, 30);

	InitQueue(&q2, 500);
	Push(&q2, 100);
	Push(&q2, 150);

	printf("queue1: %d\n", Pop(&q1));
	printf("queue1: %d\n", Pop(&q1));
	printf("queue1: %d\n", Pop(&q1));
	UninitQueue(&q1);

	printf("queue2: %d\n", Pop(&q2));
	printf("queue2: %d\n", Pop(&q2));
	UninitQueue(&q2);

	return 0;
} 
```