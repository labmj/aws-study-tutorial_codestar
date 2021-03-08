# aws-study-tutorial

## 파이프라인
![image](https://user-images.githubusercontent.com/79297534/110262905-6d760480-7ff8-11eb-8a44-604301873a89.png)

1. 소스 컨트롤에서 소스 코드를 가져옵니다.
2. 구성 파일을 lint하세요.
3. 코드베이스에서 AWS Lambda 함수에 대한 단위 테스트를 실행하세요.
4. 테스트 파이프라인을 배포하세요.
5. 테스트 파이프라인에 대해 엔드 투 엔드 테스트를 실행하세요.
6. 테스트 상태 머신 및 테스트 인프라를 정리하세요.
7. 승인자에게 승인을 보냅니다.
8. 프로덕션에 배포하세요.


## AWS codeCommit. 배포 자동화 실습

### CodeStar 프로젝트 생성
![image](https://user-images.githubusercontent.com/79297534/110263319-b2e70180-7ff9-11eb-8ad3-81090e4ea483.png)

### 프로젝트 생성 및 유형 선택 : Python 웹서비스/ AWS Lambda 선택 
![image](https://user-images.githubusercontent.com/79297534/110263426-fa6d8d80-7ff9-11eb-9227-787ebe18577a.png)

### 프로젝트 설정 : CodeCommit 리포지토리 선택
![image](https://user-images.githubusercontent.com/79297534/110263606-93040d80-7ffa-11eb-8dca-042d762e6266.png)

### 프로젝트 생성완료 및 예제 프로젝트 배포확인
![image](https://user-images.githubusercontent.com/79297534/110264536-d5c6e500-7ffc-11eb-8b03-c1b4a75044a9.png)

![image](https://user-images.githubusercontent.com/79297534/110264508-c9428c80-7ffc-11eb-9456-4963a5891abb.png)

### 브랜치 생성 확인 및 브랜치 생성 : master, staging
![image](https://user-images.githubusercontent.com/79297534/110264982-d7dd7380-7ffd-11eb-9ccb-0be2097519ce.png)
![image](https://user-images.githubusercontent.com/79297534/110265137-3a367400-7ffe-11eb-8dab-9af987e7f5f3.png)
![image](https://user-images.githubusercontent.com/79297534/110265319-a1ecbf00-7ffe-11eb-87cc-99c5e947d464.png)

### staging브랜치 output 변경
![image](https://user-images.githubusercontent.com/79297534/110265439-e8421e00-7ffe-11eb-8012-1ea68441b3c7.png)
![image](https://user-images.githubusercontent.com/79297534/110265536-1c1d4380-7fff-11eb-92e4-28d360bfd039.png)
![image](https://user-images.githubusercontent.com/79297534/110265622-5555b380-7fff-11eb-88fa-7befc4d06362.png)

### master브랜치 template.yml 파일 변경
- CodeStar는 CloudFormation 서비스로 인프라 리소스를 관리함
- Resources: LambdaExecutionRole: Properties: RoleName의 'CodeStar-${ProjectId}-Execution${Stage}'값에 -staging을 추가해 수정하여 람다 실행 권한을 별도 생성해줌

![image](https://user-images.githubusercontent.com/79297534/110273776-a9b55f00-8010-11eb-8fe8-c9fbdde24418.png)
![image](https://user-images.githubusercontent.com/79297534/110273827-c81b5a80-8010-11eb-89f1-1c7a577a8143.png)

### CloudFormation이란?
- CloudFormation은 AWS 구축한 구성을 템플릿화하여 재사용하기 쉽게 해주는 서비스 (ex: 구축한 VPC 템플릿화 할시 재사용에 용이)
- JSON 형식으로 작성된 템플릿 파일을 바탕으로 VPC, EC2 인스턴스 등을 생성 및 구축함. 이를 Stack이라함 
- AWSTemplateFormatVersion : 템플릿의 버전
- Description : 템플릿의 설명
- Parameters : 스택생성시 넘겨줄 파라미터, 템플릿 내부에서 Ref함수로 참조, outputs와 조합하여 템플릿과 템플릿을 연결가능
- Mappings : 해시 테이블 처럼 (키, 값)으로 구성가능하며, 리전마다 사용할 AMI를 다르게 하는 경우에 사용됨
- Resources : 생성할 자원들을 정의함
- Outputs : 템플릿으로 생성한 것의 결과를 출력함 (ex: VPC, SecurityGroup, E2C인스턴스, ELB IP 등을 출력할 때 사용)

### staging 브랜치용 CloudFormation 스택 추가
- 기존 CloudFormation의 스택을 Designer로 열어 템플릿 탭의 코드 복사
- 복사해온 코드에 Resources: LambdaExecutionRole: Properties: RoleName에 -stageing 문자 추가하여 S3 버킷에 저장 (S3 버킷 URL이 생성됨)
- 생성된 URL을 넣어 새로운 CloudFormation 스택생성 
- 파라미터 값은 스택명을 제외하고 기존의 스택 정보를 기입

![image](https://user-images.githubusercontent.com/79297534/110279777-06b71200-801d-11eb-8021-5d6ed438bda5.png)
![image](https://user-images.githubusercontent.com/79297534/110279830-1afb0f00-801d-11eb-9cc6-6ee4e01cffc6.png)
![image](https://user-images.githubusercontent.com/79297534/110280235-d6bc3e80-801d-11eb-9e8c-ebf553c5a26e.png)
![image](https://user-images.githubusercontent.com/79297534/110280123-a1175580-801d-11eb-9dcd-32c1a9ce4198.png)
![image](https://user-images.githubusercontent.com/79297534/110280522-4b8f7880-801e-11eb-861e-765b0e06cb76.png)
![image](https://user-images.githubusercontent.com/79297534/110281384-f8b6c080-801f-11eb-9efc-08b1fa743f90.png)
![image](https://user-images.githubusercontent.com/79297534/110281719-94e0c780-8020-11eb-91d5-95010ac7d697.png)
![image](https://user-images.githubusercontent.com/79297534/110281943-f739c800-8020-11eb-8059-ecb4bf26ea24.png)

### 참고사이트
- https://www.megazone.com/techblog_20200416_testing-and-creating-ci-cd-pipelines-for-aws-step-functions-using-aws-codepipeline-and-aws-codebuild/
- http://labs.brandi.co.kr/2019/04/08/yangjh.html
- https://galid1.tistory.com/399
