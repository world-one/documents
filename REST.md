### REST란 무엇인가
- Representational State Transfer
- HTTP URI를 통해 Resource를 명시하고, HTTP Method(GET, POST, PUT, DELETE)를 통해 CRUD Operation을 적용하는 것을 말한다.
- 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.
- REST API의 method에 따라 의도를 쉽게 파악할 수 있다.
- http://www.incodom.kr/REST

#### 구성
- 자원(Resource) - URI
- 행위(Verb) - HTTP Method
- 표현(Representations)

#### put, patch 차이
- put은 기존 정보의 대체, patch는 부분 수정
  - HTTP의 규약일 뿐이며 사용하기 나름이지만 용도에 맞게 사용하는 걸 권장한다.
  - https://tecoble.techcourse.co.kr/post/2020-08-17-put-vs-patch/