<h1>💻 AWS<2024.3.17></h1>
<h4>📖 덤프 576p ~ 584p <br></h4><br>

- 🔡데이터베이스
  - **Amazon Neptune**:  그래프 분석 서버리스 데이터베이스.<br>
규모에 관계없이 대화형 그래프 애플리케이션 생성 가능.<br>
데이터 읽기, 쓰기, 삭제와 같은 그래프 데이터 작업 및 데이터 활동 상태 모니터링 가능.<br>
데이터 관리 보안 거버넌스 규정준수 및 로그를 분석 가능.<br>
(데이터 엔터티간의 관계 분석 가능)<br>


  - **QLDB(Quantum Ledger Database**, 원장 데이터베이스)<br>
: 중앙의 신뢰할 수 있는 기관이 변경 불가능, 투명, 암호화 방식으로 트랜잭션 로그 제공.<br>
모든 애플리케이션 데이터 변경 내용을 추적하며 완전 검증가능한 시간대별 변경 기록을 유지.<br>
(일반적으로 조직의 경제 및 금융 활동을 기록하는데 사용)<br>
최소 요금  x. 사용하는 내역에 대해서만 요금 지불.
따라서 프로비저닝 필요 x<br><br>

  - NoSQL: 키-값 메서드를 사용해서 데이터를 저장하고 식별, 비관계형DB
  - RDNMS: 행과 열이 포함된 형식으로 데이터 저장. <br>주로 primary 키를 사용해 데이터를 저장하고 식별, 관계형DB<br><br>


- **Aws Fargate**는 컨테이너 기반의 서비스로, 요청 패턴을 예측하지 못하고 갑작스럽게 변화는 상황에 사용 o <br>but, Fargate는 컨테이너를 실행하기 위한 용량을 미리 예약해야 하기 때문에 요청 패턴이 <br>예측 불가능하고 갑작스럽게 변하는 경우 유연한 확장이 어려울 수 있음<br>
-> 서버리스 서비스인 Lambda 사용이 나음<br><br>

- 기본적으로 s3 객체는 비공개, 개체 소유자는 서명된  URL을 생성하여 다른 사람과 개체 공유 ㅇ. 시간제한 권한.<br>
"s3:signatureAge" 조건을 사용하여 시간 변경 ㅇ<br><br>

- 🧑‍⚖️정책과 역할
   - Lambda 리소스 정책: 누가 lambda를 관리할 수 있는지.<br>
   - Lambda IAM 역할에 대한 00역할 부여: Lambda에게 역할 부여<br><br>


- 🗂️인증
  - Amazon 인증기관(CA)는 사이트에 대한 인증서를 발급하기 전, ACM는 요청에 지정한 모든 도메인 이름을 사용자가 소유하거나 제어하고 있음을 입증해야 함<br>
-> 프라이빗 호스팅 영역이거나 기타 프리이빗 도메인의 리소스 검증X<br>따라서 DNS검증을 해야함.<br><br>DNS공급자에게 하나 이상의 CNAME 레코드를 ACM을 통해 제공해야 하고, 이를 통해 해당 도메인의 소유권을 검증할 수 있다. <br><br>또한 ACM 콘솔을 통해 최상위 도메인 example.com에 대한 일반 인증서와 *.example.com에 대한 와일드카드 인증서를 요청하여 하위 도메인에 대한 웹사이트를 암호화 할 수 있다.<br>https://docs.aws.amazon.com/acm/latest/userguide/domain-ownership-validation.html <br><br>외부 키 관리자를 사용하기 위해선, 외부키 관리자가 지원하는 KMS 외부 키 저장소를 사용한다. 외부 키 스토어의 KMS키를 사용하는 암호화 및 복호화 작업은 자체 키 보관(HYOK) 라는 암호화 키 자료를 사용해 외부 키 관리자가 수행 ㅇ

         External key stores let you control the root of trust. Data encrypted under KMS keys in your external key store can be decrypted only by using the external key manager that you control.

    https://docs.aws.amazon.com/kms/latest/developerguide/keystore-external.html






