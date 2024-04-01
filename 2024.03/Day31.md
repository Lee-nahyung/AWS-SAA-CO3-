<h1>💻 AWS<2024.3.31></h1>
<h4>📖 VCE 5회 오답 + VCE 6회<br></h4><br>

- 데이터 처리에 SQS와 EC2를 사용하면 복잡하고 운영 오버헤드 증가.

- 장애조치 AWS지역에서 DR 전략:
  - **지역 예약 인스턴스**:지역에 대한 예약 인스턴스를 구매하는 경우. <br>이는 용량을 예약하지 X.

  - **용량 예약**: 특정 가용 영역의 Amazon EC2 인스턴스에 대한 컴퓨팅 용량을 특정 기간 동안 예약할 수 있음. <br>용량은 예약되어 필요할 때 활용할 수 있으므로 장애 조치 지역에서 EC2 용량을 제공하기 위한 요구 사항을 충족.

- 동일한 데이터 세트를 반환하기 위한 반복적인 호출로 성능저하 -> Redis 및  Memcached용 Amazon ElastiCache를 구현하면 반복되는 쿼리 결과를 캐시하여 DB 로드가 줄어들음.

- 📂binlog 복제: <br>바이너리 로그(Binary log)를 사용해 DB의 변경 사항을 다른 RDS DB 인스턴스로 복제하는 매커니즘을 의미. <br>바이너리 로그는 DB에서 수행되는 모든 작업변경을 기록.<br> 따라서 'RDS 기본 노드에서 binlog 복제를 활성화한다'는 것은 마스터 DB 인스턴스의 바이너리 로그 기능을 활성화한다는 의미.<br> <U>⭐But, 읽기 전용 복제본을 추가하기 위한 목적으로는 필수 x</U>

    <br>
- Saas 키워드 = Amazon Appflow.<br>
Amazon Appflow는 (Salesforce, SAP, Zendesk 및 ServiceNow와 같은 )Saas 애플리케이션과 Amazon S3및 Amazon Redshift와 같은 AWS 서비스 간에 데이터를 안전하게 전송할 수 있는 완전 관리형 통합 서비스.

    <br>
- 네트워크 ACL은 IP 주소 범위만 차단할 수 있으며, 특정 IP 주소만 차단하는 데 적합하지 않음.<br>
 ->따라서 특정 IP를 차단하고 싶으면, AWS WAF구성을 수정하여 악성 IP 주소를 차단하는 IP 일치 조건을 사용하는 것이 좋음.

 - **공급업체 문제**:
   1. 공급업체는 회사의 AWS 계정에 대한 IAM 권한이 X, 회사가 공급업체에 권한을 부여해야 하는 상황
   -> 회사 계정에 IAM역할 생성하고, 공급업체에 필요한 권한에 대한 역할에 적절한 IAM 정책 연결.

   2.  공급업체 AWS 계정에 S3 버킷의 객체를 다운로드 하는 데 필요한 최소한의 엑세스 권한이 있는지 확인하려는 경우 -> IAM 역할에 대해 지정된 읽기 전용 엑세스 정책이 있는 교차 계정 IAM 역할을 생성. 
    

- **교차 계정 IAM 역할**<br>: 한 AWS 계정의 사용자에게 다른 AWS 계정의 리소스에 대한 엑세스 권한을 부여하는 방법. <br>교차 계정 IAM 역할에는 읽기 전용 엑세스 정책이 연결되어 있어 사용자가 객체를 수정하거나 삭제하지 않고도 S3 버킷에서 객체를 다운로드 ㅇ.


    <br>
- 🧊Glacier 스토리지 비용:<br>
    <U>Data를 Glacier에 저장할 때, 조기 삭제할 경우 비용이 발생.</U> <br>따라서 삭제를 진행해야 하는 기간을 확인하고 스토리지 클래스를 설정하는 것이 중요.

    <br>
- **높은 가용성(HA) & 애플리케이션 DB로 Amazon EC2 사용하는 경우 & 자동 장애조치** :
  - 서로 다른 가용영역에서 각각 두개의 EC2 인스턴스 배포 <br>-> HA보장.

  - <U>두 EC2 인스턴스 모두에 DB 설치하고 이를 클러스터로 구성</U> & 인스턴스간 DB 복제 설정 -> 다른 인스턴스에 장애가 발생할 경우, 한 인스턴스가 중단없이 요청을 처리. HA 보장 가능, 데이터 일관성 보장.
  
  <br>
- 🗝️Amazon S3에서 암호화되지 않은 객체 목록 찾기 & 고객이 제공한 키를 사용해 모든 보관 데이터를 암호화 하는 방법<br> :Amazon S3 인벤토리 보고서를 필터링하여 암호화되지 않은 객체 목록을 생성, <br>고객 제공 키를 사용한 서버 측 암호화를 통해 목록의 객체를 암호화 하도록 S3 배치 작업을 구성<br> + 고객 제공 키로 암호화 하도록 S3 기본 암호화 구성.

  <br>
- Amazon EC2 인스턴스에 대해 **SSH 엑세스**를 얻을 수 있는 안전한 방법<br>: AWS System manager Session Manager 사용 <br>-> AWS System manager Session Manager는 SSH 키나 배스천 호스트를 사용하지 않고도 EC2 인스턴스에 안전하게 연결하게 해주는 서비스. 

  <br>
- **동적 IP 주소가 있는 글로벌 고객**이 안전하게 엑세스 <br>-> 0.0.0.0/0에서 포트 443의 인바운드 트래픽을 허용하도록 웹 서버의 보안그룹 구성.

  <br>
- EC2 인스턴스는 임시 로컬 스토리지가 필요하지 않음 <br>-> EBS 스냅샷이 필요하지 않으며, AMI를 최신으로 유지하는 것이 중요.

  <br>
- MFA 디바이스가 분실된 경우 루트 사용자 계정에 대한 엑세스 권한을 잃지 않기 원하는 경우 <br>-> 루트 사용자 계정에 여러 MFA 장치를 추가. <br>하나의 MFA 장치가 분실된 경우에도 계정에 계속 엑세스 ㅇ

  <br>
- RDS는 2024년 3월부터 io2를 지원. 따라서 https://www.examtopics.com/discussions/amazon/view/102161-exam-aws-certified-solutions-architect-associate-saa-c03/ <br>이 문제에 대한 답은 C.

  https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html

  <br>
- <U>RDS DB 인스턴스가 필요하지 않는 경우, 중지보다 종료하는 것이 좋음.</U><br> Amazon RDS DB 인스턴스는 최대 연속 7일 동안 실행이 중지. 그 이후에는 DB 무결성을 보호하기 위해 RDS가 자동으로 DB 인스턴스를 시작. 
  https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_StopInstance.html

  <br>
- 
