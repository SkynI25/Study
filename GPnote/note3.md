# 20180302

오늘은 캘랜더에서 뜨는 modal의 그래프에 시간만 표시하는대신 시:분:초 형식으로 표시가 되도록 프론트엔드와 백엔드 부분을 수정하였다.<br>

그리고 교수님께서 피드백 주신 것처럼 cm 로 표시하는 대신 %로 값을 변환하여 표시해주었다. 이 때 나누고 곱하다 보니 값이 소수점으로<br>

나와 지저분해져 소수점을 반올림해주는 Math.round(value) 를 사용하였다.<br>

```
Math.round(value);
```