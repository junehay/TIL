# ECS(Elastic Container Service)

AWS에서 제공하는 `컨테이너 오케스트레이션 서비스`로 여러 어플리케이션 컨테이너를 쉽고 빠르게 실행하고, 컨테이너를 적절하게 분배 및 확장 & 축소 할 수 있도록 도와주는 서비스이다.

k8s 기반인 `EKS`와 비교하여 부족한 기능들도 있지만, 상대적으로 적은 러닝커브와 Devops 비용으로 비교적 쉽게 접근이 가능하다.

## 구성 요소

1. **Task definition(작업 정의)**
   Docker 컨테이너를 실행할 때 각종 설정들을 정의하기 위해 사용한다.

   - 컨테이너의 이미지, CPU/메모리 리소스 할당 설정, port 매핑, volume 설정 같은 것들이 포함되며, 기존 docker run 명령에서 가능했던  대부분 옵션이 설정 가능하다.
   - `Task definition` 에는 한개 이상의 컨테이너에 대해 정의가 가능하며, `Task definition` 내부에 정의된 컨테이너 사이는 link 설정으로 연결이 가능하다. `Task definition` 에서 정의된 대로 실제 생성된 컨테이너들을 `Task` 라고 부르게 된다.

2. **Task(작업)**

   - `Task` 는 `Cluster` 에 속한 `Container instance` 에 배포되게 된다.
   - `ECS`의 최소 단위는 `Task` 이며, `Task` 에는 컨테이너를 한개만 포함할 수도 있고, 다수의 컨테이너를 포함할 수 있다.

3. **Cluster(클러스터)**
   - `Task` 가 배포되는 `Container instance` 들은 논리적인 그룹으로 묶이게 되는데 이 단위를 `Cluster` 라고 부른다.
   - `Task` 를 배포하기 위한 instance 는 반드시 `Cluster` 에 등록되어야 한다. (Container instance)
4. **Service(서비스)**
   - `Task` 들의 Life cycle 을 관리하는 부분을 `Service` 라고 한다.
   - `Task` 를 `Cluster`에 몇 개나 배포할 것인지 결정하고, 실제 `Task` 들을 외부에 서비스 하기 위해 ELB 에 연동 되는 부분을 관리하게된다.
     만약 실행 중인 `Task` 가 어떤 이유로 작동이 중지 되면 이것을 자동으로 감지해 새로운 `Task`를 `Cluster`에 배포 하는 고가용성에 대한 정책도 `Service` 에서 관리한다.
