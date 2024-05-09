# Tree
- 자료들 사이의 관계가 계층적 관계를 갖는 자료구조
- 탐색 연산을 수행하는데 순차적인 과정을 거쳐야 하는 리스트의 단점을 트리 자료구조를 통해 해결할 수 있다.
- ex) 컴퓨터의 디렉토리 구조, 기업 및 정부의 조직도, 의사 결정 트리(decision tree)

```c
#include <stdio.h>
#include <stdlib.h>
#include <queue>
using namespace std;

typedef struct _node {

	int data;
	struct _node* lChild;
	struct _node* rChild;

}Node;

Node* AllocNode(int data) {

	Node* n = (Node*)malloc(sizeof(Node));
	n->data = data;
	n->lChild = n->rChild = NULL;

	return n;
}

void Inorder(Node* root) {

	if (root == NULL)
		return;
	Inorder(root->lChild);
	printf("%d ", root->data);
	Inorder(root->rChild);

}

void Preorder(Node* root) {
	if (root == NULL)
		return;
	printf("%d ", root->data);
	Preorder(root->lChild);
	Preorder(root->rChild);
}


void Postorder(Node* root) {
	if (root == NULL)
		return;
	Postorder(root->lChild);
	Postorder(root->rChild);
	printf("%d ", root->data);

}
void Levelorder(Node* root) {
	if (root == NULL)
		return;

	queue<Node*> q;
	q.push(root);

	while (!q.empty()) {
		Node* front = q.front();
		q.pop();
		printf("%d ", front->data);

		if (front->lChild != NULL)
			q.push(front->lChild);
		if (front->rChild != NULL)
			q.push(front->rChild);

	}
}

Node* AddNode(Node* root, int data) {
	if (root == NULL)
		return AllocNode(data);

	if (data < root->data)
		root->lChild = AddNode(root->lChild, data);
	else
		root->rChild = AddNode(root->rChild, data);

	return root;
}

void FreeNode(Node* root) {
	if (root == NULL)
		return;
	FreeNode(root->lChild);
	FreeNode(root->rChild);
	
	free(root);
}

Node* SearchNode(Node* root, int data) {

	if(root == NULL)
		return NULL;

	if (data < root->data)
		return SearchNode(root->lChild, data);
	else if (data > root->data)
		return SearchNode(root->rChild, data);
	else
		return root;
}

int main() {

	Node* root = NULL;

	root = AddNode(root, 50);
	root = AddNode(root, 30);
	root = AddNode(root, 70);
	root = AddNode(root, 10);
	root = AddNode(root, 40); 
	root = AddNode(root, 60);
	root = AddNode(root, 90);

	Inorder(root);	printf("\n\n");
	Preorder(root); printf("\n\n");
	Postorder(root); printf("\n\n");
	Levelorder(root); printf("\n\n");
	
	/*Node * p = SearchNode(root, 4);
	if (p != NULL)
		printf("search: %d\n", p->data);
	*/
	FreeNode(root);
	return 0;

}

```