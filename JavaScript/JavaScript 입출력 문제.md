# JavaScript 입출력 문제

``` javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// ["1", "2"]
// 첫째 줄의 데이터를 공백 기준으로 나누기
let line = input[0].split('');

let a = parseInt(line[0]); // 1 Number
let b = parseInt(line[1]); // 2 Number

console.log(a + b);
```

``` javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = Number(input[0].split('')[0]);
let b = Number(input[0].split('')[1]);

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(parseInt(a / b)); // 정수 형태
console.log(a % b);
```

``` javascript
// fs 모듈을 이용해 파일 전체를 읽어와 문자열로 저장하기
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = input[0];
let b = input[1];

x_1 = b[2]; // 일의 자리
x_2 = b[1]; // 십의 자리
x_3 = b[0]; // 백의 자리

console.log(Number(a) * Number(x_1));
console.log(Number(a) * Number(x_2));
console.log(Number(a) * Number(x_3));
console.log(Number(a) * Number(b));
```
