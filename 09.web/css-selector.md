### CSS selector에 따른 성능 차이
- 궁금했던 것 아래와 같이 tag 선택자를 했을 때였다.
```
    .wrap span
    .wrap > span
```
- 위와 같이 했을 경우 왼쪽의 span을 먼저 찾은 다음에 상위의 부모 엘리먼트의 조건을 일치하는 것을 찾기 때문에 성능에 좋지 못하다고 알고 있었다.
- https://csswizardry.com/2011/09/writing-efficient-css-selectors/
  - 관련 문서를 찾아보니 꽤 예전에 작성된 문서를 찾을 수 있었다.
- 분명한 성능 개선의 효과가 있지만 아주 미미한 듯 하다.
- 무시할 만큼의 수준이라 굳이 신경 쓸 필요가 없다는 문서도 있다.
  - https://meiert.com/en/blog/performance-of-css-selectors-2/
- 그럼에도 몇 십줄 이상의 비효율적인 작업이 들어가지 않는 한 스타일을 넣을 때는 클래스명을 지정하는게 좋다고 생각한다. 