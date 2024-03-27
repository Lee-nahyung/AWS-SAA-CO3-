<h1>💻 AWS<2024.3.26></h1>
<h4>📖 덤프 639p~ 648p<br></h4><br>

- 게이트웨이:
    - Direct Connect 게이트웨이:가상 프라이빗 게이트웨이(VGW)와 프라이빗 가상 인터페이스(VIF)를 그룹화한 것.<br> AWS Direct Connect 게이트웨이는 전 세계적으로 사용 가능한 리소스이므로 모든 리전에서 AWS Direct Connect 게이트웨이를 생성하고 다른 모든 리전에서 액세스할 수 있다.<br>=> 다양한 지역의 여러 VPC에 연결 ㅇ
    https://www.examtopics.com/discussions/amazon/view/132920-exam-aws-certified-solutions-architect-associate-saa-c03/

        <br>
    - Transit 게이트웨이: 가상사설 클라우드(VPC)와 온프레미스 네트워크를 상호 연결하는데 사용할 수 있는 네트워크 전송 허브. <br> 중앙 허브를 통해 VPC와 온프레미스 네트워크를 연결할 수 있다. <br>

- VIF(프라이빗 가상 인터페이스) : Direct Connect를 연결하려면 최소 하나의 VIF중 하나를 생성해야 한다.
  - **프라이빗 가상 인터페이스**: 프라이빗 IP 주소를 사용하여 Amazon VPC에 액세스하려면 프라이빗 가상 인터페이스를 사용해야 한다.
    - **퍼블릭 가상 인터페이스**: 퍼블릭 가상 인터페이스는 퍼블릭 IP 주소를 사용하여 모든 AWS 퍼블릭 서비스에 액세스할 수 있다.
    - **전송 가상 인터페이스**: Direct Connect 게이트웨이와 연결된 하나 이상의 Amazon VPC 전송 게이트웨이에 액세스하려면 전송 가상 인터페이스를 사용해야 한다.
    https://aws.amazon.com/ko/directconnect/faqs/

  <br>
- Amazon EMR: <br>AWS에서 Apache Hadoop 및 Apache Spark와 같은 빅데이터 프레임워크 실행을 간소화하여 많은 양의 데이터를 처리, 분석하는 관리형 클러스터 플랫폼.<br> EMR을 이용하여 S3및 DynamoDB와 같은 기타 AWS 데이터 스토어 및 데이터베이스에서 많은 양의 데이터를 양방향으로 변환할 수 있다.