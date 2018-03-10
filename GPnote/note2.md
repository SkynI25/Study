# 20180301

오늘은 많은 것을 하였다.

sw test 에 안가고 랩실에서 작업한 보람이 있었다 ㅎㅎ

1. 라즈베리파이와 아두이노 연동을 함

2. map 부분에서 좌표 및 경로 부분을 프론트엔드에서 백엔드로 옮겨주는 작업을 함

3. 백엔드에서 sql문을 짜서 최근 데이터만 읽어오게 함

4. 서버에 nodejs 및 mariadb 를 설치해줌

5. 서버에서 bind address 를 해제해주고 외부에서 3306 포트로 접속할 수 있게 해주었음

먼저 라즈베리파이에서 아두이노와 연동해주는 것은 <br>

라파와 아두이노를 USB 케이블로 연결해줬고<br>

아두이노를 라파에 설치해주고<br>

Grove Ultrasonic Ranger 홈피에서 라이브러리를 다운받아 라파의 아두이노에 넣어주었다.<br>

이 후 Grove Ultrasonic Ranger 와 연결하여 측정을 실행하였을 때 Serial Monitor에 값이 잘 뜨는 것을 확인하였다.<br>

그리고 Serial Monitor 에 뜨는 값을 라파에 전달해주기 위해 pySerial 이라는 모듈을 설치하였다.<br>

여기까진 아래 싸이트를 참고하였다.<br>

https://kocoafab.cc/tutorial/view/305<br>

Monitor에 뜨는 값을 라파에 전송해주는 것이 까다로웠다. 일단 read 함수를 통해 센서 값을 읽는데 여기에 센서 값과 같이<br>

'\r', '\n' ("carriage return, newline")값이 같이 포함되어 들어왔다. Monitor에 뜨는 값들은 항상 저 두개의 변수를 동반하는 것 같다.<br>

이를 처리해주는 것과 포트를 연결해준 뒤 종료하고 버퍼를 매번 비워주는 수행을 해야한다 는 것을 구글링을 보며 알았다.<br>

왜 안되는지는 알겠지만 이를 어떻게 해결해줄까 하고 구글링을 한 결과..<br>

아래와 같이 멋진 코드를 찾았다.<br>

(https://www.raspberrypi.org/forums/viewtopic.php?p=814387#p814387 참고)<br>

몇가지 예외사항을 처리해주니 정제된 값을 리스트에 담을 수 있었다. 그러나<br>

SerialException: device reports readiness to read but returned no data (device disconnected or multiple access on port?)<br>

과 같은 오류가 발생했을 때는 Exception 에러가 발생되면서 멈춰버린다. 이를 해결해줄 필요가 있다.<br>

이외에도 처음에 pySerial 을 가이드에 따라 설치를 할 때는 serial 의 inputflush() 부분에서 오류가 발생하였고 이는 업데이트를 하며 함수명이 변경된<br>

문제라 보았다. 그런데 수정을 해줘도 실행이 잘 안되었다..그래서 pySerial 최신 버전의 0.1 낮은 버전을 다운받아 설치를 해주고<br>

serial. 에서 ctrl + space 를 눌러주니 자동생성 창이 뜨는데<br>

inputflush() 의 바뀐 함수명 대신 inputflush 이 떴다.. 아무튼 이 함수를 사용하고 실행을 하니 다시 잘 되었다.<br>

다른 백엔드 부분에서 수정된 것은 javascript 폴더부분에 작성하겠다.
