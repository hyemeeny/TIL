# 쿵쿵따 끝말잇기

```javascript
const number = Number(prompt('몇 명이 참가하나요?'));

// prompt 취소 눌렀을 때 실행 안 됨
if (number) {
  const $input = document.querySelector('input');
  const $button = document.querySelector('button');
  const $order = document.querySelector('#order');
  const $word = document.querySelector('#word');
  let word; // 제시어
  let newWord; // 새 단어

  const onInput = event => {
     newWord = event.target.value;
  };
  const onClickButton = () => {
     if (!word || (word[word.length - 1] === newWord[0] && newWord.length === 3)) {
        // 비어있다
        word = newWord;
        $word.textContent = word;
        const order = Number($order.textContent);
        if (order + 1 > number) {
           $order.textContent = 1;
        } else {
           $order.textContent = order + 1;
        }
     } else {
        alert('올바르지 않은 단어입니다!');
     }
     $input.value = '';
     $input.focus();
  };

  $input.addEventListener('input', onInput);
  $button.addEventListener('click', onClickButton);
}
```

* 제시어 마지막 자리 word[word.length - 1]
* 새 단어 첫번째 자리 newWord[0]
