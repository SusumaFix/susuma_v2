# 수리 전문가 매칭 플랫폼 V2 (2025) From @groovyplanet

![title](https://github.com/user-attachments/assets/024ac0d4-db57-4204-840d-a9bd553eb899)



## **업데이트 기간**:
- 2025년 1월 8일 ~ 10일 , 16일 (3 day)

| **한정우** |
| :------: | 
| [<img src="https://avatars.githubusercontent.com/groovyplanet" height=90> <br/> @groovyplanet](https://github.com/groovyplanet) |


## **주요 변경 사항**

### **1. Oracle 테이블 및 DB 스키마 수정**
- **REQUEST 테이블**:  
  - `STATUS` 컬럼에 기본값 설정(`DEFAULT 'requested'`) 및 SQL 문법 오류(ORA-00907) 수정.
  - 테이블 및 컬럼 이름을 대문자로 통일하여 SQL 코드 일관성 유지.
- **MESSAGE 테이블**:  
  - `MESSAGE` 컬럼 크기를 기존 50자에서 255자로 확장하여 긴 메시지 저장 가능.
- **POINT_HISTORY 테이블**:  
  - 컬럼 타입 변경으로 자바와의 데이터 타입 호환성 확보.

---

### **2. Jakarta EE 전환**
- 기존 Java EE에서 Jakarta EE로 전환:
  - JSP 파일 네임스페이스를 Jakarta(`http://jakarta.ee/...`)로 수정.
  - Tomcat 10.x 환경에서 Jakarta EE 호환성 최적화.
- EC2 서버 설정:
  - 중복 라이브러리를 제거하고 배포 환경 최적화.

---

### **3. 예약 및 수리 로직 개선**
- 예약자와 수리 기사 입장에서의 버튼 표시 로직 수정:
  - **예약자 입장**:
    - 예약일 및 시간이 지나지 않은 경우 "예약 완료" 버튼 표시.
    - 예약일 및 시간이 지난 경우 "결제 요청" 버튼 표시.
  - **수리 기사 입장**:
    - 예약일이 미래일 경우 "예약 완료", 예약일이 지났을 경우 "수리 중" 버튼 표시.
- JSP의 `<c:choose>` 및 `<c:when>` 태그 활용으로 조건 처리 로직 최적화.

---

### **4. 포인트 관련 로직 개선**
- 포인트 적립 및 출금 로직에서의 안정성 개선:
  - `NullPointerException` 방지 로직 추가.
  - 잔액 계산 및 반환 값 검증 로직 강화.
- 포인트 히스토리 조회 시 데이터 타입 오류 해결.
- 포인트 유효성 검사 로직 추가.

---

### **5. 메시지 관련 로직 개선**
- 메시지 전송 로직:
  - 메시지 길이 유효성 검사(255자 제한) 추가.
  - 메시지 내역 조회 및 업데이트 로직 예외 처리 강화.
- 사용자 경험 개선:
  - 잘못된 입력에 대한 피드백 메시지 추가.

---

### **6. Tomcat 서버 설정 개선**
- **시간대 문제 해결**:
  - Tomcat의 JVM 옵션에 `-Duser.timezone=Asia/Seoul` 추가.
  - DB와 서버 간 시간 불일치 문제를 해결하여 시간 기반 로직의 정확성 확보.
- **캐싱 문제 해결**:
  - Tomcat `work/` 디렉토리 삭제를 통해 JSP 업데이트 반영 문제 해결.

---

## **테스트 결과**
- 데이터베이스 스키마 및 주요 기능 정상 작동 확인:
  - 포인트 적립/출금, 메시지 전송/조회 모두 테스트 완료.
- JSP 및 WAR 배포 후 Jakarta EE 환경에서 정상 작동 확인.
- 예약 및 수리 버튼 로직, 시간대 문제 모두 해결.

---

## **향후 개선 방향**
1. Jakarta EE 전환 후 성능 최적화를 위한 추가 테스트 계획.
2. JSP 캐싱 문제 완전 해결을 위해 빌드 및 배포 프로세스 개선.
3. EC2 서버 업그레이드(t2.micro → t2.medium) 검토 및 성능 테스트.


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


