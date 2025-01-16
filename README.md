# 수리 전문가 매칭 플랫폼 V2 (2025) From @groovyplanet

![title](https://github.com/user-attachments/assets/024ac0d4-db57-4204-840d-a9bd553eb899)



## **유지보수 기간**:
- 2025년 1월 8일 ~ 10일

| **한정우** |
| :------: | 
| [<img src="https://avatars.githubusercontent.com/groovyplanet" height=90> <br/> @groovyplanet](https://github.com/groovyplanet) |


### **주요 변경 사항**

---

### 1. **Oracle 테이블 및 DB 스키마 수정**
- `REQUEST` 테이블 생성 오류 수정:
  - **ORA-00907 (missing right parenthesis)** 해결 및 `STATUS` 컬럼 DEFAULT 값 설정 (`DEFAULT 'requested'`).
  - 테이블 및 컬럼 이름을 대문자로 통일하여 SQL 코드 일관성 확보.
- `MESSAGE` 테이블:
  - `MESSAGE` 칼럼 크기를 50자 → 255자로 확장하여 긴 메시지 저장 가능.
- `POINT_HISTORY` 테이블:
  - 칼럼 타입 변경으로 자바 `String` 처리 호환성 확보.

---

### 2. **Jakarta EE로 전환**
- 기존 Java EE 라이브러리 제거 후 Jakarta EE 라이브러리로 전환:
  - JSP 파일 내 네임스페이스를 Jakarta (`http://jakarta.ee/...`)로 변경.
  - JSP 캐싱 문제로 발생한 `ClassNotFoundException` 해결:
    - Tomcat의 `work/` 디렉토리 삭제 후 서버 재시작.
- EC2 서버 환경 설정:
  - Jakarta EE 호환성을 위해 Tomcat 10.x에서의 설정 최적화.
  - 라이브러리 충돌 방지를 위해 불필요한 중복 라이브러리 제거.

---

### 3. **포인트 관련 로직 개선**
- **적립 및 출금 로직 안정화**:
  - `earnPoints` 및 `withdrawPoints` 로직에서 `NullPointerException` 방지.
  - 잔액 계산 및 반환 값 검증 로직 추가.
- 포인트 히스토리 조회 시 데이터 타입 오류 수정.
- `pointsParam` 유효성 검사 로직 추가.

---

### 4. **메시지 관련 로직 개선**
- 메시지 전송 로직:
  - 메시지 길이 유효성 검사 추가 (255자로 제한).
  - 메시지 내역 조회 및 업데이트 로직에서 예외 처리 강화.
- 프론트엔드 수정:
  - 잘못된 입력에 대한 사용자 피드백 개선.

---

### 5. **트랜잭션 처리 및 SQL 개선**
- JDBC 트랜잭션 경계 설정 점검 및 커밋/롤백 처리 안정화.
- SQL Mapper 파일 정리 및 주석 추가.
- SQL 로깅 및 디버깅용 로그 메시지 강화.

---

### 6. **테스트 결과**
- 데이터베이스 스키마 및 주요 기능 정상 작동 확인:
  - 포인트 적립/출금, 메시지 전송/조회 모두 테스트 완료.
- MyBatis Mapper 및 SQL 쿼리 실행 시 예외 없음 확인.
- Jakarta EE 전환 후 JSP 및 WAR 배포 정상 작동 확인.

---

### **향후 개선 방향**
- Jakarta EE 환경 최적화를 위한 추가 테스트 계획.
- JSP 캐싱 문제 완전 해결을 위한 빌드 및 배포 프로세스 개선.
- EC2 서버 업그레이드(t2.micro → t2.medium) 고려. 



-----------------------------------

- **주요 기능**
   - `사용자`
      - 예약·포인트·프로필 관리 및 채팅
      - 의뢰인 : 수리 예약 및 후기 등록
      - 수리기사 : 수리 예약 승인
   - `관리자`
       - 회원 관리(수리기사 가입 승인)
       - 예약 및 후기 관리
       - 게시판 관리


<br/>

## 🤹‍♂️ 개발 환경 및 기술 스택

| 항목 | 내용 |
|---|---|
| **프로그래밍 언어** | Java 11 |
| **데이터베이스(DB)** | Oracle 11 |
| **애플리케이션 서버** | Apache Tomcat 10 |
| **웹 기술** | ✨**JSP/Servlet**, JSTL |
| **ORM** | MyBatis |
| **API** | Kakao 지도, Daum 우편번호 검색, NAVER 스마트 에디터, PortOne |
| **개발 도구(IDE)** | Eclipse, VSCode |
<br/>

## 🎡 문서

<details>
  <summary>E-R Diagram</summary>
  
![image](https://github.com/user-attachments/assets/410d6ee6-c1c6-489e-9cde-737dcdb0201b)


</details>


<details>
  <summary>요구사항 정의서</summary>
  
![제목 없음](https://github.com/user-attachments/assets/a769397f-f7e8-43ae-bb29-b4206594acaa)


</details>
<details>
  <summary>화면 구성도</summary>

![image](https://github.com/user-attachments/assets/e0b58ac3-c044-468f-adce-e9a9eda19af8)

</details>
<details>
  <summary>UI 설계</summary>
  
![image](https://github.com/user-attachments/assets/41f176e8-3aba-4ba0-8af4-fcffc0c12585)


</details>
<details>
  <summary>발표 PPT</summary>
 
- 녹화영상 - https://drive.google.com/file/d/1KPLjIDQb2eJQuXJGfi86WiTOM05YGeTK/view?usp=sharing
![SUSUMA PROJECT-1](https://github.com/user-attachments/assets/58943509-51f9-40c6-9615-2460bdd25085)
![SUSUMA PROJECT-2](https://github.com/user-attachments/assets/42860ace-d998-40f4-a8bd-d211f46235d0)
</details>

<br/>

## 🧩 기능 시연
![111](https://github.com/user-attachments/assets/b138dcb3-6ba0-479b-907d-a48cf28440be)
![444](https://github.com/user-attachments/assets/7d6ee237-be42-4fcf-a27f-5c41a89734eb)
![555](https://github.com/user-attachments/assets/9f316705-a4e2-4645-b590-901efe8b83a6)


