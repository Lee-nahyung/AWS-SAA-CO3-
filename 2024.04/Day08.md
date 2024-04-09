<h1>💻 AWS<2024.4.7></h1>
<h4>📖 VCE 7회 오답 + VCE 8회<br></h4><br>

- 특정 기간의 데이터만 필요하고, 그 후에는 사용하지 않는 경우 -> <U>TTL(Time to live) 속성을 사용해 타임스탬프를 정의</U>하여 특정 기간 이후에 삭제하도록 구성.

    <br>
- AWS Fargate 시작 유형: 기본 인프라를 관리할 필요 없이 Amazon ECS에서 컨테이너를 실행하는 서버리스 방식.

    <br>
- Amazon Recognition: 애플리케이션에 강력한 시각 분석 기능을 쉽게 추가할 수 있게 해주는 서비스. 수백만 개의 이미지를 검색, 확인 및 구성할 수 있는 애플리케이션을 쉽게 구축할 수 있다.

    <br>
- EC2 인스턴스에서 레거시 시스템 실행 중 (따라서 둘 이상의 인스턴스에서 실행될 수 X) 상황에서 시스템 복구 시간을 향상시킬 수 있는 탄력적인 솔루션: 스토리지 중복성을 위해 RAID 구성을 사용하는 두 개의 EBS 볼륨으로 EC2 인스턴스를 시작. 

        Amazon EBS 볼륨 데이터는 단일 구성 요소의 고장으로 인한 
        데이터 손실을 방지하기 위해 가용 영역의 여러 서버에 복제됩니다. 
        이 복제 기능으로 인해 Amazon EBS 볼륨이 일반 상용 디스크 드라이브보다 10배 더 안정적입니다.

    https://docs.aws.amazon.com/ko_kr/ebs/latest/userguide/raid-config.html

    <br>
- Amazon RDS DB 인스턴스를 생성할 때, 암호화를 사용하도록 할 수 있지만, 생성된 후에는 사용할 수 X. 따라서 다음과 같은 방법 사용.

         DB 인스턴스의 스냅샷을 만든 다음 해당 스냅샷의 암호화된 사본을 만들어 
         암호화되지 않은 DB 인스턴스에 암호화를 추가할 수 있습니다. 
         그런 다음 암호화된 스냅샷에서 DB 인스턴스를 복원하여
          원본 DB 인스턴스의 암호화된 사본을 얻을 수 있습니다. 
    https://docs.aws.amazon.com/ko_kr/prescriptive-guidance/latest/patterns/encrypt-an-existing-amazon-rds-for-postgresql-db-instance.html

    <br>
- 실수로 KMS 키가 삭제되는 것을 방지하기 위해, KMS 키를 삭제하려고 할 때 Amazon SNS를 사용하여 관리자에게 이메일 알림을 보내기 위한 솔루션: KMS DeleteKey가 실행될 때 반응하는 Amazon EventBridge 규칙 생성. Runbook(시스템 관리자 자동화)을 시작하도록 규칙 구성. KMS 키 삭제를 취소하도록 Runbook 구성. SNS주제를 생성하고 이를 관리자에게 알리도록 하는 EventBridge 규칙 구성.

