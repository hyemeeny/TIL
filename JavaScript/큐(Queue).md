# 큐(Queue)
큐(Queue)는 먼저 삽입된 데이터가 먼저 추출되는 자료구조다.

### 연결 리스트로 큐 구현하기
* 큐를 연결 리스트로 구현하면, 삽입과 삭제에 있어서 O(1)을 보장할 수 있다.
* 연결 리스트로 구현할 때는 머리(head)와 꼬리(tail) 두 개의 포인터를 가진다. 
* 머리(head): 남아있는 원소 중 가장 먼저 들어 온 데이터를 가리키는 포인터
  <br/>(삭제할 때 머리 위치에서 데이터를 꺼낸다.)
* 꼬리(tail): 남아있는 원소 중 가장 마지막에 들어 온 데이터를 가리키는 포인터
  <br/>(삽입할 때 꼬리 위치에 데이터를 넣는다.)

```javascript
// JavaScript 큐(Queue) 구현하기
class Queue {
  constructor() {
    this.items = {};
    this.headIndex = 0;
    this.tailIndex = 0;
  }
  enqueue(item) {
    // 삽입
    this.items[this.tailIndex] = item;
    this.tailIndex++;
  }
  dequeue() {
    // 삭제
    const item = this.items[this.headIndex];
    delete this.items[this.headIndex];
    this.headIndex++;
    return item;
  }
  peek() {
    return this.items[this.headIndex];
  }
  getLength() {
    return this.tailIndex - this.headIndex;
  }
}
```
```javascript
// 구현된 큐(Queue) 라이브러리 사용
queue = new Queue();

// 삽입(5)-삽입(2)-삽입(3)-삽입(7)-삭제()-삽입(1)-삽입(4)-삭제()
queue.enqueue(5);
queue.enqueue(2);
queue.enqueue(3);
queue.enqueue(7);
queue.dequeue();
queue.enqueue(1);
queue.enqueue(4);
queue.dequeue();

while (queue.getLength() != 0) {
  console.log(queue.dequeue()); // 3, 7, 1, 4
}
```
