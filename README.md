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

## 20180213
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


## README 를 작성하는데 도움이 된 블로그

http://codecooking.tistory.com/95

https://techstory.shma.so/art-of-readme-cd19f86b0456

http://brownbears.tistory.com/233
