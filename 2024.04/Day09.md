<h1>💻 AWS<2024.4.9></h1>
<h4>📖 VCE 7회 오답 + VCE 8회 오답<br></h4><br>

- S3 버킷에 대량의 반구조화된 데이터 저장, 병렬 데이터 처리를 사용해 데이터를 더 빨리 처리 => Amazon EMR을 사용해 S3 데이터 처리. 

    <br>
- 회사가 감사자와 DB를 공유하는 가장 안전한 방법 => DB의 암호화된 스냅샷을 생성하고 이를 감사자와 공유. Amazon KMS 암호화 키에 대한 엑세스 허용.

    <br>
- 중앙 집중식 회사 디렉터리 서비스를 사용하여 AWS 계정에 대한 엑세스를 인증해야 함. => 모든 기능을 켠 상태에서 AWS Organizations에 새 조직 생성. 조직에서 새 AWS 계정을 생성한다. (AWS Organizations는 여러 AWS 계정을 중앙에서 관리하고 제어할 수 있도록 하는 서비스.) + 조직에서 AWS IAM Identity Center를 설정. IAM Identity Center를 구성하고 회사의 회사 디렉터리 서비스와 통합 

    + AWS Organizations에는 AWS Directory Service를 직접 사용할 수 있는 인증 메커니즘이 없기 때문에 동작 x

    <br>
- API Gateway 리전 사용자 지정 도메인 이름의 경우 API와 동일한 리전에서 인증서를 요청하거나 가져와야 한다. 

    <br>
- AWS Rekognition: 부적절하거나 원치 않거나 불쾌감을 주는 콘텐츠 감지 ㅇ, 신뢰도가 낮은 예측에는 인적 검토를 사용하는 것이 적절.

    <br>
- ALB에서 리스너 규칙 사용: 클라이언트의 요청을 받아들이고 각 리스너 규칙의 조건을 확인하여 해당 조건에 맞는 동작을 실행 ex) 회사가 ALB를 사용하는 입장에서 요청이 HTTPS를 사용하도록 모든 요청을 웹사이트로 전달하려는 경우.

    <br>
- Windows File Server + AWS로 이동 => Amazon FSx File Gateway. 이는 Windows 파일 공유에 대한 온프레미스 엑세스를 최적화하여 짧은 지연시간과 공유 대역폭을 유지하면서 Windows 파일 서버용 FSx에 쉽게 엑세스할 수 있도록 함.

    <br>
- 웹 애플리케이션을 실행하는데 EC2 인스턴스가 프라이빗 서브넷에 위치하고, ALB 사용. But 인터넷 트래픽이 EC2 인스턴스에 도달하지 않는 경우 -> 각 가용 영역에서 퍼블릭 서브넷을 생성, 퍼블릭 서브넷을 ALB와 연결, 프라이빗 서브넷에 대한 경로를 퍼블릭 서브넷에 대한 경로 테이블로 업데이트 
    https://repost.aws/ko/knowledge-center/public-load-balancer-private-ec2
