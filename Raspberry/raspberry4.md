## 0429

라즈베리파이에서 부팅시 파이썬 파일 자동으로 실행시키는 방법 :

커맨드 창에서

```
sudo crontab -e
```
를 입력한다 이후 nano 편집기를 선택해서 crontab 파일의 맨 밑으로 이동, 실행시키고자 하는 파일의 위치와 이름을 아래와 같이 입력

```
@reboot sudo python /home/pi/Desktop/pyprog/pytest.py
```

출처 : https://www.dexterindustries.com/howto/auto-run-python-programs-on-the-raspberry-pi/


  SELECT sensordata.* FROM (
  	SELECT MAX(x.id) as id, x.garbageid
  	FROM sensordata x
  		JOIN (SELECT DISTINCT garbageid FROM sensordata) y
  		ON y.garbageid = x.garbageid
  	GROUP BY x.garbageid
  ) t, sensordata
  WHERE t.id = sensordata.id
