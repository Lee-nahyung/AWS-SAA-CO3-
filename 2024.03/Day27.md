<h1>💻 AWS<2024.3.27></h1>
<h4>📖 덤프 648p<br></h4><br>

- 👓각 리소스의 일일 및 주간 기록 워크로드 추세를 분석하는 자동화된 확장 계획을 수립하는 방법:
  - 예측 확장: 기록 데이터를 분석하고 향후 트래픽 패턴을 예측. 
  
    <br>
  - 동적 조정: 목표 추적을 사용하여 지정된 지표를 목표 값으로 유지. 매트릭을 상대에 가깝게 유지하기 위해 필요에 따라 그룹을 확장하거나 축소.

    <br>
- DB에서 반복 읽기의 영향을 완화하는 방법:
  - 캐시 사용. 읽기 문은 결과를 캐시할 수 있다는 것을 의미.

    <br>
- 🗂️DynamoDB 읽기 정합성 :DynamoDB는 테이블과 LSI(로컬 보조 인덱스)모두 기본적으로 읽기 작업에 대한 최종 일관성을 제공. <br>업데이트 직후 쿼리에 최신 데이터 변경 사항이 반영되지 않을 수 있으므로 강력한 일관된 읽기(Strongly Consistent Read)를 true로 설정하면 DynamoDB는 모든 이전 쓰기 작업의 업데이트를 반영하여 최신 데이터가 포함된 응답을 반환한다. <br>이는 글로벌 보조 인덱스 or DynamoDB 스트림에서 제공하지 x. <br>글로벌 테이블은 서로 다른 AWS 리전의 여러 복제본 테이블로 구성.<br> 복제본 테이블의 항목에 대한 모든 변경사항은 일반적으로 1초 내에 전역 테이블 내의 다른 모든 복제본에 복제됨.
 https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html


    <br>
- 대규모 트래픽 급증을 처리 + 순서대로 처리 + 최소 오버헤드 = Kinesis Data stream + Lambda

- 🛒S3관련.
  - **S3 동일 리전 복제(SRR)**: <br>Amazon S3 버킷에 업로드된 새 객체를 동일한 리전 내의 다른 버킷으로 자동으로 복제하는 기능.<br> 이를 통해 데이터 손실로부터 보호하고 가용성 향상 가능. <br>신규 버킷의 데이터 저장 비용 외, 네트워크 전송 용은 추가되지 않는다.<br> 새 객체가 업로드될 때, 자동으로 복제된다. 
  
     ex) 단일 S3 버킷을 사용하는 중앙 집중식 로그 분석 솔루션 구축하려 할 때, 단일 리전에서 애플리케이션이 배포된 여러 AWS계정이 있는 경우. <br>
    https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/replication.html
    
    <br>
  - **S3 양방향 복제**: 여러 개의 AWS리전 간 공유 데이터 세트를 구축하려는 경우 사용한다. <br>이 양방향 복제는 모든 객체 및 객체 메타데이터 변경 사항을 동기화된 상태로 유지하려는 경우 중요하다.<br> 리전의 트래픽이 중단되더라도 양방향 복제 규칙을 사용하여 데이터를 복제하는 동안 모든 메타데이터와 객체를 버킷간에 동기화된 상태로 유지할 수 있다. <br>
  https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/replication.html#two-way-replication-scenario <br>+ 단방향 복제는 설정 및 관리가 간단하지만, 데이터 손실 가능성이 있으며 업로드 대기 시간이 증가할 수 ㅇ.
        
    <br>
  - **S3 다중 지역 액세스 포인트**: 애플리케이션이 여러 AWS 리전에 있는 S3 버킷의 요청을 이행하는 데 사용할 수 있는 글로벌 엔드포인트를 제공한다. <br>단일 리전에서 사용되는 것과 동일한 아키텍처로 다중 리전 애플리케이션을 구축하면, 전 세계 어디에서나 해당 애플리케이션 실행 ㅇ. <br>다중 리전 액세스 포인트 글로벌 엔드포인트에 대한 애플리케이션 요청은 AWS Global Accelerator를 사용하여 AWS 글로벌 네트워크를 통해 라우팅 상태가 액티브인 가장 가까운 S3 버킷으로 자동으로 라우팅된다. 
  
    <br>S3 교차 리전 복제를 사용해 해당 리전의 버킷 간에 데이터를 동기화할 수 있다. <br>그 다음 다중 리전 엑세스 포인트 글로벌 엔드포인트를 통해 데이터를 요청하거나 쓸 수 있다. <br>다중 리전 엑세스 포인트는  Amazon S3용 AWS PrivateLink를 사용하는 애플리케이션을 포함하여 Amazon Virtual Private Cloud(VPC)에서 실행되는 애플리케이션과도 호환 ㅇ.
    https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/MultiRegionAccessPoints.html

- AWS SNS(Simple notification service): 구독자로 메세지를 전송하는 관리형 서비스.  
    - Keyword: 여러대상 ~에, 메세지 필터링, 메세지 보안.
    - 서버 측 암호화는 AWS KMS에서 제공하는 암호화 키를 사용하여 Amazon SNS 주제에 저장된 메시지 내용을 보호한다.
    - Amazon SNS와 Virtual Private Cloud(VPC) 간에 프라이빗 연결을 설정할 수도 있다.
        <br>https://www.examtopics.com/discussions/amazon/view/132929-exam-aws-certified-solutions-architect-associate-saa-c03/
        <br>https://docs.aws.amazon.com/ko_kr/sns/latest/dg/welcome.html