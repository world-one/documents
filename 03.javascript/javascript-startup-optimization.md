https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/javascript-startup-optimization?hl=ko

### 자바스크립트 최적화
#### 네트워크
- 사용자에게 필요한 코드만 전송
  - 코드 분할
  - 지연 로딩
- 최소화
  - uglifyJs, babel-minifym uglify-es 등 코드 최소화
- 압축
  - gzip을 사용하여 텍스트 기반 리소스 압축
  - Brotli가 gzip 보다 압축률 우수
- 미사용 코드 제거
- 네트워크 트립 최소화를 위한 코드 캐싱
  - HTTP 캐싱 https://web.dev/http-cache
  - 서비스 워커 캐싱
  - 웹팩의 파일 이름 해싱 등 장기적인 캐싱을 사용하여 변경되지 않은 리소스의 리로드 방지

#### 파싱/컴파일
- 크롬 데브툴스의 Performance 패널에 노란색의 스크립팅 시간
  - Bottom-Up, Call Tree에서 정확한 파싱/컴파일 타이밍을 볼 수 있다.
  - 자바스크립트는 같은 크기의 이미지보다도 사용하는 자원이 크다.
  - 기기별로 성능 차이가 심하니 내가 사용하는 기기를 기준으로 하지말라.
  - chrome://flags/#enable-devtools-experiments -> Chrome 다시 시작 -> DevTools로 이동 -> Settings -> Experiments -> Shift 6번 입력 -> Timeline: V8 Runtime Call Stats on Timeline이라는 옵션 체크 후 DevTools를 닫고 다시 열어준다.
- 불필요한 자바스크립트는 제거하여 전송 시간, CPU를 많이 소모하는 파싱과 컴파일, 잠재적인 메모리 오버헤드를 감소시키자.
  
#### 실행 시간
- 빠른 실행을 위해 알아보라..

#### 기타 비용
- 메모리누수, 가비지 컬렉션의 잦은 중지를 방지
- 런타임시 장기 실행중인 자바스크립트는 기본 스레드를 차단하여 페이지가 반응하지 않는다. 작업을 작은 조각으로 나눠 응답 문제를 최소화
  - requestAnimationFrame(), requestIdleCallback()
  
#### 자바스크립트 전달 비용 감소 패턴
- PRPL: PRPL(푸시, 렌더링, 사전 캐시, 지연 로드)는 적극적인 코드 분할 및 캐싱을 통해 상호작용을 최적화하는 패턴입니다.
- 점진적 부트스트랩
  