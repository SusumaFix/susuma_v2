# 🚀 **수리 전문가 매칭 플랫폼 V2 (2025)** 

![Image](https://github.com/user-attachments/assets/7a08badf-2063-4be1-838b-f08d4bff7ce2)  

---

## 🌟 **프로젝트 개요**  
"수리 전문가 매칭 플랫폼 V2"는 V1에서의 모든 경험과 피드백을 바탕으로 **완전한 재설계와 기능 강화**를 통해 배포까지 성공적으로 완료한 프로젝트입니다.  
V2는 최신 Jakarta EE 표준과 JSP를 기반으로 AJAX Pulling 기술을 활용하여 **실시간 대화 기능**과 안정적인 예약 관리 시스템을 제공합니다.  
사용자 경험과 성능을 극대화하며, **실제 서비스로의 상용화** 가능성을 염두에 둔 완성도 높은 플랫폼입니다.  

---

## 🗓️ **개발 기간**  
- 2025년 1월 8일 ~ 10일, 16일 (총 4일간 집중 개발)  

| **한정우** |  
| :------: |  
| [<img src="https://avatars.githubusercontent.com/groovyplanet" height=90> <br/> @groovyplanet](https://github.com/groovyplanet) |  

---

## ✨ **주요 개선 사항**  

### 📊 **1. 데이터베이스 및 스키마 최적화**  
- **REQUEST 테이블**:  
  - `STATUS` 컬럼에 기본값(`DEFAULT 'requested'`) 설정, SQL 오류(ORA-00907) 수정.  
  - 테이블 및 컬럼 이름 대문자 통일로 SQL 코드 가독성과 유지보수성 개선.  
- **MESSAGE 테이블**:  
  - 메시지 컬럼 크기를 기존 50자에서 255자로 확장, 긴 메시지도 안정적으로 저장 가능.  
- **POINT_HISTORY 테이블**:  
  - 컬럼 타입을 Java 호환성에 맞게 수정, 데이터 무결성 강화.  

---

### ⚙️ **2. Jakarta EE 기반으로 완전 전환**  
- **표준 기술 적용**:  
  - Java EE에서 Jakarta EE로 전환, 최신 JSP 네임스페이스(`http://jakarta.ee/...`)로 변경.  
  - Tomcat 10.x 기반의 최신 서버 환경에 최적화.  
- **배포 안정성 강화**:  
  - 중복 라이브러리 제거 및 EC2 서버 최적화.  

---

### 🔄 **3. AJAX Pulling을 활용한 실시간 대화 구현**  
- **실시간 대화 기능**:  
  - WebSocket이 아닌 **AJAX Pulling 기술**을 활용해 서버 부하를 최소화하면서 실시간 메시지 송수신 가능.  
  - 메시지 전송 시 유효성 검사와 예외 처리 강화.  
  - 사용자 입력에 대한 즉각적인 피드백 제공.  
- **유연한 데이터 처리**:  
  - 255자 메시지 길이 제한 내에서 안정적인 데이터 전송 및 조회 가능.  

---

### 📅 **4. 예약 및 수리 로직 전면 개선**  
- **사용자 맞춤 예약 관리**:  
  - **예약자**: 예약일 및 시간이 지나지 않은 경우 "예약 완료" 버튼, 예약일이 지난 경우 "결제 요청" 버튼 표시.  
  - **수리기사**: 예약일 상태에 따라 "수리 중" 또는 "예약 완료" 버튼 표시.  
- **JSP 기반 로직 최적화**:  
  - `<c:choose>` 및 `<c:when>` 태그를 활용하여 로직의 직관성과 유지보수성을 향상.  

---

### 💰 **5. 포인트 시스템 안정성 강화**  
- 포인트 적립 및 출금 로직 개선:  
  - NullPointerException 방지 로직 추가.  
  - 잔액 계산 및 반환 값 검증 강화로 데이터 무결성 확보.  
- 포인트 히스토리 조회와 데이터 검증 로직을 최적화하여 사용자 신뢰도 상승.  

---

### 🌐 **6. 서버 및 배포 환경 최적화**  
- **시간대 불일치 문제 해결**:  
  - Tomcat JVM 옵션에 `-Duser.timezone=Asia/Seoul` 추가하여 서버와 DB 간 시간 동기화 문제 해결.  
- **배포 프로세스 개선**:  
  - JSP 캐싱 문제 해결을 위해 Tomcat `work/` 디렉토리 삭제 프로세스를 자동화.  

---

## ✅ **테스트 결과**  
- 데이터베이스 및 주요 기능 정상 작동 확인:  
  - 포인트 적립/출금, 메시지 송수신, 예약 로직 모두 테스트 완료.  
- AJAX Pulling 기반의 실시간 대화 기능 성공적으로 구현 및 배포.  
- Jakarta EE 환경에서 JSP와 WAR 배포 정상 작동 확인.  

---

## 🧩 **주요 기능**  
- **사용자 기능**  
  - 예약 관리, 포인트 적립/출금, 프로필 관리, 실시간 메시지 기능.  
  - 의뢰인: 수리 예약, 후기 등록, 채팅을 통한 수리기사와의 커뮤니케이션.  
  - 수리기사: 예약 승인, 진행 상태 관리.  
- **관리자 기능**  
  - 수리기사 가입 승인 및 회원 관리.  
  - 예약 및 후기 검토 및 게시판 관리.  

---

## 🛠️ **개발 환경 및 기술 스택**  
- **언어**: Java 11  
- **데이터베이스**: Oracle 11  
- **서버 환경**: Apache Tomcat 10  
- **웹 기술**: JSP/Servlet, JSTL, AJAX  
- **ORM**: MyBatis  
- **API**: Kakao 지도, Daum 우편번호 검색, NAVER 스마트 에디터, PortOne  

---

## 🎥 **기능 시연**  
- **예약 관리 및 수리기사와의 실시간 대화**  
  ![기능 시연 1](https://github.com/user-attachments/assets/b138dcb3-6ba0-479b-907d-a48cf28440be)  
- **포인트 적립 및 사용 로직**  
  ![기능 시연 2](https://github.com/user-attachments/assets/7d6ee237-be42-4fcf-a27f-5c41a89734eb)  
- **관리자 페이지에서의 회원 및 예약 관리**  
  ![기능 시연 3](https://github.com/user-attachments/assets/9f316705-a4e2-4645-b590-901efe8b83a6)  
