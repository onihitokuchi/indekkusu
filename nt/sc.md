```batch
services.msc
```

```sh
sc.exe [<servername>] create [<servicename>] [type= {own | share | kernel | filesys | rec | interact type= {own | share}}] [start= {boot | system | auto | demand | disabled | delayed-auto}] [error= {normal | severe | critical | ignore}] [binpath= <binarypathname>] [group= <loadordergroup>] [tag= {yes | no}] [depend= <dependencies>] [obj= {<accountname> | <objectname>}] [displayname= <displayname>] [password= <password>]
```

```sh
sc create  "<service_name>" binpath= "<binary_path>"
sc stop    "<service_name>"
sc queryex "<service_name>"
sc delete  "<service_name>"
```
