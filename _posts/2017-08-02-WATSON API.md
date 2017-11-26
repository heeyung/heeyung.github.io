---
layout: post
title: WATSON API
---

#  WATSON API

### 1.  IBM WATSON API란?

기업의 **Cognitive Business**를 지원하기 위해 **클라우드** 형태로 제공되는 인지 소프트웨어 플랫폼.
기업에서 쓰는 프로그램에서 인지/인공지능 기능을 불러와서 사용할 수 있도록 다양한 프로그램 인터페이스를 제공.

 	1. Cognitive Business란?
     digital business + digital intelligence를 뜻하며 전에는 활용하지 못했던 비정형 데이터(휴대폰의 사진, 콜센터 직원과의 상담 내용) 들을 이해하고 추론하고 학습을 통해 유의미한 결과를 제공함
 	2. 클라우드
     watson은 물리적인 슈퍼 컴퓨터의 형태로 존재하지 않고 클라우드 플랫폼에서 구동되는 API형태

### 2. WATSON API 종류

1. Conversation
   애플리케이션에 자연어 인터페이스를 추가하여 일반 사용자와의 상호작용을 자동화.
   쉽게 챗봇을 구현할 수 있는 기능
2. Discovery
   인지형 검색 및 콘텐츠 분석 엔진을 신속하게 구축할 수 있으며, 변환, 정규화, 농축을 통해 비정형 데이터의 가치를 추가.  ex) 자기 회사의 리뷰 글들(비정형)의 특정 키워드를 뽑아 가치를 측정하기(positive,negative)
3. Document Conversion
   HTML, PDF, MS Word를 정규화된 HTML, TXT, JSON 형태로 변환
   자신이 가지고 있는 여러 형태의 DATA들을 WATSON API의 input으로 사용할 수 있게 변환.
4. Language Translator
   번역 기능, 입력할 텍스트와 언어를 설정하고 타입(뉴스, 일반 대화, 전문 분야)를 선택해서 번역.(한국어는 뉴스와 전문분야만)
5. Natural Language Classifier
   자연어를 해석하고 분류하는 기능, 특정한 문장이나 구문을 입력하면 그거와 일치하는 최선의 클래스를 리턴, 학습 시킬 수 있음
6. Natural Language Understanding
   텍스트를 분석하여 컨텐츠의 개념, 엔티티, 키워드, 카테고리, 감성, 관계등의 메타데이터를 추출
7. Personality Insights
   텍스트를 읽어들인 후 개인의 성격에 대한 분석, 외향적 성격 유무, 성실유무, 친화력, 보수, 진보 등의 성격적 특성 분석 제공 (SNS 및 기사 댓글 분석)
8. Retrieve and Rank
   검색과 기계 학습 알고리즘을 조합해서 데이터에서 signals를 발견해 조회에 맞는 가장 적합한 정보를 찾음. 학습 시킬 수 있음
9. Speech To Text
   목소리를 문자로 변환
10. Text To Speech
    문자를 음성으로 변환, 음성의 스타일 변환 가능
11. Tone Analyzer
    텍스트의 어조를 좀 더 심층적으로 분석. 하나의 텍스트를 읽고 감정, 어투, 사회성 등을 분석할 수 있음
12. Visual Recognition
    시각적 인지 기능을 통해 사진이 무엇이지를 분류할 수 있는 기능
