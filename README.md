# 🔨 DD Market (땅땅마켓)
> **본 저장소는 팀 프로젝트 종료 후, 개인 리팩토링 및 트러블 슈팅 정리를 위해 Fork한 저장소입니다.**
> * **팀 메인 저장소:** [uizzuu/ddauction-project](https://github.com/uizzuu/ddauction-project)
> * **프로젝트 기간:** 2025.10.14 ~ 2025.12.16

실시간 양방향 통신 기술로 경매의 현장감을 구현하고, 국세청 API 기반의 사업자 검증 시스템을 통해 투명한 거래 환경을 제공하는 **경매·중고거래·스토어 올인원 커머스 서비스**입니다.

---

## 본인 기여 및 주요 업무
* **핵심 비즈니스 로직 구현:** 상품 및 게시판 등 대용량 데이터 처리를 위한 핵심 CRUD 구현
* **실시간 소통 환경 구축:** WebSocket 기반의 실시간 양방향 채팅 기능 개발
* **AI 서비스 연동:** LangChain 및 OpenAI를 활용한 RAG 기반 스마트 서비스 아키텍처 설계 참여

---

## 기술 스택 (Tech Stack)

### Management & Infra
<img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white"> <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"> <img src="https://img.shields.io/badge/aws-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white">

### Languages & Frontend
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"> <img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">

### Backend & AI
<img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> <img src="https://img.shields.io/badge/websocket-010101?style=for-the-badge&logo=socket.io&logoColor=white"> <img src="https://img.shields.io/badge/langchain-1C3C3C?style=for-the-badge&logo=chainlink&logoColor=white">

---

## 트러블 슈팅 (Troubleshooting)

### 1. 초기 경매 중심 설계로 인한 비즈니스 확장성 한계 극복
* **Issue:** 서비스 초기 아키텍처가 경매(Auction) 데이터 중심으로만 설계되어 있어, 이후 추가된 '스토어' 및 '중고거래' 등 다양한 비즈니스 모델로 확장할 때 구조적 한계가 발생했습니다.
* **Solve:** 거래 유형 유연화를 위한 DB 스키마 재설계를 주도하여 하나의 통합 테이블 및 범용 엔티티 구조를 확보했고, 다양한 거래 유형을 안정적으로 통합 관리할 수 있는 확장성을 마련했습니다.

### 2. WebSocket 도입을 통한 실시간 채팅 사용성 개선
* **Issue:** 초기 채팅 구현 시 메시지 송수신 후 화면을 새로고침해야만 상대방의 메시지가 갱신되어 실시간성이 크게 떨어지고 사용자 경험이 저하되는 불편함이 있었습니다.
* **Solve:** 상시 연결을 유지하는 WebSocket 기술을 전격 도입하여 별도의 물리적 새로고침 없이도 즉각적인 실시간 양방향 대화가 가능하도록 인터랙션을 구현했습니다.

### 3. '1일 2회 스크럼' 문화 도입을 통한 비동기 협업 효율성 제고
* **Issue:** 팀원들의 개별 작업 시간대 및 개발 진척도 차이로 인해 실시간 싱크 맞추기와 프로젝트 최종 마일스톤 관리에 리스크가 예상되었습니다.
* **Solve:** 가벼운 이슈 공유 및 '1일 2회 스크럼' 루틴을 팀 내에 제정하여 서면으로 진척도를 강제 동기화했고, 리소스 낭비를 줄여 전체적인 프로젝트 협업 효율성을 극대화했습니다.

---

## 개인 추가 리팩토링 진행 사항 (In Progress)
> 팀 프로젝트 종료 이후, 코드 품질 향상과 성능 최적화를 위해 개인적으로 진행 중인 항목입니다.
- [ ] 엔티티 연관관계 최적화 및 N+1 문제 방지를 위한 페치 조인(Fetch Join) 적용
- [ ] 예외 처리 최적화 및 글로벌 예외 핸들러(GlobalExceptionHandler) 리팩토링
