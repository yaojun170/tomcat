## 源码导入步骤
1. git clone xxx.tomcat
2. git checkout 8.5.x //切换到分支
3. 增加pom文件，见本目录下pom.xml
4. 导入idea

## 启动tomcat
1.启动类是 org.apache.catalina.startup.Bootstrap ，直接运行这个类里面的 main 方法， 需要增加下面vm option
```
-Dcatalina.home=/Users/yaojun/work/devcode/opensources/tomcat
-Dcatalina.base=/Users/yaojun/work/devcode/opensources/tomcat
-Djava.endorsed.dirs=/Users/yaojun/work/devcode/opensources/tomcat/endorsed
-Djava.io.tmpdir=/Users/yaojun/work/devcode/opensources/tomcat/temp
-Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager
-Djava.util.logging.config.file=/Users/yaojun/work/devcode/opensources/tomcat/conf/logging.properties
-Duser.language=en
-Duser.region=US
```

2.启动完成，浏览器访问http://localhost:8080，报500错误，
在 org.apache.catalina.startup.ContextConfig.java 中添加下面这句话
```
context.addServletContainerInitializer(new JasperInitializer(), null);
```

3.部署程序
如果想在这个 Tomcat 中部署程序的话，需要把程序放在 ~/work/devcode/opensources/tomcat\webapps\ROOT ，这个是我自己本地的路径，你们的路径自己做拼接。

## QA
参考:https://my.oschina.net/u/1018146/blog/1524309
