<h1>💻 AWS<2024.3.16></h1>
<h4>📖 덤프 558p ~ 576p <br></h4><br>

- Auto Scaling과 On-Demand모두 확장성이 뛰어나지만,
Auto Scaling은 알려진 트래픽 패턴에 적용되고
On-Demand는 알려지지 않은 트래픽 패턴에 더 좋다.<br>
이 둘 중에서 비용적인 면에선 더 비싸지만 확장성이 더 좋은 옵션은 On-Demand

       (온디맨드 가격 책정 모델은 트래픽이 몇 초 또는 몇 분 만에 급증할 수 있고, 부족하게 프로비저닝된 용량이 사용자 경험에 영향을 미칠 수 있는 급증하는 워크로드, 새로운 워크로드 또는 예측할 수 없는 워크로드에 이상적)

       (DynamoDB Auto Scaling은 실제 워크로드가 몇 분 동안 지속적으로 높아지거나 낮아지는 경우에만 프로비저닝된 처리량 설정을 수정한다는 점에 유의하는 것이 중요. 이는 DynamoDB 테이블의 프로비저닝 용량을 확장하거나 축소하는 데 적용. 가끔씩 사용량이 급증하는 경우 Auto Scaling이 제때에 반응하지 못할 수도 있다.)

       https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/capacity.html
<br>


- 스키마를 빠르게 발전시킬 수 있는 기능 -> NoSQL(ex. DynamoDB). <br>
Aurora와 같은 관계형 DB는 스키마 변경이 어렵다.<br><br>

- SQL 주입 및 XSS공격: 7계층 공격. <br>
이는 WAF로 방어할 수 있음.<br>
(XSS:웹 페이지에 악성 스크립트를 삽입하여 다른 사용자의 브라우저에서 실행되도록 하는 공격)<br><br>

- 사용자에게 AWS 리소스에 대한 엑세스 권한 제공<br>
-> SAML 기반 페더레이션 구성, 적절한 정책이 연결된 역할 생성 후 Active Directory 그룹에 매핑<br><br>

- Amazon Cognito : 모바일 및 웹 애플리케이션 개발자가 사용자 인증, 권한 부여 및 사용자 관리를 간편하게 구현하는 서비스.<br><br>

- 🛜 네트워크 관리 서비스
  - AWS WAF(Web Application Firewall)는 특정 국가의 사용자가 특정 콘텐츠에 액세스하는 것을 차단하여 보장할 수 있음.
https://repost.aws/knowledge-center/cloudfront-geo-restriction<br><br>
  - Route53: DNS 서비스로서 route53 만을 이용해 특정 지역을 차단하기 어려움.<br><br> +운영 오버헤드를 최소화하면서 가용성을 최대화 (= 서버리스),
자동화 ㅇ 서비스<br>
=> Route53<br><br>


- S3 Storage Lens: 스토리지 사용량 및 활동 추세에 대한 가시성을 제공. 불완전한 멀티파트 업로드를 찾을 수 ㅇ


- RDS 블루/그린 배포
: 프로덕션 DB 환경을 별도의 스테이징 환경에 복사
=> 프로덕션 환경에 영향을 주지 않고 스테이징 환경에서 데이터베이스 변경 ㅇ(데이터 손실 없이 기능 업그레이드, 테스트 ㅇ)
  
-  ECS Fargate: 사용량에 따라 요금이 부과되는 서버리스 컴퓨팅 엔진. 서버관리나 리소스할당, <br>규모 조정을 자동으로 함.

