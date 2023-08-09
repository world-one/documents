### [OWASP Secure Coding](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)
- 이 가이드는 개발시 포괄적으로 적용할 수 있는 보안 코딩 규칙의 안내 문서입니다.
- OWASP란??
  - OWASP(The Open Web Application Security Project)는 오픈소스 웹 애플리케이션 보안 프로젝트이다. 

> 최신 버전: v2.0.1

### 소개
- 이 규칙을 적용한다면 가장 일반적인 소프트웨어 취약점을 완화시킬 수 있습니다.
- 2009년 SANS 연구결과에 따르면 애플리케이션 계층에 대한 공격이 인터넷에서 발견되는 전체 공격 시도의 60% 이상을 차지하고 있습니다.

### Secure Coding Checklist
#### Input Validation
- 신뢰 시스템의 모든 데이터 유효성을 검증 (예: 서버)
- 모든 데이터의 출처를 확인하고 신뢰/비신뢰로 구분하라. 출처를 신뢰하지 못하는 모든 데이터를 검증 (예: 데이터베이스, 파일 스트림 등)
- 애플리케이션의 입력값 검증 루틴은 중앙 집중화(단일화)
- 모든 입력값에 대해 UTF-8 과 같은 단일 문자셋(character set) 정의
- 데이터를 검증하기 전에 단일 문자셋으로 인코딩(정형화)
- 입력값 검증을 실패했을 때는 입력(처리) 거부
- 시스템이 UTF-8 확장 문자셋을 지원한다면, UTF-8 디코딩 후 검증
- 데이터를 처리하기 전, 모든 파라메터, URL 과 HTTP 헤더(예: 쿠키 명과 값)을 포함한 사용자 측에서 전송된 모든 데이터를 검증하라. 자바스크립트, 플래쉬, 다른 임베디드 코드에서 자동 생성한 POST 값도 포함하는 것을 잊어서는 안된다.
- 요청과 응답 헤더가 ASCII 문자만 포함하는 지 검증
- 리다이렉트된 데이터 검증(공격자는 리다이렉트되는 목표로 직접 악의적인 내용을 전송할 수 있다. 이를 통해, 리다이렉트 되기 전 수행되는 애플리케이션 로직과 입력값 검증을 우회할 수 있다.)
- 예상되는 데이터 형 검증
- 데이터 범위 검증
- 데이터 길이 검증
- 특수한 상황을 제외하고, 허용된 문자의 “화이트” 리스트에 맞춰 모든 입력값 검증
- 잠재적으로 위험한 문자가 반드시 입력되어야 한다면, 출력값 인코딩, 안전한 작업을 위한 API, 그리고 애플리케이션 전체에 대한 데이터가 활용되는 감사 기능과 같은 추가적인 통제기능 구현. 
  - 일반적으로 위험한 문자의 예는 다음과 같다: < \” ' % ( )& + \ \' \”
- 표준 검증 루틴이 다음 입력값을 처리하지 못한다면, 개별적으로 명확하게 점검 
  - 널 바이트 점검 (%00)
  - 개행 문자 점검 (%0d, %0a, \r, \n)
  - 상대경로(../ 또는 ..\) 변경 문자 (UTF-8 확장 문자셋 인코딩이 지원되는 경우 %c0%ae%c0%ae/와 같은 추가적인 변경이 가능하다. 이중 인코딩 또는 다른 형태의 난독화 공격을 해결하려면 정형화(canonicalization)를 활용하라)

#### Output Encoding
- 신뢰된 시스템의 모든 인코딩을 적용(예: 서버)
- 외부로 나가는 인코딩에 대해 표준적이고, 시험이 된 루틴 이용
- 애플리케이션의신뢰범위(trust boundary) 외부로 부터 클라이언트로 반환된 모든 데이터는 상황에 맞는 출력 값 인코딩. HTML 엔터티 인코딩 이 예가 될 수 있지만, 모든 경우에 그런 것은 아니다.
- 사용하는 인터프리터에서 안전하다고 알려진 문자 이외의 모든 문자를 인코딩
- SQL, XML, 그리고 LDAP 에 쿼리하는 신뢰받지 못하는 데이터의 모든 출력 값을 상황에 맞게 필터링
- 운영체제 명령어로 전달되는 신뢰받지 못한 데이터의 모든 출력 값을 필터링

#### Authentication and Password Management
- 의도적으로 공개하는 경우를 제외한 모든 페이지와 자원은 인증 실시
- 모든 인증 통제는 반드시 신뢰 시스템에서 수행(예: 서버)
- 특수한 경우를 제외하곤, 표준화되고 검증된 인증 서비스를 확립하고 이용
- 외부 인증 서비스를 호출하는 라이브러리를 포함한 모든 인증 통제는 중앙 집중화하여 사용하라
- 요청된 자원과 인증 로직을 구분하고 중앙집중화된 인증 통제 정보를 주고받는데는 리다이렉트를 사용하라
- 모든 인증 통제는 안전하게 인증 실패 처리
- 모든 관리자 기능과 계정관리기능은 최소한 주요한 인증메커니즘만큼 안전하게 관리
- 애플리케이션이 인증정보를 저장해야 하는 경우, 패스워드의 경우 암호학적으로 강한 단방향 해쉬값으로 저장되도록 하고, 패스워드와 키를 저장하는 테이블/파일은 해당 애플리케이션만 쓰기가 가능하도록 보장
- 패스워드 해쉬 연산은 반드시 신뢰되는 시스템에서 수행(예: 서버)
- 모든 데이터 입력이 완료되었을 때만 인증 데이터를 검증. 특히 순차적 인증(sequential authentication) 을 수행할 때 주의하라
- 인증 실패 메시지는 어떤 인증 정보가 틀렸는지를 나타내서는 안된다. 
  - 예를 들면, “잘못된 사용자명” 또는 “잘못된 패스워드”를 대신하여, 두 경우 모두에 대해 단지 “잘못된 사용자명/패스워드”라고 명시한다. 에러 응답은 이 두 경우에 대해 동일하게 표시함은 물론 소스코드도 동일해야 한다.
- 민감 정보 또는 기능과 관련된 외부시스템에 연결시에도 인증을 활용
- 애플리케이션의 외부 서비스 접근을 위한 인증 정보는 암호화하여 신뢰받는 시스템의 보호된 영역에 저장(예: 서버). 소스 코드는 안전한 장소가 아니다.
- 인증 정보를 전송할 때에는 반드시 HTTP POST 요청을 사용
- 패스워드는 반드시 암호화된 통신 또는 암호화된 이메일과 같은 암호화된 데이터로 전송. 이메일리셋과같은임시패스워드는예외가될수있다
- 정책 또는 규제에 따른 패스워드 복잡성 요구사항을 적용. 
  - 인증 정보는 운영(배치)환경에서 일반적 위협이 있는 공격에 충분히 대응할 수 있어야 함. (예: 알파벳 사용과 더불어 숫자 또는 특수문자를 요구) -정책또는규제에따라패스워드길이요구사항을적용. 8자리가일반적으로 사용되지만, 16 자리가 더 나을 수 있으며, 패스워드 문구를 사용하는 것도 고려해보라.
- 패스워드 입력은 사용자 화면에서 드러나선 안 된다. (예: 웹 폼에서 사용되는 input type “password”) 
- 사전에 정의된 로그인 실패 시도후엔 계정 잠금을 적용(예: 일반적으로5번 시도를 허용한다). 계정은 인증에 대한 무차별 대입 공격(brute force guessing)을 대응할 수 있도록 계정에 대한 시간길이를 반드시 비활성화해야 하지만, 서비스 거부 공격(denial-of-service)이 가능할 정도로 너무 긴 시간동안 허용해서는 안됨.
- 패스워드 재설정과 변경 작업은 계정 생성과 인증과 동일한 수준의 통제가 요구된다.
- 패스워드 재설정에 사용되는 질문은 예측 불가능한 답변이 되어야 한다. (예:“좋아하는 책”은 좋은 예가 아니다. 왜냐하면, 가장 일반적인 답이 “성경”이기 때문이다.)
- 이메일을 기반으로 패스워드 재설정 기능을 사용할 경우,사전에 등록된 주소로만 임시 링크 또는 임시 패스워드를 전송하라.
- 임시 패스워드와 임시 링크는 짧은 기간동안만 유효하도록 해야 함
- 다음 사용 시에는 임시 패스워드를 변경하도록 해야함
- 패스워드 재설정이 된 경우 사용자에게 알려라
- 패스워드 재사용을 금지하라
- 비밀번호 재사용으로 인해 발생 가능한 공격을 예방하기 위해 패스워드는 최소한 하루 이상 지난 후에 변경 가능해야 함
- 정책 또는 규제에 따라 패스워드 변경 주기를 적용. 주요시스템은 보다 잦은 변경을 요구할 수 있다. 재설정 시간은 관리자가 통제해야 한다.
- 패스워드 폼필드에대한 필드값 자동저장을 비활성화
- 사용자의 가장 최근 사용기록(성공적인 로그인 또는 실패한 로그인) 을 사용자가 다음 번 로그인했을 때 그 사용자에게 알려주도록 함
- 동일한 패스워드를 사용한 다중 사용 계정에 대한 공격을 인지할 수 있도록 모니터링하라. 이 공격 유형은 사용자ID를 수집했거나 추측 가능할 때 표준 잠금을 우회하기 위해 자주 사용된다
- 벤더가 제공한 모든 기본 패스워드와 사용자 ID 를 변경하거나 관련 계정을 비활성화
- 중요한 작업을 수행하기 전에는 사용자를 재인증
- 매우 민감하거나 매우 중요한 업무 계정에 대해선 다중 인증(Multi-Factor Authenti-cation) 사용
- 인증을 위해 제3자코드를 사용할 경우,악의적인 코드에 영향을 받았는지 여부를 확인하기 위해 해당 코드를 주의깊게 점검하라

#### Session Management
- 서버 또는 프레임워크의 세션 관리 통제기능을 사용. 애플리케이션은 이들 세션 식별자만을 유효하다고 인지해야 함
- 세션 식별자 생성은 항상 신뢰된 시스템에서 이루어져야 한다 (예: 서버)
- 세션 관리 통제기능은 세션 식별자의 무작위성(random)을 보장할 수 있도록 엄격히 심사된 알고리즘을 사용해야 함
- 인증된 세션 식별자를 포함한 쿠키에 대해 도메인과 경로를 설정하여 사이트에 대한 적절히 제한
- 로그아웃 기능은 관련된 세션과 접속을 완벽하게 종료해야 함
- 로그아웃 기능은 인증에 의해 보호되는 모든 페이지에서 적용되어야 함
- 세션 비활성 타임아웃(session inactivity timeout)은 위험과 비즈니스 기능 요구사항의 균형에 기반하여 가능한 짧아야 설정. 대부분의 경우 3~5 시간정도를 초과해서는 안됨
- 장기적으로 로그인하는 기능을 허가하지 말고 세션이 활성화되어 있더라도 주기적으로 세션 종료. 
  - 특히 네트워크 접속이 많은 경우(rich network connections) 또는 주요한 시스템의 접속을 지원하는 애플리케이션의 경우에 적용해야 함.
  - 부정적 효과를 최소화하려면 종료 시간은 비즈니스 요구사항을 따라야 하며, 사용자에겐 종료 이전에 충분한 알려야 함
- 세션이 로그인 이전에 생성된다면, 로그인후에는 이전 세션을 종료하고 새로운 세션을 생성
- 재인증 할때엔 언제나 새로운 세션 식별자를 생성
- 동일한 사용자 ID에 대해 동시(복수) 로그인을 허용하지 말 것
- URL, 에러 메시지, 로그에 세션 식별자를 노출하지 말 것. 
  - 세션 식별자는 오직 HTTP 쿠키 헤더에만 존재해야 한다. 예를 들면, 세션 식별자를 GET 인자로 전달하지 말 것
- 서버의 다른 사용자와 서버의 다른 접근 통제를 악용해 서버 측 세션 데이터에 불법적인 접근을 하지 못하도록 할 것
- 새로운 세션 식별자를 생성하고 주기적으로 지난 세션 식별자를 비활성화(이는 인증식별자가 노출되었때 발생할 수 있는 세션 하이재킹 시나리오를 예방할 수 있음)
- 인증 과정 중 접속보안이 HTTP에서 HTTPS로 변경되었을 땐 새로운 세션 식별자를 생성. 
  - 애플리케이션 내부에선 HTTP 에서 HTTPS 로 변경하는 것보다 지속적으로 HTTPS 활용할 것을 장려
- 계정관리와 같은 민감한 서버측기능(업무)을 위해 세션별로 강력한 무작위 토큰 또는 파라메터를 이용해 표준 세션 관리를 보완. 
  - 이 방법은 크로스 사이트 요청 위조(Cross Site Request Forgery) 공격을 예방할 수 있음
- 매우 민감하거나 중요한 기능(업무)을 위해 세션별이 아닌 요청별로 강력한 무작위 토큰 또는 파라메터를 이용해 표준 세션 관리를 보완
- TLS 접속을 통해 전송되는 쿠키에 대해 “secure” 속성을 설정
- 쿠키 값을 읽거나 설정을 위해 사용자 측 스크립트를 애플리케이션에서 사용하지 않는다면, 쿠키에 HttpOnly 속성을 설정

#### Access Control
- 접근 권한 결정을 할 때는 신뢰된 시스템 객체(예: 서버측 세션 객체)만을 사용
- 접근 권한을 확인할 때에는 한 사이트 전체에 적용되는 한 개의 컴포넌트(single site-wide component)를 사용. 이는 외부 권한 서비스를 호출하는 라이브러리도 포함
- 접근 통제는 안전하게 실패를 처리하도록 해야 함
- 애플리케이션에서 보안 설정 정보에 접근할 수 없을 때에는 모든 접근을 거부
- 서버 측 스크립트에서 “includes”로 생성된 요청, AJAX 와 플래쉬 같은 리치 사용자측(rich client-side) 기술로 생성된 요청을 포함하여 모든 요청에 대해 인증 통제를 적용
- 다른 애플리케이션 코드와 권한 로직을 구분
- 애플리케이션 직접 통제를 받지 않는 자원을 포함하여, 파일 또는 다른 자원에 대해 권한이 있는 사용자만이 접근할 수 있도록 제한
- 권한이 있는 사용자만 보호된 URL에 접근할 수 있도록 제한
- 권한이 있는 사용자만 통제된 기능에 접근할 수 있도록 제한
- 권한이 있는 사용자에게만 직접 객체 참조 허용
- 권한이 있는 사용자에게만 서비스 접근 허용
- 권한이 있는 사용자에게만 애플리케이션 데이터 접근 허용
- 접근 통제에 사용되는 사용자, 데이터 속성, 그리고 정책정보에 대한 접근 제한
- 권한이 있는 사용자에게만 보안 관련 설정 정보에 대한 접근 제한
- 접근 통제 정책의 서버 측 구현내용과 표현 계층(presentation layer)의 처리가 일치해야 함
- 사용자측에 상태 정보(state data)가 저장되어야 하는 경우, 상태 조작을 탐지할 수 있도록 암호화와 서버 측에서 무결성 점검을 수행
- 애플리케이션 논리 흐름을 비즈니스 정책을 따르도록 적용
- 일정한 시간 동안 한 명의 사용자와 장치가 수행할 수 있는 처리 건수를 제한. 
  - 처리 건수와 시간은 실제 비즈니스 요구보다는 많아야 하지만, 자동화 공격을 탐지할 수 있을 정도로 작아야 함
- “레퍼러(referer)” 헤더는 단지 참고 용도로만 사용. 레퍼러는 조작 가능하므로 단독 권한 점검으로 적합하지 못함
- 장시간의 인증 세션을 허용하면, 사용자가 권한을 가지고 있는지 주기적으로 사용자의 권한을 재확인하라.
  - 권한을 가지고 있다면, 사용자를 로그아웃 시키고 재인증
- 계정 감사 기능을 구현하고 사용하지 않는 계정은 비활성화(예: 계정 패스워드의 종료일이 30 일 이상 지난 경우)
- 애플리케이션은 사용 권한이 중지되었을 때 계정을 비활성화하고, 세션 종료가 가능해야 함 (예: 역할, 고용 상태, 비즈니스 프로세스 등의 변화)
- 서비스 계정 또는 외부 시스템 접속을 지원하는 계정은 최소한의 권한을 가져야함
- 접근이 적절하게 실행되고 통제될 수 있도록 애플리케이션의 비즈니스 역할, 데이터 유형, 접근 통제 표준과 프로세스를 문서화한 접근 통제 정책을 구축. 
  - 여기에 데이터와 시스템 자원 모두의 접근 요구사항도 포함

#### Cryptographic Practices
- 애플리케이션 사용자로의 비밀데이터를 보호하기 위해 사용되는 모든 암호화 기능은 신뢰 시스템에서 실행되어야 한다 (예: 서버)
- 인증되지 않은 접근으로 부터 마스터 키(master secrets) 보호
- 암호화 모듈은 안전하게 실패 처리
- 모든 무작위 숫자, 무작위 파일명, 무작위 GUID, 그리고 무작위 문자열이 추측 불가능한 값이어야 할 경우, 암호화 모듈의 검증된 난수 생성기를 사용하여 생성
- 애플리케이션에 사용되는 암호화 모듈은 FIPS 140-2 또는 동급의 표준을 준수 (http://csrc.nist.gov/groups/STM/cmvp/validation.html 참조)
- 암호화키 관리 방법에 대한 정책과 프로세스를 확립하고 이용

#### Error Handling and Logging
- 시스템 상세 정보,세션 식별자 또는 계정 정보를 포함한 민감정보를 에러 메시지에 노출 금지
- 디버깅과 스택 추적 정보(stack trace information)를 사용자에게 표시하지 않는 에러 핸들러 사용
- 일반 에러메시지를 구현하고, 사용자 전용 에러페이지 사용
- 애플리케이션은 서버에서 사용되는 에러처리를 사용하는 대신 애플리케이션 에러 처리
- 에러 조건이 발생한 경우 할당된 메모리를 알맞게 해제
- 보안 통제와 관련된 에러 처리로직은 기본적으로 접근을 거부
- 모든 감사기록 통제는 신뢰된 시스템에서 수행(예: 서버)
- 감사 기록 통제는 특정보안 이벤트의 성공과 실패 모두를 지원해야함
- 감사기록에는 중요한 로그 이벤트 데이터(log event data)를 포함하도록 보장
- 비신뢰 데이터를 포함한 로그 엔터리가 로그 열람 인터페이스 또는 소프트웨어에서 코드로써 실행되지 않도록 보장
- 권한이 있는 자에게만 감사기록 접근 허용
- 모든 감사기록을 운영할 때에는 마스터 루틴(master routine)을 활용
- 필요 이상의 시스템 상세내용, 세션 식별자 또는 패스워드를 포함하여 민감한 정보를 감사기록에 저장해선 안 됨
- 감사 기록 분석을 할 수 있는 메카니즘이 존재해야함
- 모든 입력값 검증 실패를 감사 기록
- 모든 인증 시도,특히 실패를 감사 기록
- 모든 접근 통제 실패를 감사 기록
- 의도되지 않은 상태데이터 변경을 포함한 모든 눈에 띄는 부정 시도를 감사 기록
- 모든 시스템 예외를 감사 기록
- 보안 설정 변화를 포함한 모든 관리자 활동을 감사 기록
- 모든 벡엔드 TLS 접속 실패를 감사 기록
- 암호화 모듈 실패를 감사 기록
- 감사 입력 무결성 확인을 위해 암호화 해쉬 함수 사용

#### Data Protection
- 기능, 데이터와 시스템 정보를 수행하는데 필요한 최소한의 권한을 부여하고 사용자를 제한
- 서버에 저장된 민감한 데이터의 캐쉬 또는 임시파일에 대한 허가되지 않은 접근을 차단하고 더 이상 필요하지 않은 경우 즉각적으로 임시 작업 파일을 삭제
- 인증 확인 데이터와 같은 매우 민감한 저장 정보에 대해선 강력한 암호화를 적용(이는 서버 측에서도 동일하다) 
  - 항상 충분히 검증된 알고리즘를 사용. 추가적인 가이드는 “암호화 규칙” 참고
- 사용자가 다운로드하는 서버측 소스코드를 보호
- 사용자측 에패스워드,접속정보 또는 다른 민감한 정보가 일반 텍스트 또는 암호화 되지 않은 채로 저장해선 안됨. 
  - MS viewstate, 어도비 플래쉬 또는 컴파일된 코드와 같이 안전하지 않는 포맷으로 포함되어선 안됨
- 벡엔드 시스템 또는 다른 민감 정보를 노출할 수 있는 주석 정보를 사용자가 접근 가능한 코드에서 제거
- 공격자에게 유용한 정보를 노출할 수 있는 불필요한 애플리케이션과 시스템 문서를 제거
- HTTP GET 요청 파라메터에 민감한 정보를 제외
- 인증을 포함하여 민감한 정보가 포함될 수 있는 폼에 대해 자동완성 기능 비활성
- 민감한 정보를 포함하는 페이지에서 사용자측 캐싱을 비활성화. 
  - HTTP 헤더 콘트롤 “Pragma: no-cache”와 결합하여 사용할 수 있는 Cache-Control: no-store 를 사용할 수 있다.
  - Cache-Control: no-store 는 Pragma: no-cache 보다 비효율적이지만, HTTP/1.0 이후 버전과 호환된다.
- 애플리케이션은 민감한 데이터가 더 이상 필요하지 않은 경우 그 데이터를 삭제하는 기능을 포함해야 함(예: 개인정보 또는 특정 금융데이터)
- 서버에 저장된 민감한 데이터에 대해 적절한 접근 통제 적용. 
  - 캐시데이터,임시파일과 특정 시스템 사용자만 접근 가능한 데이터에서도 동일하게 적용

#### Communication Security
- 민감한 정보 전송시 데이터 암호화. 
  - 통신 보호를 위해 TLS를 사용해야하며, 민감한 파일 또는 HTTP 기반 접속이 아닌 경우에도 개별 암호화를 통해 보호
- TLS 인증서는 유효한 것을 사용하고, 올바른 도메인 명과 기한이 만료되지 않은 것 사용. 또한 필요한 경우에는 중개 인증서가 설치되어야 함
- TLS 접속이 실패한 경우 안전하지 않은 접속으로 다시 이동해선 안됨
- 인증된 접근이 요구되는 모든 콘텐츠와 모든 민감한 정보에 대해 TLS접속을 활용
- 민감한 정보 또는 기능을 포함한 외부 시스템에 접근할 때 TLS를 활용
- 올바르게 설정된 한 개의 표준 TLS를 구현
- 모든 접속에 대해 문자 인코딩을 정의
- 외부 사이트로 연결할 때 HTTP referer 에 민감한 정보를 포함한 파라메터가 전달되지 않도록 구현

#### System Configuration
#### Database Security
#### File Management
#### General Coding Practices