<h1>💻 AWS<2024.3.19></h1>
<h4>📖 덤프 592p ~ 599p <br></h4><br>

- VoIP(Voice over IP): IP네트워크를 통해 음성 통화를 제공하는 기술 <br> ex)스카이프, 카카오톡의 보이스톡<br><br>

- Global Accerlerator: IP 주소 캐싱에 의존하지 않고, 전세계 사람들에게 트래픽전달 ㅇ,<br>
VoIP제공, 자동화된 장애조치 ㅇ <br><br>

- ALP나 AWS EC2 인스턴스 같은 AWS 오리진을 퍼블릭 인터넷 트래픽에 노출하면 악의적 공격 발생 가능 <br>
-> Global Accerlerator가 2개의 정적 진입점을 사용해 공격위험 줄임. <br><br>


- Glacier 검색 속도:<br>
Glacier 즉시 검색> Glacier Retrieval > Glacier 유연한 검색<br><br>

- RDS와 SCP는 직접적으로 연결  불가능.<br>
RDS 인스턴스에 대한 엑세스 권한은 IAM 정책을 통해 제어<br><br>

- 인스턴스 무제한 모드:<br>
성능 순간 확장 가능 인스턴스는 필요한 경우 원하는 기간 동안 높은 CPU 사용률 유지 ㅇ,<br>
실행 중이거나 중지된 T 인스턴스의 크레딧 사양을 unlimited와 standard 간에 언제든지 전환할 수 있다.<br><br>

- 🗂️ 리소스 관리 서비스
  - AWS Service Catalog<br>
:배포 전 사용한다. 카탈로그 사용 시 카탈로그에 있는 제품의 여러 버전을 관리할 수 있으며 세분화된 엑세스 제어가 가능하다.<br>

  - 서비스 카탈로그가 관리하는 IT서비스 : 가상 머신 이미지, 서버, 소프트웨어, 데이터베이스 등<br>


  - AWS Config<br>
:인프라 배포 후, 변경 사항을 추적하고 감사할 수 있게 도와줌<br><br>

- 🛜 네트워킹 서비스
  - Amazon S3용 게이트웨이 엔드포인트<br>
:VPC내에서 S3에 연결시 사용, But 연결을 온프레미스 위치로 확장하지x <br><br>
  - AWS Transit Gateway: <br>VPC와 온프레미스 네트워크간 트래픽 라우팅, S3 엑세스를 위한 직접 게이트웨이로 사용 X <br><br>
  - Amazon S3용 인터페이스 엔드포인트<br>
:AWS 리전과 온프레미스 위치 모두에서 S3에 안전한게 엑세스 ㅇ<br><br>
