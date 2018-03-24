## 20180318

라파에서 서버로 값을 보내줄 때<br>

처음에는 key를 날짜로 받아주었지만 날짜 또한 DB에 넣어줘야 하기 때문에 key 는 data라는 string에 count 값을 더한 값을 key로 정해줬다.<br>

파이썬에서 dict 를 json으로 변환해서 보내주려고 하는데 서버에서 제대로 받지를 못한다. ㅠ 왜 때문일까<br>

http://bluese05.tistory.com/37

라파에서 보내주는 값을 서버에서 받아 DB에 저장해주려고 하였다.<br>

이를 위해선 라파에서 보내주는 형식이 dict 이기 때문에 json으로 변환해줘야 했다.<br>

그러나 서버에서 받은 형식을 보면 올바른 json 형태로 오지 않는다.<br>

그리고 중요한 heads up..

node.js 에선 어떻게 thread를 사용하는가?<br>

> single thread, non-blocking I/O Model, 이벤트 기반 비동기 방식.

https://qkraudghgh.github.io/node/2016/10/23/node-async.html

http://www.nextree.co.kr/p7292/

## 20180322

오류제어 성공..ㅠ

파이썬의 requests 모듈을 사용해서 post를 이용하거나 json 으로 변환해 데이터를 보내주는 것은 성공하지 못했다<br>

대신 리스트 형태 [] 에서 튜플 형태 () 로 바꿔줘도 딕셔너리 형태로  잘 들어갔고 서버에서도 받는데도 문제가 없었다<br>

관건은 get 으로 보낼 때 서버에 깨짐없이 전달이 되느냐인데..<br>
이게 왠일..get Req 로 보내고 get Res 로 받는데 이전과 달리 데이터가 깨짐없이 전달되었고 이를 DB에 저장할 수 있기 까지 했다??<br>

인터넷에 나와있는 거처럼 JSON으로 변환해 줄 필요도 없었고 다양한 parameter이 들어가서 post 로 보내주지도 않았고 단순히<br>

dict = { 'data' : ('a', 'b', 'c')} 와 같이 보내주었는데 서버에선 이를 잘 사용하였다..저 a, b, c를 감싸주는 데이터 형태를 리스트에서 튜플로만바꿔줬을 뿐인데 이게 될 줄이야<br>

첨에 데이터가 ' ' 와 같이 하나의 따옴표로만 감싸진 dict 형태라 node.js 에서 이를 사용하지 못했고 "" (쌍따옴표)로 감싸진 JSON 형태로 변환해 사용해주고자 했다. 근데 파이썬의 requests 에서 JSON 으로 보내려면 post로만 보낼 수 없는데 post로 보낼 때마다 빈 값 {} 이 날라와 이를 몇일 간 해결하지 못했다<br>

어제 자기전 requests DOC 를 정독하면서 파이썬 3. 버전에서 돌리면 좋다는 것과 튜플로도 다양한 데이터를 보낼 수 있다는 것을 보고 이를 사용하였는데 바라던대로 문제가 잘 해결되어 기쁘다 ㅎ<br>

그러면서 우리의 프로젝트의 방향에 대해서 다시 생각하게 되었다 나이스한 방법으로 개발하는 것도 좋지만 중요한 것은 하드웨어가 값을 측정해서 서버로 보내주는 것이므로..간단하더라도 동작하는 쪽으로 개발하는 것이 맞겠다고 생각하였다<br>

## 20180324

내 철학은 최소한의 자원을 활용해 최대한의 효율을 뽑아내는 것이다<br>

그래서 10분마다 보내는 것은 꽉 찼을 때의 상태 만이고 꽉 차지 않았을 때는 1시간 마다 한꺼번에 보내주어 에너지를 아끼고자 했다<br>

근데 10000mAh 보조 바테리를 몇 시간 동안 사용하였는데도 1칸 밖에 달지 않았다 ㅋ..<br>

그리고 파이썬에서 dictionary 형태로 {data:['one', '80', '2018-03-24 18:00:00]} 와 같이 보내주는데 서버가 이를 받아 시간 순으로 정렬해 DB에 넣어주고자 했다. 정렬하는 이유는 dict 은 순서가 없기 때문에 {'data2':['one', '80', '2018-03-24 18:00:33], 'data1':['one', '80', '2018-03-24 18:00:00]} 같이 먼저 나타난 데이터 대로 정렬되지 않고 무작위로 값이 들어가 있기 때문이다. 허나 이것도 또한 간단하지 않았다<br>

javascript에서 오브젝트를 시간 순으로 정렬하려면 날짜에 대한 key가 있어야 한다(파이썬의 dict --> json --> javascript 의 오브젝트)
이를 위해 {data:['id': 'one', 'heights' : '80', 'time' : '2018-03-24 18:00:00]} 같이 해주는 것은 오류를 띄우며 제대로 전달이 되지 않았다<br>

결국 수많은 구글링, 정보들은 다 no 쓸모가 되버리고(물론 그 와중에 많은 것을 배웠다) 10분마다 서버로 보내주는 것으로 변경하였다<br>

나는 기술적으로 간단하게 구현한 것이 볼품 없다는 생각에 잡혀있었다. 그래서 뭔가 기술적으로 멋져보이게, 얘기하자면 꾸미는 것에 집중을 했던 경향이 있는 것 같다<br>

다시 생각해보면 그게 필요하지 않는 아집이였달까 오기 였던 것 같다. 필요없진 않지만 결국 간단하게 하는 방향으로 가는 것을 보니 그렇게 깊이 고민하고 열성적으로 해결하려던 모습들이 부질없이 느껴졌다<br>

```
Error: Connection lost: The server closed the connection.
    at Protocol.end (/home/ubuntu/js/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:113:13)
    at Socket.<anonymous> (/home/ubuntu/js/server_side_javascript/node_modules/mysql/lib/Connection.js:109:28)
    at emitNone (events.js:111:20)
    at Socket.emit (events.js:208:7)
    at endReadableNT (_stream_readable.js:1064:12)
    at _combinedTickCallback (internal/process/next_tick.js:138:11)
    at process._tickCallback (internal/process/next_tick.js:180:9)
Program node kitae_mysql.js exited with code 1
```

위의 오류는 DB 와 연결이 끊키기 때문에 발생하는 문제, 아마 nodejs로 웹 서버를 만들어 mysql 과 연결하면 다들 발생하는 문제라고 생각함<br>

해결방법은 연결이 끊키는 오류를 제어하는 코드를 넣는것(말은 쉽다) 아래와 같은 코드를 넣으면 해결이 가능하다<br>

```
var db_config = {
  host: 'localhost',
    user: 'root',
    password: '',
    database: 'example'
};

var connection;

function handleDisconnect() {
  connection = mysql.createConnection(db_config); // Recreate the connection, since
                                                  // the old one cannot be reused.

  connection.connect(function(err) {              // The server is either down
    if(err) {                                     // or restarting (takes a while sometimes).
      console.log('error when connecting to db:', err);
      setTimeout(handleDisconnect, 2000); // We introduce a delay before attempting to reconnect,
    }                                     // to avoid a hot loop, and to allow our node script to
  });                                     // process asynchronous requests in the meantime.
                                          // If you're also serving http, display a 503 error.
  connection.on('error', function(err) {
    console.log('db error', err);
    if(err.code === 'PROTOCOL_CONNECTION_LOST') { // Connection to the MySQL server is usually
      handleDisconnect();                         // lost due to either server restart, or a
    } else {                                      // connnection idle timeout (the wait_timeout
      throw err;                                  // server variable configures this)
    }
  });
}

handleDisconnect();
```

참고 : https://stackoverflow.com/questions/20210522/nodejs-mysql-error-connection-lost-the-server-closed-the-connection
