# 20180301

기존의 contents 부분의 코드

```
  var contents = '<div class="wrap" style="width: 250px; padding: 7px">' +
      '    <div class="info">' +
      '        <div class="title">' +
      '            쓰레기통 : one' +
      '        </div>' +
      '        <div class="body">' +
      '            <div class="desc">' +
      '                <div class="ellipsis">최근 적재량 : 70%</div>' +
      '                <div class="jibun ellipsis">시간 : 2018-03-09 14:19:08%</div>' +
      '                <form action="/data/statistics/device" method="post">\
                         <input type="text" name="name" value="one" hidden>\
                         <input type="submit" value="상세정보">\
                       </form>' +
      '            </div>' +
      '        </div>' +
      '    </div>' +
      '</div>';
```

를 다음과 같이 바꿔주었다.


```
    // 마커를 표시할 위치와 내용을 가지고 있는 객체 배열입니다
    var positions = [];

    <% for(var i = 0; i < result.length; i++) {%>
       positions.push({
         content: '<div class="wrap" style="width: 250px; padding: 7px">' +
           '    <div class="info">' +
           '        <div class="title">' +
           '            쓰레기통 : <%= result[i].title %>' +
           '        </div>' +
           '        <div class="body">' +
           '            <div class="desc">' +
           '                <div class="ellipsis">최근 적재량 : <%= result[i].latestHeightPercent %></div>' +
           '                <div class="jibun ellipsis">시간 : <%= result[i].latestTime %></div>' +
           '                <form action="/data/statistics/device" method="post">\
                              <input type="text" name="name" value="one" hidden>\
                              <input type="submit" value="상세정보">\
                            </form>' +
           '            </div>' +
           '        </div>' +
           '    </div>' +
           '</div>',
          title: "<%= result[i].title %>",
          latlng: new daum.maps.LatLng(<%= result[i].lat %>, <%= result[i].lng %>)
       });
    <% } %>
```

그리하여 일일이 프론트엔드에서 마커 코드를 읽어서 출력하는 것이 아니라 서버에서 값을 전달받아 for문을 통해 생성할 수 있도록 바꿔주었다.

서버에선

```
app.get('/location', function(req, res) {
  var sql = `
  SELECT sensordata.* FROM (
  	SELECT MAX(x.id) as id, x.garbageid
  	FROM sensordata x
  		JOIN (SELECT DISTINCT garbageid FROM sensordata) y
  		ON y.garbageid = x.garbageid
  	GROUP BY x.garbageid
  ) t, sensordata
  WHERE t.id = sensordata.id
  `;

  conn.query(sql, function(err, datas) {
    if (err) {
      console.log(err);
      res.status(500).send('Internal Server Error');
    } else {
      console.log(datas)

      var result = [
        {
          latestHeightPercent: 70,
          latestTime: "2018-03-09 14:19:08",
          title: '공학1관 쓰레기통',
          lat: 36.765797,
          lng: 127.281271
        },
        {
          latestHeightPercent: 70,
          latestTime: "2018-03-09 14:19:08",
          title: '인문경영관 쓰레기통',
          lat: 36.765220,
          lng: 127.281771
        },
        {
          latestHeightPercent: 50,
          latestTime: "2018-03-09 14:19:08",
          title: '담헌 쓰레기통',
          lat: 36.765937,
          lng: 127.282200
        }
      ];

      res.render('map', {
        // datas: datas,
        // devices: device,
        dates: ['', ''],
        result: result
      });
    }
  });
});
```

와 같이 작성해주었고

```
`
  SELECT sensordata.* FROM (
  	SELECT MAX(x.id) as id, x.garbageid
  	FROM sensordata x
  		JOIN (SELECT DISTINCT garbageid FROM sensordata) y
  		ON y.garbageid = x.garbageid
  	GROUP BY x.garbageid
  ) t, sensordata
  WHERE t.id = sensordata.id
  `
```
부분을 통해서 DB에 있는 가장 최근 값(테이블의 가장 맨 밑에 있는 데이터)을 가져온다.

그리고

```
      var result = [
        {
          latestHeightPercent: 70,
          latestTime: "2018-03-09 14:19:08",
          title: '공학1관 쓰레기통',
          lat: 36.765797,
          lng: 127.281271
        },
        {
          latestHeightPercent: 70,
          latestTime: "2018-03-09 14:19:08",
          title: '인문경영관 쓰레기통',
          lat: 36.765220,
          lng: 127.281771
        },
        {
          latestHeightPercent: 50,
          latestTime: "2018-03-09 14:19:08",
          title: '담헌 쓰레기통',
          lat: 36.765937,
          lng: 127.282200
        }
      ];
```

같이 배열을 선언하였고 배열 값을 프론트엔드에 넘겨준다.

```
latestHeightPercent: 70,
latestTime: "2018-03-09 14:19:08",
title: '공학1관 쓰레기통',
```

과 같은 부분은 sql 쿼리를 처리하면서 받아온 datas를 통해 lastestHeightPercent = datas.height, latestTime = datas.time 과 같이
해줌으로서 DB의 값을 받아 넘겨줄 수 있다.
