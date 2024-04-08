# 숫자야구

```javascript
const $input = document.querySelector('#input');
const $form = document.querySelector('#form');
const $logs = document.querySelector('#logs');

const numbers = []; // [1,2,3,4,5,6,7,8,9]
for (let n = 0; n < 9; n += 1) {
  numbers.push(n + 1);
}
const answer = [];
for (let n = 0; n < 4; n += 1) {
  // 네 번 반복
  // Math.floor(Math.random() * 9 + 1) => (0~9 정수)
  const index = Math.floor(Math.random() * numbers.length); // 0~8 정수
  answer.push(numbers[index]);
  numbers.splice(index, 1);
}
console.log(answer);

const tries = [];
function checkInput(input) {
  if (input.length !== 4) {
    // 길이는 4가 아닌가
    return alert('4자리 숫자를 입력해 주세요.');
  }
  if (new Set(input).size !== 4) {
    // 중복된 숫자가 있는가 (new Set = 중복을 제거한 값)
    return alert('중복되지 않게 입력해 주세요.');
  }
  if (tries.includes(input)) {
    // 이미 시도한 값은 아닌가
    return alert('이미 시도한 값입니다.');
  }
  return true;
} // 검사하는 코드

function defeated() {
  const message = document.createTextNode(`패배! 정답은 ${answer.join('')}`);
  $logs.appendChild(message);
  // appendChild(createTextNode 필요) 상위 개념 -> append
  // $logs.append(`패배! 정답은 ${answer.join('')}`);
}

let out = 0;
$form.addEventListener('submit', event => {
  event.preventDefault(); // 기본 동작 막기
  const value = $input.value; // $input.value = event.target.value
  $input.value = '';
  if (!checkInput(value)) {
    return;
  }
  // 입력값 문제없음
  if (answer.join('') === value) {
    // [3, 1, 4, 6] -> '3146'
    $logs.textContent = '홈런!'; // textContent 문자열 인식 / innerHTML 태그로 인식
    return;
  }
  if (tries.length >= 4) {
    defeated();
    return;
  }
  // 몇 스트라이트 몇 볼인지 검사
  let strike = 0;
  let ball = 0;
  // answer: 3146, value: 1347
  for (let i = 0; i < answer.length; i++) {
    const index = value.indexOf(answer[i]); // indexOf = 요소의 자료형까지 같아야 함 (요소의 값과 위치까지 알려줌)
    if (index > -1) {
      // 일치하는 숫자 발견
      if (index === i) {
        // 자릿수도 같음
        strike += 1;
      } else {
        // 숫자만 같음
        ball += 1;
      }
    }
  }
  if (strike === 0 && ball === 0) {
    out++;
    $logs.append(`${value}: ${out} 아웃`, document.createElement('br'));
  } else {
    $logs.append(`${value}: ${strike} 스트라이크 ${ball} 볼`, document.createElement('br'));
  }
  if (out === 3) {
    defeated();
    return;
  }
  tries.push(value); // 값을 기록, 몇 번 시도 세는 역할
  $input.focus();
});
```
