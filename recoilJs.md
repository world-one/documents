### Recoil js
- shared state도 React의 내부의 상태 처럼 간단한 인터페이스로 사용할 수 있도록 boilerplate-free API를 제공한다.
- React의 다른 새로운 기능과도 호환할 수 있다.
- 코드 분할이 가능
- 상태를 사용하는 컴포넌트를 수정하지 않고도 상태를 파생된 데이터로 대체할 수 있다.
- 파생된 데이터를 사용하는 컴포넌트를 수정하지 않고도 파생된 데이터는 동기식과 비동기식 간에 이동할 수 있다.
- 우리는 탐색을 일급 개념으로 취급할 수 있고 심지어 링크에서 상태 전환을 인코딩할 수도 있다.
- 역호환성 방식으로 전체 애플리케이션 상태를 유지하는 것은 쉬우므로, 유지된 상태는 애플리케이션 변경에도 살아남을 수 있다.

#### 주요 개념
- atoms -> selectors

##### Atoms
- 상태의 단위
- 업데이트와 구독이 가능
- atoms는 런타임에서 생성될 수 도 있다.
- React의 state 대신 사용할 수 있다.
```
const fontSizeState = atom({
  key: 'fontSizeState',
  default: 14,
});
```
- 고유한 키가 필요

```
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  return (
    <button onClick={() => setFontSize((size) => size + 1)} style={{fontSize}}>
      Click to Enlarge
    </button>
  );
}
```

##### Selectors
- atoms, selectors를 입력으로 받아들이는 순수 함수