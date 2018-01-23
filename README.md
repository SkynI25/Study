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
var dates = time.match(new RegExp("\\d*-\\d*-\\d*", "g")); <!-- RegExp는 정규표현식 객체이다 --> 

d 는 숫자 문자를 일컫으며 *은 0이상 연속으로 반복되는 앞선 문자를 찾게 해준다.

g 는 Global로 'g' 를 사용하지 않으면 일치하는 것 하나만 찾아주고 끝나지만 g를 해줌으로써 일치하는 모든 것을 찾게 된다.

*(별) 사용에 대한 예로써

"aaa".match(RegExp("a*", "g")) 의 결과값은 0 이상이므로 null, ('aaa') 가 나오게 된다.

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

results["<%=datas[i].time%>".match(new RegExp("\\d*-\\d*-\\d*", "g"))[0]]["<%=datas[i].result%>"] += 1;

(0123)
sql 데이터를 chart.js 를 이용하여 나타내는 방법

정말 어려운 부분이고 까다로운 부분이었는데, 이 또한 동기가 도와주어서 해결할 수 있었다.

동기는 time 포맷을 javascript에서 받을 수 있도록 변형해주어 sql를 전송해주었고

받은 sql 데이터를 javascript 정규식을 이용하여 javascript에서 이해할 수 있는 형태로 변환하여 숫자 데이터 값을

만들었고 이를 출력해주었다.

var sql = 'select result, date_format(time, "%Y-%m-%d") as time from hana where time >= ? and time <= DATE_ADD(?, INTERVAL 1 DAY)';

date_format으로 해주어 년-월-일 형태로 나타나게 해주었고 이 때 컬럼의 이름을 as time으로 해주어 js에서 time으로 쓸 수 있도록 해주었다.

https://www.w3schools.com/sql/func_mysql_date_format.asp

  <script>
    function pad(n, width, z) {
      z = z || '0';
      n = n + '';
      return n.length >= width ? n : new Array(width - n.length + 1).join(z) + n;
    }

    var ctx = document.getElementById("myChart");
    var results = {};
    var dates = ["<%=dates[0]%>", "<%=dates[1]%>"];
    var start = new Date(0);
    start.setFullYear(dates[0].split("-")[0], dates[0].split("-")[1] - 1, dates[0].split("-")[2]);
    var end = new Date(0);
    end.setFullYear(dates[1].split("-")[0], dates[1].split("-")[1] - 1, dates[1].split("-")[2]);

    if (start <= end) {
      while (start <= end) {
        var str = (start.getYear() + 1900) + "-" + pad((start.getMonth() + 1), 2) + "-" + pad(start.getDate(), 2);
        results[str] = {};
        results[str]["OK"] = 0;
        results[str]["NO"] = 0;
        start = new Date(start.getTime() + 86400000);
      }
      console.log(results);
      <%
       for(var i = 0; i < datas.length; ++i) {
      %>
      results["<%=datas[i].time%>"]["<%=datas[i].result%>"] += 1;
      <%
       }
       %>

      console.log(results);
    }
    var OKs = [];
    for (var key in results) {
      OKs.push(results[key]["OK"]);
    }
    var NOs = [];
    for (var key in results) {
      NOs.push(results[key]["NO"]);
    }

    var mixedChart = new Chart(ctx, {
      type: 'line',
      data: {
        datasets: [{
          // OK
          label: 'OK',
          data: OKs,
          lineTension: 0,
          backgroundColor: 'transparent',
          borderColor: '#007bff',
          borderWidth: 4,
          pointBackgroundColor: '#007bff'
        },
          // NO
        {
          label: 'NO',
          data: NOs,
          lineTension: 0,
          backgroundColor: 'transparent',
          borderColor: '#ff3400',
          borderWidth: 4,
          pointBackgroundColor: '#ff3400',
          type: 'line'
        }],
        labels: Object.keys(results)
      },
      options: {
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true
            }
          }]
        },
        legend: {
          display: true
        }
      }
    });
  </script>


코드가 꽤 긴데 처음에 pad라는 함수를 선언해준 것을 볼 수 있다. pad는 빈공간을 0으로 채워주는 함수이다.

그리고 ctx 라는 변수로 chart를 그려주는 변수가 선언되어있고

이후 results라는 객체를 생성한다.

그리고 hana_mysql2 파일에서 쿼리문을 통해 날린 dates를 형태를 변환하여 받는다.

보통의 js는 dates[i] 와 같은 형태로 받을 수 있으나 ejs의 특징으로 인하여 앞 뒤로 <%=변수%> 와 같은 형태를 취해주어야 했다.

이를 알아내는데 꽤 많은 시간이 들었다.

그리고 단순히 숫자값 형태로 두 개가 날라오기 때문에 스트링 형태로 배열에 저장하는 식으로 dates 를 선언해주었다.

이 후 start 와 end를 new Date(0)으로 선언해주었다.

new Date(0)은 1900-01-01 으로 되어있는 날짜 값으로 new Date(0) 작업은 초기화를 해준 것이라 볼 수 있다.

이후 setFullYear라는 함수로 쿼리문에서 날라온 dates 데이터들을 start 와 end 에 set 해주었다. 이 때 중간에 월은

-1 을 해주는데 이유는 javascript에서는 "1 월에서 12 월까지의 월을 나타내는 0에서 11 사이의 정수" 로 표시해주기 때문에 -1를 해주었다.

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/setFullYear

이 후 if(start <= end) { while(start <= end) { 로 start의 날짜가 end의 날짜에 다다를 때 까지 반복을 해준다.

str의 변수에는 년 월 일을 세팅해준다. 이 때 연에 +1900을 해주는 이유는 getYear가 2017이 있을 때 117만을 가져오기 때문이다.

월과 일은 pad를 이용하여 1~9까지의 숫자에 앞에 0이 붙도록 해주었다. start.getMonth()를 하여 start의 월을 가져오고

+1 해주어 1 부족한 값을 더해준다. 이 후 콤마 다음의 2는 너비로 2로 해주면 두자리의 수까지 표현하게 되고 5을 하게 되면 000XX 와 같이 숫자가

나오는 이외의 자리에 0이 더 붙어서 나온다(pad의 역할) 2자리 숫자를 표현할 때 10이상의 숫자이면 앞에 0이 더 붙지 않는다.

results[str] = {} 로 해주어 results의 str 프로퍼티를 초기화해주고

results[str]["OK"] = 0;

results[str]["NO"] = 0; 와 같이 해주어 OK와 NO가 들어올 자리를 초기화 해주었다.

이 후 for문을 통해 날라온 datas 의 길이만큼 반복을 하는데 

results["<%=datas[i].time%>"]["<%=datas[i].result%>"] 에 1씩 더해주게 된다. 이는 쿼리문으로 날짜와 결과(OK or NO)가 날아왔을 때

html에서 선언해준 results 오브젝트(OK or NO)(results[str][OK or NO])에 하나씩 더해지게 되는 것이다.

이 후 OKs와 NOs 라는 배열을 만들어 for(key in result) { OKs.push(results[key]["OK"]); } 와 같이 results 객체의 프로퍼티들에서

OK와 NO 값이 있는 것들을 각각 OKs, NOs 배열에 대입해주어 이를 chart에서 출력해주게 하였다.

https://www.w3schools.com/js/js_arrays.asp
https://www.w3schools.com/js/js_loop_for.asp

그리고 chart에서 labels를 표시 할 때 keys 함수를 사용하여 프로퍼티들을 표시를 하였다. keys는 오브젝트의 프로퍼티 이름을 표시해주는 함수이다.

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/keys

http://www.chartjs.org/docs/latest/

그리고 ticks : {beginAtZero : true}로 해주어 0부터 시작할 수 있게하였고 legend : { display : true, }로 하여 라벨을 표시하게 하였다.

배경그림 선택할 때 유용한 싸이트

http://www.colorhexa.com/007bff
