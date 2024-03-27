<h1>💻 AWS<2024.3.25></h1>
<h4>📖 덤프 629p~ 639p<br></h4><br>

- SCP는 조직의 권한을 관리하는 데 사용할 수 있는 조직 정책 유형.<br>
  <br>if)특정 계정집합에 SCP 적용하려면

  - 해당 조직에 SCP 연결 <br>-> 특정 조직에만 SCP가 적용.
  <br>

  - 해당계정에 대한 OU를 생성하고 SCP를 OU에 연결 <br>-> 해당 OU의 멤버 계정에만 영향을 미침.<br> but, 앞이랑 결과가 같지만 이 옵션이 더 확장성과 관리가 용이함.
  <br>

  - SCP를 루트 OU에 연결 <br>-> 조직의 모든 계정에 적용.
https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html
  <br>


- Route53 Resolver: Direct Connect 또는 VPN 연결을 통해 VPC 및 온프레미스 네트워크에 대한 DNS 확인을 제공.<br>
<br>
  - 인바운드 엔드포인트: 네트워크에서 Resolve로 DNS 쿼리를 전달하기 위해 사용. <br>
  <br>
  - 아웃바운드 엔드포인트: 하나 이상의 VPC에 있는 Amazon EC2 인스턴스에서 시작된 DNS쿼리를 네트워크에 전달.
 <br>


-  🕛CloudWatch Application Load Balancer의 지표

    - **RequestCount**<br>
     :IPv4 및 IPv6를 통해 처리된 요청 수. <br>이 지표는 로드 밸런서 노드가 대상을 선택할 수 있었던 요청에 대해서만 증가. <br>대상이 선택되기 전에 거부된 요청은 이 지표에 반영되지 않는다.

      <br>
    - **RequestCountTarget** : 대상 그룹의 대상당 평균 요청 수. <br>대상 그룹은 TargetGroup 차원을 사용하여 지정해야 한다. <br>대상이 Lambda 함수인 경우 이 지표는 적용되지 않는다.<br>
 이 수는 대상 그룹에서 받은 총 요청 수를 대상 그룹의 정상 대상 수로 나눈 값. <br>대상 그룹에 정상 대상이 없는 경우 총 대상 수가 보고됨. <br>보고 기준: 항상 보고
    <br>
    - **ActiveConnectionCount** :클라이언트에서 로드 밸런서로, 그리고 로드 밸런서에서 대상으로 동시에 연결되는 활성 TCP 연결 총 수.<br>
 보고 기준: 0이 아닌 값이 있을 때
    <br>
    - **TargetResponseTIme** :로드 밸런서에서 요청 신호를 전송한 후 대상에서 응답 신호가 수신될 때까지 결과된 시간(초). <br>이 지표는 액세스 로그에서 target_processing_time 필드와 동일.<br> 
보고 기준: 0이 아닌 값이 있을 때

    <br> https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html
<br>

- 라우팅 알고리즘: 요청을 수신할 대상을 결정할 때 로드 밸런서에서 사용하는 방법.<br>

  - **라운드 로빈**:대상 그룹의 정상 대상 간에 요청을 순차적으로 균등하게 라우팅.<br>이 알고리즘은 일반적으로 받는 요청의 복잡성이 비슷하거나, 등록된 대상의 처리 능력이 비슷하거나, 요청을 대상 간에 균등하게 분배해야 하는 경우에 사용.

    <br>
  - **최소 미해결 요청**:진행 중인 요청 수가 가장 적은 대상으로 요청을 라우팅. <br>이 알고리즘은 일반적으로 수신되는 요청의 복잡성이 다양하고 등록된 대상의 처리 능력이 다를 때 사용.<br> But 슬로우 스타트 모드에서는 사용 불가.<br>
ex) 이미 과부화된 인스턴스에 새 요청이 전달되기를 원하지 않는 상황.

     <br>
  - **가중치 기반 랜덤**: 가중치 무작위 라우팅 알고리즘은 대상 그룹의 정상 대상 간에 요청을 무작위 순서로 균등하게 라우팅.<br>
이 알고리즘은 자동 목표 가중치 (ATW) 이상 현상 완화를 지원.<br>
But 슬로우 스타트 모드에서는 사용 불가.

    <br> https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/load-balancer-target-groups.html#modify-routing-algorithm

- Amazon Managed Streaming for Apache Kafka(Amazon MSK):Apache Kafka를 사용하여 스트리밍 데이터를 처리하는 애플리케이션을 구축하고 실행할 수 있게 해주는 완전관리형 서비스.
     <br>
  - 클러스터 생성, 업데이트, 삭제와 같은 제어 플레인 작업 제공.

    <br>
  - 클러스터 생성, IAM 역할 생성, 클라이언트 머신 생성...... 등으로 시작할 수 있다.

    <br>
  +Apache: 정적 및 동적 웹페이지를 제공하는데 사용. 

    <br>
  +Apache Kafka: 분산 스트리밍 플랫폼으로, 대용량의 데이터 스트림을 신속하게 처리하고 실시간으로 전송할 수 있는 기능을 제공

- AWS Transfer family SFTP 내부서버: <br>프라이빗 연결을 통해 SFTP 프로토콜을 사용하여 온프레미스 시스템에서 AWS로 주문 파일을 안전하게 전송 ㅇ.<br> 내부 서버는 고가용성과 내결함성을 위해 두 개의 가용 영역에 배포됨.

  <br>
- Transfer family 관리형 워크플로:<br> 파일이 SFTP 서버에 업로드되자마자 Lambda 함수를 트리거하여 파일 처리 작업의 조정을 단순화함.<br> 관리형 워크플로는 오류 처리, 재시도 정책 및 로깅 기능도 제공.<br>
https://docs.aws.amazon.com/transfer/latest/userguide/what-is-aws-transfer-family.html

  <br>
- Amazon EMR: <br>AWS에서 Apache Hadoop 및 Apache Spark와 같은 빅데이터 프레임워크 실행을 간소화하여 많은 양의 데이터를 처리, 분석하는 관리형 클러스터 플랫폼.<br> EMR을 이용하여 S3및 DynamoDB와 같은 기타 AWS 데이터 스토어 및 데이터베이스에서 많은 양의 데이터를 양방향으로 변환할 수 있다.
