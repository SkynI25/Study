# 20180318

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