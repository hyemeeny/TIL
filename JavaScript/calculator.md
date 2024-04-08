# 계산기 만들기

```javascript
let numOne = '';
let operator = '';
let numTwo = '';
const $operator = document.querySelector('#operator');
const $result = document.querySelector('#result');
/* 고차 함수 (high order function)
중복함수 매개변수로 변환(number) => (return 생략) => {} */
const onClickNumber = event => {
  if (!operator) {
     // 비어있다
     numOne += event.target.textContent;
     $result.value += event.target.textContent;
     return;
  }
  // 비어있지 않다
  if (!numTwo) {
     // numTwo가 없으면 비워라
     $result.value = '';
  }
  numTwo += event.target.textContent;
  $result.value += event.target.textContent;
};
document.querySelector('#num-0').addEventListener('click', onClickNumber);
document.querySelector('#num-1').addEventListener('click', onClickNumber);
document.querySelector('#num-2').addEventListener('click', onClickNumber);
document.querySelector('#num-3').addEventListener('click', onClickNumber);
document.querySelector('#num-4').addEventListener('click', onClickNumber);
document.querySelector('#num-5').addEventListener('click', onClickNumber);
document.querySelector('#num-6').addEventListener('click', onClickNumber);
document.querySelector('#num-7').addEventListener('click', onClickNumber);
document.querySelector('#num-8').addEventListener('click', onClickNumber);
document.querySelector('#num-9').addEventListener('click', onClickNumber);

const onClickOperator = op => () => {
  if (numOne) {
     operator = op;
     $operator.value = op;
  } else {
     alert('숫자를 먼저 입력하세요.');
  }
};
document.querySelector('#plus').addEventListener('click', onClickOperator('+'));
document.querySelector('#minus').addEventListener('click', onClickOperator('-'));
document.querySelector('#divide').addEventListener('click', onClickOperator('/'));
document.querySelector('#multiply').addEventListener('click', onClickOperator('*'));
document.querySelector('#calculate').addEventListener('click', () => {
  if (numTwo) {
     switch (operator) {
        case '+':
           $result.value = parseInt(numOne) + parseInt(numTwo);
           break;
        case '-':
           $result.value = numOne - numTwo;
           break;
        case '*':
           $result.value = numOne * numTwo;
           break;
        case '/':
           $result.value = numOne / numTwo;
           break;
        default:
           break;
     }
  } else {
     alert('숫자를 먼저 입력하세요.');
  }
});
document.querySelector('#clear').addEventListener('click', () => {
  numOne = '';
  operator = '';
  numTwo = '';
  $operator.value = '';
  $result.value = '';
});
```

## if문 중첩 줄이기
1. if문 다음에 나오는 공통된 절차를 각 분기점 내부에 넣는다.
2. 분기점에서 짧은 절차부터 실행하게 if문을 작성한다.
3. 짧은 절차가 끝나면 return(함수 내부의 경우)이나 break(for문 내부의 경우)로 중단한다.
4. else를 제거한다(이때 중첩 하나가 제거된다).
5. 다음 중첩된 분기점이 나올 때 1~4의 과정을 반복한다.

```javascript
function test() {
   let result = '';
   if (!a) {
      result = 'a';
      result += 'b';
      return result;
   }
   if (!b) {
      result = 'c';
   }
   result += 'b';
   return result;
}
```

## switch문을 if문으로 바꿨을 때
```javascript
if (numTwo) {
   switch (operator) {
      case '+':
         $result.value = parseInt(numOne) + parseInt(numTwo);
         break;
      case '-':
         $result.value = numOne - numTwo;
         break;
      case '*':
         $result.value = numOne * numTwo;
         break;
      case '/':
         $result.value = numOne / numTwo;
         break;
      default:
         break;
   }
}
  
if (operator === '+') {
  $result.value = parseInt(numOne) + parseInt(numTwo);
} else if (operator === '-') {
  $result.value = numOne - numTwo;
} else if (operator === '*') {
  $result.value = numOne * numTwo;
} else if (operator === '/') {
  $result.value = numOne / numTwo;
}
```
