https://github.com/airbnb/javascript

## Types
1.1 Primitives
1.2 Complex

## References
2.1 `const`를 사용하고 `var` 사용을 피하라.
2.2 재할당 해야 할 경우는  `var` 대신  `let`을 사용하라.
2.3 `let`과 `const`는 block-scoped, `var`는 function-scoped

## Object
3.7 `hasOwnProperty`, `propertyIsEnumerable`, `isPrototypeOf와` 같은 `Object.prototype` 메소드를 직접 호출하지 말라. 객체의 속성과 겹칠 수도 있어서?
```
// bad
console.log(object.hasOwnProperty(key));

// good
console.log(Object.prototype.hasOwnProperty.call(object, key));

// best
const has = Object.prototype.hasOwnProperty; // 모듈스코프에서 한 번 캐시하세요.
console.log(has.call(object, key));
/* or */
import has from 'has'; // https://www.npmjs.com/package/has
console.log(has(object, key));
```

## Arrays
4.5 array like 객체를 배열로 변환할 때는 `Array.from` 사용
```
const arrLike = { 0: 'foo', 1: 'bar', 2: 'baz', length: 3 };

// bad
const arr = Array.prototype.slice.call(arrLike);

// good
const arr = Array.from(arrLike);
```
4.6 매핑할 때는 전개 구문 ... 대신 `Array.from`을 사용. 중간 배열 생성을 방지하기 때문.
```
// bad
const baz = [...foo].map(bar);

// good
const baz = Array.from(foo, bar);

```

## 