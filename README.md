# 레포지토리 명

### autoscoring

<br>

## 목차
1. [프로젝트 개요](#프로젝트-개요)
2. [프로젝트 기술 스택](#프로젝트-기술-스택)
3. [개발 기간](#개발-기간)
4. [개발 인원](#개발-인원)
5. [스크린샷](#스크린샷)


<br>

### 본 프로젝트는 기업내부 수행 과제로 코드를 공개하지 않습니다.

## 프로젝트 개요
- 수강생 과제 점수 채점 및 업데이트 자동화 프로젝트
  - 수강생 과제 제출 정보 추출(AWS DynamoDB)
  - 수강생 데이터 추출(MySQL)
  - 채점 로직 적용
  - Google Sheets 업데이트


<br>

### 프로젝트 시작 배경
- 수강생 과제 제출시간(21시)에 맞추어 점수를 업데이트 해야함
- 기존 회사 내부 툴은 기본적인 대기시간이 120초가 소요되며 에러가 자주 발생하여 업무 소요시간이 10분이 초과함
- 격월로 진행되는 세션에 평균 영업일인 22일을 적용할 때, 220분/월 * 6개월로 1년에 1320분을 아낄 수 있음을 고려 
- 비효율적인 시스템을 개선하고자 프로젝트 기획 및 구현 진행

<br>

### 문제 상황 해결과정
- 파이썬 프로그래밍을 통해 ETL 파이프라인 구현
  - 추출(Extract)
    - 수강생 과제 제출 데이터 : Pytest를 통해 제출되어 AWS DynamoDB에 저장되는 데이터를 추출
    - 수강생 개인 정보 데이터 : 사내 MySQL에 저장되어 있는 수강생 데이터를 추출
  - 변환(Transform) : 채점 로직을 적용하여 Pandas DataFrame의 형태로 변수에 할당
  - 적재(Load) : 변환이 완료된 데이터를 Google Sheets에 업데이트
    - Worksheets 생성 : 기존에 존재하는 Worksheets를 복제
    - Workshees 데이터 추출 : Pandas DataFrame으로 추출
    - VLOOKUP 함수 적용 : 변환이 완료된 데이터(수강생 정보 + 과제 점수)를 Worksheets에서 추출한 데이터에 Merge하여 해당 데이터를 합침
    - Google Sheets 업데이트 : 데이터 적재 진행
  - 스케쥴링 구현을 위한 과제 점수 업데이트 순서 적용

<br>

### 프로젝트 진행과정
- 수강생 데이터 및 제출 과제 데이터 추출 - 2일
- 채점 로직 적용 - 3일
- Google Sheets 연결 및 변환 데이터 업데이트 - 4일
- 영업일 기준 날짜 데이터 및 기수별 수강 날짜 추출 - 2일
- 과제 추출 시간 적용 및 업데이트 시점 설정 - 2일
- 캡슐화 및 문서정리 - 2일

<br>

### 한계점 및 해결 방안
- 한계점
  - 사내 DB 이용 및 AWS 권한 설정 변경을 위한 요청과 답변의 시간이 소비됨
  - 기능 구현에 대한 설계(함수 및 클래스 설계) 미흡
  - 퇴사로 인한 추가 기능 개발 불가
- 해결 방안
  - 명확한 기능 설계를 위한 워크플로우 설계를 선행함에 따라 기능 분배
  - 문제 해결의 효과와 기능 개발에 들어가는 시간 및 확장성을 고려하여 프로젝트를 진행

<br>

## 프로젝트 기술 스택

### PipeLine
<section>
<img src="https://img.shields.io/badge/Python-3776AB?logo=Python&logoColor=white"/>
<img src="https://img.shields.io/badge/MySQL-4479A1?logo=MySQL&logoColor=white"/>
<img src="https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?logo=Amazon%20DynamoDB&logoColor=white"/>
<img src="https://img.shields.io/badge/Pandas-150458?logo=Pandas&logoColor=white"/>
<img src="https://img.shields.io/badge/Google%20Sheets-34A853?logo=Google%20Sheets&logoColor=white"/>
</section>


### Tools
<section>
<img src="https://img.shields.io/badge/GitHub-181717?logo=GitHub&logoColor=white"/>
</section>


<br>


## 개발 기간
- 2022/07/05 ~ 2022/07/19 (15일)

