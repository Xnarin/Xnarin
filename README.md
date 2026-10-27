<h1 align="center">Xnarin</h1>
<p align="center"><strong>Aspiring AI Agent Engineer</strong><br>Tool Calling · RAG · MCP</p>

<p align="center">
  <a href="https://github.com/Xnarin/finpilot">FinPilot</a> ·
  <a href="https://github.com/Xnarin/financial-rag-agent">Financial RAG Agent</a>
</p>

<br>

금융 데이터와 문서를 근거로 답하는 AI 에이전트를 만들고 있습니다.
LLM이 도구를 선택하는 과정, 잘못된 실행을 막는 검증, 검색과 답변의 품질을 평가하는 일에 관심이 있습니다.

## Featured Projects

### 01 · [FinPilot](https://github.com/Xnarin/finpilot)

**OpenDART 공시를 조회하고, 코드로 계산한 재무 수치를 출처와 함께 보여주는 에이전트**

개인 프로젝트 · `Python` `LangGraph` `Gemini` `MCP` `Streamlit` `pytest`

- **도구 실행 검증** — 회사·연도에 대한 사용자 발화 근거를 대조하고, 확정되지 않은 조건의 조회를 차단합니다.
- **계산과 답변 분리** — 매출·영업이익은 공식 API로 조회하고, 비율·표·비교 문장은 코드로 생성합니다.
- **실패 처리와 도구 재사용** — 호출 한도·캐시·되묻기를 구현하고, 같은 금융 도구 4개를 MCP 서버로 제공합니다.

[Repository](https://github.com/Xnarin/finpilot) · [Agent Code](https://github.com/Xnarin/finpilot/blob/main/agent_core.py) · [Evaluation](https://github.com/Xnarin/finpilot/blob/main/docs/evaluation/eval_results.md)

<details>
<summary>실제 실행 화면 보기</summary>

<br>

![FinPilot — 여러 회사의 연도별 재무 지표를 비교하는 화면](https://raw.githubusercontent.com/Xnarin/finpilot/main/docs/assets/chat_trend.png)

</details>

### 02 · [Financial RAG Agent](https://github.com/Xnarin/financial-rag-agent)

**금융 PDF 23개에서 근거를 찾고, 부족하면 재검색한 뒤 파일명·페이지를 붙여 답하는 에이전트**

3인 팀 실습 프로젝트 · `Python` `LangChain` `LangGraph` `Gemini` `Chroma` `BM25`

- **문서 구조를 반영한 청킹** — 표의 제목·헤더, 용어 정의, 약관 조항을 보존하고 이웃 청크를 함께 전달합니다.
- **근거 판단과 재검색** — 벡터·키워드 Hybrid 검색에 질문 분류와 근거 판단을 더하고, 재검색은 최대 2회로 제한합니다.
- **같은 조건에서 비교** — 120문항 평가에서 기본 RAG **0.854 → Agent 0.904**. 품질과 함께 호출 수·비용·지연을 기록했습니다.

<sub>프로젝트 자체 비교 실험 결과입니다. 점수는 채점 LLM이 기준 답안과 비교해 부여한 0·0.5·1점의 평균입니다.</sub>

[Repository](https://github.com/Xnarin/financial-rag-agent) · [Agent Code](https://github.com/Xnarin/financial-rag-agent/blob/main/agent/graph.py) · [Experiments](https://github.com/Xnarin/financial-rag-agent/blob/main/docs/실험기록.md)

## How I Build

| 관심 | 프로젝트에서 다루는 방식 |
| :--- | :--- |
| 근거 있는 답변 | API 출처와 문서 페이지를 남기고, 조회·계산·생성을 구분합니다. |
| 실패를 다루는 흐름 | 정보가 부족하면 되묻고, 근거가 부족하면 재검색하며, 반복 실행에 한도를 둡니다. |
| 측정하고 선택하기 | 기준선과 같은 조건으로 비교하고, 품질·비용·지연을 함께 기록합니다. |

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-222222?style=flat-square&logo=modelcontextprotocol&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

Retrieval: Chroma · BM25 · Kiwi &nbsp; / &nbsp; Validation: pytest · Golden-set Evaluation

