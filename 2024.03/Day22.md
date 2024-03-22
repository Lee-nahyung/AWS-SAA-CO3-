<h1>💻 AWS<2024.3.22></h1>
<h4>📖 VCE 3회, 오답 풀이<br></h4><br>

- AWS Transfer Familly -> S3에 수신 파일을 저장할 FTP 서버 생성 + Lambda를 사용해 파일을 처리하고 처리 후 삭제<br>
: 배치 스케줄링, 인프라 관리 필요하지 않은 서버리스 솔루션.<br> + S3 이벤트 알림을 사용하여 함수를 호출하여 거의 실시간으로 처리 가능.<br><br>


- 공유 블록 장치 볼륨 Key word = EBS<br><br>

- Rest API에 대한 자격증명, 최소한의 노력(서버리스)<br>
=> Cognito를 사용하여 각 요청을 검증하도록 API Gateway에서 사용자 풀 권한 부여자 구성. <br>
**"Cognito 사용자 풀 권한 부여자는 액세스 제어를 위해 Cognito와 API 게이트웨이 간의 원활한 통합을 허용"**<br><br>

- **Lambda@Edge 함수**는 CloudFront 엣지 위치에서 Lambda함수를 실행하게 해주는 서비스.<br>
외부 이미지 관리 라이브러리와 함께 사용하고 CloudFront 동작과 연결하면 Lambda@Edge 함수를 사용해 이미지를 동적으로 조정<br><br>

- **Cloud 오리진 요청 정잭**: CloudFront가 오리진에 보내는 요청에 포함된 값(URL 쿼리 문자열, HTTP 헤더 및 쿠키)를 제어하는 정책. <br><br>

- 🧷PRO 복구 솔루션
  - **DB 전역 테이블** 구성, RPO 복구의 경우 애플리케이션이 다른 AWS 리전을 가르키도록 함 <br>
-> 리전 장애 발생 시 리디렉션은 ㅇ, But 데이터 손상에는 취약함.<br>
글로벌 테이블에서 새로 작성된 항목은 일반적으로 1초 이내에 모든 복제본 테이블에 전파되어 데이터를 잘못 건들여도 전파 ㅇ <br><br>

  - **DB 지정 시간 복구** 구성, RPO 복구의 경우 원하는 시점으로 복원<br>
-> DynamoDB는 주문형 백업을 제공, 규정 준수 요구 사항에 대한 장기 보존 및 보관을 위해 테이블의 전체 백업을 생성할 수 ㅇ<br>
-> 우발적인 쓰기 및 삭제 작업으로부터 테이블을 보호하는데 도움 <br><br>

- 👨‍💼System Manager⭐
    - 사용자, 그룹 또는 역할에 IAM권한이 있는지 확인. <br><br>
    - **세션 매니저**: EC2, 엣지 디바이스, 온프레미스 서버 및 가상 머신을 관리 ㅇ. <br>인바운트 포트를 열거나, 배스쳔 호스트를 유지하거나, SSH 키를 관리할 필요 없이 노드 관리를 제공함.<br><br>
  - **Run Command**:일반적인 관리 작업을 자동화하고 대규모로 일회성 구성 변경을 수행할 수 있음.
  ex) 회사는 중요한 보안 취약점을 수정하기 위해 가능한 한 빨리 모든 EC2 인스턴스에서 타사 소프트웨어를 패치해야 한다.

            AWS Systems Manager의 기능인 Run Command를 사용하면 
            관리형 노드의 구성을 원격으로 안전하게 관리할 수 있습니다. 
            관리 형 노드는 Systems Manager용으로 구성된 하이브리드 및 
            멀티클라우드 환경 의 Amazon Elastic Compute Cloud(Amazon EC2) 
            인스턴스 또는 비EC2 시스템입니다 
            
     https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html<br><br>

  - **Patch Manager**: 패치를 즉시 실행할 수 x, SSM 에이전트와 패치 소스에 대한 연결, S3 엔드포인트 엑세스 등의 확인이 필요함.<br>
https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager-prerequisites.html<br><br>

 - 🗝️암호화 모드
     - 규정준수 모드: 객체에 엄격한 보존 정책을 적용해 수정이나 삭제 방지.<br><br>
     - 거버넌스 모드: 문서에 필요한 불변성 제공 x, 잠재적인 수정이나 삭제가 허용<br><br>
  

- 🌩️CloudFront vs Global Accerlerator 사용사례
  - **CloudFront**: 모든 HTTP 원본을 사용하여 온디맨드 비디오(VOD) 또는 라이브 스트리밍 비디오를 제공<br><br>
  - **Global Accerlertaor**: 게임(UDP), IoT(MQTT) 또는 음성과 같은 HTTP가 아닌 사용 사례에 적합<br><br>

- 북마크: AWS Glue에서 작업 실행의 상태 정보를 유지하여 ETL 작업의 실행중에 이미 처리된 데이터를 추적.-> 이 지속된 상태 정보를 "작업 북마크"라 함. <br>=> **작업 북마크는 Glue가 유지 관리하는데 도움**울 줌.<br><br>


- 👜S3 Inventory: <br>(S3에서 기본 암호화 설정을 활성화 하면 새로 추가된 객체에 대해 자동으로 암호화. )<br>But, 기존 객체를 암호화 하기 위해선 새로운 솔루션 필요.<br><br> => Inventory 기능을 사용해 암호화 되지 않은 객체 목록을 생성, 복사 명령을 사용해 해당 객체를 암호화하는 S3 배치 작업을 수행.<br><br>

- Aurora를 사용할 경우, AWS Backup 기능을 사용하지 않고도 오로라 교차 리전 복제본(Aurora Cross Region Replica)를 사용하여 데이터를 다른 리전으로 복제할 수 있음.<br><br>

- S3 지능형 계층화(S3 Intelligent-Tiering): 엑세스가 불규칙한 패턴에 적합, 검색 비용이 없음 <br>-> 비용 효율적. <br><br>

- 3자가 소유한 AWS 계정에 대한 엑세스 제공 방법<br>
: IAM 그룹을 생성하지 않고, IAM 역할을 사용하여 해당 리소스에 대한 엑세스 권한을 위임 ㅇ<br>https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.html<br><br>

- ☃️DataSync vs Snowball
  - DataSync: NFS 파일 시스템 간 대용량 데이터 이동에 최적화된 데이터 전송 서비스. 온라인으로 데이터 전송 ㅇ<br>
  ex) 두 리전의 NFS 파일 시스템 간에 대량의 데이터를 주고 받아야 하는 상황<br><br>
  - Snowball : 주로 대용량 데이터 전송을 통한 마이그레이션 시 사용.<br>데이터를 전송하기 위해 물리적 디바이스가 필요.<br> 온라인 데이터 전송 솔루션이x<br><br>

- DynamoDB를 사용하는 상황에서 애플리케이션 재구성x 성능 효율성 높이는 방법:<br> Amazon DynamoDB Accelerator(DAX)사용<br>
=> Amazon DynamoDB용으로 구축된 완전 관리형 고가용성 캐싱 서비스, 초당 수백만 건의 요청에서도 밀리초에서 마이크로초까지 최대 10배의 성능 향상을 제공. <br>기존 DynamoDB와 통합 가능.<br>
https://aws.amazon.com/dynamodb/dax/<br><br>

- Stroage Gateway
    - 파일 게이트웨이: 온프레미스의 파일서버와  S3간의 연결을 지원.<br><br>
    - 볼륨 게이트웨이: 블록 기반의 볼륨을 가상 머신(VM)형태로 제공하여 온프레미스 애플리케이션에 연결할 수 있도록 함.<br> 이는 파일 수준의 접근보다는 데이터에 대한 블록 수준의 접근에 적합함.<br><br>
  
- 🧷사내 네트워크 -> 외부 인터넷 -> 배스천 호스트 -> 애플리케이션인 일반적인 상황에서의 보안그룹 설정
    - **Bastion Host**는 퍼블릭 서브넷 내에 NAT 게이트웨이와 함께 위치하며 네부 네트워크에 접근할 수 있는 유일한 창구. <br>SSH 접근도 이곳을 통과해야 가능.<br> 배스천 호스트로 오는 트래픽은 외부 인터넷을 통해서 온 회사의 IP 이므로, 배스천 호스트의 보안 그룹을 회사의 외부 IP 범위에서만 인바운드 엑세스를 허용하는 보안그룹으로 설정해야함.<br><br>
   - 그 다음, **배스천 호스트-> 애플리케이션**으로 오는 트래픽을 허용해야 하는데, <br>이미 배스천 호스트에서 안쪽의 내부 네트워크와 통신하기 위해 private IP를 들고 왔기 때문에 애플리케이션 인스턴스의 보안 그룹은 배스천 호스트의 개인 IP 주소에서만 인바운드 SSH 엑세스를 허용하도록 설정해야함.<br><br>

- 연속 백업<br>
  : 연속백업은 **DynamoDB**의 기본 기능으로, 서버나 클러스터를 관리할 필요 없이 모든 규모에서 작동하며, AWS 리전 및 계정 전체에서 지난 35일 중 원하는 시점으로 초당 단위로 데이터를 내보낼 수 있음.<br>
  ex) DynamoDB를 사용하는 상황에서, 최소한의 코딩으로 Amazon S3버킷에 대한 지속적인 백업을 구성해야 하는 상황.<br>
https://aws.amazon.com/blogs/aws/new-export-amazon-dynamodb-table-data-to-data-lake-amazon-s3/<br><br>

- 🪙리소스 관련(Day20 참고)
   - **Config**: 리소스 구성 사항 변경 추적. <br>AWS 리소스의 구성을 평가, 감사 및 평가할 수 있는 완전관리형 서비스<br><br>
   - **CloudTail**: 리소스 내역 기록. <br>AWS 리소스에  대한 자세한 API 활동 기록을 제공하는 완전관리형 서비스. <br>(API 호출을 한 사람, 호출한 시각, 호출의 영향을 받은 리소스를 포함하여  AWS계정의 모든 API 활동을 기록.)<br>
=> 이 정보를 통해 AWS 리소스에서 발생할 수 있는 의심스러운 활동을 조사할 수 있음.<br><br>

