# complier


```shell

odb -d mysql --generate-query --generate-schema employee.hxx

```



not work
```shell

g++ -c person-odb.cxx c++ -DDATABASE_MYSQL -c driver.cxx c++ -o driver driver.o person-odb.o -lodb-mysql -lodb

```


```shell

g++ -c person-odb.cxx
g++ -DDATABASE_MYSQL -c driver.cxx
g++ -o driver driver.o person-odb.o -lodb-mysql -lodb
```


```shell
scp person.sql root@60.205.225.118:~

mysql --user=root --password=5Edidada --database=odb_test < person.sql

./driver --user root --password 5Edidada --database odb_test --host 60.205.225.118
```

执行结果

```shell

testodbcomposite --user root --password 5Edidada --database odb_test --host 60.205.225.118
Mr Joe Dirt <joe@example.com>
  nickname: Squeaky
  alias: Anthony Clean
  phone 1: 555 5555
  phone 2: 666 6666
Mr Joe Dirt

```
