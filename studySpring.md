## spring MVC project 생성시 플러그인 날 경우 해결방법

해결방법은 POM.xml에

```
<dependency>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-resources-plugin</artifactId>
    <version>2.4.3</version>
</dependency>
```

이런식으로 디펜던시를 추가해주면 된다.(현재 날짜 기준으로 최신버전인 3.2.1은 되지 않는다.)

이렇게 작성해준 뒤에, 

1. 프로젝트 우클릭 > Run As > Maven Install
2. 이클립스 프로젝트 탐색기에서 해당 프로젝트 클릭 후 F5(새로고침)
3. 프로젝트 우클릭 > Maven > Update Project 

끝!

출처 : http://jin-study.blogspot.kr/2014/03/maven-maven-plug-in.html
