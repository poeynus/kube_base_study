# kube_base_study

쿠버네티스 입문

인프런 강의 보고 실습 및 간단한 요약 - 강의명: 초보를 위한 쿠버네티스 안내서

## Section 01

- Docker를 모른다면 쿠버네티스를 완벽하게 이해할 수 없음

- 컨테이너 오케스트레이션

        Cluster, State, Scheduling, Rollout/Rollback, Service Discovery, Volume

- 배포과정

        Developer => Git => Build => Deploy => K8s => Scale Out

- 학습과정

        도커 실행 => 쿠버네티스 배포 => 외부 접속 => 스케일 아웃

## Section 02

- 쿠버네티스 내부적 흐름

        상태체크 => 차이점 발견 => 조치  LOOP
        컨테이너, 노드, 서비스 등 여러 곳에서 사용

- 용어

        master, node, k8s, etcd, pod, istio, helm, knative

        cloud native: 처음부터 클라우드에 상주하도록 설계된 애플리케이션

        etcd: 모든 상태와 데이터를 저장, 분산 시스템으로 구성하여 안전성 높임, 백업 필수

        api server: etcd와 유일하게 통신하는 모듈, rest api 형태로 제공, 권한 기능, 수평 확장

        Scheduler: 새로 생성된 pod를 감지하고 실행할 노드를 선택

        Controller: 끊임 없이 상태를 체크하고 원하는 상태를 유지, 단일 프로세스

        kublet: pod를 실행/중지하고 상태를 체크, CRI(Container Runtime Interface)

        proxy: 네트워크 프록시와 부하분산 역할

- 흐름

        Controller, Scheduler <=> API Server(권한 확인) <=> etcd

- 쿠버네티스 오브젝트

        pod: 가장 작은 배포 단위, 고유 IP 존재, pod 하나에 여러개의 컨테이너가 있을 수 있음(네트워크 공유)

        ReplicaSet: 여러개의 pod를 관리, 신규 pod를 생성하거나 기존 pod를 제거하여 원하는 수 유지(Replicas)

        Deployment: 배포 버전 관리, 내부적으로 ReplicaSet 사용

        ClusterIP: 클러스터 내부에서 서비스 연결은 DNS를 사용, 내부에서만 사용가능 외부에서 요청 불가

        NordPort: 외부에서도 요청할 수 있게 하는 것

        Ingress: 도메인 또는 경로별 라우팅, loadBalancer 총 관리자

---

- 나중에 따로 공부해 볼 부분

        1. 다양한 환경별 특징(BARE METAL, EKS ...)
        2. 쿠버네티스 패턴(사이드카, 어댑터 ...)
        3. 관련 생태계(서비스메시, 서버리스)
        4. GitOps CI/CD
        5. 승인제어 등 고급 기능
