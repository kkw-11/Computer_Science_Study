# Breadth-First-Search
-   넓이 우선 탐색, BFS
-   트리, 그래프 탐색의 대표적인 알고리즘으로 레벨탐색이라고도 불린다.
-   부모노드의 인접하여 연결된 자식노드를 모두 탐색한 후 다시 자식노드의 연결된 다음 레벨의 자식노드를 탐색하는 방식이다.
-   DFS(Depth-First-Search, 깊이 우선 탐색)과 반대로 넓이를 먼저 탐색하고 다음 레벨을 탐색하는 완전탐색방법이다.
-   DFS에서는 스택 자료구조를 사용하지만 BFS는 큐를 사용한다.

## 사용한 자료구조
-   큐
    -   First In First Out(선입선출 방식의 데이터 구조로 먼저 들어간 데이터를 먼저 삭제하는 자료구조)

```c++
#include <cstdio>
#include <cstdlib>
#include <queue>
using namespace std;

struct Node {

	int data;
	Node* link;
};
Node* AllocNode(int data) {

	Node* p = new Node;
	p->data = data;
	p->link = NULL;

	return p;
}
void AddNode(Node*& head, int data) {
	if (head == NULL)
		head = AllocNode(data);
	else {
		Node* tail;
		for (tail = head; tail->link != NULL; tail = tail->link)
			;
		tail->link = AllocNode(data);
	}
}
void PrintNode(Node* head) {
	for (Node* p = head; p != NULL; p = p->link)
		printf("%d\n", p->data);
}
void DestroyNode(Node* head) {
	for (Node* p = head; p != NULL; p = p->link) {
		Node* np = p->link;
		delete p;
		p = np;

	}
}

//////////////////////////////////////////////////////
struct Graph {
	Node** head;
	int verSize;

};
void AddEdge(Graph* pg, int sv, int ev) {
	AddNode(pg->head[sv], ev);

}
void PrintGraph(Graph* pg) {

	printf("V: ");
	for (int i = 0; i < pg->verSize; ++i)
		printf("%d ", i);
	printf("\n");
	for (int i = 0; i < pg->verSize; ++i) {
		pg->head[i];
		printf("E: ");
		for (Node* p = pg->head[i]; p != NULL; p = p->link) {
			printf("(%d,%d)", i, p->data);
		}
		printf("\n");
	}

}
void InitGraph(Graph* pg, int verSize) {
	pg->verSize = verSize;
	pg->head = new Node * [verSize];
	for (int i = 0; i < verSize; ++i) {
		pg->head[i] = NULL;
	}
}
void UninitGraph(Graph* pg) {
	for (int i = 0; i < pg->verSize; ++i)
		DestroyNode;
	delete[] pg->head;
}
void _DFS(Graph* pg, int ver, int* visited) {
	visited[ver] = 1;
	printf("%d ", ver);
	for (Node* p = pg->head[ver]; p != NULL; p = p->link) {
		if (!visited[p->data])
			_DFS(pg, p->data, visited);

	}

}
void BFS(Graph* pg, int ver) {
	int* visited = new int[pg->verSize];
	for (int i = 0; i < pg->verSize; ++i) {
		visited[i] = 0;
	}
	queue<int> q;
	q.push(ver);
	visited[ver] = 1;

	while (!q.empty()) {
		int cur = q.front();
		q.pop();
		printf("%d ", cur);
		for (Node* p = pg->head[cur]; p != NULL; p = p->link) {
			if (!visited[p->data]) {
				q.push(p->data);
				visited[p->data] = 1;
			}
		}
	}
	printf("\n");
	delete[] visited;

}
int main() {

	Graph g;
	InitGraph(&g, 5);
	AddEdge(&g, 0, 1);
	AddEdge(&g, 0, 3);

	AddEdge(&g, 1, 0);
	AddEdge(&g, 1, 2);
	AddEdge(&g, 1, 3);

	AddEdge(&g, 2, 1);
	AddEdge(&g, 2, 3);

	AddEdge(&g, 3, 0);
	AddEdge(&g, 3, 1);
	AddEdge(&g, 3, 2);
	AddEdge(&g, 3, 4);

	AddEdge(&g, 4, 3);

	PrintGraph(&g);

	
	BFS(&g, 0);

	UninitGraph(&g);

	system("pause");
}

```