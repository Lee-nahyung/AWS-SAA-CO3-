<h1>💻 AWS<2024.3.28></h1>
<h4>📖 VCE 4회 오답<br></h4><br>

- 작업
  - **독립실행형 작업**(Standalone Task): <br>독립적으로 실행되며 다른 작업과 독립적으로 관리. 종속성 x.  <br>But 이는 작업이 실행되지 않는 경우에도 작업 스케줄러를 실행하기 위해 리소스를 프로비저닝하고 비용을 지불해야함.

    <br>
  - **예약된 작업**: 프로비저닝할 필요 없이, 작업이 실행된 기간에 대해서만 비용을 지불. <br>예약된 작업은 작업 예약 및 리소스 크기 조정을 자동으로 처리.
  
    <br>
- **AWS Config**: AWS 리소스 구성을 지속적으로 모니터링 및 기록하고, 원하는 구성으로 기록된 구성을 자동으로 평가해준다. <br>ex) Aamazon S3 버킷에 무단 변경이 없는지 확인해야 하는 경우.

    <br>
- Amazon VPC 엔드포인트를 사용해 퍼블릭 인터넷에 노출하지 않고 DynamoDB에 접근하는 예시:
  - DynamoDB에 대한 VPC 엔드포인트를 사용하면 VPC의 Amazon EC2 인스턴스가 퍼블릭 인터넷에 노출되지 않고도 프라이빗 IP 주소를 사용해 DynamoDB에 액세스할 수 있음.<br>-> EC2 인스턴스에 퍼블릭 IP지정할 필요 X. <br>VPC에서 인터넷 게이트웨이, NAT 디바이스 또는 가상 프라이빗 게이트웨이 필요 X.<br>
  https://www.examtopics.com/discussions/amazon/view/117251-exam-aws-certified-solutions-architect-associate-saa-c03/<br>
  https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/vpc-endpoints-dynamodb.html

  <br>
- Organizaions의 조직에 계정을 가지고 있는데, 조직의 특정 AWS 계정에서 생성된 모든 리소스에 태그를 지정하는 솔루션:
  1. 특정 AWS계정을 마스터 계정에서 OU로 이동, 모든 기존 리소스에 올바른 비용 센터 태그가 있어야 하는 SCP를 생성. OU에 SCP를 적용하는 솔루션 <br>-> OU는 리소스 태깅과 직접적 관련 X. <br>SCP는 리소스 생성을 제어할 수 있지만, 기존 리소스에 태그를 자동으로 추가하지X

  2. Lambda 함수가 DB에서 적절한 비용 센터를 조회한 후 리소스에 태그를 지정하는 Lambda 함수 생성. AWS CloudTail 이벤트에 반응하여 Lambda 함수를 호출하는 AWS EventBridge 규칙 생성. <br>-> Lambda 함수 + EventBridge 규칙을 사용해 리소스 태깅 자동화 ㅇ. <br>Lambda 함수는 필요에 따라 확장하여 많은 리소스 처리 ㅇ.<br> => AWS Lambda + CloudTail + EventBridge 규칙을 사용해 필요한 모든 기능을 제공하는 유연하고 자동화된 솔루션 생성 가능.

  <br>
- 🚪스토리지 게이트웨이 (+Day22)

  - **볼륨 게이트웨이**:온프레미스 애플리케이션에 클라우드에서 지원하는 iSCSI 블록 스토리지 볼륨을 제공. 
  https://aws.amazon.com/ko/storagegateway/volume/

    <br>
  - **테이프 게이트웨이**<br>:존 백업 워크플로를 변경하지 않아도 온프레미스에서 물리적 테이프를 AWS에서 가상 테이프로 대체할 수 있다.<br> 테이프 게이트웨이는 모든 주요 백업 애플리케이션을 지원하며 데이터 액세스 시 대기 시간을 낮추도록 온프레미스에서 가상 테이프를 캐시.<br>게이트웨이와 AWS 간의 데이터를 암호화하고 Amazon S3와 Amazon S3 Glacier Flexible Retrieval 또는 Amazon S3 Glacier Deep Archive 간에 데이터를 압축하고 가상 테이프를 전환하여 스토리지 비용을 최소화
  https://aws.amazon.com/ko/storagegateway/vtl/

    <br>
  - **FSx게이트웨이**<br>:Amazon FSx for Windows File Server에서 완전 관리형의 매우 안정적인 파일 공유에 대한 온프레미스 액세스를 최적화.<br>Amazon FSx File Gateway는 파일 기반 스토리지를  클라우드로 빠르게 마이그레이션하여 더 빠른 성능, 향상된 데이터 보호 및 비용 절감을 지원.<br> 충돌 일관성이 있는 자동화된 백업을 활용하고 중앙 집중식 백업 및 보존을 위해 AWS Backup을 사용할 수 있다.
  https://aws.amazon.com/ko/storagegateway/file/fsx/
  
    <br>
  - **S3 게이트웨이**<br>: 온프레미스 애플리케이션을 클라우드에 원활하게 연결하여 아카이브 리포지토리, 애플리케이션 데이터 및 데이터베이스 백업을 Amazon S3에 내구성 있는 객체로 저장하고 액세스.<br>S3의 객체에 대한 파일 프로토콜 액세스가 필요한 온프레미스 데이터 집약적 애플리케이션에 사용.
  https://aws.amazon.com/ko/snow/

  <br>
- 클러스터 배치 그룹<br>: 네트워크 지연 시간을 최소화하기 위해 서로 가깝게 배치되는 단일 가용 영역 내 EC2 인스턴스의 논리적 그룹.<br> 높은 네트워크 성능이 욕되는 대기 시간에 민감한 **HPC 워크로드에 적합.**

- Oracle -> AWS 마이그레이션, DR 설정시:
  1. RDS Custom으로 마이그레이션, 다른 AWS 리전의 DB에 대한 읽기 전용 복제본 생성 <br>-> 기본 운영 체제에 대한 엑세스 유지 ㅇ, But Oracle 복제본의 경우 "리전 간" RDS Custom for Oracle 복제본 생성 불가능. <br>읽기 복제본은 DR에 적합X
   https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/UserGuide/custom-rr.html#custom-rr.limitations


  2.  EC2 인스턴스로 마이그레이션, 다른 AWS 리전으로 DB 복제 설정 <br>-> 기본 운영체제에 대한 엑세스 유지 ㅇ. <br>또한 다른 리전으로 데이터베이스를 복제하여 DR설정 가능.
  
- Cognito
  - **사용자 풀** 구성<br>:앱 또는 API에 사용자를 인증하고 권한을 부여하려는 경우 사용.
  
  - **자격 증명 풀** 구성<br>:인증된 사용자나 익명 사용자가 AWS 리소스에 액세스할 수 있도록 권한을 부여하는 경우 사용.