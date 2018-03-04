# Study

>공부하면서 도움이 되었던 지식들을 모아놓은 저장소입니다.

JSON이란 ?

Data format(more detail information ==> http://egloos.zum.com/killins/v/3013974)<br>

In python, how to check the list data type is empty or not?

권장하는 방법)
``` 
if not seq:
if seq:
```
In python, about operator overloading

http://blog.eairship.kr/287

USB 메모리는 NTFS와 FAT 가운데 뭘로 포맷해야 하나요?

http://it.donga.com/23132/

# 20180213
졸작을 진행하면서 여러 측정값들이 스트링으로 배열(파이썬에선 리스트) 로 저장이 되어 있을 때 각 값들의 개수를 세고 그 중 가장 빈도수가<br>

가장 큰 값을 서버로 전달해주고자 하였다.<br>

빈도수를 세서 딕셔너리에 저장하는 것은 어렵지 않게 하였으나 딕셔너리에서 가장 큰 값을 가진 key만을 추출하는 것이 직접 하기 어려웠다.<br>

해결하기 위해 구글링을 하니 이와 같이 해결하는 것을 알 수 있었다.<br> (https://stackoverflow.com/questions/268272/getting-key-with-maximum-value-in-dictionary)

```
max(stats.keys(), key=(lambda k: stats[k]))
```

또는

```
max(stats, key=stats.get)
```

어떤 원리로 해당 코드들이 딕셔너리에서 가장 큰 값을 가진 key를 반환해주는지에 대해선 이해가 알지못했으나 해당 부분을 구현할 수 있었다.<br>

단 위와 같은 방법들은 한 가지 값만을 리턴한다. 만약 {'a' : 3000, 'b':3000} 과 같이 둘 다 최대값을 가졌을 때는 둘 중 하나만을 리턴한다.<br>

# 20180304

졸작으로 라파와 서버 DB간의 통신을 해주는 와중에 방화벽 문제로 라파에서 서버 DB에 접근 및 접속이 되지 않았다.<br>

이를 해결 하기 위해선 서버에 고정 IP를 할당하고 포트 포워딩을 해주어야 했다.<br>

같은 와이파이를 계속 통신하면 되지만 라파에서도 계속 같은 와이파이를 사용할 수 있으리라는 보장이 없으므로 포트 포워딩은 필수적이었다.<br>

서버 컴퓨터는 교내 와이파이로 인터넷 통신을 하고 있었는데 고정 IP가 아니고 포트가 외부에서 접근할 때 달라질 수 있는<br>

문제점이 있었다.<br>

이로 인해 서버 컴퓨터와 공유기에 유선 랜을 연결하여 고정 IP를 할당해주고<br>

공유기 관리페이지에서 포트 포워딩 또한 허용해주도록 했다.<br>

그리고 라파에서 서버의 DB로 접근할 때의 방법에서도 조언을 받았다. <br>

1. 기존에는 바로 DB에 접속하여 쿼리문을 날려주려고 하였다.<br>

그러나 이와 같은 방법이 보안적으로 취약하다는 지적을 받고<br>

2. 클라이언트 페이지에서 http Request를 서버로 날려 이를 통해 쿼리문을 날려주도록 하는 것이 낫다<br>

는 방법을 또한 착안하였다. 두 가지 방법 모두 시도를 해봐야겠다.<br>
