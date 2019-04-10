# TableBoard_Shop
게시판-Shop 의 TODO 완성하기!

## 기존 파일
```
 .
├── css - board_form.php와 index.php 에서 사용하는 stylesheet
│   └── ...
├── fonts - 폰트
│   └── ...
├── images - 아이콘 이미지
│   └── ...
├── vender - 외부 라이브러리
│   └── ...
├── js - board_form.php와 index.php 에서 사용하는 javascript
│   └── ...
├── function
│   └── insert.php - 게시글 작성 기능 구현
│   └── update.php - 게시글 수정 기능 구현
│   └── delete.php - 게시글 삭제 기능 구현
├── board_form.php - 게시글 작성/수정 시 사용하는 form이 포함된 php 파일
├── index.php - 게시글 조회 기능 구현
```

## MySQL 테이블 생성!

[여기에 테이블 생성 시, 사용한 Query 를 작성하세요.]
```
create tableboard_shop ( num int not null, date date not null, order_id char(20) not null, name char(20) not null, price int not null, quantity int not null, primary key(num));
```
Note: 
- table 이름은 tableboard_shop 으로 생성
- 기본키는 num 으로, 그 외의 속성은 board_form.php 의 input 태그 name 에 표시된 속성 이름으로 생성
- 각 속성의 type 은 자유롭게 설정 (단, 입력되는 값의 타입과 일치해야 함)
    - ex) price -> int
    - ex) name -> char or varchar
    
## index.php 수정
 - mysql db 연동
    - mysql_connect : mysql 계정 연동
    - mysql_select_db : 계정의 db 연동
 - mysql 쿼리 스트링 전송
    - mysql_query
 - 레코드 가져오기
    - mysql_fetch_array
 - 가져온 데이터 출력
    - while문을 이용해 가져온 데이터 전부 echo로 출력
## board_form.php 수정
- db 불러오기
    - mysql_connect, mysql_select_db
- 쿼리 스트링 전송
    - mysql_query
- 데이터 출력
    - select *from tableboard_shop where num='$_GET[num]', mysql_fetch_array로 num에 해당하는 레코드 데이터 가져옴
    - echo로 레코드값 출력

## function
### insert.php 수정
- db 불러오기
    - mysql_connect, mysql_select_db
- 값 집어넣기
    - insert를 이용해 각 필드에 데이터 집어넣음 ($_POST를 이용해 입력받은 데이터 읽어옴)
- 쿼리 스트링 전송
   - mysql_query
- 오류 메세지
   - 쿼리 스트링 전송 false라면 오류 메세지를 출력
### update.php 수정
- db 불러오기
    - mysql_connect, mysql_select_db
- 쿼리 스트링 전송
    - mysql_query
- 값 수정하기
    - update를 이용해 각 필드에 데이터 집어넣음 ($_POST를 이용해 입력받은 데이터 읽어옴 / $_GET을 이용해 수정하고자 하는 레코드 지정)
- 오류 메세지
   - 쿼리 스트링 전송 false라면 오류 메세지를 출력
### delete.php 수정
- db 불러오기
    - mysql_connect, mysql_select_db
- 쿼리 스트링 전송
    - mysql_query
- 값 삭제하기
    - delete를 이용해 각 필드에 데이터 집어넣음 ($_GET을 이용해 삭제하고자 하는 레코드 지정)
- 오류 메세지
   - 쿼리 스트링 전송 false라면 오류 메세지를 출력
