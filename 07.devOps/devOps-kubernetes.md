### 예전의 devOps
- 서버의 구매 및 설치를 직접 했다.
- 많은 노력과 시간 필요
- 유동적으로 성능(자원)을 높이거나 낮추기 어렵다.(scale up/down)

### Docker
- 컨테이너 기반의 오픈소스 가상화 플랫폼
- os와 각 세팅들을 image에 담아 하나의 컨테이너로 만들어 사용이 편함
- 작은 서비스로 쪼개져서 여러 컨테이너가 생겨나게 되고 각 관리 및 운영이 어렵게 되었다.

### Container Orchestration
- Docker Container의 관리를 쉽게 할 수 있다.
  - 배포, 운영 등
  - Docker Swam, ECS, Nomad, Marathon, Kubernetes
- 이 중에서 Kubernetes가 대세로 떠오르며 거의 표준처럼 사용됨
- learning curve가 높다.
  - cli, yaml, k8s 등


#### ingress
- Load balancer
- Nginx같은 역할로 보면 된다. 들어오는 url에 따라 해당 서비스로 연결 시켜주는?

#### namespace & label
- 하나의 클러스터를 논리적으로 구분한다.
- dev, alpha, beta, real

#### desired state
- 세팅된 상태를 유지하려고 계속 지켜보고 있다.
  - 서버가 죽으면 다시 되살리는 등

#### kubernetes Object
- Pod
- ReplicaSet : Pod들을 모아둔 것

#### Kustomize Setting
- 용도에 따라 파일명 구분하여 사용하면 된다.
- config-map.yaml
- deployment.yarm
- virtual-service-http.yarm

### 배포 전략
- Rolling Update
- Blue Green
- Canary