# 20180316

파이썬에서 DB 접속해서 쿼리문 삽입 하는 방법 :

> http://pythonstudy.xyz/python/article/202-MySQL-%EC%BF%BC%EB%A6%AC

라즈베리파이에서 GET Request 보내기 :

> http://dgkim5360.tistory.com/entry/python-requests

> https://www.geeksforgeeks.org/get-post-requests-using-python/

## 20180317

GrovePi를 사용해 초음파센서로 측정을 하기 위해 아래 url에서 지시한 대로 작업을 하였다<br>

https://www.dexterindustries.com/GrovePi/get-started-with-the-grovepi/setting-software/

설치 후 초음파센서로 측정을 하니 알수 없는 TypeError 가 계속 떴다<br>

```
except TypeError as e :
 print(e)
```

로 해줘서 오류를 자세히 보니 int' object has no attribute '__getitem__' 와 같은 오류가 계속 발생하였다<br>

grove pi 제작사인 dexterInd 홈피에 들어가서 보니 이는 펌웨어 업데이트가 되지않아서 발생하는 문제라고 하여 펌웨어 업데이트를 해주었다<br>

https://www.dexterindustries.com/GrovePi/get-started-with-the-grovepi/updating-firmware/

그리고 파이썬에서 requests 란 모듈을 사용하면 get/post request를 보낼 수 있어 해당 모듈을 설치후 사용하였다<br>

처음에 request만 하고 서버에서 response 를 해주지 않아 timing out error 가 계속 떴다 이를 발견하고 res.send('ok') 라고 수정해주니<br>

해결이 되었다<br>

다양한 유저가 요청을 하게 될 때 홈피를 사용하다 서로 엉키지 않을 까라는 생각을 하였다<br>

이는 멀티유저라는 것을 nodejs에서 처리를 해주므로 문제 없이 사용이 가능하다 서버의 포트가 64000이면 사용자들은 해당 포트로 들어와 분기가 된다<br>

각각만의 request는 각각의 response 를 받는다<br>
