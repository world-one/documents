### Atomic Design
처음 접한 건 이전 회사에서 진행한 프로젝트였다. 이미 어느 정도 프로젝트 구성이 되어 있는 상태에서
아토믹 디자인을 접하게 되었고 지금까지 쓰고 있다.

#### 기본 구조
- Atom
- Molecule
- Organism
- Template
- Page

위의 다섯 가지 기본 구조를 가지고 컴포넌트를 분리해둔다. 적절한 기준이 있다면 위치에 대한 고민이 줄어 들어서 좋았다.
다만 Organism과 Template에 대한 기준이 좀 모호했다.
그리고 해당 페이지에서만 사용하는 구성은 내부에 또 templates라는 디렉토리를 만들어서 거기에 넣어두었다.
위의 구조는 두 곳 이상에서 사용되는 공통 컴포넌트만 추가해두었다.
이게 아토믹 디자인의 의도에 맞는 사용 방법인지는 잘 모르겠지만 현재는 나름 편하게 잘 쓰고 있다.
그럼에도 다시 차분히 기준을 잡고 프로젝트를 정리해보는 시간을 가지면 좋을 듯 하다.