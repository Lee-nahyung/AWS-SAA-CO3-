<h1>💻 AWS<2024.3.18></h1>
<h4>📖 덤프 584p ~ 592p <br></h4><br>

- 세션 선호도 keyword: <br>공용 ALB (not NLB, GLB) 생성.<br>
 애플리케이션 대상 그룹을 지정한 다음,
AWS WAF에서 웹 ACL을 생성.<br>
이 ACL를 ALB 엔드포인트와 연결함.<br><br>

- NLB와 GLB는 고정 세션을 처리X.<br>
애플리케이션 수준 개념(쿠키)이므로 ALB가 작동한다.<br>
탄력적 IP를 사용하지 못하는 이유는, 고정 세션을 무효화하기 때문이다.<br><br>

- CIDR 범위 업데이트를 위해 보안 그룹 규칙 관리를 중앙 집중화하는 방법: <br> CIDR 목록이 포함된 VPC 고객 관리형 접두사 목록 생성<br>
(관리형 접두사 목록은 하나 이상의 CIDR 블록 집합.<br>
접두사 목록을 사용하면 보안 그룹과 라우팅 테이블 쉽게 관리 ㅇ)<br><br>

- 네트워크를 확장하고 다른 CIDR 블록의 트래픽을 허용하고 싶은 경우:
접두사 목록을 업데이트 하면, 접두사 목록을 사용하는 모든 보안 그룹이 업데이트 된다.<br>
https://docs.aws.amazon.com/vpc/latest/userguide/managed-prefix-lists.html<br><br>
접두사 목록 생성 후 Resource Access Manager(AWS RAM)을 사용해 조직 전체에 접두사 목록 공유 ㅇ<br><br>

- Lustre용 FSx는 SMB나 NFS 제공 x, <br>Lustre 제공<br><br>
