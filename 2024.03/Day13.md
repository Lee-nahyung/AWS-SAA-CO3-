<h1>💻 AWS<2024.3.13></h1>
<h4>📖 덤프 369p ~ 372p <br></h4><br>

- 📂파일 시스템
   - Amazon EFS: NFS 버전 4를 기반으로, 관리형 NAS 파일러.
파일 시스템은 가용 영역에 분산되어 I/O 병목 현상을 제거하고
데이터 내구성 향상시킴 <br><br>

   - Amazon FSx : Windows SMB를 기반으로 파일 서비스를 실행하는 관리형 windows 서비스. 탄력적인 설계는 az내에서 데이터를 자동으로 복제. 향후 감사 및 분석을 위해 CloudTail에 대한 시스템 이벤트 및 API 호출 기록함<br><br>

  - Lustre 파일 시스템: 일반적으로 컴퓨터 클러스터에서 실행되는 고성능 컴퓨텅 워크로드를 위해 설계<br><br>

- RDS 프록시: 연결 풀링 사용, DB 엑세스의 보안, 성능 및 확장성을 향상.
<br><br>

- ACM은 SSL/TLS 인증서 생성, 관리 및 배포.<br>
이 인증서는 Amazon EC2 인스터스, ELB, API Gateway와 통합이 가능.<br>
but, S3와는 통합이 불가하다.<br><br>

- Amazon Macie는 민감한 데이터를 식별하고 분류할 수 ㅇ<br>
but 민감한 데이터를 암호화는 x <br><br>

