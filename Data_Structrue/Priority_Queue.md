# Priority Queue
- 데이터 삽입 순서에 상관없이 우선순위가 높은 데이터가 먼저 추출되는 자료구조

## Priority Queue 구현 방법
- '우선순위 큐'의 구현 방법은 힙 자료구조 사용
- '우선순위 큐'는 배열 또는 연결리스트를 이용해서도 구현할 수 있지만 비효율적이다. 데이터가 많아질수록 데이터 삽입시 기존에 있는 모든 데이터와 우선순위를 비교 해야하기 때문이다.

# Heap
- '우선순위 큐' 구현을 위해 사용하는 특수한 형태의 자료구조
- 특별한 형태의 완전이진트리로, 모든 노드에 저장된 값은 자식 노드에 저장된 값보다 우선순위가 높거나 같아야 한다.


```python
import heapq

class PriorityQueue:
    '''
    우선순위 큐를 힙으로 구현합니다
    '''

    def __init__(self) :
        self.data = [0]
        # self.data = []

    def push(self, value) :
    
        # heapq.heappush(self.data, value)
        
        '''
        우선순위 큐에 value를 삽입합니다.
        '''
        self.data.append(value)
        # self.data[0] += 1
        
        child = len(self.data) -1
        parent = child // 2
        
        while child > 1:
            if self.data[parent] > self.data[child]:
                self.data[parent], self.data[child] = self.data[child], self.data[parent]
                
                child = parent
                parent = child // 2
            else:
                break


    def pop(self) :
        '''
        우선순위가 가장 높은 원소를 제거합니다.
        '''
#         if len(self.data) == 0:
#             return
#         heapq.heappop(self.data)
        
        if len(self.data) == 1:
            return
        
        self.data[1], self.data[-1] = self.data[-1], self.data[1]
        self.data.pop()
        
        
        parent = 1 
        child = parent * 2
        
        while True:
            lastIndex = len(self.data) - 1
            # print("sldkfjas")

            
            if child > lastIndex: #자식이 없는경우
                break
            elif child + 1 > lastIndex: # 왼쪽 자식만 있는경우
                pass
            else:
                if self.data[child] > self.data[child + 1]:
                    child = child + 1
            
            if self.data[parent] > self.data[child]:
                self.data[parent], self.data[child] = self.data[child] , self.data[parent]  
                parent = child
                child = parent * 2
            else:
                break


    def top(self) :
        '''
        우선순위가 가장 높은 원소를 반환합니다. 만약 우선순위 큐가 비어있다면 -1을 반환합니다.
        '''
        
        if len(self.data) == 1:
            return -1
            
        return self.data[1]

```
