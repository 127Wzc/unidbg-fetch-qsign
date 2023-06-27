# unidbg-fetch-qsign

获取QQSign参数通过Unidbg，开放HTTP API。

# 部署方法

- 系统安装jdk或者jre，版本1.8或以上(仅1.0.3及更高版本，老版本要求jdk11)。如果报错找不到类，请尝试1.8或略靠近1.8的版本

- 解压后cd到解压目录，执行以下命令启动程序。<br>
```shell
bash bin/unidbg-fetch-qsign --port=8080  --count=1 --library=txlib\8.9.63
```
- 注意：你需要手动从apk安装包的`lib/arm64-v8a`目录中提取出[libfekit.so](txlib%2F8.9.63%2Flibfekit.so)、[libQSec.so](txlib%2F8.9.63%2FlibQSec.so)文件并存放至一个文件夹，然后使用`--library`指定该文件夹的`绝对路径`，结构例如：
> - your_dir<br>
>     - libfekit.so<br>
>     - libQSec.so<br>

> --library=`/home/your_dir`

 - --port=你的端口
 - --count=unidbg实例数量
 - --library=存放核心so文件的文件夹绝对路径

# 使用API

### 原始energy

```kotlin
# http://127.0.0.1:8080/custom_energy?salt=[SALT HEX]&data=[DATA]
```

### sign

```kotlin
# http://127.0.0.1:8080/sign?uin=[UIN]&qua=V1_AND_SQ_8.9.63_4188_HDBM_T&cmd=[CMD]&seq=[SEQ]&buffer=[BUFFER]
```

### 登录包energy(tlv544)

下面这个只是个例子

```kotlin
# http://127.0.0.1:8080/energy?&version=6.0.0.2534&uin=1234567&guid=ABCDABCDABCDABCDABCDABCDABCDABCD&data=810_f
```