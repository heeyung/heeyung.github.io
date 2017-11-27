# rails & windows on ubuntu errors

설치 과정의 힘듦은... 다른 글에서 다시 작업하겠습니다.
여기는 **windows on ubuntu**를 사용하면서 겪었던 뻘짓을 정리해보겠습니다.

### mysql error

```shell
Mysql2::Error (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)):
```

이런 에러가 수도 없이 많이 납니다. 

해결 방법은 여러가지가 있는데 일단 윈도우에 있는 mysql을 종료해줘야 합니다. 
~~저는 귀찮아서 아예 삭제했습니다.~~

그 이후에도 컴퓨터를 종료했다가 다시 작업을 하려고 하면 오류가 다시 납니다. 
이 경우는 mysql을 start 해줘야 합니다.

```shell
sudo service mysql start
```

