# JavaScript 조건문 문제

### 시험 성적
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

data = Number(input[0]);

function check(a) {
  if (90 <= a && a <= 100) console.log('A');
  else if (80 <= a && a <= 89) console.log('B');
  else if (70 <= a && a <= 79) console.log('C');
  else if (60 <= a && a <= 69) console.log('D');
  else console.log('F');
}

check(data);
```

### 알람 시계
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let hour = Number(input[0].split('')[0]);
let minute = Number(input[0].split('')[1]);

if (minute < 45) {
  // 분이 45분 미만이라면
  hour -= 1;
  minute += 15;
  if (hour < 0) hour = 23;
} else minute -= 45;

console.log(hour + '' + minute);
```

### 오븐 시계
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// map 배열의 원소에 각각 함수를 적용한 결과를 리턴
let [a, b] = input[0].split('').map(Number);
let c = Number(input[1]);

let totalMinute = a * 60 + b + c; // 분의 형태로 바꾸기
totalMinute %= 1440;
let hour = parseInt(totalMinute / 60);
let minute = totalMinute % 60;

console.log(hour + '' + minute);
```

### 주사위 세개
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = Number(input[0].split('')[0]);
let b = Number(input[0].split('')[1]);
let c = Number(input[0].split('')[2]);

// 세 개의 수가 모두 같은 경우
if (a == b && b == c) console.log(10000 + a * 1000);
// 세 개의 수가 전부 같지는 않지만, 두 개의 수가 같은 경우
else if (a == b) console.log(1000 + a * 100);
else if (a == c) console.log(1000 + a * 100);
else if (b == c) console.log(1000 + b * 100);
// 세 개의 수가 전부 다른 경우
else console.log(Math.max(a, b, c) * 100);
```
