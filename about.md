---
layout: about
title: About
banner: "/assets/images/banners/home.jpg"
---

## 🌈 About me

<div style="display: flex; gap: 20px;">

<div style="flex: 1;">
  <img src="https://drive.google.com/thumbnail?id=1yK_oOQA0N_1WyBGol2V1smrhh0LdLnU3&sz=w1000" alt="Profile" style="max-width: 100%;">
</div>

<div style="flex: 1;">
  <p style="font-size: 32px; font-weight: bold; margin-top: 0; margin-bottom: 0px;">김승유</p>
  <p style="font-size: 24px; font-weight: bold; margin-top: 0; margin-bottom: 0px;">Seungyu Kim</p>
  <hr style="margin-top: 6px; margin-bottom: 4px;">
  <p style="font-size: 20px; font-weight: bold; margin-bottom: 4px;">Contacts</p>
  <ul style="font-size: 16px;">
    <li>📞 +82 10-4759-8718</li>
    <li>📧 seungyu.k@outlook.com</li>
    <li>🌐 <a href="https://ksyu0508.github.io" target="_blank">ksyu0508.github.io</a></li>
    <li>🔗 <a href="https://www.linkedin.com/in/seungyu-kim-b77774279/" target="_blank">LinkedIn Profile</a></li>
  </ul>
</div>

</div>

---

끊임없이 배우고, 문제를 정의하고, 더 나은 서비스를 만들어가는 것을 즐기는 문제 해결형 개발자 김승유입니다. 통계, 머신러닝, 소프트웨어 공학에 대한 폭넓은 이해를 바탕으로 교육, 의료 등 다양한 도메인에서 문제를 풀어왔습니다. 실제 서비스와 연계된 프로젝트 경험과 인프라 기반 기술 스택을 함께 갖추고 소프트웨어 엔지니어로서 성장하고 있습니다.

---

## 👔 Work Experiences

* **SAP Labs Korea** (2024.07 ~ 현재)
    - HANA QA Infrastructure 팀 (2025.01 ~ 현재)
        - RAG 및 AI Agent를 활용한 사내 CI/CD pipeline 챗봇 위젯 서비스 개발
        - RAG를 활용한 서비스 개념 및 사용법에 대한 질문 처리
        - AI Agent를 활용한 서비스 내부 장애 진단 
    - Research & Innovation (2024.07 ~ 2024.12)
        - Cardinality Estimation ML 모델 학습 및 HANA 벤치마킹
        - FastAPI + Kubernetes 기반 API 서버 배포 및 Jenkins 자동화 파이프라인 구축

---

* **삼성전자** (2024.03 ~ 2024.06)
    - DS 부문 혁신 센터 AI 플랫폼 파트
    - 개별 인스턴스 사용자를 위한 Grafana 리소스 대시보드 관리 API 개발
    - 인스턴스 사용률 기반 유휴 리소스 절감 검출에 활용
    - `fastapi`, `grafana`, `keycloak`, `promethus`, `skaffold`, `github actions`, `kubernetes`

---

* **[newcureM](https://www.newcurem.com/)** (2022.08 ~ 2023.02)
    - GAN 기반 CT-to-MRI 이미지 변환 모델 개발
    - RSNA 2023에 CT-MRI 변환 연구 초록 채택
    - GAN 기반 PET 이미지 노이즈 제거 모델 개발
    - 의료기기 임상시험 통과 (2등급 의료기기 소프트웨어)

---

* **[zezedu](https://zezedu.com/ko)** (2020.06 ~ 2020.08)
    - KoBERT 기반 수학문제 유형 분류기 개발
    - 분류기를 벡터 임베딩 모델로 활용하여 유사도 기반 검색 시스템 개발

---

## 🏫 Education

* 2016.03 ~ 2019.02 **대전과학고등학교 졸업**
* 2019.03 ~ 2025.02 **연세대학교 산업공학과 학사**

---

## 🎯 Featured Projects

### 1. mY-calY

**mY-calY**는 2024년에 GDGoC Yonsei에서 진행한 oTP 프로젝트입니다. **mY-calY**는 연세대학교 통합 정보 캘린더 앱으로서, mY-calY는 연세대학교 학부생들이 학사, 장학, 취업 등 다양한 교내외 정보를 하나의 캘린더 앱으로 통합하여 관리할 수 있도록 기획된 서비스입니다. 기존 Learn-us 시스템의 한계와 정보의 분산 문제를 해결하고자 시작된 프로젝트입니다.

[👉 GitHub 링크](https://github.com/ksyu0508/mY-Caly-Crawler)

[📑 발표자료 링크](https://github.com/ksyu0508/mY-Caly-Crawler/blob/main/Demo%20Day-Learnus%20Manager.pdf)

![](https://drive.google.com/thumbnail?id=1zDGosHqJm1TpgjepGhTQ9tf4yUmu6y5j&sz=w1000)

#### 🎯 프로젝트 목표
- 분산된 교내외 정보를 통합 관리할 수 있는 앱 제공
- 사용자 맞춤형 정보 접근성과 알림 경험 개선

#### 🔍 기획 배경
* Learnus의 알림 기능 한계: 강의, 과제 등의 알림이 제대로 연동되지 않아 학생들이 정보를 놓치는 경우가 많음
* 정보의 분산: 장학금, 학사 일정, 진로/취업 관련 정보가 커리어 연세, 학과 홈페이지, 공지사항 등 여러 채널에 흩어져 있어 관리가 어려움
* 관심사 기반 필터링 부족: 자신에게 필요한 정보만 골라보기 어려움

#### 💡 솔루션 개요
* 분산된 정보 수집: 커리어 연세, 학과 홈페이지 등의 정보를 자동으로 취합
* 정보 분류: 사용자의 관심 키워드 및 소속 학과에 따라 정보를 자동으로 분류
* 캘린더 기반 통합 관리: 사용자 맞춤 정보가 일정으로 등록되어 캘린더에서 확인 가능
* 러너스 연동 기능은 pivot: 이미 다른 기능으로 해결 가능하여 주요 기능에서 제외

#### 👨‍💻 나의 역할
- 프로젝트 리드 및 서비스 구조 구성
- FastAPI 기반 정보 크롤링 모듈 개발
- 관심 키워드/학과 기반 분류 로직 설계

#### 구현

구현은 총 세가지 부분으로 나누어서 진행을 하였습니다.
* Front-end: 모바일 어플리케이션
* Back-end: 유저 정보 처리
* Back-end: 학교 정보 수집

![](https://drive.google.com/thumbnail?id=1GcB9OGlXASAacM812tQP8ZbbQpowrCt8&sz=w1000)

FastAPI를 활용하여 API서버를 구성하였습니다.
학교 게시판의 정보들을 일괄적으로 BS4를 활용하여 크롤링을 진행합니다.
크롤링은 API call을 통해서 진행되고, 또 cronjob을 활용하여 일정 주기마다 진행됩니다.
추출된 데이터는 전처리나 분류 작업 없이 DB에 저장되어 있으며, 전처리되지 않았다고 표시되고
사용자에게는 노출되지 않습니다.
EasyOCR을 활용하여 사용자에게서 문자열을 추출하고, 이 문자열을 기반으로 lamma3모델을 활용하여
필요한 정보(기간, 대상, 문서유형 등)을 추출하고 DB에 저장하게 됩니다.
클라이언트가 API를 통해서 정보를 요청하면, 사용자가 추가로 제공한 태그 등을 필터로 하여
게시글 정보를 리턴합니다.

####  📽 데모영상

![](https://www.youtube.com/embed/QwDtp_JndF4)

[동영상 링크](https://www.youtube.com/watch?v=QwDtp_JndF4)

#### 📌 프로젝트 결과 및 회고

연세대학교와 고려대학교 GDGoC가 연합하여 진행한 Demo Day 행사에서 최종적으로 장려상을 수상할 수 있었습니다.

BM이 없는 서비스인 만큼 최대한 무료 리소스를 활용하여 개발을 진행하려 하였습니다.
AWS의 free-tier unit, Groq의 무료 LLM 토큰 등을 활용하여 개발을 진행하였습니다.
학교 게시판의 경우 문서 기반의 게시물도 있지만, 포스터만 올리거나 중요한 정보가 사진에 들어가 있는 경우가 있기에
OCR을 진행하여 정보를 추출하여야 했는데, OCR 리퀘스트의 경우 무료로 서비스를 배포하는데에 어려움이 있기 때문에
이를 최대한 오픈소스를 활용하여 API 서버 자체에서 활용하고자 하였습니다.
주어진 자원(무료) 제한 안에서는 최대한 해결책을 찾으려 한 것 같지만, 이로 인해서
오히려 서비스의 기획이 중간에 바뀌거나, 다양한 기능 제공이나 정확도에서 부족함이 발생하여 아쉬움이 남았습니다.

### 2. 심심한 와빅이

**심심한 와빅이**는 2020년에 YBIGTA에서 진행한 YBIGTA 16기 컨퍼런스 프로젝트입니다. **심심한 와빅이**는 BERT를 기반으로 사용자와 자유로운 대화가 가능하며 연세대학교 빅데이터 동아리인 YBIGTA 관한 정보를 알려주는 챗봇으로 기획된 서비스입니다. 동아리의 다음 기수 모집을 위한 정보 제공 및 홍보 목적으로 제작된 프로젝트이기도 합니다.

[👉 GitHub 링크](https://github.com/ksyu0508/ybigta_chatbot)

[📑 발표자료 링크](https://github.com/ksyu0508/ybigta_chatbot/blob/master/%EC%8B%AC%EC%8B%AC%ED%95%9C%20%EC%99%80%EB%B9%85%EC%9D%B4(%EC%B5%9C%EC%A2%85).pdf)

<div style="display: flex; gap: 20px;">
  <div style="flex: 1;">
    <img src="https://raw.githubusercontent.com/ksyu0508/ybigta_chatbot/master/imgs/kakaotalk_1.jpg" alt="kakaotalk_1" style="width: 100%; border-radius: 8px;">
  </div>
  <div style="flex: 1;">
    <img src="https://raw.githubusercontent.com/ksyu0508/ybigta_chatbot/master/imgs/kakaotalk_2.jpg" alt="kakaotalk_2" style="width: 100%; border-radius: 8px;">
  </div>
</div>

#### 🎯 프로젝트 목표
- YBIGTA 동아리를 위한 인공지능 기반 챗봇 서비스 제작
- 실제 사용을 목적으로 목표한 서비스

#### 🔍 기획 배경
* 교내에 많은 빅데이터/인공지능/개발 동아리가 존재하는데, 동아리의 정체성을 보여줄 수 있는 프로젝트로 차별화된 홍보를 시행하고자 하였음.

#### 💡 솔루션 개요
사용자 시나리오를 두가지로 구분하여, 크게 두가지로 나누어 기능 구성
* 시나리오형 챗봇
    - 사용자 발화를 지정하여 미리 준비된 답변 출력
    - YBIGTA 17기 모집 일정, 팀 소개 등의 답변 제공
* 대화형 챗봇
    - 딥러닝 모델을 기반으로 한 자연스러운 대화 출력
    - 사전에 준비하지 못한 시나리오에 대한 답변 가능

#### 👨‍💻 나의 역할
- 프로젝트 리드 및 서비스 구조 구성
- BERT 알고리즘 학습 및 학습을 위한 데이터 수집

#### 구현

![](https://drive.google.com/thumbnail?id=1HLGFfAAwLByTr3jlvl_-u1qbogCG-fWz&sz=w1000)


챗봇은 사용자의 접근성을 고려하여 카카오톡을 활용하여 구성하였습니다.
언어 모델은 BERT 모델을 활용하여, BERT를 인코더로, GRU를 디코더로 활용하여 구성하고,
공개된 한국어 챗봇 데이터와 자체적으로 수집한 채팅방 데이터를 활용하여 학습을 진행하였습니다.
구현된 모델을 서버로 올리기 위해서, python으로 구현된 Django를 활용하여 모델을 서빙하였습니다.
시나리오형 챗봇은 카카오톡 챗봇 서비스의 기능을 활용하여,
키워드를 기반으로 사용자의 질문을 감지하고, 사전에 준비되지 않은 질문을 언어모델을 활용하여 답변하는 형태로 구성하였습니다.

####  📽 데모영상

![](https://www.youtube.com/embed/HolUf6CVwAw?start=675)

[동영상 링크](https://www.youtube.com/watch?v=QwDtp_JndF4?start=675)

#### 📌 프로젝트 결과 및 회고

당시 NLP 모델 중 SOTA인 BERT를  활용하며 이해하는 기회였고, 챗봇 서비스에 인공지능 접목할 시 고려할 사용자 경험 요소 역시 파악할 수 있었습니다. 접근성이 좋은 카카오톡 채널을 활용한 만큼, 발표 시 청중이 직접 사용할 수 있게 모델 사이즈를 최대한 줄이고, 서버의 GPU 사이즈를 최대한 키웠음에도, 실제 발표 시연 시 많은 사용자가 동시에 작업을 요청하며 서비스 속도가 느려짐을 알 수 있었고, 인공지능 기반의 서비스를 기획 시에는 사용량 및 부하 예측 역시 중요한 요소임을 느꼈습니다.

또 문제가 되었던 부분은 챗봇 인공지능 모델 학습을 위한 데이터 확보가 매우 어려웠다는 점입니다. KoBERT는 한국어로 작성된 위키백과를 기반으로 학습되어, 챗봇에 필요한 구어체 및 일상대화에 대한 정보는 부족했습니다. 따라서 추가적인 학습을 요구로 하였지만 한국어로 작성된 챗봇 데이터셋은 약 10000개의 문답 페어로 구성된 것이 전부였습니다. 그래서 팀원들과 함께 다양한 방법으로 구어체 및 일상대화가 포함된 데이터를 구하기 위해 고민했고, 조원의 실제 카카오톡 대화 데이터를 활용하고, 영화나 드라마 자막파일 등에서 대화를 추출하는 방법을 고안했습니다. 추후 실용적인 인공지능 서비스를 개발하기 위해서는 안정적인 서비스를 위한 인프라 확보와 데이터 확보를 위한 노력 및 비용이 매우 중요할 것이라는 것을 체감할 수 있었습니다. 

---

## 🗂 More Projects

<div style="display: flex; gap: 20px; flex-wrap: wrap;">

  <div style="flex: 1 1 250px; background-color: #f7f7f7; border-radius: 12px; padding: 15px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <img src="https://raw.githubusercontent.com/ksyu0508/Computer-Vision/refs/heads/master/pix2pix/imgs/test1.png" alt="pix2pix" style="width: 100%; border-radius: 8px;">
    <h4>Pix2Pix로 피카츄 색칠하기</h4>
    <p>YBIGTA 신입 컨퍼런스 발표 프로젝트, Pix2Pix를 활용한 피카츄 채색 모델 개발</p>
    <a href="https://github.com/ksyu0508/Computer-Vision/tree/master/pix2pix">자세히 보기</a>
  </div>

  <div style="flex: 1 1 250px; background-color: #f7f7f7; border-radius: 12px; padding: 15px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <img src="https://raw.githubusercontent.com/ksyu0508/NLP/refs/heads/master/image.png" alt="KorQuAD" style="width: 100%; border-radius: 8px;">
    <h4>KorQuAD 기반 Q/A 시스템</h4>
    <p>국내 데이터셋 KorQuAD 2.0을 기반으로 한 BERT 기반 질문 응답 시스템 구현</p>
    <a href="https://github.com/ksyu0508/NLP/blob/master/korquad%20%EC%B5%9C%EC%A2%85.pdf">자세히 보기</a>
  </div>

  <div style="flex: 1 1 250px; background-color: #f7f7f7; border-radius: 12px; padding: 15px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <img src="https://raw.githubusercontent.com/ksyu0508/alpha-omok/refs/heads/master/imgs/endgame.png" alt="Alpha-Omok" style="width: 100%; border-radius: 8px;">
    <h4>Alpha-Omok</h4>
    <p>Alpha-Zero 강화학습 알고리즘을 이용한 오목 AI 제작</p>
    <a href="https://github.com/ksyu0508/alpha-omok">자세히 보기</a>
  </div>

  <div style="flex: 1 1 250px; background-color: #f7f7f7; border-radius: 12px; padding: 15px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <img src="https://drive.google.com/thumbnail?id=1EW-m9YHblHQXd-uH9Wzd48tvNprVOo9l&sz=w1000" alt="Alpha-Omok" style="width: 100%; border-radius: 8px;">
    <h4>4ocus</h4>
    <p>대학생을 대상으로 하는 학교 수업 일정 및 필기 공유 서비스 기획</p>
    <a href="https://drive.google.com/file/d/1SwSYULJarZVjHC_bu8RiMQSrmsGSBK-s/view?usp=drive_link">자세히 보기</a>
  </div>

</div>

---

## 📄 Extracurricular Activities

* **YBIGTA (연세대학교 빅데이터 학회)**  
    - 2019.07 ~ 2021.02  
    - 회장(17기) 및 Data Engineering / Data Science 팀 활동

* **UXIM (연세대학교 UX/UI 학회)**  
    - 2023.03 ~ 2023.12  
    - UXIM 10기 부회장

* **GDGoC Yonsei (Google Developers Group on Campus)**  
    - 2024.09 ~ 2025.06  
    - ML/AI 세션 참여

* **연세대학교 생활관 RA (Resident Assistant)**  
    - 윤동주 하우스 2023.02 ~ 2023.12

* **KSCY 13th facilitator**  
    - 2019.11 ~ 2020.02
    - 컴퓨터과학 세션
    - 학생 학술 활동 피드백 및 멘토링

---

## 🛠 Skills

**Language**
- C++, Java, Python

**ML/DL**
- PyTorch, scikit-learn  
- Medical Imaging: `pydicom`, `nibabel`, `torchio`

**Backend**
- FastAPI, Flask
- Docker, Kubernetes
- Jenkins, Grafana
- SQL: MySQL, PostgreSQL

---

## 🎓 Certification

- SQLD (SQL 개발자)
- ADSP (데이터 분석 준전문가)

---

## ♟ Military Service

- 대한민국 육군 병장 만기 전역 (2021.02 ~ 2022.08)
