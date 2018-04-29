## 라즈베리파이에서 부팅시 파이썬 파일 자동으로 실행시키는 방법 :

1.

커맨드 창에서

```
sudo crontab -e
```
를 입력한다 이후 nano 편집기를 선택해서 crontab 파일의 맨 밑으로 이동, 실행시키고자 하는 파일의 위치와 이름을 아래와 같이 입력

```
@reboot sudo python /home/pi/Desktop/pyprog/pytest.py
```

출처 : https://www.dexterindustries.com/howto/auto-run-python-programs-on-the-raspberry-pi/

2.

command 창에서 /home/pi/.profile을 연다

```
sudo leafpad /home/pi/.profile
```

그리고 맨 마지막 줄에 자신이 실행되길 원하는 bash 명령을 입력한다

```
(sleep 10 && /usr/bin/python /home/pi/myscript.py)&
```

&& 은 앞의 명령을 끝낸 후 뒤의 명령을 실행하고

&   은 앞의 명령을 백그라운드에서 실행하고 그 다음 명령을 같이 실행한다.

10초를 sleep 한 후 파이썬 명령을 내리는 이유는 bash명령이 부팅 후에 실행되는 것이 아니라, 부팅 도중에 동시에 실행 된다.

따라서 파이썬 스크립트가 경우에 따라 제대로 실행되지 않는 결과가 나타날 수 있기 때문에 10초를 sleep 후에 파이썬 코드를 실행 시킨다.
