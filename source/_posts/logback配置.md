---
title: logoback日志文件注释
top: false
cover: false
toc: true
summary: logoback配置文件
categories: 其他
tags: 测试
abbrlink: 13522
date: 2021-02-21 19:12:41
img:
password:
---

## 看个视频呀
<iframe src="//player.bilibili.com/player.html?aid=80664494&bvid=BV1CJ411W7zk&cid=138050520&page=1" 
	style="width: 640px; height: 430px; max-width: 100%"
	scrolling="no" 
	border="0" 
	frameborder="no" 
	framespacing="0" 
	allowfullscreen="true">
</iframe>

## 配置文件

```xml
<configuration>
	<contextName>SpringBootDrugLogbacK</contextName>
	<!--设置系统日志放置路径，可为绝对路径，也可为相对路径,我这里是放到D盘-->
    <property name="LOG_PATH" value="D:/" />
    <!--<property name="LOG_PATH" value="./" />-->
    <!--设置系统日志目录-->
    <property name="APPDIR" value="log" />
    <!--设置系统日志放置项目目录，可不配置-->
    <property name="PROJECTDIR" value="drug" />

    <!-- 日志记录器，日期滚动记录 -->
    <appender name="error" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 正在记录的日志文件的路径及文件名 -->
        <!--<file>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/log_error.log</file>-->
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 日志文件的路径，例如今天是2017-09-21日志，当前写的日志文件路径为file节点指定，可以将此文件与file指定文件路径设置为不同路径，从而将当前日志文件或归档日志文件置不同的目录。
            	而2017-09-21的日志文件在由fileNamePattern指定。%d{yyyy-MM-dd}指定日期格式，%i指定索引 -->
            <fileNamePattern>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/error/log-error-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!-- 除按日志记录之外，还配置了日志文件不能超过2M，若超过2M，日志文件会以索引0开始， 命名日志文件，例如log-error-2017-09-21.0.log -->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>10MB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <!-- 追加方式记录日志 -->
        <append>true</append>
        <!-- 日志文件的格式 -->
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>==**error**==%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%t] %logger Line:%-3L - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!-- 此日志文件只记录error级别的 -->
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>error</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <!-- 日志记录器，日期滚动记录 -->
    <appender name="debug" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 正在记录的日志文件的路径及文件名 -->
        <!--<file>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/log_debug.log</file>-->
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 归档的日志文件的路径，例如今天是2017-09-21日志，当前写的日志文件路径为file节点指定，可以将此文件与file指定文件路径设置为不同路径，从而将当前日志文件或归档日志文件置不同的目录。
           		 而2017-09-21的日志文件在由fileNamePattern指定。%d{yyyy-MM-dd}指定日期格式，%i指定索引 -->
            <fileNamePattern>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/debug/log-debug-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!-- 除按日志记录之外，还配置了日志文件不能超过2M，若超过2M，日志文件会以索引0开始，命名日志文件，例如log-error-2017-09-21.0.log -->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>50KB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <!-- 追加方式记录日志 -->
        <append>true</append>
        <!-- 日志文件的格式 -->
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>==**debug**==%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%t] %logger Line:%-3L - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!-- 此日志文件只记录debug级别的 -->
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>debug</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <!-- 日志记录器，日期滚动记录 -->
    <appender name="info" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 正在记录的日志文件的路径及文件名 -->
       <!-- <file>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/log_info.log</file>-->
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 归档的日志文件的路径，例如今天是2017-09-21日志，当前写的日志文件路径为file节点指定，可以将此文件与file指定文件路径设置为不同路径，从而将当前日志文件或归档日志文件置不同的目录。
            			而2017-09-21的日志文件在由fileNamePattern指定。%d{yyyy-MM-dd}指定日期格式，%i指定索引 -->
            <fileNamePattern>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/info/log-info-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!-- 除按日志记录之外，还配置了日志文件不能超过2M，若超过2M，日志文件会以索引0开始，  命名日志文件，例如log-error-2017-09-21.0.log -->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>10MB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <!-- 追加方式记录日志 -->
        <append>true</append>
        <!-- 日志文件的格式 -->
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>==**info**==%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%t] %logger Line:%-3L - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!-- 此日志文件只记录info级别的 -->
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>info</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <!-- 日志记录器，日期滚动记录 -->
    <appender name="mybatis" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 正在记录的日志文件的路径及文件名 -->
        <!--<file>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/log_mybatis.log</file>-->
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 归档的日志文件的路径，例如今天是2017-09-21日志，当前写的日志文件路径为file节点指定，可以将此文件与file指定文件路径设置为不同路径，从而将当前日志文件或归档日志文件置不同的目录。
            			而2017-09-21的日志文件在由fileNamePattern指定。%d{yyyy-MM-dd}指定日期格式，%i指定索引 -->
            <fileNamePattern>${LOG_PATH}/${APPDIR}/${PROJECTDIR}/mybatis/log-mybatis-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!-- 除按日志记录之外，还配置了日志文件不能超过10M，若超过10M，日志文件会以索引0开始，  命名日志文件，例如log-mybatis-2017-09-21.0.log -->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>10MB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <!-- 追加方式记录日志 -->
        <append>true</append>
        <!-- 日志文件的格式 -->
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>==**mybatis**==%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%t] %logger Line:%-3L - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!-- 此日志文件只记录debug级别的 -->
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <!--   <level>trace</level> -->
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <!-- 为单独的包配置日志级别，若root的级别大于此级别， 此处级别也会输出   应用场景：生产环境一般不会将日志级别设置为trace或debug，但是为详细的记录SQL语句的情况， 可将mybatis的级别设置为debug -->
    <!-- 配置mybatis打印SQL日志，按包所在目录配置 -->
    <logger name="com.hd.wms.dao" level="debug" additivity="true">
        <appender-ref ref="mybatis" />
    </logger>

 <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <!--encoder 默认配置为PatternLayoutEncoder-->
        <encoder>
            <pattern>===%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%t] %logger Line:%-3L - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!--此日志appender是为开发使用，只配置最底级别，控制台输出的日志级别是大于或等于此级别的日志信息-->
        <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
            <level>debug</level>
        </filter>
    </appender>

  <!-- 生产环境下，将此级别配置为适合的级别，以免日志文件太多或影响程序性能 -->
    <logger name="com.hd" level="debug" additivity="false">
        <appender-ref ref="error" />
        <appender-ref ref="debug" />
        <appender-ref ref="info" />
          <!-- 生产环境将请 stdout 去掉 -->
        <appender-ref ref="STDOUT" />
    </logger>
    <root level="debug">
        <!-- 生产环境将请 stdout 去掉 -->
         <appender-ref ref="STDOUT" />
    </root>


    <logger name="javax.activation" level="WARN"/>
    <logger name="javax.mail" level="WARN"/>
</configuration>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!--  输入文件的根目录  -->
    <property name="log.path" value="logs"/>
    <!-- 日志输出格式 -->
    <property name="log.pattern"
              value="%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} [%method,%line] : %msg%n"/>

    <!-- 控制台输出 -->
    <appender name="console" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>${log.pattern}</pattern>
        </encoder>
    </appender>

    <!-- 系统日志输出 -->
    <appender name="file_info" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>${log.path}/info.log</file>
        <!-- 循环政策：基于时间创建日志文件 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 日志文件名格式 -->
            <fileNamePattern>${log.path}/info.%d{yyyy-MM-dd}.log</fileNamePattern>
            <!-- 日志最大的历史 30天 -->
            <maxHistory>30</maxHistory>
        </rollingPolicy>
        <encoder>
            <pattern>${log.pattern}</pattern>
        </encoder>
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <!-- 过滤的级别 -->
            <level>INFO</level>
            <!-- 匹配时的操作：接收（记录） -->
            <onMatch>ACCEPT</onMatch>
            <!-- 不匹配时的操作：拒绝（不记录） -->
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <appender name="file_error" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <file>${log.path}/error.log</file>
        <!-- 循环政策：基于时间创建日志文件 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 日志文件名格式 -->
            <fileNamePattern>${log.path}/error.%d{yyyy-MM-dd}.log</fileNamePattern>
            <!-- 日志最大的历史 30天 -->
            <maxHistory>30</maxHistory>
        </rollingPolicy>
        <encoder>
            <pattern>${log.pattern}</pattern>
        </encoder>
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <!-- 过滤的级别 -->
            <level>ERROR</level>
            <!-- 匹配时的操作：接收（记录） -->
            <onMatch>ACCEPT</onMatch>
            <!-- 不匹配时的操作：拒绝（不记录） -->
            <onMismatch>DENY</onMismatch>
        </filter>
    </appender>

    <!-- 系统模块日志级别控制  -->
    <logger name="com.blockchain" level="info"/>
    <!-- Spring日志级别控制  -->
    <logger name="org.springframework" level="warn"/>

    <!-- 系统操作日志 -->
    <root level="info">
        <appender-ref ref="console"/>
    </root>

    <!-- 记录文件 -->
    <root level="info">
        <appender-ref ref="file_info"/>
    </root>
    <root level="error">
        <appender-ref ref="file_error"/>
    </root>
</configuration>
```

```yaml
#日志配置路径
logging:
  config: classpath:logback/logback.xml
```
## 结尾

感谢阅读。

