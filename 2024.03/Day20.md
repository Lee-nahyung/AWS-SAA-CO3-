<h1>💻 AWS<2024.3.20></h1>
<h4>📖 덤프 599p~ 604<br></h4><br>

- 🏴태그 정책을 사용하는 방법: 
  - **AWS organizations**를 사용하여 "태그정책"을 관리한다.<br> 조직의 관리 계정에 로인하고 organizations를 사용해 태그 정책 기능을 활성화. <br>
태그 정책을 생성 후 조직 엔터티에 연결하여 해당 태그 규칙 적용 .<br><br>
  - **AWS Resource Groups** 사용하여 "태그정책 준수"관리. Resource Groups를 사용하여 계정의 리소스에서 정책 미준수 태그를 찾음. <br>리소스를 생성한 aws 서비스에서 정책 미준수 태그를 수정한다. <br><br>

- Amazon FSx 파일 게이트웨이(FSx 파일 게이트웨이)를 사용하려면 <br>Windows 파일 서버용 Amazon FSx 파일 시스템이 하나 이상 있어야 한다.<br>
https://docs.aws.amazon.com/filegateway/latest/filefsxw/file-gateway-fsx-concepts.html<br><br>

- Amazon RDS는 단일 대기 인스턴스가 포함된 다중 AZ 배포 사용 <br>-> DB 인스턴스에 대한 고가용성 및 장애조치 제공.

        But, 고가용성 옵션은 읽기 전용 시나리오에 대한 확장 솔루션이 아닙니다. 읽기 트래픽을 제공하기 위해 대기 복제본을 사용할 수 없습니다. 읽기 전용 트래픽을 제공하려면 대신 다중 AZ DB 클러스터 또는 읽기 전용 복제본을 사용하십시오.
        
    https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZSingleStandby.html<br>


- 인메모리 데이터베이스
  - Redis<br>
:다양한 데이터 지원
캐싱, 세션관리, 메세징, 게임 순위표,
미디어 스트리밍, 실시간 분석등에 사용<br><br>
  - Memcached<br>
:단순 문자열 지원
주로 캐싱 용도로 사용.<br><br>


- 🕶️모니터링 도구
  - Cloudwatch logs
:EC2 인스턴스, CloudTail, Route53 등에서 로그 파일을 모니터링, 저장, 엑세스할 수 있다.<br>
Cloudwatch logs를 사용하면 로그를 확장성이 뛰어난 단일 서비스로 중앙 집중화할 수 있다.<br>
민감한 데이터가 있는 경우 데이터 보호 정책을 통해 해당 데이터를 감사하고 마스킹할 수 있다.<br><br>

  - CloudTail<br>
:AWS 계정의 운영 및 위험 감사, 거버넌스 및 규정 준수를 지원한다. <br>사용자, 역할, AWS 서비스가 수행한 작업이 CloudTail에 이벤트로 기록된다.<br><br>
+CloudTail Lake: 감사 및 보안 목적으로 사용자 및 API 활동을 엑세스, 저장, 분석하기 위한 관리형 데이터 레이크.<br>
=> AWS 인프라 전반에 걸쳐 계정 활동을 보고, 검색, 다운로드, 보관, 분석하고 이에 대응할 수 있다. <br><br>


- 🕛헷갈릴 수 있는 부분
    - "Near Real Time" 패턴:<br>
CloudWatch Logs에서 로그를 수집합니다.<br>
Subscription Filter를 사용하여 특정 로그 그룹의 로그 이벤트를 필터링합니다.<br>
Kinesis Data Firehose를 통해 필터링된 로그 이벤트를 전송합니다.
Amazon OpenSearch로 로그를 전송합니다.

  - "Real Time" 패턴:<br>
CloudWatch Logs에서 로그를 수집합니다.<br>
Subscription Filter를 사용하여 특정 로그 그룹의 로그 이벤트를 필터링합니다.<br>
AWS Lambda 함수를 사용하여 필터링된 로그 이벤트를 처리합니다.<br>
Lambda 함수에서 Amazon OpenSearch로 로그를 직접 전송합니다.<br><br>


- 🗂️생소한 DB 개념
 - Timestream<br>
:시계열 데이터에 특화.<br> 
ex) IoT 센서 데이터, 애플리케이션 로그, 모니터링 및 메트릭 데이터
사용한양 만큼 요금 청구<br><br>

  - Keyspaces<br>
:Cassandra와 유사. 호환성 높음, 키-값 쌍으로 구성된 데이터 처리<br>
ex) 애플리케이션 데이터, 캐싱, 게임 데이터 등<br>
빠르고 확장 가능하며, 높은 내구성과 가용성 제공<br><br>

- 🗝️KMS 키 개념들 정리<br>
KMS : CloudTail을 통해, 키를 사용하기 위해 이루어진 모든 API 호출을 감사할 수 있다.<br>

  - **KMS키, CMK(=고객 마스터 키, 고객 관리형 키)**<br>
:무료. SSE-S3타입 암호화나 DynamoDB 사용할 떄 사용하는 키.<br>
순환을 활성화 시켜야 함. <br>
(1년마다 순환, but 임포트한 키일 경우 수작업으로만 순환시킬 수 있음. 이 경우 별명을 사용)<br>
CMK는 IAM을 통해 권한을 부여받아 제어 가능하다.<br><br>

  - **서버 관리형 키** <br>
:무료, KMS에서 제공됨.  키가 지정된 서비스 안에서만 사용 가능.<br>
자동으로 1년마다 순환 .<br><br>

  - **고객제공 암호화, CES**<br>
:1달에 1달러.<br>
고객이 직접 암호화 키를 생성하고 관리. <br><br>

  - +대칭 키: 암호화/복호화시 필요한 암호화 키가 1개
