# JavaScript 배열 문제

### 최소, 최대
```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let arr = input[1].split('').map(Number);

/*
모든 정수는 -1,000,000보다 크거나 같고, 
1,000,000보다 작거나 같은 정수이다.
*/

let minValue = 1000001; // 일단 큰 수로 초기화
let maxValue = -1000001; // 일단 작은 수로 초기화
for (let i = 0; i < n; i++) {
  if (minValue > arr[i]) minValue = arr[i];
  if (maxValue < arr[i]) maxValue = arr[i];
}
console.log(minValue, maxValue);
```

```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let data = input[1].split(' ').map(x => Number(x));

// Math.min Math.max 실수나 정수와 같은 데이터가 들어왔을 때 더 작은 값과 큰 값을 리턴하는 각각의 함수
let minValue = data.reduce((a, b) => Math.min(a, b));
let maxValue = data.reduce((a, b) => Math.max(a, b));

console.log(minValue + ' ' + maxValue);
```

### 최댓값
```javascript
//readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let maxIndex = 0;
let maxValue = 0;
for (let i = 0; i < 9; i++) {
  // 모든 데이터를 하나씩 확인하며
  let data = Number(input[i]);
  if (maxValue < data) {
    maxValue = data;
    maxIndex = i;
  }
}

console.log(maxValue);
console.log(maxIndex + 1);
```

```javascript
//readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let data = input.map(x => Number(x));
let max = Math.max(...data);

console.log(max);
console.log(input.indexOf(max) + 1);
```

### 나머지
```javascript
//readline 모듈보다는 fs를 이용해 파일 전체를 읽어 들여 처리하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let data = input.map(Number);
let mySet = new Set(); // 집합 객체 생성

// 원소를 하나씩 확인하며
for (let i = 0; i < 10; i++) {
  mySet.add(data[i] % 42); // 42로 나눈 나머지를 집합의 원소로 삽입
  // add 중복된 원소 처리
}

// 집합에 포함된 원소의 개수 출력
console.log(mySet.size);
```

### 평균은 넘겠지
```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let testCases = Number(input[0]);
for (let t = 0; t <= testCases; t++) {
  // 각각의 테스트 케이스를 확인
  let data = input[t].split(' ').map(Number);
  let n = data[0]; // 첫 번째 수는 데이터의 개수
  let summary = 0; // n개의 점수에 대하여 평균 계산
  for (let i = 1; i <= n; i++) {
    summary += data[i];
  }
  let average = summary / n;
  let cnt = 0; // 점수가 평균을 넘는 학생 수 계산
  for (let i = 1; i <= n; i++) if (data[i] > average) cnt += 1;
  // 점수가 평균을 넘는 학생의 비율을 소수점 아래 셋째 자리까지 출력
  console.log(`${((cnt / n) * 100).toFixed(3)}%`);
}
```

### 평균
```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let scores = input[1].split(' ').map(Number);

let maxValue = scores.reduce((a, b) => Math.max(a, b));
let update = [];
for (let i = 0; i < n; i++) {
  // 수정된 원소 하나씩 저장
  update.push((scores[i] / maxValue) * 100);
}

// 배열에 포함된 원소의 평균 출력
console.log(update.reduce((a, b) => a + b) / n);
```
