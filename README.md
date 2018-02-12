# Study

JSON이란 ?

: Data format(more detail information ->)
http://egloos.zum.com/killins/v/3013974

In python, how to check the list data type is empty or not?

권장하는 방법)
    if not seq:
    if seq:

In python, about operator overloading

http://blog.eairship.kr/287


(20180112)
우분투에 외부 접속을 허용하기 위한 방법 :

https://blog.naver.com/atm007/220109914861

https://blog.naver.com/hwangs88/20165014828

http://abc1211.tistory.com/289

굉장히 잘 설명해놓았다.

우분투 컴퓨터 ip 서버로 접속이 안되는 문제가 있었는데 알고보니 같은 공유기를 사용하고 있는 내부 네트워크에서는  포트 포워딩 까지 해줄 필요가 없었다..그냥 접속이 되는 것이었는데 lael 블로그를 따라 방화벽 설정을 해주니 접속이 안되는 거였다. iptables -F 로 초기화를 해주고 다시 접속을 해보니 잘 되었다.

MySQL 사용자 생성 및 삭제 문법 :

http://damduc.tistory.com/4

http://ourcstory.tistory.com/45

Useful code for developing Node.js :

http://blog.kichul.co.kr/2017/01/27/2017-03-27-node-js-notes/

HTML Table in Jade Templatee :

https://stackoverflow.com/questions/28187290/how-rotate-html-table-using-jade-template-node-express-jade

MySQL 테이블 생성시 DATETIME 타입에 DEFAULT로 현재 시간 입력하기 :

http://jsonobject.tistory.com/122

Useful Homepage UI stuff :

https://semantic-ui.com/modules/dropdown.html#search-dropdown

어제와 오늘 헤매다가 해결한 것들 정리(20180118)

어제는 이미지를 클릭했을 때 그 이미지를 띄우지 못해서 애를 먹었다

이는 app.use(express.static('./')); 에서 기본 경로를 ./(현재 디렉토리)로 설정하면서 해결하였다.

그리고 검색한 자료를 띄우기 에서는

redirect 를 사용하지 않고 검색한 자료로 view2로 render 하여 띄워주었다.

view2의 form에서 'data/list'로 post 방식으로 자료를 보내주고

app.post('/data/list')로 데이터를 받아 입력한 자료를 받아 select * from hana where=?

로 치환자의 값으로 form 에서 보낸 데이터를 받아 select 검색이 되도록 하였다.

Display Calendar by using jQuery :

http://www.nextree.co.kr/p9887/

To hide element in HTML :

<table>
  <tr><th>Test Table</th><tr>
  <tbody style="display:none">
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
    <tr><td>123456789</td><tr>
  </tbody>
</table>

https://stackoverflow.com/questions/6910349/hiding-table-data-using-div-style-displaynone

how to install Ubuntu using USB :

http://sergeswin.com/1178

https://medium.com/ics-lab/%EC%9A%B0%EB%B6%84%ED%88%AC-ubuntu-%EB%A1%9C-%EA%B0%9C%EB%B0%9C%ED%95%98%EA%B8%B0-1-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-%EB%93%80%EC%96%BC%EB%B6%80%ED%8C%85-9964f088c9ac
