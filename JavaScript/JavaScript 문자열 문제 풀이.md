# JavaScript 문자열 문제 풀이

### 숫자의 합
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let string = input[1];

let answer = 0;
// 문자열에 포함된 문자를 하나씩 확인하며
for (let x of string) {
  // 모든 숫자를 더하기
  answer += Number(x);
}

console.log(answer);
```

### 문자열 반복
```javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let testCases = Number(input[0]);

// 한 줄(line)씩 입력받기
for (let i = 1; i <= testCases; i++) {
  let [r, s] = input[i].split(' ');
  let result = '';
  // 현재 문자열의 각 문자를 하나씩 확인하며
  for (let j = 0; j <= s.length; j++) {
    // r번 반복한 문자열을 뒤에 이어붙이기
    result += s.charAt(j).repeat(r);
  }
  console.log(result);
}
```

### 상수
```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = input[0].split(' ')[0];
let b = input[0].split(' ')[1];

let newA = a[2] + a[1] + a[0];
let newB = a[2] + a[1] + a[0];

console.log(Math.max(Number(newA), Number(newB)));
```

### 그룹 단어 체커
```javascript
function check(data) {
  let setData = new Set(data[0]);
  for (let i = 0; i < data.length - 1; i++) {
    // 오른쪽 단어와 다르다면
    if (data[i] != data[i + 1]) {
      // 이미 등장한 적 있는 알파벳이라면
      if (setData.has(data[i + 1])) {
        return false;
      } else {
        setData.add(data[i + 1]);
      }
    }
  }
  return true;
}
```

```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let n = Number(input[0]);
let summary = 0;

for (let i = 1; i <= n; i++) {
  let data = input[i];
  if (check(data)) summary += 1;
}
console.log(summary);
```

### 단어의 개수
```javascript
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// trim() 메서드는 문자열 양 끝의 공백을 제거한다.
// 공백으로 구분된 단어의 개수 출력한다.
let data = input[0].trim().split(' ');

if (data == '') {
  console.log(0);
} else {
  console.log(data.length);
}
```
