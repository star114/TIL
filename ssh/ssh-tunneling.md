# ssh-tunneling

```
$ ssh 터널링 접속 아이디@터널링서버 IP -p 22 -N -L 10555:실제 접속하고싶은 IP:22
```

이렇게 작성을 하시면 실제 터널링을 열어주게 된 것이다.

사용된 옵션 :

* -p [number] : number 포트번호로 접속한다.
* -N : 원격 쉘을 실행시키지 않고 접속만 유지한다.
* -L [로컬포트번호:호스트:호스트포트번호] : 로컬 포트번호로 listen 소켓을 열고 들어오는 패킷을 원격지에서 호스트:호스트포트번호로 전송한다.

그런다음 새로운 터미널에서 이렇게 하면 터널링에 접속이 된다!

```
$ ssh (실제 접속하고싶은 IP)에서 사용될 ID@127.0.0.1 -p 10555
```
