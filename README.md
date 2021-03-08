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


### 참고사이트
- https://www.megazone.com/techblog_20200416_testing-and-creating-ci-cd-pipelines-for-aws-step-functions-using-aws-codepipeline-and-aws-codebuild/
- http://labs.brandi.co.kr/2019/04/08/yangjh.html
