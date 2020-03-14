---
title: docker常用命令
date: 2020-03-07 19:10:54
tags:
- docker
- 容器

---

#### docker容器开机自动启动

> --restart=always

### idea docker自动构建镜像

pom文件：

```xml

```

```
<build>
    <finalName>${project.artifactId}</finalName>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
        <!-- 跳过单元测试 -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <configuration>
                <skipTests>true</skipTests>
            </configuration>
        </plugin>
        <!--使用docker-maven-plugin插件-->
        <plugin>
            <groupId>com.spotify</groupId>
            <artifactId>docker-maven-plugin</artifactId>
            <version>1.0.0</version>
            <!--将插件绑定在某个phase执行-->
            <executions>
                <execution>
                    <id>build-image</id>
                    <!--用户只需执行mvn package ，就会自动执行mvn docker:build-->
                    <phase>package</phase>
                    <goals>
                        <goal>build</goal>
                    </goals>
                </execution>
            </executions>
            <configuration>
                <!--指定生成的镜像名-->
                <imageName>yuding/${project.artifactId}</imageName>
                <!--指定标签-->
                <imageTags>
                    <imageTag>latest</imageTag>
                </imageTags>
                <!-- 指定 Dockerfile 路径-->
                <dockerDirectory>${project.basedir}</dockerDirectory>
                <!--指定远程 docker api地址-->
                <dockerHost>http://111.229.111.34:2375</dockerHost>
                <!-- 这里是复制 jar 包到 docker 容器指定目录配置 -->
                <resources>
                    <resource>
                        <targetPath>/</targetPath>
                        <!--jar 包所在的路径  此处配置的 即对应 target 目录-->
                        <directory>${project.build.directory}</directory>
                        <!-- 需要包含的 jar包 ，这里对应的是 Dockerfile中添加的文件名　-->
                        <include>${project.build.finalName}.jar</include>
                    </resource>
                </resources>
            </configuration>
        </plugin>

    </plugins>
</build>
```

```

```

