https://ko.wikipedia.org/wiki/%ED%95%A8%EC%88%98%ED%98%95_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D

### 함수형 프로그래밍 (Functional programming)
- 자료 처리를 수학적 함수의 계산으로 취급하고 상태와 가변 데이터를 멀리한다.
- 함수의 응용을 강조
- 문이 아닌 식이나 선언으로 수행되는 선언형 프로그래밍 패러다임을 따르고 있다.
- 람다 대수에 근간을 두고 있다.
- 명령형의 함수는 프로그램 상태의 값을 바꿀 수 있는 부작용이 생길 수 있으며 이 때문에 참조 투명성이 없고, 같은 코드라도 실행 되는 프로그램의 상태에 따라 다른 결과값이 나올 수 있다.
- 함수형 코드는 그 함수에 입력된 인수에만 의존하므로 항상 같은 값이 나온다.
- 부작용을 제거하면 프로그램 동작을 이해하고 예측하기가 훨씬 쉽게 된다.

#### 역사
- IPL
- 리스트
- 스킴
- ML
- 미란다
- OCaml
- 하스켈

#### 순수한 함수
- 부작용이 없는 함수, 함수의 실행이 외부에 영향을 끼치지 않는 함수
#### 익명 함수
#### 고계 함수
- 함수를 다루는 함수
- 함수도 값으로 취급


### javascript
- 부작용이 없는 순수함수
    - 받은 인자값으로만 결과를 내야한다.
- 원본 데이터 불변
- map, filter, reduce가 대표적인 함수형 프로그래밍 함수
https://www.zerocho.com/category/JavaScript/post/576cafb45eb04d4c1aa35078