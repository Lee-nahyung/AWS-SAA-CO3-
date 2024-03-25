<h1>💻 AWS<2024.3.24></h1>
<h4>📖 덤프 617p~628p<br></h4><br>

- 임의 IP에서 발생하는 DDos에 대해 웹 애플리케이션 보호 솔루션<br>-> Shield Advanced를 구독하고 DDos 대응 팀 (DRT)와 협력하여 완화 제어 기능을 서비스에 통합시킴.
<br>

- Lustre: 고성능 컴퓨팅(HPC) 환경에서 많이 사용되는 분산 파일 시스템.
<br>

- HPC 클러스터에 일관된 밀리초 미만의 지연시간과 Snowball Edge Storage Optimized 디바이스의 데이터에 높은 처리량 엑세스를 제공하기 위한 방법 :<br>-> Amazon FSx for Lustre 파일 시스템 구성 + s3버킷과 통합.
<br>

- AWS Transfer for SFTP: 데이터를 백업하는 것보다 제3자에게 데이터를 전송하는 것에 특화된 서비스.<br>
교환에 적합한 SFTP 프로토콜을 사용하여 안전한 파일 전송을 제공하는 완전관리형 서비스.
<br>

- 데이터베이스 마이그레이션 시:
1. 메모리 최적화 복제 인스턴스를 사용해 AWS Database Migration Service(DMS)와 AWS Schema Convertion Tool 사용->데이터베이스 객체를 변환한다.<br>
2. 전체 로드 및 변경 데이터 캡처(CDC) 복제 작업 및 테이블 매핑을 생성하여 모든 테이블을 선택한다.<br>
(ex.복제본 지연이 0일 때 Aurora PostgreSQL 읽기 전용 복제본을 독립형 Aurora PostgreSQL DB 클러스터로 승격한다.)
<br>

- (ex. 비정상적인 트래픽 엑세스 패턴 발생) -> 인프라에 대한 가시성 향상 원하는 상황:<br>
  - S3에 대한 ALB 엑세스 로깅 활성화 -> S3에 접근하는 모든 요청에 대한 로그 수집 ㅇ, 이를 통한 보안 강화 ㅇ
  - Athena를 통해 테이블을 생성하고 로그를 쿼리 -> 이를 통한 가시성 향상 ㅇ
<br>

- NAT 게이트웨이:
  - public NAT Gateway: 퍼블릭 인터넷에 엑세스 하기 위함.
  - private NAT Gateway: 다른 VPC 또는 온프레미스 네트워크 연결에 사용.
