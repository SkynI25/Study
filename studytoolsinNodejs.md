one of the way to store file path to DB :<br>

https://stackoverflow.com/questions/20208878/storing-images-in-server-using-expressjs<br>

> (20180112)

와...하루동안 삽질했는데 npm 모듈 설치하니까 에러가 해결됬다..

npm install mysql 해주니 해결이 됬다.

nodejs로 mysql을 연결하여 하려하는데 오류가 발생하였다.

success!!
{ Error: ER_ACCESS_DENIED_ERROR: Access denied for user 'hana'@'192.168.0.251' (using password: YES)
    at Handshake.Sequence._packetToError (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Sequence.js:30:14)
    at Handshake.ErrorPacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Handshake.js:67:18)
    at Protocol._parsePacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:197:24)
    at Parser.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Parser.js:62:12)
    at Protocol.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:37:16)
    at Socket.ondata (_stream_readable.js:557:20)
    at emitOne (events.js:101:20)
    at Socket.emit (events.js:191:7)
    at readableAddChunk (_stream_readable.js:178:18)
    at Socket.Readable.push (_stream_readable.js:136:10)
    --------------------
    at Protocol._enqueue (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:110:26)
    at Protocol.handshake (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:42:41)
    at Connection.connect (/opt/server_side_javascript/node_modules/mysql/lib/Connection.js:81:18)
    at Object.<anonymous> (/opt/server_side_javascript/database_mysql.js:8:6)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
    at Function.Module._load (module.js:439:3)
    at Module.runMain (module.js:605:10)
  code: 'ER_ACCESS_DENIED_ERROR',
  errno: 1045,
  sqlState: '28000',
  fatal: true }
tag@tag-desktop:/opt/server_side_javascript$ node database_mysql.js
success!!
{ Error: ER_ACCESS_DENIED_ERROR: Access denied for user 'hana'@'localhost' (using password: YES)
    at Handshake.Sequence._packetToError (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Sequence.js:30:14)
    at Handshake.ErrorPacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/sequences/Handshake.js:67:18)
    at Protocol._parsePacket (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:197:24)
    at Parser.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Parser.js:62:12)
    at Protocol.write (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:37:16)
    at Socket.ondata (_stream_readable.js:557:20)
    at emitOne (events.js:101:20)
    at Socket.emit (events.js:191:7)
    at readableAddChunk (_stream_readable.js:178:18)
    at Socket.Readable.push (_stream_readable.js:136:10)
    --------------------
    at Protocol._enqueue (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:110:26)
    at Protocol.handshake (/opt/server_side_javascript/node_modules/mysql/lib/protocol/Protocol.js:42:41)
    at Connection.connect (/opt/server_side_javascript/node_modules/mysql/lib/Connection.js:81:18)
    at Object.<anonymous> (/opt/server_side_javascript/database_mysql.js:8:6)
    at Module._compile (module.js:571:32)
    at Object.Module._extensions..js (module.js:580:10)
    at Module.load (module.js:488:32)
    at tryModuleLoad (module.js:447:12)
    at Function.Module._load (module.js:439:3)
    at Module.runMain (module.js:605:10)
  code: 'ER_ACCESS_DENIED_ERROR',
  errno: 1045,
  sqlState: '28000',
  fatal: true }

생각해보니 공부를 할 때에도 npm install --save node-mysql 작업을 해주었는데

mariadb 를 설치하니 별개의 npm을 설치해줘야한다는 생각에 저 작업을 하지 않았었다.

당연히 mysql 과 연결하려면 저 모듈을 설치해줘야 한다..설치를 진행하면서 전체적인 과정을 잘 정리하지 못하여 생긴 문제이다.

앞으로는 설치해야하는 모듈들이 많을 때는 체크를 해나가며 단계적으로 해나가도록 해야겠다.

Useful code for developing Node.js :

http://blog.kichul.co.kr/2017/01/27/2017-03-27-node-js-notes/
