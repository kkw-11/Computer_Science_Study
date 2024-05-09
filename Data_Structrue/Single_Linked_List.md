# Single Linked List

```c++
#include <stdio.h>
#include <stdlib.h>

struct _node {
	int data;
	struct _node* link;
};
typedef struct _node Node;

void FreeNode(Node* head) {
	for (Node* p = head; p != NULL;) {
		Node* np = p->link;
		free(p);
		p = np;
	}
}

Node* AllocNode(int data) {
	Node* n= (Node*)malloc(sizeof(Node));
	n->data = data;
	n->link = NULL;
	
	return n;
}
int main() {

	Node* head = NULL;
	Node* tail = NULL;
	Node* new_node;
	new_node = AllocNode(10);
	tail = head = new_node;

	new_node = AllocNode(20);
	tail->link = new_node;
	tail = new_node;

	new_node = AllocNode(30);
	tail->link = new_node;
	tail = new_node;

	new_node = AllocNode(40);
	tail->link = new_node;
	tail = new_node;

	new_node = AllocNode(50);
	tail->link = new_node;
	tail = new_node;

	Node* p = head;
	p = p->link;
	Node* bp = p;  
	p = p->link;
	// p노드 삭제
	Node* np = p->link;
	bp->link = np;
	free(p);

	for (Node* p = head; p != NULL; p = p->link) {
		printf("%d\n", p->data);
	}

	FreeNode(head);

	return 0;
}
```
