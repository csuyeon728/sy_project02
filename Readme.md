## 📌 프로젝트 개요

- 과학기술정보통신부와 한국지능정보화사회진흥원(NIA)에서 주관하는 「SW 여성인재 역량강화 기반조성 사업 데이터 분석가 과정」 데잇걸즈 6기 수강생으로 구성된 팀 ‘내일의 집’ 의 데이터 분석 프로젝트입니다.
<br></br>
### 추진 배경

- 집들이 선물을 하려고 오늘의 집에 들어갔는데 구매할 상품을 결정하는 데 어려움이 있었다. 지난 1년 간 네이버 포털 사이트 키워드 검색 결과에서는 집들이 선물이 ‘선물’을 키워드로 하는 다른 검색어보다 검색량이 2배 이상 많다는 것을 발견했다.
    
     집들이 선물에 대한 고민을 해결해보고자 라이프스타일 애플리케이션(앱)인 오늘의 집 내 커뮤니티 ‘집들이’ 컨텐츠를 분석하여 사용자가 원하는 집들이 선물을 추천해줄 수 있는 분석 프로젝트를 진행하기로 했다.
<br></br>
### 프로젝트 목적

- 「오늘의 집 집들이 컨텐츠 기반 집들이 선물 추천」
<br></br>
### 워킹 프로그램 & 사용 프레임 워크

- Language : `Python`
- Tool : `Pandas` `matplotlib` `Tableau` `Excel` `Power Point` <br></br>

## 📌 프로젝트 주제

### 오늘의 집 커뮤니티 ‘집들이’ 컨텐츠 기반 집들이 선물 추천  
<br></br>
### 문제정의 및 가설 설정

- **문제 정의 :**
    - 상품을 정하지 않고 물건을 고를 때 (ex : 원하는 분위기의 상품을 찾을 때, 신혼부부에게 좋은 선물을 찾을 때)는 기존 필터에서 도움을 받기 어렵다.
    - 현재 추천 탭 분류 기준에서는 선물을 위한 제품 선택이 다소 어렵고, 추천 상품이 너무 많다.

- **가설 설정 :**
    - 집들이 컨텐츠를 활용한다면 상품 구매 시 구매 목적과 고려하는 부분을 만족시키는 상품 분류가 가능할 것이다.
        - 새로운 필터 생성
        
            (예시) 우리가 새로 만든 카테고리(분위기)로 필터링된 상품 리스트
            
    - 추천 탭을 재구성한다면 추천 시스템에 대한 소비자의 만족도가 올라갈 것이다.
        - 추천 탭 재구성
        
            (예시) 함께 꾸미기 좋은 상품 (분위기 기반)
<br></br>
## 📌 데이터 소개

### **데이터 수집 → 전처리**

- **수집 기간 :** 2022.10
- **수집 데이터 종류 :**
    - 이용자 정보 데이터 : 커뮤니티 ‘집들이’ 컨텐츠 기준 약 4천 6백 개
    - 상품 데이터 : 약 22만 개
    - 리뷰 데이터 : 위 상품에 대한 리뷰 데이터
    - 설문조사 데이터 : 집들이 선물에 대한 인식 조사

- **데이터 주요 전처리 :**
    - 데이터 타입 및 형태 통일 / 파생컬럼 생성
    - 스크래핑 시점 차이로 인한 데이터 업데이트 내용 일괄 변경
    - 미입점 데이터(Null값) 삭제
<br></br>
## 📌 데이터 분석

### **데이터 분석 방법**

**[Step1] 상품별 분위기 정의**

- 집들이 컨텐츠 내 태깅 여부를 기준으로 태깅 된 상품은 태깅된 집들이의 ‘스타일’  필터에 따른 분위기 설정
    - 집들이 컨텐츠에 태깅(tagging)된 상품
        
        **→** (태깅 횟수 **/** 스타일별 게시글 수) 가 높은 분위기를 상품 분위기로 선정
        
        **예.** 집 분위기를 스타일 필터에서 ‘유니크&믹스매치’로 정의 
        → 이 집에 태깅된 상품 분위기는 ‘유니크&믹스매치’로 정의해서 라벨링
        
        * 같은 상품들이 여러가지 다른 분위기의 게시글에 태깅되었다면, 중복으로 가장 많이 태깅된 게시글의 분위기를 최종 상품 분위기로 설정.
        
    
    - 집들이 컨텐츠에 태깅되지 않은 상품
        
        **단계1.** 집들이 컨텐츠 제목에 나타나는 키워드로  분위기별 특징 키워드를 선정  
        **단계2.** 위 특징 키워드를 상품별 리뷰 텍스트 분석을 통해 추출한 키워드와 비교해서 많이 들어가 있는 키워드 분위기를 상품 분위기로 설정.
        

**[Step2] 지표 설정**

- 추천 상품 정렬을 위한 지표 > ‘긍정 비율’ 생성

**[Step3] 추천 상품 정렬**

- 리뷰 감성 분석(Clova centimenti) 기반으로 긍정비율순 정렬

**[Step4] 상품 조합 추천**

- 연관분석(Apriori 알고리즘) Lift(향상도) 높은 순으로 추천
<br></br>
## 📌 **결과**

- 오늘의 집 유저가 원하는 ‘분위기’에 어울리는 상품 추천 가능
- 특정 상품의 분위기와 어울리는 상품 조합 추천 가능
<br></br>
## 📌 팀 소개

- 김민지 | Data Analyst : dallaemin.kim@gmail.com
- 김예원 | Data Analyst : kimyewon09826@gmail.com
- 박유정 | Data Analyst : skyggg3@gmail.com
- 송나현 | Data Analyst : skgusgo@gmail.com
- 이소현 | Data Analyst : skshyun123@gmail.com
- 이지혜 | Data Analyst : snidel@naver.com
- 최수연 | Data Analyst : tndus8945@gmail.com
