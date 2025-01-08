# 수리 전문가 매칭 플랫폼 V2 (2025) From @groovyplanet

![title](https://github.com/user-attachments/assets/024ac0d4-db57-4204-840d-a9bd553eb899)



## **유지보수 기간**:
- 2025년 1월 8일 ~ 9일

| **한정우** |
| :------: | 
| [<img src="https://avatars.githubusercontent.com/groovyplanet" height=90> <br/> @groovyplanet](https://github.com/groovyplanet) |


## **주요 변경 사항**

### 1. **Oracle 테이블 생성 오류 수정**
- REQUEST 테이블 생성 시 발생한 **ORA-00907 (missing right parenthesis)** 문제 해결
  - STATUS 컬럼의 DEFAULT 값 설정 구문 수정 (`DEFAULT 'requested'`).
  - 테이블 및 컬럼 이름을 대문자로 통일하여 SQL 코드의 일관성 확보.
  - PRIMARY KEY 제약 조건 추가를 위한 **ALTER TABLE** 구문 작성.
  - SQL 스크립트 전반 검토 및 오류 없는 실행 보장.

### 2. **Jakarta EE 기반으로 라이브러리 전환**
- 기존 **Java EE** 라이브러리(`jstl.jar`, `standard.jar`) 제거.
- Jakarta EE 라이브러리 (`jakarta.servlet.jsp.jstl`, `jakarta.servlet.jsp.jstl-api`)로 대체:
  - JSP 파일 내 URI를 Jakarta 네임스페이스 (`http://jakarta.ee/...`)로 변경.
  - 기존 라이브러리로 인한 호환성 문제 해결.
- **EC2 서버에서 Jakarta EE 전환 작업 진행:**
  - Jakarta Migration Tool을 사용해 `.war` 파일 구조를 자동 변환 시도.
  - 초기 **Invalid or corrupt jarfile** 오류 해결:
    - 적합한 `jakarta-migration.jar` 버전 다운로드 및 사용.
  - JSP 컴파일 문제 발생:
    - `org.apache.jasper.JasperException: java.lang.ClassNotFoundException` 문제 해결.
  - JSP 캐싱 문제로 인해 `org.apache.jsp.main_jsp` 관련 오류를 디버깅.

---

## **EC2 서버 환경 개선**

### EC2 서버 Jakarta EE 배포
1. **톰캣(Tomcat) 설정 및 재배포:**
   - EC2 서버의 Tomcat 10.x에 **Jakarta EE 호환성 환경 구축**.
   - `~/tomcat/bin/setenv.sh` 파일에 `-Duser.timezone=UTC` 설정 추가:
     - 로컬과 서버 환경에서 일관성 있는 타임존 동작 보장.
2. **서버와 로컬 간 불일치 해결:**
   - JSP 구조와 라이브러리를 Jakarta EE에 맞게 조정.
   - Tomcat의 `/lib` 디렉토리와 WAR 파일 내 라이브러리 충돌 검토:
     - 불필요한 중복 라이브러리 제거.

---

## **트러블슈팅 기록**

### 1. **Jakarta Migration Tool 설정 오류**
- 문제: 초기 Jakarta Migration Tool 실행 시 `NoClassDefFoundError` 발생.
- 원인: 올바른 `jakarta-migration.jar` 다운로드 실패.
- 해결:
  - 적합한 Jakarta Migration CLI 버전 수동 다운로드 및 실행.
  - `org.eclipse.transformer.cli`와 의존성을 포함한 CLI 패키지를 사용하여 변환 성공.

### 2. **EC2 서버에서 JSP 파일 로드 오류**
- 문제: `HTTP Status 500 - NoClassDefFoundError` (javax.servlet.jsp.tagext.TagLibraryValidator).
- 원인:
  - Java EE 라이브러리와 Jakarta EE 라이브러리 혼용.
  - JSP 파일에서 Java EE 네임스페이스 사용.
- 해결:
  - Java EE 라이브러리(`jstl.jar`, `standard.jar`) 제거.
  - JSP 네임스페이스를 `http://jakarta.ee/...`로 변경.

### 3. **JSP 컴파일 문제**
- 문제: `HTTP Status 500 - ClassNotFoundException: org.apache.jsp.main_jsp`.
- 원인:
  - JSP 캐싱 문제로 인해 이전 컴파일된 JSP 파일이 충돌.
- 해결:
  - Tomcat의 `work/` 디렉토리 삭제 후 Tomcat 재시작:
    ```bash
    rm -rf ~/tomcat/work/*
    ~/tomcat/bin/shutdown.sh
    ~/tomcat/bin/startup.sh
    ```

---

## **추가 작업**
- JSP 구조와 SQL 스크립트를 활용한 플랫폼 핵심 기능 복습 및 재구현.
- Jakarta EE 전환 과정 중 발생한 모든 주요 오류 기록 및 해결 방안 공유:
  - EC2 서버와 로컬 환경 간 설정 일관성 확보.
  - JSP 파일과 Jakarta EE 라이브러리의 완전한 호환성 확보.

---

## **향후 개선 방향**
- Jakarta EE 환경 최적화를 위한 추가 테스트 계획.
- JSP 캐싱 문제 완전 해결을 위한 빌드 및 배포 프로세스 개선.
- EC2 서버 자원 업그레이드(t2.micro → t2.medium) 고려.


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


