<h1>💻 AWS<2024.4.1></h1>
<h4>📖 VCE 6회 오답<br></h4><br>

- DynamoDB Streams<br>: 모든 DynamoDB 테이블의 항목 수준 수정 사항을 시간순으로 캡처하여 최대 24시간 동안 해당 정보를 지속적으로 저장한다.<br> 애플리케이션은 거의 실시간으로 DynamoDB 스트림에서 항목 변경 사항이 포함된 일련의 스트림 레코드에 액세스할 수 있다.
  https://aws.amazon.com/ko/blogs/database/dynamodb-streams-use-cases-and-design-patterns/<br>https://www.examtopics.com/discussions/amazon/view/102169-exam-aws-certified-solutions-architect-associate-saa-c03/


    <br>
- IAM 역할은 IAM 그룹에 연결되지 않음. IAM 정책은 IAM 역할, IAM 그룹 또는 IAM 사용자에 연결 ㅇ. (2024.03/Day17 정책과 역할 차이 참고)

    <br>
- 👛특정 기간 동안 할당된 예산 임계값에 도달하면 알림을 받고 AWS 계정에 추가 리소스 피로비저닝을 자동으로 방지하는 방법: <br>
  - AWS 예산을 사용하여 예산을 생성. 필요한 AWS 계정의 결제 대시보드에서 예산 금액을 설정.
  
  - 필요한 권한으로 예산 작업을 실행하기 위해 AWS 예산에 대한 IAM 역할을 생성.
  
  - 각 계정이 예산 임계값을 충족할 때 회사에 알리는 경고를 추가. 추가 리소스의 프로비저닝을 방지하기 위해 적절한 SCP로 생성된 IAM 자격 증명을 선택하는 예산 작업을 추가.

  <br>
- Workload Discovery: <br>거의 실시간 데이터를 기반으로 AWS 계정의 리소스에 대한 자세한 시각화를 구축, 사용자 정의 및 공유할 수 있다. <br>ex)솔루션 아키텍트는 모든 계정에 걸쳐 다양한 워크로드의 관계 세부 정보를 구축하고 매핑해야 합니다.

  https://www.examtopics.com/discussions/amazon/view/109433-exam-aws-certified-solutions-architect-associate-saa-c03/
