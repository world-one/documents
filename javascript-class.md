### Class
- ES6(ECMA2015)에서 처음 추가되었다.
- class는 함수다.
- class는 호이스팅이 일어나지 않는다.
- 아래와 같이 class 표현식으로도 쓸 수 있다.
```
const className = class {}
```
- static method 인스터스화 없이 호출 할 수 있다.
- class로 만든 함수엔 내부 프로퍼티인 `[[FunctionKind]]:"classConstructor"` 가 붙는다.
- 생성자 함수의 synatic sugar는 아니다. 내부 동작이 다르다.


https://urbanbase.github.io/dev/2021/03/28/ECMAScript6.html   
https://valuefactory.tistory.com/210   
https://overreacted.io/ko/how-are-function-components-different-from-classes/