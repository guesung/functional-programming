# Iterable & Iterator

### 순회

```js
const list = [1, 2, 3];
for (var i = 0; i < list.length; i++) {
  log(list[i]);
}
const str = "abc";
for (var i = 0; i < str.length; i++) {
  log(str[i]);
}
// 기존(ES5) : 어떻게 순회하는지가 중심

for (const a of list) {
  log(a);
}
for (const a of str) {
  log(a);
}
// 신규(ES6) : 무엇을 순회하는지가 중심
```

### 이터러블/이터레이터 프로토콜

: 이터러블을 for…of, 전개 연산자 등과 함께 동작하도록 한 규약

- e.g. `array`, `set`, `map`
- JS의 순회가 가능한 자료형, 브라우저에서 사용되는 DOM API 등 많은 값은 모두 이터러블/이터레이터 프로토콜을 따름

    <img src='https://github.com/guesung/react-native-webview/assets/62178788/72c0262e-7519-4621-a5c5-950b5d221ee3' width=400 />
    <img src='https://file.notion.so/f/s/7c7cf6a4-21bf-4816-85bb-b48665970f9f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-05-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.17.38.png?id=f8c7a578-1a92-4173-9682-fae0dea3b034&table=block&spaceId=0634ecca-151f-489c-958f-a813ecd17586&expirationTimestamp=1684646563775&signature=KBfj3_cBW64faTI3f-EiRlcO9F_mi8uP00t3IVtW2-c&downloadName=%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA+2023-05-14+%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE+3.17.38.png' width=400/>
    <img src='https://file.notion.so/f/s/58b84de7-2274-4b69-b6a0-a4654f2a4d00/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-05-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.17.45.png?id=e318c480-7c1a-4cbb-a10a-be3094b6163a&table=block&spaceId=0634ecca-151f-489c-958f-a813ecd17586&expirationTimestamp=1684646596913&signature=SLYyLG35anGfikTkaWzLv7YhWUuLSewKoU-BvYv8bsM&downloadName=%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA+2023-05-14+%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE+3.17.45.png' width=400 />

### 이터러블

: 이터레이터를 리턴하는 `[Symbol.iterator]()` 메서드를 가진 값

### 이터레이터

: {value,done} 객체를 리턴하는 next()를 가진 값

### 이터러블 직접 만들기

```js
const iterable = {
  [Symbol.iterator]() {
    let i = 0;
    return {
      next() {
        return i == 3 ? { done: true } : { value: i++, done: false };
      },
      [Symbol.iterator]() {
        return this;
      },
    };
  },
};
let iterator = iterable[Symbol.iterator]();
log(iterator.next());
log(iterator.next());
log(iterator.next());
```

- 위 코드는 `for(const a of iterable) log(a);`와 동일
- `Symbol.iterator`: 객체가 iterable이라는 것을 정의하는데 사용되는 내장 Symbol입니다. iterable 객체는 반복 가능한 데이터 콜렉션(예: 배열, 문자열 등)을 나타내며, 이는 for-of 반복문 등에서 사용할 수 있습니다.
- `[Symbol.iterator]()`: iterable 객체가 어떻게 반복될 것인지를 정의합니다. 이 메서드는 iterator 객체를 반환해야 합니다.
- `next()`: iterator 객체가 다음 요소를 반환하는 방법을 정의합니다. next 메서드는 {value, done} 형태의 객체를 반환해야 합니다. value는 다음 요소의 값이며, done은 모든 요소가 반복되었는지의 여부를 나타냅니다.
