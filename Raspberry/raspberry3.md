## how to reboot linux machine using python?

shell

```
reboot
```

python
```
import os
os.system('reboot')
```
> https://stackoverflow.com/questions/35546497/how-to-shutdown-and-then-reboot-linux-machine-using-python-language-or-shell-scr

<br>

## 파이썬 실행 시에 자동으로 파이썬 파일 실행되도록 하는 방법

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

> http://youagain.tistory.com/5
