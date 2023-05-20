# Iterable & Iterator

순회

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

- 이터러블 : 이터레이터를 리턴하는 \[Symbol.iterator]() 메서드를 가진 값

  <img src='https://file.notion.so/f/s/7c7cf6a4-21bf-4816-85bb-b48665970f9f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-05-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.17.38.png?id=f8c7a578-1a92-4173-9682-fae0dea3b034&table=block&spaceId=0634ecca-151f-489c-958f-a813ecd17586&expirationTimestamp=1684646563775&signature=KBfj3_cBW64faTI3f-EiRlcO9F_mi8uP00t3IVtW2-c&downloadName=%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA+2023-05-14+%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE+3.17.38.png' width=400/>

- 이터레이터 : {value,done} 객체를 리턴하는 next()를 가진 값
  <img src='https://file.notion.so/f/s/58b84de7-2274-4b69-b6a0-a4654f2a4d00/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-05-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.17.45.png?id=e318c480-7c1a-4cbb-a10a-be3094b6163a&table=block&spaceId=0634ecca-151f-489c-958f-a813ecd17586&expirationTimestamp=1684646596913&signature=SLYyLG35anGfikTkaWzLv7YhWUuLSewKoU-BvYv8bsM&downloadName=%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA+2023-05-14+%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE+3.17.45.png' width=400 />

- 이터러블/이터레이터 프로토콜 : 이터러블을 for…of, 전개 연산자 등과 함께 동작하도록 한 규약
  - e.g. `array`, `set`, `map`
