<h1>💻 AWS<2024.3.23></h1>
<h4>📖 덤프 604p ~ 617p<br></h4><br>

- 애플리케이션 배포 상황: <br> ex) 회사에서 특정 지역에서 일부 애플리케이션을 실행할 수 없는 상황<br>
-> 어떤 지역에 "애플리케이션 배포" 키워드 배제.<br><br>
    회사의 VPC를 eu-central-1에서 선택한 로컬 영역으로 확장하여 AWS 로컬 영역에 애플리케이션을 배포가 정답.<br> + Wavelength Zone에 확장은 x, 이는 모바일 네트워크용<br><br>
  
- **온프레미스와 AWS클라우드의 VPC**의 연결 -> 전송 게이트웨이 생성. <br>전송 게이트웨이는 연결된 네트워크 간의 라우터 역할을 하며 필요한
피어링 또는 VPN 연결 수를 줄여 새 연결 관리를 단순화.<br>
전송 게이트웨이를 생성하고 VPC및 VPN 연결을 사용하면 최소한의 관리 오버헤드 가능.<br><br>

- 기계학습(ML) 교육 및 예측에 관리형 서비스 사용예시
    - **AWS SageMaker** 사용: S3 버킷에 저장된 기록 데이터를 사용해 기게 학습 모델을 교육할 수 ㅇ<br>
    - **Amazon Forecast** 예측기 사용: 기계 학습(ML)을 사용하여 Ml 경험 없이도 매우 정확한 예측 생성 가능.<br>https://aws.amazon.com/blogs/machine-learning/automating-your-amazon-forecast-workflow-with-lambda-step-functions-and-cloudwatch-events-rule/<br><br>

- S3 버킷에 직접 데이터 업로드
-> 회사 내부의 네트워크를 통해 데이터를 전송하여 대역폭 절약, 전송속도 향상 가능 But, S3 멀티파트 업로드가 훨신 빠름.

- S3 버킷의 Cache-Control 헤더의 메타 데이터를 **no-cache**로 설정: <br>클라이언트가 콘텐츠를 캐시하는 것을 방지<br>-> 클라이언트가 매번 요청할때마다 원본서버에서 데이터를 가져오게 하여 **즉시 새 콘텐츠를 반환**하는 강력한 일관성을 가짐. <br><br>

- 🗺️Route53
   - **지연시간 라우팅 정책**: 여러 AWS 리전에 리소스가 있고, 최상의 지연 시간을 제공하는 리전으로 트래픽을 라우팅하는 경우에 사용.<br>
  = 전 세계 사용자를 대상으로 애플리케이션 성능을 향상시키는데 도움을 줌.<br><br>
   - **장애조치 라우팅 정책**: 활성-수동 장애 조치를 구성하려는 경우 사용.<br><br>
   - **지리적 위치 라우팅 정책**: 사용자의 위치를 기반으로 트래픽을 라우팅하려는 경우 사용.<br><br>
   - **지리 근접 라우팅 정책**: 리소스 위치에 따라 트래픽을 라우팅하고, 선택적으로 한 위치의 리소스에서 다른 위치의 리소스로 트래픽을 이동하려는 경우에 사용.<br><br>
  +가장 가까운 위치에 있는 서버가 반드시 최고의 성능을 제공하는 것은 아님.<br>https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html<br><br>

- 3개의 가용영역에서 EC2 인스턴스를 사용하도록 수정<br>
=> 웹 애플리케이션이 트래픽 증가를 처리하고, 1개 or 2개의 가용 영역의 장애를 허용할 수 ㅇ<br><br>

- Amazon CloudWatch Container Insights: <br>마이크로서비스 기반 아키텍처는 여러 개의 독립적인 마이크로서비스가 각각 컨테이너로 실행. <br>이를 CloudWatch Container Insights는 컨테이너화된 애플리케이션 및 마이크로서비스에서 지표와 로그를 수집, 집계 및 요약 제공.<br> EKS및 kubernetes와 통합되어 클러스터, 노드, 작업 및 서비스 수준에서 지표 제공 ㅇ.<br><br>

- AWS X-Ray: 애플리케이션이 제공하는 요청에 대한 데이터 수집, 보고, 필터링하고 통찰력 얻는데 사용할 수 있는 도구를 제공. <br>EKS 및 Kubernetes와 통합되어 마이크로서비스가 보내는 요청을 추적 ㅇ<br>
-> X-Ray를 사용하면 오류, 장애, 성능 문제의 근본 원인을 분석하고 애플리케이션의 서비스 맵 시각화 ㅇ  <br><br>

- KMS키 정책을 통해 고객 IAM 역할을 제외한 모든 보안 주체에 대한 암호 해독 권한 거부 ㅇ<br>(S3 버킷 정책이 아님.)<br><br>
                 
            {
            "Version": "2012-10-17",
             "Statement": [
                  {
               "Effect": "Deny",
               "Principal": "*",
                "Action": "kms:Decrypt",
               "Condition": {
                 "StringNotEquals": {
                      "aws:PrincipalArn": [
                       "arn:aws:iam::123456789012:role/MyCustomerRole"
                      ]
                    }
                }
             }
          ]
        }   
