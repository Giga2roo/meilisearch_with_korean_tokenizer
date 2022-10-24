# 이어드림스쿨 2기 기업연계 Project

## 회의 및 아카이빙 

https://www.notion.so/10-0be92ed65b874f2fa27c6fc0638d492d

## 주관: 중소기업벤처부 이어드림 스쿨 2기

<br>

## Abstract

| 프로젝트 명 | 연계 기업 | 목적 |
|------------------| ------ | ----- |
| 검색엔진 고도화를 위한 자연어 처리 | 메디스트림 | 형태소 분석 및 사용자 사전 적용을 통한 검색 기능 향상 (도메인 딕셔너리, mecab)|

| 활용 데이터 |     데이터 입수 난이도    |      사용방법     |
|------------------| :------: | ----- |
| 한의학 전공 서적| 하 | OCR, 전처리, mecab 사전 생성기 |
| 온라인 한의학 사전| 하 | 다운로드, 전처리, mecab 사전 생성기 |
| 온라인몰 컨텐츠(검색 대상) | 하 | GCP gsutil, 검색엔진에 인덱싱, 성능시험 Test-set 구축 |

|  Task  |  Task 난이도  |  난이도 적용 사유  |  비고 |
|------------------| :------: | ----- | ----- |
| 도메인 단어사전 구축 | 하 | OCR 작업 후, 정규표현식을 적용한 전처리, Mecab 사전등록 | add-userdic.sh |
| Meilisearch 이해 | 중 | "Hello, 검색엔진 world!" | IR(Information Retrieval)이 뭐죠? |
| Rust를 이용한 형태소 분석기 빌드 | 상 | Rust 언어에 대한 낮은 이해도(feat. 첫만남) | Meilisearch는 **Rust**로 구현되어 있습니다. |
| 검색엔진 구현 | 중 | GCP 및 AWS 인스턴스 세팅, Meilisearch에 데이터 업로드 | |
| 평가 | 중 | 다양한 검색엔진 평가방식을 학습하고 본 프로젝트에 적절한 방식과 테스트셋을 구축 | 

<br>

### Search engine development project (feat. Meilisearch)

---

|  프로젝트 순서 |     Point    | 세부 내용 |  
|------------------| -----|------|
| 문제 정의 | 띄워쓰기 기반 tokenization의 한계 확인 | 서비스 현황 확인, 문제 사례 검토 |
| 데이터 수집 | 기업자료, 한의학 단어 데이터 | GCP gsutil 이용 데이터 수령, 한의학 교재 OCR, 한의학 단어사전(인터넷) |
| 형태소 분석기 연구 | Mecab 등 한글 형태소 분석기 검토 | 엔진과 연계된 Mecab 외 다른 형태소 분서기 |
| 데이터 전처리 | 문제에 따른 전처리 방향 설정 | 검색 엔진 인덱싱, 성능평가 테스트셋 구성 |
| 검색엔진 이해 | Meilisearch 각 라이브러리의 의존성 도식화 | 어떤 라이브러리에서 어떤 작업을 해야하는지 확인 |
| 연관 데이터 추가|추가 수집 | 훈련, test |
| 평가 metric 선택 | 서비스 특성을 고려한 성능평가 방식 선정 | Precision@k, F1 score |   
| 결론 및 제안 도출 | 형태소 분석 적용에 따른 검색 성능 평가, 유지관리 가이드 라인 제안 | |

<br>

### Basic information

**공식기간: 2022.09.05 ~ 2022.10.24**


- 팀원
  - 김성수: 전공서적 OCR, 사전 구축, 검색엔진 작동 테스트, 성능 평가
  - 서동국: 형태소 기반 토크나이저 빌드(by Rust), 검색엔진 빌드, 인스턴스 관리
  - 안세호: 전공서적 OCR, 기업데이터 EDA, 테스트셋 구성, 커뮤니케이션
- 협업장소: Slack huddle, Github
- 소통: Slack, Notion
- 저장소: Github
- 개발환경: Visual studio code, Juypter Notebook, colab
- 언어: Python 3.8.x, Rustup 1.25.1 
- 라이브러리: Pandas, Meilisearch
- 시각화 라이브러리: Seaborn, Matplotlib, Plot, Plotly
