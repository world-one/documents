### Chrome HTTP Strict Transport Security
local 환경에서 https를 사용하던 중 http를 강제로 https로 연결시켰다.   
크롬에서는 한 번이라도 접속한 이력이 있다면 보안을 위해 무조건 https로 이동시킨다.   
이를 해제하는 방법은 아래와 같다.

- chrome://net-internals/#hsts 로 이동
- Query HSTS/PKP domain 에서 설정되어 있는지 확인 가능하다.
- Delete domain security policies 에서 해당 도메인을 입력하여 삭제 할 수 있다.
- 크롬을 완전히 종료한 뒤 확인한다.