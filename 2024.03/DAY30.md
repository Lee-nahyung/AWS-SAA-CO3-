<h1>💻 AWS<2024.3.30></h1>
<h4>📖 VCE 4회 오답, VCE 5회 풀기<br></h4><br>

- AWS 생소한 개념
  - **Amazon Lex**: 음성 및 텍스트를 사용하는 애플리케이션에 대화형 인터페이스를 구축하기 위한 AWS 서비스. <br>새로운 애플리케이션과 기존 애플리케이션에 정교한 자연어 챗봇을 구축할 수 있다. <br>Amazon Lex는 자연어 이해 (NLU) 및 자동 음성 인식 (ASR) 의 심층적인 기능과 유연성을 제공.
  https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/amazon-lex.html

    <br>
  - **Amazon Comprehend**: 자연어 처리를 사용하여 문서 내용에 대한 인사이트를 추출.<br> 문서에 있는 개체, 핵심 문구, 언어, 감정 및 기타 일반적인 요소를 인식하여 인사이트를 개발한다. <br>Amazon Comprehend는 PHI를 포함하는 데이터와 함께 사용할 수 있다.
  https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/amazon-comprehend.html

    <br>
  - **Amazon Polly**: 텍스트 -> 스피치로 변환하는 서비스.<br>
ex) 시각 장애 환자는 의학적 지침을 받고 음성 합성 형태의 안내서를 사용한다. <br>
https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/amazon-polly.html

    <br>
  - **Amazon Transcribe**: 고급 기계 학습 기술을 사용하여 오디오 파일의 음성을 인식하고 이를 텍스트로 변환.<br>
ex)미국 영어 및 멕시코 스페인어 오디오를 텍스트로 변환하고 오디오 파일의 콘텐츠를 통합하는 애플리케이션을 만들 수 있다. <br>Amazon Transcribe는 데이터를 보관하거나 저장하지 않으며 API에 대한 모든 호출은 SSL/TLS로 암호화.<br>
https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/amazon-transcribe.html
    
    <br>
  - **Amazon Translate**:온디맨드 방식으로 고품질 번역을 제공. 구조화되지 않은 텍스트 문서를 번역하거나 여러 언어로 작동하는 애플리케이션을 구축할 수 있다.  PHI를 포함하는 문서는 Amazon Translate로 처리할 수 있음.
  https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/amazon-translate.html

    <br>
  - **Amazon Textract**: 기계 학습 기술을 사용하여 스캔한 문서에서 텍스트와 데이터를 자동으로 추출. <br>ex)고객은 Amazon Textract를 사용하여 보험 청구 또는 의료 처방에서 데이터를 추출하고 해당 문서에서 키-값 쌍을 자동으로 인식하여 민감한 문서를 수정할 수 있다.
  https://docs.aws.amazon.com/ko_kr/whitepapers/latest/architecting-hipaa-security-and-compliance-on-aws/textract.html

    <br>
  - **Amazon Transcribe, Amazon Translate, Amazon Comprehend 사용 예시**:<br>https://www.examtopics.com/discussions/amazon/view/109639-exam-aws-certified-solutions-architect-associate-saa-c03/

- Amazon Aurora Serverless v2: 가장 까다롭고 매우 가변적인 워크로드에 적합. ex) 데이터베이스 사용량이 짧은 시간 동안 높게 나타나고 오랜 시간 동안 작업이 적거나 전혀 작업이 없을 수 있는 상황.
  https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/AuroraUserGuide/aurora-serverless-v2.how-it-works.html

- AWS에서 스팟 블록은 사용 중지함.

