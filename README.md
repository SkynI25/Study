# Study

JSON이란 ?

: Data format(more detail information ->)
http://egloos.zum.com/killins/v/3013974

In python, how to check the list data type is empty or not?

권장하는 방법)
    if not seq:
    if seq:

In python, about operator overloading

http://blog.eairship.kr/287

one of the way to store file path to DB

https://stackoverflow.com/questions/20208878/storing-images-in-server-using-expressjs


(20180112)
와...하루동안 삽질했는데 npm 모듈 설치하니까 에러가 해결됬다..

npm install mysql

해주니 해결이 됬다.

nodejs로 mysql을 연결하여 하려하는데 오류가 발생하였다.

success!!
{ Error: ER_ACCESS_DENIED_ERROR: Access denied for user 'hana'@'192.168.0.251' (using password: YES)
    at Handshake.Sequence._packetToError (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Sequence.js:30:14)
    at Handshake.ErrorPacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Handshake.js:67:18)
    at Protocol._parsePacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:197:24)
    at Parser.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Parser.js:62:12)
    at Protocol.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:37:16)
    at Socket.ondata (_stream_readable.js:557:20)
    at emitOne (events.js:101:20)
    at Socket.emit (events.js:191:7)
    at readableAddChunk (_stream_readable.js:178:18)
    at Socket.Readable.push (_stream_readable.js:136:10)
    --------------------
    at Protocol._enqueue (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:110:26)
    at Protocol.handshake (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:42:41)
    at Connection.connect (/opt/server_side_javascript/node_modules/mysql/lib/Connection.js:81:18)
    at Object.<anonymous> (/opt/server_side_javascript/database_mysql.js:8:6)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
    at Function.Module._load (module.js:439:3)
    at Module.runMain (module.js:605:10)
  code: 'ER_ACCESS_DENIED_ERROR',
  errno: 1045,
  sqlState: '28000',
  fatal: true }
tag@tag-desktop:/opt/server_side_javascript$ node database_mysql.js
success!!
{ Error: ER_ACCESS_DENIED_ERROR: Access denied for user 'hana'@'localhost' (using password: YES)
    at Handshake.Sequence._packetToError (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Sequence.js:30:14)
    at Handshake.ErrorPacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Handshake.js:67:18)
    at Protocol._parsePacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:197:24)
    at Parser.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Parser.js:62:12)
    at Protocol.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:37:16)
    at Socket.ondata (_stream_readable.js:557:20)
    at emitOne (events.js:101:20)
    at Socket.emit (events.js:191:7)
    at readableAddChunk (_stream_readable.js:178:18)
    at Socket.Readable.push (_stream_readable.js:136:10)
    --------------------
    at Protocol._enqueue (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:110:26)
    at Protocol.handshake (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:42:41)
    at Connection.connect (/opt/server_side_javascript/node_modules/mysql/lib/Connection.js:81:18)
    at Object.<anonymous> (/opt/server_side_javascript/database_mysql.js:8:6)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
    at Function.Module._load (module.js:439:3)
    at Module.runMain (module.js:605:10)
  code: 'ER_ACCESS_DENIED_ERROR',
  errno: 1045,
  sqlState: '28000',
  fatal: true }

생각해보니 공부를 할 때에도 npm install --save node-mysql 작업을 해주었는데

mariadb 를 설치하니 별개의 npm을 설치해줘야한다는 생각에 저 작업을 하지 않았었다.

당연히 mysql 과 연결하려면 저 모듈을 설치해줘야 한다..설치를 진행하면서 전체적인 과정을 잘 정리하지 못하여 생긴 문제이다.

앞으로는 설치해야하는 모듈들이 많을 때는 체크를 해나가며 단계적으로 해나가도록 해야겠다.

(20180112)
우분투에 외부 접속을 허용하기 위한 방법 :

https://blog.naver.com/atm007/220109914861

https://blog.naver.com/hwangs88/20165014828

http://abc1211.tistory.com/289

굉장히 잘 설명해놓았다.

우분투 컴퓨터 ip 서버로 접속이 안되는 문제가 있었는데 알고보니 같은 공유기를 사용하고 있는 내부 네트워크에서는  포트 포워딩 까지 해줄 필요가 없었다..그냥 접속이 되는 것이었는데 lael 블로그를 따라 방화벽 설정을 해주니 접속이 안되는 거였다. iptables -F 로 초기화를 해주고 다시 접속을 해보니 잘 되었다.

MySQL 사용자 생성 및 삭제 문법 :

http://damduc.tistory.com/4

http://ourcstory.tistory.com/45

Useful code for developing Node.js :

http://blog.kichul.co.kr/2017/01/27/2017-03-27-node-js-notes/

HTML Table in Jade Templatee :

https://stackoverflow.com/questions/28187290/how-rotate-html-table-using-jade-template-node-express-jade

MySQL 테이블 생성시 DATETIME 타입에 DEFAULT로 현재 시간 입력하기 :

http://jsonobject.tistory.com/122

Useful Homepage UI stuff :

https://semantic-ui.com/modules/dropdown.html#search-dropdown

어제와 오늘 헤매다가 해결한 것들 정리(20180118)

어제는 이미지를 클릭했을 때 그 이미지를 띄우지 못해서 애를 먹었다

이는 app.use(express.static('./')); 에서 기본 경로를 ./(현재 디렉토리)로 설정하면서 해결하였다.

그리고 검색한 자료를 띄우기 에서는

redirect 를 사용하지 않고 검색한 자료로 view2로 render 하여 띄워주었다.

view2의 form에서 'data/list'로 post 방식으로 자료를 보내주고

app.post('/data/list')로 데이터를 받아 입력한 자료를 받아 select * from hana where=?

로 치환자의 값으로 form 에서 보낸 데이터를 받아 select 검색이 되도록 하였다.

Display Calendar by using jQuery :

http://www.nextree.co.kr/p9887/

To hide element in HTML :

<table>
  <tr><th>Test Table</th><tr>
  <tbody style="display:none">
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
  </tbody>
</table>

https://stackoverflow.com/questions/6910349/hiding-table-data-using-div-style-displaynone

how to install Ubuntu using USB :

http://sergeswin.com/1178

https://medium.com/ics-lab/%EC%9A%B0%EB%B6%84%ED%88%AC-ubuntu-%EB%A1%9C-%EA%B0%9C%EB%B0%9C%ED%95%98%EA%B8%B0-1-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-%EB%93%80%EC%96%BC%EB%B6%80%ED%8C%85-9964f088c9ac


(0122)
javascript에서 달력 Ui를 고를 때 아주 좋은 싸이트를 찾았다

http://www.daterangepicker.com/

꽤 많은 종류의 달력들이 있고 심지어 범위 지정이 가능한 Ui도 있어 많이 유용하다

위의 Ui를 통해 날짜를 검색해서 데이터를 띄울 때 post 방식으로 데이터를 전달받았지만

형식이 달라 이를 쿼리 검색식으로 추려내는 것이 어려웠다.

많은 자료를 찾아보았지만 동기가 정규식을 이용하여 아래와 같이 해결해주었다.

https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D

var time = req.body.time;
var dates = time.match(new RegExp("\\d*-\\d*-\\d*", "g"));

body 값의 time에 input 박스안에 있는 값들이 날려오고

time.match(new RegExp("\\d*-\\d*-\\d*", "g")); 식을 통해 년월일을 가져오게 된다

RegExp 내용안의 형식과 같은 값을 추려내준다. 이 때 달력 Ui에서 년월일은 '월, 일, 년' 이었기에 '년-월-일'로 나오도록 바꿔주었다.

값이 잘 추려졌고 기간 내의 값을 검색하기 위해 mariadb에서 date를 내의 값을 검색하는 방법을 찾아서 아래와 같이 하였다.

https://mariadb.com/kb/en/library/select-based-upon-date/

var sql = 'select * from hana where time >= ? and time <= DATE_ADD(?, INTERVAL 1 DAY)';

이 때 두번 째 치환자 앞 뒤로 함수들이 붙어있는데

DATE_ADD(#1, #2) 는 #1 기간에 #2 기간만큼을 더 더해주는 함수이다.

기간 내의 검색을 할 때 쿼리식에서 '<=' 해주었는데 마지막 날짜가 포함해주지 않아서 mariadb에서 참조한 함수로 마지막 날짜에 하루를 더 더해주도록 하였다.

https://mariadb.com/kb/en/library/date_add/
