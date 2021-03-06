### 객체지향 개발 5대 원리
- 2000년대 초반 로버트 마틴이 명명
- 이를 마이클 페더스가 두문자어로 소개

#### 단일 책임 원칙 (SRP)
- Single Responsibility Principle
- 한 클래스는 하나의 책임만 가져야 한다.
- 그 책임을 완전히 캡슐화해야 한다.
  
#### 개방-페쇄 원칙 (OCP)
- Open-Closed Principle
- 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.
- 확장에 대해 열려 있다.
  - 모듈의 동작을 확장할 수 있다. 요구에 맞게 새로운 동작을 추가해 모듈을 확장할 수 있다.
- 수정에 대해 닫혀 있다.
  - 모듈의 소스 코드를 수정하지 않아도 모듈의 기능을 확장하거나 변경할 수 있다.

#### 리스코프 치환 원칙 (LSP)
- 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.
#### 인터페이스 분리 원칙 (ISP)
- 특정 클라이언트를 위한 인터페이스 여러 개가 법용 인터페이스 하나보다 낫다.
#### 의존관계 역전 원칙 (DIP)
- 프로그래머는 추상화에 의존해야지, 구제화에 의존하면 안된다.