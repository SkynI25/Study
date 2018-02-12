HTML Table in Jade Templatee :<br>

https://stackoverflow.com/questions/28187290/how-rotate-html-table-using-jade-template-node-express-jade

Useful Homepage UI stuff :<br>

https://semantic-ui.com/modules/dropdown.html#search-dropdown

>어제와 오늘 헤매다가 해결한 것들 정리(20180118)

어제는 이미지를 클릭했을 때 그 이미지를 띄우지 못해서 애를 먹었다

이는 app.use(express.static('./')); 에서 기본 경로를 ./(현재 디렉토리)로 설정하면서 해결하였다.

그리고 검색한 자료를 띄우기 에서는

redirect 를 사용하지 않고 검색한 자료로 view2로 render 하여 띄워주었다.

view2의 form에서 'data/list'로 post 방식으로 자료를 보내주고

app.post('/data/list')로 데이터를 받아 입력한 자료를 받아 select * from hana where=?

로 치환자의 값으로 form 에서 보낸 데이터를 받아 select 검색이 되도록 하였다.<br>

Display Calendar by using jQuery :<br>

http://www.nextree.co.kr/p9887/

To hide element in HTML :<br>
```
<table>
  <tr><th>Test Table</th><tr>
  <tbody style="display:none">
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
  </tbody>
</table>
```

https://stackoverflow.com/questions/6910349/hiding-table-data-using-div-style-displaynone


>(0122)

javascript에서 달력 Ui를 고를 때 아주 좋은 싸이트를 찾았다<br>

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

배경그림 선택할 때 유용한 싸이트 :<br>

http://www.colorhexa.com/007bff<br>

results["<%=datas[i].time%>".match(new RegExp("\\d*-\\d*-\\d*", "g"))[0]]["<%=datas[i].result%>"] += 1;<br>

(0123)<br>
sql 데이터를 chart.js 를 이용하여 나타내는 방법

정말 어려운 부분이고 까다로운 부분이었는데, 이 또한 동기가 도와주어서 해결할 수 있었다.

동기는 time 포맷을 javascript에서 받을 수 있도록 변형해주어 sql를 전송해주었고

받은 sql 데이터를 javascript 정규식을 이용하여 javascript에서 이해할 수 있는 형태로 변환하여 숫자 데이터 값을

만들었고 이를 출력해주었다.

var sql = 'select result, date_format(time, "%Y-%m-%d") as time from hana where time >= ? and time <= DATE_ADD(?, INTERVAL 1 DAY)';

date_format으로 해주어 년-월-일 형태로 나타나게 해주었고 이 때 컬럼의 이름을 as time으로 해주어 js에서 time으로 쓸 수 있도록 해주었다.

https://www.w3schools.com/sql/func_mysql_date_format.asp

```
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
```

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

(0125) <br>
이번에는 달력에 날짜별로 OK와 NO의 갯수를 출력하는 작업을 하였다. 이 역시 동기가 도와주어서 잘 진행할 수 있었다. <br>
작업을 하면 할수록 javascript를 다시 공부해서 메소드에 대한 공부를 한번 해야겠다는 생각이 든다. <br>아래와 같이 한 작업은 모두 
문서를 참고하여 js에서 받아들일 수 있도록 변형해주는 작업이기 때문이다.<br>
전체적으로 fullCalendar라는 javascript event calendar에 전달받은 sql데이터의 날짜별 갯수를 출력해준다.<br>
소스는 아래와 같다.<br>

```
  <!-- Calendar -->
  <script>

    function pad(n, width, z) {
      z = z || '0';
      n = n + '';
      return n.length >= width ? n : new Array(width - n.length + 1).join(z) + n;
    }

    var results = {};
    var today = new Date();
    var start = new Date(0);
    start.setFullYear(today.getFullYear(), today.getMonth(), 1);
    var end = new Date(0);
    end.setFullYear(today.getFullYear(), today.getMonth() + 1, 1);
    while(start < end) {
      var str = (start.getFullYear()) + "-" + pad((start.getMonth() + 1), 2) + "-" + pad(start.getDate(), 2);
      results[str] = {};
      results[str]["OK"] = 0;
      results[str]["NO"] = 0;
      start.setTime(start.getTime() + 86400000);
    }

    <%
      for(var i=0; i<datas.length; ++i) {
    %>
    results["<%=datas[i].time%>"]["<%=datas[i].result%>"] += 1;
    <%
      }
    %>
    var events = [];
    for(var date in results) {
      events.push({
        title: 'OK : ' + results[date]['OK'],
        color : '#ffffff',
        textColor : '#000000',
        start: date
      });
      events.push({
        title: 'NO : ' + results[date]['NO'],
        color : '#ffffff',
        textColor : '#000000',
        start: date
      });
    }
  $(document).ready(function() {

    $('#calendar').fullCalendar({
      header: {
        left: 'prev,next today',
        center: 'title',
        right: 'month,basicWeek,basicDay'
      },
      defaultDate: (today.getFullYear()) + "-" + pad((today.getMonth() + 1), 2) + "-" + pad(today.getDate(), 2),
      navLinks: true, // can click day/week names to navigate views
      editable: false,
      eventLimit: true, // allow "more" link when too many events
      events: events
    });

  });

</script>
<style>

  body {
    margin: 40px 10px;
    padding: 0;
    font-family: "Lucida Grande",Helvetica,Arial,Verdana,sans-serif;
    font-size: 14px;
  }

  #calendar {
    max-width: 1000px;
    margin: 0 auto;
  }

</style>

```

pad함수는 chart를 그릴 때 하던 것과 비슷하다. <br>
마찬가지로 results 오브젝트를 생성하여준다. chart는 기간을 설정하여 그 기간내에 해당하는 데이터를 가져와 보여주었다.<br>
달력도 이와 비슷하게 첫 일과 끝 일을 현재 달을 기준으로 생성하여 이 날짜들 간에 해당하는 데이터를 가져와 보여준다.<br>
(ex. start = 1, end = 31)<br>
today는 현재 달의 첫 일과 끝 일을 구하기 위해 생성한 날짜 변수이다.<br>
start와 end는 new Date(0)으로 생성해주었는데 today처럼 new Date() 로 해주지 않은 이유는 시분초를 일치시키기 위해서이다.<br>
new Date() 하게 되면 입력한 그 순간의 시간이 들어오게 되므로 start와 end를 비교할 때 시분초에서 차이가 발생하게 된다.<br>
그리하여 1초 차이로 이 후에 나올 while(start < end) 구간에서 end를 포함시켜 오류를 발생시킬 여지가 있으므로<br>
new Date(0)으로 하여 시분초를 일치시켜주었다. (new Date(0) == Thu Jan 01 1970 09:00:00 GMT+0900 (대한민국 표준시))<br>

이 후 setFullYear를 이용하여 start와 end의 날짜를 설정해준다. start와 end는 1월을 기준으로 2018-01-01, 2018-02-01로 각각 생성이 된다.<br>
end는  end.setFullYear(today.getFullYear(), today.getMonth() + 1, 1); 과 같이 설정해주어 2018-02-01 값이 된다.<br>
이 후 while(start < end)를 통해 2월 1일 전 일인 1월 31일까지 처리가 된다.<br>
str를 start 날짜의 년월일을 받아 2018-01-01 과 같은 형식으로 선언해주었다.<br>
그리고 results[str] = {}; 로 results[str]을 초기화를 시켜주었고<br>
results[str]["OK"] = 0; results[str]["NO"] = 0; 로 OK와 NO를 받을 오브젝트 프로퍼티를 초기화 해주었다.<br>
이 후 start.setTime(start.getTime() + 86400000); 작업으로 하루 씩 더해준다. 86400000는 하루를 밀리초로 환산한 값이다.<br>
이 후 for문으로 데이터의 갯수만큼 반복을 하며 results 오브젝트에 1을 더해주게 된다.<br>
그리고 events 라는 오브젝트 배열을 생성해주고 fullCalendar 문서에 정의된 형식에 따라 데이터를 넣어주었다.<br>
https://fullcalendar.io/docs/event_data/events_array/<br>

```
$('#calendar').fullCalendar({
    events: [
        {
            title  : 'event1',
            start  : '2010-01-01'
        },
```
문서에 정의된 배열형태로의 이벤트는 위와 같다. <br>

여기서 for(var date in results) 루프를 반복하며 results 오브젝트에 있는 데이터를 events 오브젝트 배열에 다음과 같이 push 해주었다. <br>
```
events.push({
        title: 'OK : ' + results[date]['OK'],
        color : '#ffffff',
        textColor : '#000000',
        start: date
      });
```

title은 표시될 이름으로 OK와 NO의 갯수를 표현해주기 위해 title: 'OK : ' + results[date]['OK'] 와 같이 해주었다. <br>
그리고 start(날짜) 값은 for문의 date값을 지정해주었다.<br>
이와 같은 작업으로 문서에 정의된 형식에 맞게 event 오브젝트 배열을 만들어주었고 그대로 fullCalendar 함수에 만들어준 event 오브젝트를 대입하여<br>
날짜별로 데이터들이 뜨도록 만들 수 있었다. 그리고 editable: false 로 해줌으로써 drag event가 발동하지 않도록 해주었다.<br>
이와 같이 javascript를 응용하고 원하는 방식으로 구현하는 것은 javascript를 제대로 이해하고 있어야지 가능하다고 생각이 들었다. <br>
node.js 를 공부를 끝내고 javascript도 다시 공부해야겠다는 생각을 하게 되었다.<br>

(0130)<br>
달력에서 날짜를 클릭했을 때 그 날의 데이터가 모달형식으로 뜨면서 차트 데이터를 보여주는 것<br>
https://getbootstrap.com/docs/4.0/components/modal/<br>

이번 작업은 기간을 정해서 chart 라이브러리를 이용해 보여주었던 자료를 응용하여 만든 것으로<br>

특정 일을 클릭하면 dayClick 이벤트가 실행되면서 특정 일에 대한 date를 서버에 post로 전달하고 서버는<br>

이 데이터를 post로 받아 처리한다. 이 때 데이터를 date를 처리할 때 하루만 지정해서 받는 문법이 mariadb에서는<br>

존재하는 것처럼 보이지 않았다. 그리하여 아래와 같이 하루 전날과 하루 다음 날 사이의 날짜의 날짜를 select하도록 하여<br>

특정 일에 대한 데이터를 쿼리 할 수 있게 하였다.<br>

var sql = 'select result, date_format(time, "%Y-%m-%d") as time from hana where time >= ? and time < DATE_ADD(?, INTERVAL 1 DAY)';

달력에는 기본적으로 그 날에 result 값의 갯수가 표시 되어있다. (OK : 2, NO : 1) 그러나 0개로 표시되는 경우는 데이터가<br>

존재하지 않는 경우 이므로 datas 가 존재하지 않을 때는 [0,1] 형태로 클라이언트에 보내주게 하였다.<br>

만일 데이터가 있다면 daychart라는 클라이언트 페이지에 보내준다.<br>

daychart 페이지는 chart를 표현한 index2 와 거의 유사하나 기간 데이터가 넘어오지 않고 [result,time]이 담긴 date만<br>

넘어오므로 var start = "<%=date[0].time%>"; 이와 같이 받았다.<br>

이 후 results 오브젝트에서 results[start]={}; 와 같이 해주어 results 오브젝트의 start 프로퍼티에 대한 값을 저장할 수 있도록<br>

초기화 해주었고 OK와 NO 데이터를 받을 수 있도록 초기화 해주었다.<br>

이 후 전달된 date 오브젝트의 개수만큼 반복을 하며 results[start][OK or NO] 데이터에 1씩 더해주었고 이를 chart로 표현해주었다.<br>

바 형태로 표시해주었고 색깔은 chart.js 홈페이지를 참고하여 꾸몄다<br>

이번작업은 날짜를 클릭했을 때 그 데이터가 post형식으로 서버로 보내주도록 형식을 꾸며주는 것이 어려웠다.<br>

https://fullcalendar.io/docs/mouse/dayClick/<br>

https://www.w3schools.com/jquery/ajax_post.asp<br>

예시에는 단순히 asp로 보낸다고 되어 있어 잘 이해를 못하였는데, 이는 서버로 데이터를 보낸다는 뜻이다.<br>

나의 경우는 node.js를 이용해 서버를 구현하고 express를 이용한 app.post('/~~~')와 같이 post 및 get방식으로 보내는<br>

데이터를 처리하므로 $.post("/data/daychart", { 로 해주어 클릭하였을 때 해당 날짜에 대한 데이터를 보내줄 수 있었다.<br>

그리고 이를 모달 형태로 뜨도록 하는 것도 어려웠다. 동기에게 도움을 요청하여 모달 형태로 띄워주려고 하였는데<br>

동기도 이를 띄우는데 $(...).modal('show') is not a function 이라는 오류를 직면하면서 계속 해결을 하지 못하였다. <br>

결국 자기가 만든 홈페이지에서 모달 형식을 이용한 html 코드를 그대로 붙여넣으니 위의 오류는 뜨지 않았지만 이제는 모달이 뜨질 않았다.<br>

오류도 안뜨는데 모달이 뜨지 않아서 멘붕이 와있었는데 동기가 bootstrap.min.js 코드를 맨 마지막에 넣으니 modal이 보였다.<br>

이러한 상태에서는 특정 일을 클릭하면 그 날에 대한 데이터가 차트 형식으로 보이나 연달아 일을 클릭하면 이전에 실행된 모달 html 코드와 중복이<br>

되며 겹치는 현상이 일어났다. 이를 해결하기 위해선 독립적인 id를 부여해야지 중복이 되지 않는다는 동기의 조언을 참고하여

동기가 홈페이지에서 사용한 코드를 참고하여 아래와 같이 작성하였다.<br> https://dong-gi.github.io/Study/Java/index.html<br>

```
var graph = new Set();
    var idx = Math.floor((Math.random() * 1000) + 1);
    $(document).ready(function() {
      $('#calendar').fullCalendar({
        dayClick: function(date, jsEvent, view) {
          alert('Clicked on: ' + date.format());
          $.post("/data/daychart", {
              date : date.format()
            },
            function(data) {
              showModal(data,idx);
            });

          $(this).css('background-color', 'red');
        },
        header: {
          left: 'prev,next today',
          center: 'title',
          right: 'month,basicWeek,basicDay'
        },
        defaultDate: (today.getFullYear()) + "-" + pad((today.getMonth() + 1), 2) + "-" + pad(today.getDate(), 2),
        navLinks: true, // can click day/week names to navigate views
        editable: false,
        eventLimit: true, // allow "more" link when too many events
        events: events
      });
    });
    function showModal(data,idx) {
      if(!graph.has(idx)) {
      $("body").append(
        '<div id="graph-modal'+idx+'" class="modal code-modal" tabindex="-1" role="dialog">\
            <div class="modal-dialog modal-dialog-centered modal-lg" role="document">\
                <div class="modal-content">\
                    <div class="modal-header">\
                        <span>\
                            <h2 style="display: inline-block;" class="modal-title">Graph</h2>\
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">\
                                <span aria-hidden="true" style="color: black; font-size: 2em; font-weight: bold;">&times;</span>\
                            </button>\
                        </span>\
                    </div>\
                    <div class="modal-body">\
                        <p>Modal body text goes here.</p>\
                    </div>\
                    <div class="modal-footer">\
                        <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>\
                    </div>\
                </div>\
            </div>\
        </div>');
        graph.add(idx);
      }
       $("div#graph-modal" +idx+ " div.modal-body").html(data);
       $("div#graph-modal"+idx).modal("show");
    }
```

graph라는 set 자료형을 선언하고 idx라는 변수를 1~1000까지 random하게 만들어 이를 modal의 id에 추가하였고 마지막으론 graph set 자료형에<br>

add 해주었다. 그리고 if(!graph.has(idx)) 와 같은 조건을 통해 같은 id가 있는지 검사를 하고 없으면 차트 html를 모달의 body에 append 할 수 있도록 해주었다.<br>

https://www.w3schools.com/jsref/jsref_random.asp<br>

(0201)<br>

이번에는 위에 랜덤을 통해 id를 생성했던 코드를 수정하여 작성하였다.<br>

```
    var graph = new Set();
    $(document).ready(function() {
      $('#calendar').fullCalendar({
          dayClick: function(date, jsEvent, view) {
            if (!graph.has(date.format())) {
              $.post("/data/daychart", {
                  date: date.format()
                },
                function(data) {
                  $("body").append(
                    '<div id="graph-modal' + date.format() +
                    '" class="modal code-modal" tabindex="-1" role="dialog">\
                    <div class="modal-dialog modal-dialog-centered modal-lg" role="document">\
                        <div class="modal-content">\
                            <div class="modal-header">\
                                <span>\
                                    <h2 style="display: inline-block;" class="modal-title">Graph</h2>\
                                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">\
                                        <span aria-hidden="true" style="color: black; font-size: 2em; font-weight: bold;">&times;</span>\
                                    </button>\
                                </span>\
                            </div>\
                            <div class="modal-body">\
                                <p>Modal body text goes here.</p>\
                            </div>\
                            <div class="modal-footer">\
                                <button type="button" class="btn btn-danger" data-dismiss="modal">Close</button>\
                            </div>\
                        </div>\
                    </div>\
                </div>'
                  );
                  graph.add(date.format());
                  $("div#graph-modal" + date.format() + " div.modal-body").html(data);
                  $("div#graph-modal" + date.format() + " div.modal-body canvas").attr('id', 'chart' + date.format());
                  showModal(date.format());
                });
            } else {
              showModal(date.format());
          }
          $(this).css('background-color', 'red');
        },
        header: {
          left: 'prev,next today',
          center: 'title',
          right: 'month,basicWeek,basicDay'
        },
        defaultDate: (today.getFullYear()) + "-" + pad((today.getMonth() + 1), 2) + "-" + pad(today.getDate(), 2),
        navLinks: true, // can click day/week names to navigate views
        editable: false,
        eventLimit: true, // allow "more" link when too many events
        events: events
      });
    });

    function showModal(idx) {
      $("div#graph-modal" + idx).modal("show");
    }
  </script>
```

id를 랜덤함수를 이용하여 생성하는 부분을 지우고 그 대신 클릭한 날짜의 숫자(2018-01-31)을 모달의 id에 덧붙였다.<br>

그리고 이전에는 달력의 날짜를 클릭을 할 때 마다 post가 보내지는 비효율적인 방식으로 작성이 되어 있어서 이 부분을<br>

set 데이터 객체를 만들고 여기에 데이터가 있는지 has 함수를 이용해 확인을 하고 없으면 그 때 post로 데이터를 보내도록<br>

하였다. 또 set 객체를 사용하는 이유는 중복을 없애기 위해서 인데 보통 set 자료형을 생각하면<br>

set = {1,1,1,1,1} 일 경우 set = {1} 과 같이 된다. 여기서 적용할 때는 처음 클릭할 때는 해당 날짜의 데이터를<br>

모달의 바디에 append 하여 보여준다. 이후 같은 날짜를 연속해서 클릭하게 되는 경우에는 이미 이전에 클릭하여<br>

set 데이터 객체에 저장된 자료를 가지고 있으므로 그냥 showModal을 해준다.<br>

이미 이전에 클릭해서 가지고 있으니까 다시 append 할 필요없이 보여주면 되는 것이다.<br>

이 때 else { showModal(data.format()) } 처리를 해주지 않으면 같은 날짜를 연속해서 클릭했을 때 모달창이 뜨지 않기 때문에<br>

이와 같이 처리를 해주었다. 그리고 데이터가 1월에 한정되어 있었고 데이터가 뜨는 것이 현재 시간을 기준으로 그 달의 데이터들만<br>

뜨도록 처리했기 때문에 지난달의 데이터를 볼 수 없었고 오늘과 같이 2월달이 되었을 때 2월달 데이터가 없으니 이전달 데이터를 가져오는데<br>

오류가 떴다. 그리하여 start.setFullYear(today.getFullYear()-1, today.getMonth(), 1); 처럼 getFullYear-1을 해주어 1년 이전의 데이터들도<br>

띄우도록 하니 오류가 없어졌다.<br>
