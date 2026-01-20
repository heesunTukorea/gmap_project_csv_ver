# LLM + 협업필터링 기반 Google Maps 장소 추천 시스템

Google Maps **리뷰/메타데이터**를 활용해  
**Item 기반 추천 + User 기반 추천 + RAG 챗봇**을 결합한 **장소 추천 프로토타입(Streamlit)** 입니다.
<img width="625" height="350" alt="image" src="https://github.com/user-attachments/assets/df556f45-cb0b-4cdb-80c0-88ea0bdf3b55" />

---

## 활용 데이터
- **데이터 종류**
  - **Review data**: 666,324,103 rows (원본)
  - **Meta data**: 4,963,111 rows (원본)
- **범위**
  - 지역: 미국 50개 주 + 워싱턴 D.C. 등 **총 52개 지역**
  - 기간: **~ 2021년 9월**
- **분석 대상 지역**
  - 추천에 필요한 리뷰 수 확보를 위해 **California로 확정**
- **전처리 후(최종 사용)**
  - Review: **67,834,806**
  - Meta: **479,847**

---

## 핵심 기능
- **Item 기반 추천**
  - Co-review(공동 리뷰) 기반 후보 생성
  - Embedding을 통한 리뷰 텍스트 유사도 기반 추천
  - GBDT모델을 활용한 Co-review를 종속변수로한 분류 기반 추천
  - GBDT/Hybrid(리뷰 텍스트 유사도 feature 결합)모델을 활용한 추천
- **User 기반 추천**
  - ALS / FM 기반 개인화 추천
- **RAG 챗봇**
  - 질문을 **메타 정보 vs 리뷰 정보**로 분기(라우팅)
  - FAISS(Vector DB) 검색 결과 기반 답변 생성

---

## RAG 구성(요약)
Unstructured Data → Embedding → **FAISS 검색** → Relevant Chunks → Prompt → **LLM 응답**

---

## 사용 기술(요약)
- 추천: 협업필터링(ALS/FM), 트리 기반 랭킹(GBDT), 리뷰 임베딩(SBERT) + PCA
- RAG: LangChain, FAISS(IVF-PQ), MultiQueryRetriever(+MMR)
- 서비스: Streamlit

---

## 기대 효과
- 리뷰/메타데이터 기반 **정밀 추천**
- 대화형 챗봇으로 **검색/추천 UX 개선**
