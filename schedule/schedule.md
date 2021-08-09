# project

→ pig!data(픽!데이터) - 한번 생각해 봤습니다 ㅎ...제목은 가볍게 생각하고 던져주세요! - 이근호

→오늘은 뭐 해먹지?

→냉장고를 부탁해

→

---

08/09

- 

    주제 :  재료 입력 → [데이터자료](http://data.go.kr)  - 웹 (이름)

    Q) 정해야 할 것들
    0. 테이블 칼럼 정하기

    1. 재료들을 →1) 체크박스 - 2) 검색
    2. 재료를 팔것인가 ? 결제
    3. 프로젝트 이름
    4. DB 구성 셋팅

    ERD 예시 

    - ERD

        ![./img/1.jpg](./img/1.jpg)

        ![project%205ec15d1e06e4436493f72283d42747f7/2.jpg](project%205ec15d1e06e4436493f72283d42747f7/2.jpg)

        ![project%205ec15d1e06e4436493f72283d42747f7/3.jpg](project%205ec15d1e06e4436493f72283d42747f7/3.jpg)

    전구 안에 박스는 shift +enter 쳐야지 줄이 늘어납니다

    1. 직원 테이블  

    Employee table : 
     

    직원 번호(pk) ,직원 아이디 ,비밀번호 ,직원 이름(?) , 사무실 번호

    ---

    이근호

    - 직원 번호 (employee_no) : PK
    - 직원 아이디(employee_id)
    - 비밀번호(employee_pw)
    - 이름(employee_name)
    - 입사일(employee_hire_date)
    - 직무(employee_job_id)
    - 연락처(employee_phone)
    - 사무실 연락처(employee_office_num)
    - 이메일(employee_email)
    - 주소(employee_address)

    ---

    2.공지사항 테이블

    Notice table :

    공지사항 번호  제목,내용,종류,파일, 조회수, 

    ---

    이근호

    - 글 번호 (notice_no) : PK

    → 개인적으로 현재 배운 게시글 번호 매기는 방식이 조금 잘못 됐다고 생각합니다.예를들어 1,2,3,4 번의 게시물이 있다가 3번이 지워지면 다른 번호가 땡겨지면서 1,2,3 번이 돼야 하는데 1,2,4 번으로 나옵니다. 다음글을 작성하면 5번으로 나오고요. 그래서 이부분은 개발시 수정해서 구현해보고 싶습니다.(어려운건 아니고 count(row) 같은걸로 하면 되지않을까 생각은 듭니다.)

    - 제목 (notice_title)
    - 내용 (notice_con)
    - 등록일 (notice_date)
    - 첨부 파일(notice_file)
    - 조회수(notice_count)
    - 작성자 (employee_id) : 참조키 관계

    ---

    3.회원 테이블

    member table : 

    아이디,비번,닉네임, 이메일,이메일확인

    ---

    이근호

    - 회원ID (member_id): PK
    - 비밀번호 (member_pw)
    - 닉네임 (member_nickname)
    - 주소 (member_address)
    - 이름 (member_name)
    - 전화번호 (member_phone)
    - 생일 (member_birth)
    - 성별 (member_sex)
    - 이메일 (member_email)
    - 이메일 수신여부 (member_email_chk)

    ---

    메뉴 테이블 - 재료, 부재료, 추천, 조회수

    1. 메뉴 테이블

    menu table

    음식 이름 ,재료, 부재료, 추천,조회수, 파일 

    ---

    이근호

    - 메뉴 번호(menu_no) : PK
    - 메뉴 레시피(menu_recipe) : PK
    - 이름(menu_name)
    - 썸네일(menu_img)
    - 주 재료(menu_main_ingredient) - menu_main_item (ingredient 쓸데없이 긴느낌이 있어서)
    - 부 재료(menu_sub_ingredient) - menu_sub_item
    - 추천수(menu_recommend)
    - 조회수(menu_count)
    - 작성자(Employee_id) : 참조키 관계
    - 작성자(Member_id) : 참조키 관계

    ---

    게시판 테이블

    Board table

    게시판 번호,조회수,날짜,파일, 댓글(?)

    ---

    이근호 

    → 이게 자유게시판? 이런 느낌의 게시판이었나요? 잘 기억이 ㅎ...

    - 글 번호(board_no) : PK
    - 글 제목(board_title)
    - 글 내용(board_con)
    - 첨부 파일(board_file)
    - 조회수(board_count)
    - 댓글(comment_no) : 참조키 관계
    - 작성자(member_id) : 참조키 관계

    ---

    코멘트 테이블

    comment table

    번호 ,아이디, 날짜 , 파일(?) 

    ---

    이근호 

    →일단 게시판에만 댓글을 달수있다고 생각하고 만들어 봤는데, 혹시 메뉴나 공지사항, 칼럼에도 댓글을 달 수 있다고 생각하면 수정이 필요합니다.

    - 댓글 번호(comment_no) : PK
    - 댓글 내용(comment_con)
    - 댓글 작성일시(comment_date)
    - 글 번호(board_no) : 참조키 관계
    - 댓글 작성자(member_id or employee_id) : 참조키 관계

    ---

    즐겨찾기 테이블

    Favorites(bookmarks)table :

    북마크 번호(pk) ,종류 ,  fk ~

    ---

    이근호

    - 메뉴 번호 or 메뉴 이름(menu_no or menu_id) : 참조키 관계  + PK
    - 회원ID (member_id) : 참조키 관계 + PK

    ---

    칼럼 테이블

    column table :

    ?

    ---

    이근호

    → 근데 이거 만들고 보니까 칼럼테이블 따로 만들 필요없이 공지사항 테이블에 종류 칼럼(ex . notice_kind) 추가하고 같이 써도 될 것 같습니다.

    - 글 번호(column_no) : PK
    - 칼럼 제목(column_title)
    - 칼럼 내용 (column_con)
    - 작성 일시(column_date)
    - 첨부파일(column_file)
    - 조회수(column_count)
    - 작성자(employee_id) : 참조키 관계

    ---

    ERD는 어떻게 올려야 할지 모르겠어서 월요일에 만든거 가져가겠습니다. - 이근호

    스크랩(즐겨 찾기 등록-레시피/칼럼)

---

노션 -
0) 2시 - 목소리 - 회의 - set null, cascade + DB계정, 비밀번호 통일

1. 컬럼명 (줄인걸로)확정된거 업로드

1. DB 각자 만들어오기(set null, cascade, x) 내용은 빼고

---

→ 개인적으로 컬럼 만들어 봤습니다. 내일 회의 후 수정예정

- 컬럼 예시

    CREATE TABLE NOTICE(
    NOTICE_NO NUMBER NOT NULL,
    NOTICE_TITLE VARCHAR2(200) NOT NULL,
    NOTICE_CON VARCHAR2(2000) NOT NULL,
    NOTICE_DATE DATE NOT NULL,
    NOTICE_FILE VARCHAR2(2000),
    NOTICE_KIND NUMBER NOT NULL,
    NOTICE_CNT NUMBER NOT NULL,
    EMP_NO NUMBER
    );

    CREATE TABLE EMPLOYEES(
    EMP_NO NUMBER NOT NULL,
    EMP_ID VARCHAR2(20) NOT NULL,
    EMP_PW VARCHAR2(300) NOT NULL,
    EMP_NAME VARCHAR2(20) NOT NULL,
    EMP_HIRE_DATE DATE NOT NULL,
    EMP_JOB VARCHAR2(20),
    EMP_PHONE VARCHAR2(20) NOT NULL,
    EMP_OFFICE_NUM VARCHAR2(20),
    EMP_EMAIL VARCHAR2(50) NOT NULL,
    EMP_ADDR VARCHAR2(200) NOT NULL,
    EMP_DETAIL_ADDR VARCHAR2(200) NOT NULL
    );

    CREATE TABLE MENU(
    MENU_NO NUMBER NOT NULL,
    MENU_RECIPE VARCHAR2(3000) NOT NULL,
    MENU_NAME VARCHAR2(200) NOT NULL,
    MENU_IMG VARCHAR2(200),
    MENU_MAIN_ITEM VARCHAR2(200) NOT NULL,
    MENU_SUB_ITEM VARCHAR2(300),
    MENU_RECMND NUMBER NOT NULL,
    MENU_CNT NUMBER NOT NULL,
    EMP_NO NUMBER
    );

    CREATE TABLE BOOKMARK(
    MENU_NO NUMBER NOT NULL,
    MENU_RECIPE VARCHAR2(3000) NOT NULL,
    BOOKMARK_KIND NUMBER NOT NULL
    );

    CREATE TABLE MENU_COMMENT(
    CMNT_NO NUMBER NOT NULL,
    MENU_NO NUMBER NOT NULL,
    MENU_RECIPE VARCHAR2(3000) NOT NULL,
    MEM_ID VARCHAR2(20) NOT NULL,
    CMNT_CON VARCHAR2(1000) NOT NULL,
    CMNT_DATE DATE NOT NULL
    );

    CREATE TABLE MEMBER(
    MEM_ID VARCHAR2(20) NOT NULL,
    MEM_PW VARCHAR2(300) NOT NULL,
    MEM_NICK VARCHAR2(30) NOT NULL,
    MEM_NAME VARCHAR2(20) NOT NULL,
    MEM_PHONE VARCHAR2(20),
    MEM_SEX CHAR(1),
    MEM_EMAIL VARCHAR2(50) NOT NULL,
    MEM_EMAIL_CHK CHAR(1) NOT NULL
    );

    CREATE TABLE BOARD(
    MEM_ID VARCHAR2(20) NOT NULL,
    BOARD_NO NUMBER NOT NULL,
    BOARD_TITLE VARCHAR2(200) NOT NULL,
    BOARD_CON VARCHAR2(3000) NOT NULL,
    BOARD_FILE VARCHAR2(200),
    BOARD_CNT NUMBER NOT NULL
    );

    CREATE TABLE BOARD_COMMENT(
    CMNT_NO NUMBER NOT NULL,
    CMNT_MEM_ID VARCHAR2(20) NOT NULL,
    BOARD_MEM_ID VARCHAR2(20) NOT NULL,
    BOARD_NO NUMBER NOT NULL,
    CMNT_CON VARCHAR2(1000) NOT NULL,
    CMNT_DATE DATE NOT NULL
    );

---

→ 참조관계 개인적인 의견 입니다. (이근호)

1) 직원 - 공지사항 (on set null)

2) 직원 - 메뉴 (on set null)

3) 메뉴 - 즐겨찾기(on cascade)

4) 메뉴 - 메뉴댓글(on cascade)

5) 회원 - 메뉴댓글(on cascade)

6) 회원 - 게시판(on cascade)

7) 회원 - 게시판댓글(on cascade)

8) 게시판 - 게시판댓글(on cascade)

---

식별 : 부모 테이블에 데이터가 삭제되면 자식테이블 데이터도 삭제돼야 되는경우 (on cascade)
비식별 : 부모 테이블 데이터가 삭제되더라도 자식테이블 데이터는 삭제되지 않는경우 (on set null)
자식테이블에 데이터가 있을 때 부모테이블 데이터 삭제되면 안되는 경우(X : 아무 관계도 안 준 경우)

---

---

![project%205ec15d1e06e4436493f72283d42747f7/Untitled.png](project%205ec15d1e06e4436493f72283d42747f7/Untitled.png)

웹 프로젝트 - 2 주

css, jQuery, Ajax - 2주

![project%205ec15d1e06e4436493f72283d42747f7/Untitled%201.png](project%205ec15d1e06e4436493f72283d42747f7/Untitled%201.png)

저번에 그린 레이아웃 대충 잡아봤습니다.(라인은 레이아웃 구분을 위해 잡았습니다.)

수정/보완 -1

[]()
