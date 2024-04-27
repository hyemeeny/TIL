# 트리(Tree)와 우선순위 큐(Priority Queue) 

## 트리(Tree)
* 트리는 가계도와 같이 계층적인 구조를 표현할 때 사용할 수 있는 자료구조이다.
* 나무의 형태를 뒤집은 것과 같이 생겼다.
  
1. 루트 노드(root node): 부모가 없는 최상위 노드
2. 단말 노드(leaf node): 자식이 없는 노드
3. 깊이(depth): 루트 노드에서의 길이(length)
> 이때, 길이란 출발 노드에서 목적지 노드까지 거쳐야 하는 간선의 수를 의미한다.<br/>
> 트리의 높이는 루트 노드에서 가장 깊은 노드까지의 길이를 의미한다.
---
* 이진 트리(Binary Tree): 최대 2개의 자식을 가질 수 있는 트리
* 완전 이진 트리(Complete Binary Tree): 모든 노드가 왼쪽 자식부터 차근차근 채워진 트리
* 높이 균형 트리(Height Binary Tree): 왼쪽 자식 트리와 오른쪽 자식 트리의 높이가 1 이상 차이 나지 않는 트리

## 우선순위 큐
* 우선순위 큐는 우선순위에 따라서 데이터를 추출하는 자료구조
* 컴퓨터 운영체제, 온라인 게임 매칭 등에서 활용
* 우선순위 큐는 일반적으로 힙(heap)을 이용해 구현

#### 추출되는 데이터
* 스택 -> 가장 나중에 삽입된 데이터
* 큐 -> 가장 먼저 삽입된 데이터
* 우선순위 큐 -> 가장 우선순위가 높은 데이터
---
* 리스트 자료형 -> 삽입 시간 O(1) / 삭제 시간 O(N)
* 힙(Heap) -> 삽입 시간 O(logN) / 삭제 시간 O(logN)

## 힙(Heap)
* 힙(Heap)은 원소들 중에서 최댓값 혹은 최솟값을 빠르게 찾아내는 자료구조이다.
* 힙은 원소의 삽입과 삭제를 위해 O(logN)의 수행 시간을 요구한다.
* 단순한 N개의 데이터를 힙에 넣었다가 모두 꺼내는 작업은 정렬과 동일하다.
> 이 경우 시간 복잡도는 O(NlongN)이다.
---
1. 최대 힙(max heap): 값은 큰 원소부터 추출한다.
* 부모 노드의 키 값이 자식 노드의 키 값보다 항상 크다.
* 루트 노트가 가장 크며, 값이 큰 데이터가 우선순위를 가진다.
2. 최소 힙(min heap): 값은 작은 원소부터 추출한다.
* 부모 노드의 키 값이 자식 노드의 키 값보다 항상 작다.
* 루트 노드가 가장 작으며, 값이 작은 데이터가 우선순위를 가진다.

```javascript
// 최대힙(Max Heap)
let pq = new PriorityQueue(function (a, b) {
  return a.cash - b.cash;
});

pq.enq({ cash: 250, name: 'Doohyun Kim' });
pq.enq({ cash: 300, name: 'Gildong Hong' });
pq.enq({ cash: 150, name: 'Minchul Han' });
console.log(pq.size()); // 3
console.log(pq.deq()); // { cash: 300, name: 'Gildong Hong' }
console.log(pq.peek()); // { cash: 250, name: 'Doohyun Kim' }
console.log(pq.size()); // 2
  ```
