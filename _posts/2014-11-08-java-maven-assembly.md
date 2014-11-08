---
layout: post
keywords: maven-assembly-plugin
description: 介绍使用maven-assembly插件构建一个完成的发布包
title: "使用maven-assembly插件构建完整的发布包"
categories: [java]
tags: [maven,assembly]
---
{% include codepiano/setup %}

在日常java工程开发中，经常使用的打包方式是：打成jar包、web工程打成war包、脚本直接运行的完整的发布包。前2种利用mvn直接发布，这里介绍一下利用maven的assembly插件构建一个完成的发布包，他的目标是：一个发布包，放到服务器上，解压后，直接执行脚本。

再通过一张图看看我们最终的程序目录结构。

<img src="/image/20141108-1@2x.png" />

这张图主要是4个目录，logs目录是执行程序后，日志输出时自动生成的，其他的三个目录，是自动构建的

{% highlight bash lineno %}
bin
conf 
lib
logs #日志输出时自动生成的
{% endhighlight %}

直接看看pom.xml文件中maven-assembly插件的配置，主要是指定assemble具体的文件位置。

{% highlight xml %}
<plugin>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <appendAssemblyId>false</appendAssemblyId>
        <descriptors>
            <descriptor>src/main/assemble/package.xml</descriptor><!-- 这里是具体配置文件的位置 -->
        </descriptors>
    </configuration>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal><!-- 只运行一次 -->  
            </goals>
        </execution>
    </executions>
</plugin>
{% endhighlight %}

再看看src/main/assemble/package.xml的配置

{% highlight xml %}
<assembly xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/assembly-1.0.0.xsd">
    <id>maven-assembly-plugin-sample</id>
    <formats>
        <format>zip</format><!-- 文件类型。支持：zip;gz;tar;tar.gz;tar.bz2 -->
    </formats>
    <includeBaseDirectory>true</includeBaseDirectory><!-- 压缩包是否包含项目本身的文件夹 -->
    <fileSets>
        <fileSet>
            <directory>src/main/resources</directory><!-- 将项目中的文件输出到发布包的目录。这里是将resources目录下的配置文件输出到conf目录下 -->
            <outputDirectory>/conf</outputDirectory>
        </fileSet>
        <fileSet>
            <directory>src/main/bin</directory><!-- 这里放的是执行脚本 -->
            <outputDirectory>/bin</outputDirectory>
        </fileSet>
    </fileSets>
    <dependencySets>
        <dependencySet><!-- 将依赖的jar输出到lib目录下 -->
            <outputDirectory>lib</outputDirectory>
            <scope>compile</scope>
        </dependencySet>
    </dependencySets>
</assembly>

{% endhighlight %}

再看看整个项目的结构，更加直观。

<img src="/image/20141108-1@2x.png" />

到这里，我们最基本的目标就达到了，assembly插件更多的功能可以去详细的学习。

再把一个比较通用的执行脚本也贴上，完整的sample项目可以作为简单项目的模板了。

{% highlight bash lineanchors %}
#!/bin/bash
#设置环境变量
. /etc/profile
. ~/.bash_profile

MY_ROOT=$(cd "$(dirname "$0")"; pwd)
echo $MY_ROOT
cd $MY_ROOT

JAVA_OPTS="$JAVA_OPTS -Drun_dir=$MY_ROOT"
JAVA_OPTS="$JAVA_OPTS -Xss256k -Xms1024m -Xmx1024m -Xss256k"
JAVA_OPTS="$JAVA_OPTS -XX:PermSize=128m -XX:MaxPermSize=128m"
JAVA_OPTS="$JAVA_OPTS -XX:+DisableExplicitGC -XX:ParallelGCThreads=16 -XX:+CMSClassUnloadingEnabled -XX:+UseConcMarkSweepGC -XX:+UseParNewGC"
JAVA_OPTS="$JAVA_OPTS -XX:CMSFullGCsBeforeCompaction=5 -XX:CMSInitiatingOccupancyFraction=80 -XX:MaxTenuringThreshold=15 "
#JAVA_OPTS="$JAVA_OPTS -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintSafepointStatistics -XX:+PrintTenuringDistribution -XX:+PrintHeapAtGC -Xloggc:./gc.log "
JAVA_OPTS="$JAVA_OPTS -Dclient.enczoding.override=UTF-8 -Dfile.encoding=UTF-8 -Duser.language=zh -Duser.region=CN"
JAVA_OPTS="$JAVA_OPTS -Djava.ext.dirs=../lib -Djava.library.path=../lib -cp ../conf/"

echo $JAVA_OPTS

java $JAVA_OPTS com.jihaoxian.sample.MavenAssembly $@ &

{% endhighlight %}


最后把整个项目的源码贴上，github地址：[maven-assembly-plugin-sample](https://github.com/aiter/maven-assembly-plugin-sample)


