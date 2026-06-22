# DD Market (땅땅마켓)
> **본 저장소는 팀 프로젝트 종료 후, 개인 리팩토링 및 트러블 슈팅 정리를 위해 Fork한 저장소입니다.**
> * **팀 메인 저장소:** [uizzuu/ddauction-project](https://github.com/uizzuu/ddauction-project)
> * **프로젝트 기간:** 2025.10.14 ~ 2025.12.16

실시간 경매의 맛을 살리고, 국세청 API 기반의 사업자 검증까지 안전하게 처리하는 **경매·중고거래·스토어 올인원 커머스 서비스**입니다.

---

## 본인 기여 및 주요 업무
* **핵심 기능 개발:** 상품 및 게시판 등록/조회 등 기본적이고 필수적인 CRUD 전반 구현
* **실시간 채팅:** WebSocket을 활용해 유저 간 끊김 없는 실시간 채팅 기능 구축
* **AI 연동 지원:** LangChain과 OpenAI를 활용한 RAG 기반 스마트 서비스 설계 참여

---

## 기술 스택 (Tech Stack)

### Management & Infra
<img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white"> <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"> <img src="https://img.shields.io/badge/aws-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white">

### Languages & Frontend
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"> <img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">

### Backend & AI
<img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> <img src="https://img.shields.io/badge/websocket-010101?style=for-the-badge&logo=socket.io&logoColor=white"> <img src="https://img.shields.io/badge/langchain-1C3C3C?style=for-the-badge&logo=chainlink&logoColor=white">

---

## 문제 해결 기록 (Troubleshooting)

### 1. 초기 경매 중심 설계로 인한 서비스 확장 한계 해결
* **Issue:** 서비스 초기 단계에서 경매(Auction) 구조로만 DB를 짜다 보니, 나중에 '스토어'나 '중고거래' 같은 다른 형태의 거래 기능을 추가할 때 구조적으로 꼬이는 한계가 있었습니다.
* **Solve:** 거래 유형에 상관없이 범용적으로 데이터를 관리할 수 있도록 DB 스키마를 전면 재설계하여, 향후 새로운 비즈니스 모델이 추가되어도 쉽게 확장할 수 있는 안정적인 구조를 만들었습니다.

### 2. 서비스 확장(중고거래/스토어)에 따른 실시간 양방향 채팅 시스템 구축
* **Issue:** 1번의 스키마 개편을 거쳐 중고거래 기능이 새롭게 도입되면서 판매자와 구매자 간의 원활한 소통 창구가 요구되었습니다. 기존의 일방향적인 '댓글' 방식은 흥정이나 실시간 문의를 처리하기에 시차가 발생하여 유저 경험을 저해하는 한계가 있었습니다.
* **Solve:** 기능 확장 목적에 맞춰 상시 연결이 유지되는 웹소켓(WebSocket) 기술을 전격 도입했습니다. 주기적으로 데이터를 요청하는 HTTP 폴링 방식 대비 서버 리소스 트래픽 부담을 줄이면서, 별도의 새로고침 없이 메시지가 즉각 주고받아지도록 구현했습니다.

### 3. '1일 2회 스크럼' 루틴 도입으로 협업 공백 최소화
* **Issue:** 팀원마다 개인 작업 시간대나 개발 속도가 제각각이다 보니, 서로 진행 상황을 제때 파악하지 못해 전체 일정을 맞추기가 어려워질 우려가 있었습니다.
* **Solve:** 개발 흐름이 끊기지 않도록 매일 두 번씩 서면으로 가볍게 진척도를 공유하는 '1일 2회 스크럼' 루틴을 제안하고 팀 내에 정착시켰습니다. 결과적으로 불필요한 소통 리소스를 줄이고 팀의 개발 싱크를 맞추며 효율적으로 프로젝트를 마무리했습니다.

---

## 개인 추가 리팩토링 진행 사항 (In Progress)
> 팀 프로젝트 종료 이후, 코드 품질 향상과 성능 최적화를 위해 개인적으로 진행 중인 항목입니다.
- [ ] 엔티티 연관관계 최적화 및 N+1 문제 방지를 위한 페치 조인(Fetch Join) 적용
- [ ] 예외 처리 최적화 및 글로벌 예외 핸들러(GlobalExceptionHandler) 리팩토링
