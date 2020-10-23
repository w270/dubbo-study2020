# 说明
dubbo-admin是打好包的，默认连接zookeeper是127.0.0.1:2181,如果zookeeper不是本地安装，则需要重新打包即可
启动命令：dubbo-admin，直接java -jar dubbo-admin***.jar执行

监控中心项目 dubbo-monitor 启动时保错
原因：8080端口号被占用，是因为zookeeper版本不同，内置了jetty占用了8080，而monitor中心启动也需要jetty，也是8080端口
解决：修改zookeeper配置文件，添加admin.serverPort=8888或修改monitor的配置文件dubbo.jetty.port=8080端口。
启动：assembly.bin下的start.bat
