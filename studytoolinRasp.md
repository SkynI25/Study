How to edit rasp file in root directories :<br>

https://elmoslapatop.wordpress.com/2014/01/29/raspberry-pi-cant-open-file-to-write-error-message/<br>

How to set wifi(WPA-EAP, PEAP) in RASP :<br>

http://zelkun.tistory.com/entry/018-Raspberry-Pi-%EB%9D%BC%EC%A6%88%EB%B2%A0%EB%A6%AC-%ED%8C%8C%EC%9D%B4-%ED%95%99%EA%B5%90-WiFi-%EC%82%AC%EC%9A%A9-%EC%84%A4%EC%A0%95-WPA-EAP-PEAP<br>

How to install Raspberry OS :<br>

https://brunch.co.kr/@topasvga/52<br>

# 20180214

설 전까지도 열일!! 아 아니..열졸!!<br>

라즈베리 파이와 초음파 센서를 연결해서 쓰레기통의 높이를 측정하였다.<br>

초음파센서와 라즈베리파이를 연결하여 거리를 측정할 때 참고한 사이트들, 두 개의 사이트 모두 회로도와 코드가 깔끔하게 나와있다.<br>

https://codefooo.gitbooks.io/raspberry-experiments/content/%EC%8B%A4%ED%97%988-%EC%B4%88%EC%9D%8C%ED%8C%8C-%EA%B1%B0%EB%A6%AC-%EC%84%BC%EC%84%9C.html

https://m.blog.naver.com/PostView.nhn?blogId=roboholic84&logNo=220319850312&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F

그리고 라파에서<br>

```
GPIO.output(pin_trigger, GPIO.HIGH) # shoot the signal for 10 us
time.sleep(.00001) # 10 us
GPIO.output(pin_trigger, GPIO.LOW)
```

일 때 sleep(.5)로 하면 1초 마다 찍히는 것을 알 수 있었다.<br>

그리고 센서와 파이 코블러, 저항을 연결할 때 사용해야 할 저항 값을 확인할 때 아래 사이트들을 참고하였다.<br>

http://programfrall.tistory.com/65

https://m.blog.naver.com/PostView.nhn?blogId=ansdbtls4067&logNo=220625603453&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F

이 후 라파에서 작성한 파이썬 코드를 실행할 때는 파이썬 코드가 위치한 디렉토리에서 sudo python 파이썬파일.py 을 해주면 된다.<br>

라파에서 파이썬코드 실행하는 방법에 대해 참고한 사이트 :<br>

https://m.blog.naver.com/PostView.nhn?blogId=post_human&logNo=220047845238&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F

# 20180315
만약 라파 OS를 설치했는데 No Wireless Interface Found 로 뜨고 어떤 설정을 변경해도 변함이 없이 연결이 안되면 어떻게 해야할까..<br>

필자의 경우는 그냥 다시 포맷을 하였다(무식한 방법이 최고?)<br>

포맷 후 처음에는 인터넷 연결 리스트가 비어 있으므로<br>

sudo leafpad /etc/wpa_supplicant/wpa_supplicant.conf 로 하여 설정파일에 연결할 wifi 네트워크 정보를 입력해주고<br>

```
service networking restart
```

와 같이 해주어 리스타트를 해주면 해결이 되었다.<br>

그리고 PEAP 방식의 wifi 를 연결해주고자 한다면 무선 wifi 동글을 쓰는게 확실하다.<br>

파이3 wifi와 연결이 되는 공유기가 있고 안되는게 있기 때문에 안되는 경우는 동글을 쓰면 된다고 한다.<br>

경험상으로도 필자가 연결하려는 교내 와이파이도 라파3 만 가지곤 연결이 안되고 무선 동글을 같이 써야지 연결이 되었다(이것만 가지고 몇일을 삽질함 ㅠ)<br>
