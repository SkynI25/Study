printf로 출력할 때의 서식 :<br>

http://shaeod.tistory.com/283<br>

비주얼스튜디오 코드 재 정렬 :<br>

Ctrl + K, F<br>

atoi(), itoa() 함수에 관련한 정보 :<br>

http://norux.me/24<br>

int to string :<br>

https://stackoverflow.com/questions/5590381/easiest-way-to-convert-int-to-string-in-c<br>

difference between char s[] and char *s : <br>

https://stackoverflow.com/questions/1704407/what-is-the-difference-between-char-s-and-char-s<br>

std::string을 const char* 나 char*로 바꾸는 방법 :<br>

http://hashcode.co.kr/questions/88/stdstring%EC%9D%84-const-char%EB%82%98-char%EB%A1%9C-%EB%B0%94%EA%BE%B8%EB%8A%94-%EB%B0%A9%EB%B2%95<br>

sizeof를 이용하여 배열을 크기 만큼 출력하는 방법: <br>

for(int i=0; i<sizeof(arr)/sizeof(int); i++) 과 같이 sizeof를 배열 앞에 cast 해주고 이를 다시 sizeof(int)로 나눠준다. 이때 arr는 int형 배열이다.<br>

visual studio 에서 소수점을 출력할 때 <br>

```
printf("%lf", 1/2)
```

이런식으로 정수를 나눈 것을 출력하려고 하면 0이 출력된다. <br>

이를 올바르게 출력시키려면

```
printf("%lf", (double)1 / 2);
```

와 같이 자료형을 앞에 붙여 cast 해주거나

```
printf("%lf", 1.0/2.0)
```

과 같이 소수점을 붙여줘야 한다.
