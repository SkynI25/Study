# Study

>공부하면서 도움이 되었던 지식들을 모아놓은 저장소입니다.

JSON이란 ?

Data format(more detail information ==> http://egloos.zum.com/killins/v/3013974)<br>

In python, how to check the list data type is empty or not?

권장하는 방법)
``` 
if not seq:
if seq:
```
In python, about operator overloading

http://blog.eairship.kr/287

USB 메모리는 NTFS와 FAT 가운데 뭘로 포맷해야 하나요?

http://it.donga.com/23132/

## 20180213
졸작을 진행하면서 여러 측정값들이 스트링으로 배열(파이썬에선 리스트) 로 저장이 되어 있을 때 각 값들의 개수를 세고 그 중 가장 빈도수가<br>

가장 큰 값을 서버로 전달해주고자 하였다.<br>

빈도수를 세서 딕셔너리에 저장하는 것은 어렵지 않게 하였으나 딕셔너리에서 가장 큰 값을 가진 key만을 추출하는 것이 직접 하기 어려웠다.<br>

해결하기 위해 구글링을 하니 이와 같이 해결하는 것을 알 수 있었다.<br> (https://stackoverflow.com/questions/268272/getting-key-with-maximum-value-in-dictionary)

```
max(stats.keys(), key=(lambda k: stats[k]))
```

또는

```
max(stats, key=stats.get)
```

어떤 원리로 해당 코드들이 딕셔너리에서 가장 큰 값을 가진 key를 반환해주는지에 대해선 이해가 알지못했으나 해당 부분을 구현할 수 있었다.<br>

단 위와 같은 방법들은 한 가지 값만을 리턴한다. 만약 {'a' : 3000, 'b':3000} 과 같이 둘 다 최대값을 가졌을 때는 둘 중 하나만을 리턴한다.<br>


## README 를 작성하는데 도움이 된 블로그

http://codecooking.tistory.com/95

https://techstory.shma.so/art-of-readme-cd19f86b0456

http://brownbears.tistory.com/233

## What Is a Socket?

Normally, a server runs on a specific computer and has a socket that is bound to a specific port number. The server just waits, listening to the socket for a client to make a connection request.

On the client-side: The client knows the hostname of the machine on which the server is running and the port number on which the server is listening. To make a connection request, the client tries to rendezvous with the server on the server's machine and port. The client also needs to identify itself to the server so it binds to a local port number that it will use during this connection. This is usually assigned by the system.

<center><img src="https://docs.oracle.com/javase/tutorial/figures/networking/5connect.gif" width="301" height="73"></center>

If everything goes well, the server accepts the connection. Upon acceptance, the server gets a new socket bound to the same local port and also has its remote endpoint set to the address and port of the client. It needs a new socket so that it can continue to listen to the original socket for connection requests while tending to the needs of the connected client.

<center><img src="https://docs.oracle.com/javase/tutorial/figures/networking/6connect.gif" width="301" height="73"></center>

On the client side, if the connection is accepted, a socket is successfully created and the client can use the socket to communicate with the server.

The client and server can now communicate by writing to or reading from their sockets.

Definition
- A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to.

An endpoint is a combination of an IP address and a port number. Every TCP connection can be uniquely identified by its two endpoints. That way you can have multiple connections between your host and the server.

The java.net package in the Java platform provides a class, Socket, that implements one side of a two-way connection between your Java program and another program on the network. The Socket class sits on top of a platform-dependent implementation, hiding the details of any particular system from your Java program. By using the java.net.Socket class instead of relying on native code, your Java programs can communicate over the network in a platform-independent fashion.

Additionally, java.net includes the ServerSocket class, which implements a socket that servers can use to listen for and accept connections to clients. This lesson shows you how to use the Socket and ServerSocket classes.

If you are trying to connect to the Web, the URL class and related classes (URLConnection, URLEncoder) are probably more appropriate than the socket classes. In fact, URLs are a relatively high-level connection to the Web and use sockets as part of the underlying implementation. See Working with URLs for information about connecting to the Web via URLs<br>

출처 : https://docs.oracle.com/javase/tutorial/networking/sockets/definition.html

그나저나..왜 이미지 중앙 배치가 적용이 안되는거야 ㅎ ㅡ.ㅡ<br>

https://nachoi.github.io/studynote/2017/11/23/Github-resize-image.html


