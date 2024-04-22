# JavaScript 반복문 문제

### 합
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// 문자열을 수로 변환할 때 parseInt에 비하여 Number의 속도가 더 빠르게 동작
let n = Number(input[0]);
let summary = 0;

for (let i = 1; i <= n; i++) {
  summary += i;
}

console.log(summary);
// 등차수열의 합 공식
console.log((n * (n + 1)) / 2);
```

### 구구단
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// 문자열을 수로 변환할 때 parseInt에 비하여 Number의 속도가 더 빠르게 동작
let n = Number(input[0]);

for (let i = 1; i <= 9; i++) {
  // 템플릿 리터럴을 사용해 문자열 내부에 변수를 포함합니다. (백틱 문자 사용)
  console.log(`${n}*${i}=${n * i}`);
}
```

### 별 찍기 - 1
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// 문자열을 수로 변환할 때 parseInt에 비하여 Number의 속도가 더 빠르게 동작
let n = Number(input[0]);

let result = '';
for (let i = 0; i < n; i++) {
  // 층(행)만큼 반복
  for (let j = 0; j <= i; j++) {
    // 현재 행만큼 별을 출력
    result += '*';
  }
  result += '\n';
}
console.log(result);
```

### 빠른 A+B
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// 문자열을 수로 변환할 때 parseInt에 비하여 Number의 속도가 더 빠르게 동작
let testCase = Number(input[0]);
let answer = '';

for (let t = 1; t <= testCase; t++) {
  let data = input[t].split('');
  let a = Number(data[0]);
  let b = Number(data[1]);
  answer += a + b + '\n';
}

console.log(answer);
```
