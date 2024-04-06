<h1>💻 AWS<2024.4.2></h1>
<h4>📖 VCE 6회 오답 + VCE 7회<br></h4><br>

- SQS 엑세스 정책: 자체 계정 권한을 포기하지 않고 다른 회사에 SQS 대기열에 대한 엑세스를 제공하는 방법.

    <br>
- Route53을 사용하는데, 가장 고성능 경험을 제공하기 위해 어떤 Route53구성을 사용해야 하나:<br>
    -> 지연 시간 라우팅 정책(= 대기 시간 정책, latency policy)사용.


    <br>
- Amazon GuardDuty는 AWS 계정과 워크로드 전체에서 악의적인 활동과 무단 행동을 지속적으로 모니터링하는 위협 방지 서비스. GuardDuty는 AWS Security Hub에 조사 결과를 보고할 수 있다.
https://www.examtopics.com/discussions/amazon/view/121177-exam-aws-certified-solutions-architect-associate-saa-c03/

    <br>
- AWS Systems Manager을 사용해 실행 중인 애플리케이션을 중단하지 않고 EC2 인스턴스를 패치하는 방법.
  - EC2 인스턴스에 여러 정책을 연결할 수 X. 
  - 따라서 Systems Manager에서 기본 호스트 구성 관리를 활성화하여 EC2 인스턴스를 관리한다.

    <br>
- 🚪API Gateway API에 대해 설정할 엔드포인트 유형 선택
  - **엣지 최적화** API 엔드포인트<br>: 일반적으로 요청을 가장 가까운 POP ( CloudFront Point of Presence) 로 라우팅하므로 <U>클라이언트가 지리적으로 분산되어 있는 경우에 도움. </U><br>(API Gateway REST API의 기본 엔드포인트 유형)
  https://www.examtopics.com/discussions/amazon/view/116906-exam-aws-certified-solutions-architect-associate-saa-c03/

  - **리전** API 엔드포인트<br>: 동일 리전의 클라이언트를 위한 것.<br> 리전 API는 <U>연결 오버헤드를 줄인다.</U> 리전 API에 대해 API가 배포된 리전별로 고유한 사용자 지정 도메인 이름이 사용된다. <br>여러 리전에 배포된 리전 API를 배포하는 경우, 모든 리전에서 동일한 사용자 지정 도메인 이름을 사용할 수 있다.
  
  - **프라이빗** API 엔드포인트<br>: 인터페이스 VPC 종단점을 사용해서 <U>VPC에서만 액세스할 수 있는 API 엔드포인트</U>

  - https://docs.aws.amazon.com/ko_kr/apigateway/latest/developerguide/api-gateway-api-endpoint-types.html

    <br>
- Lambda 함수에 프로비저닝된 동시성 구성 -> Lambda함수에서 사용할 수 있는 컴퓨팅 리소스의 양을 설정할 수 있으므로 한 번에 더 많은 요청을 처리하고 지연 시간을 줄일 수 ㅇ.

<hr>
- Gateway Load balancer: 방화벽, 침입 탐지 및 방지 시스템, 심층 패킷 검사시스템과 같은 가상 어플라이언스를 배포, 확장, 관리할 수 ㅇ
ex)솔루션 설계자는 트래픽이 웹 서버에 도달하기 전에 애플리케이션에 대한 모든 트래픽을 검사하기 위해 웹 애플리케이션을 어플라이언스와 통합해야 합니다.
