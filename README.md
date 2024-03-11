# AWS-SAA-CO3-
AWS 공부 기록장 TIL<br>
주로 그날 잊지말아야 할 중요 개념을 메모.<br>
(시험 전 까지의 TIL은 마크다운 언어로 코드로 적지 않을 것.)<br>
그 전까지의 기록은 없다.<br>
 <hr>
 
<body>
<strong>⭐<2024.3.10></strong><br><br>
덤프 242p~311p <br>
<br>
<ul>
  <li>NoSQL중 하나인 AWS에서 제공하는 DynamoDB는 계층형 데이터 구조를 지원한다.</li>
  <li>규칙에서 보안 그룹 ID를 사용하면 필요한 통신만 허용하고 최소권한원칙을 준수할 수 있다.</li>
  <li>AMI를 설정한다는 것은 빠른 인스턴스 배포 뿐만 아니라, 고가용성 및 재해복구를 지원하며 자동 스케일링 가능하다.</li>
  <li>API Gateway REST API를 설정하면 클라이언트가 마이크로서비스에 도달하기 위해 호출할 수 있는 HTTPS 엔드포인트를 정의 가능하다.</li>
  <li>NAT 인스턴스는 레거시 기술. (자동 장애조치X) . 따라서 NAT 게이트웨이로 교체. (자동 장애조치 ㅇ, 여러 가용영역에 걸쳐 고가용성 제공)</li>
  <li>Go언어는 Lambda@Edge와 CloudFront 함수에서 지원하지 x</li>
  <li>Oracle에서 PL/SQL 사용 시, 마이그레이션이 매우 복잡하므로 답안 배제.</li>
  <li>다중 AZ 배포를 사용하면 대기 인스턴스가 항상 기본 인스턴스와 동기화되어 데이터 변경 사항이 지속적으로 복제 =>1초 미만의 RPO 달성.</li>
  <li>NetApp ONTAP은 멀티 프로토콜을 지원해 다양한 운영체제와 애플리케이션의 통합을 가능하게 함(LINUX + WINDOWS)<br>https://www.examtopics.com/discussions/amazon/view/99512-exam-aws-certified-solutions-architect-associate-saa-c03/</li>
<br>
</ul>
<strong>⭐<2024.3.10></strong><br><br>
덤프 312p~361p <br><br>
 <ul>
  <li>Lambda: 스크립트 기능이 있으며, 서버리스 컴퓨팅 서비스로서 자동 확장이 가능.</li>
  <li>Cognito는 사용자 인증 및 권한 관리를 위한 AWS 서버리스 인증서비스. 모바일 웹 및 앱 어플리케이션에서 사용자 인증과 데이터 및 엑세스 관리, (추가비용X)</li>
  <li>배스천(Bastion)인스턴스: 보안을 강화하고 원격 엑세스를 관리하기 위한 중간서버 (=점프서버, 접근서버), but 원격 엑세스가 필요하므로 인터넷에 노출</li>
  <li>EBS 스토리지를 사용하는 Kinesis Firehose에서 Redis로 이동하고 구독 -> 거의 실시간으로 수집 및 쿼리 제공<br>
  but EBS볼륨에 장애 발생 시 데이터 손실될 위험 ㅇ</li>
  <li>Kinesis-> Redshift이동 시, 데이터를 로드하는 작업이 필요해 지연 시간 발생.</li>
  <li>Athena에서도 실시간 기능 부족.</li><br>
  <li>
   <ul>
    <li>s3: x-amz-acl 헤더: 해당 객체에 대한 엑세스 권한을 제어하는데 사용.(private를 설정하면 객체에 대한 엑세스가 제한.)</li>
    <li>asw:SecureTransport 헤더: 요청이 안전한 연결(HTTPS)을 통해 이루어져야 함을 나타냄.</li>
    <li>x-amz-server-side-encryption 헤더: 객체 업로드 시 서버 측 암호화를 수행하도록 지시. 데이터를 자동으로 암호화하여 저장.</li>
   </ul>
  </li><br>
  <li>지연시간 없이 온프레미스 sys에서 모든 파일 형식에 즉시 엑세스 하려면, 저장된 볼륨 형식 필요</li>
  <li>멀티파트 업로드: 대형객체에 사용, 불완전한 멀티파트 업로드는 정리하지 않을수록 스토리지 소모.(따라서 정리하도록 S3 수명 주기 정책 구성 필요.)</li>
  <li>빠른 스냅샷 복원 기능을 사용해  AMI 프로비저닝: AMI를 생산하는 가장 빠르고 효율저인 방법.</li>
  <li>AWS Aurora Global Database: Amazon Aurora 데이터베이스 클러스터의 다중 리전 배포를 지원하는 서비스. <br>-> 여러 지역에 걸쳐 데이터베이스를 배포하고 글로벌 환경에서 응용 프로그램의 가용성과 성능 향상 o</li><br>
  <li>
   <ul>
    <li>Compute Saving Plans : 인스터스 패밀리, 크기, AZ, 리전, OS 또는 테넌시와 관계없이 EC2 인스턴스 사용량에 적용 </li>
    <li>EC2 instance Savings Plans: AZ, 규모, OS 또는 테넌시에 관계없이 해당 리전에서 선택한 인스턴스 패밀리의 비용이 자동으로 절감</li>
   </ul>
  </li><br>
  <li><strong>보안관련 사항:</strong>
  <ul>
   <li>GuardDuty: AWS 계정 내에서 악성 활동을 탐지하고 경보 생성. 이상 징후를 실시간으로 모니터링.(보안 전문가에게 알림 및 이벤트 기록 보냄)</li>
   <li>Security Hub: 민감한 데이터의 위치와 엑세스 패턴을 감지하고 분류하는 데이터보안 및 개인정보 보호 서비스 (기계학습 사용)</li>
   <li>WAF: 웹 애플리케이션에 대한 보안 강화, 특히 HTTP 및 HTTPS 트래픽 공격 차단. <strong>DDos 공격 대응 서비스</strong> (애플리케이션 레벨, 나라에 대한 엑세스)</li>
   <li>Shield Advanced: <strong>DDos 공격 방어</strong>, (네트워크 계층)</li>
   <li>Macie: 데이터의 민감한 정보를 감지하고 보호하기 위한 서비스. 취약점 스캐닝 목적 x</li>
   <li>Inspector: 애플리케이션 및 인프라의 취약점을 검사하고 보고서를 생성하는 보안서비스</li>
   <li>Detective : 클라우드 환경에서 발생하는 보안 이벤트를 실시간으로 모니터링하고 감지(ex, 비정상적인 로그인 시도, 민감한 리소스 접근 시도 등의 이벤트 식별하고 경고 생성)</li>
  </ul>
  </li>
 </ul>
</body>


