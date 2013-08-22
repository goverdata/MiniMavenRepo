Refer: https://github.com/sxyx2008/maven-repo

=============================================================================================

使用方法
1 在pom.xml中添加repository

<repositories>
    <repository>
        <id>maven-repo-public-releases</id>
        <url>https://raw.github.com/sxyx2008/maven-repo/master/releases</url>
    </repository>
    <repository>
        <id>maven-repo-public-snapshots</id>
        <url>https://raw.github.com/sxyx2008/maven-repo/master/snapshots</url>
    </repository>
</repositories>

2 在pom.xml添加distributionManagement

<distributionManagement>
    <repository>
        <id>maven-repo-public-releases</id>
        <url>https://raw.github.com/sxyx2008/maven-repo/master/releases</url>
        </repository>
    <snapshotRepository>
        <id>maven-repo-public-snapshots</id>
        <url>https://raw.github.com/sxyx2008/maven-repo/master/snapshots</url>
    </snapshotRepository>
    <!-- 
    <repository>
        <id>nexus-releases</id>
        <url>http://localhost:8081/nexus/content/repositories/releases</url>
        <name>Nexus Releases Repository</name>
    </repository>
    <snapshotRepository>
        <id>nexus-snapshots</id>
        <url>http://localhost:8081/nexus/content/repositories/snapshots</url>
        <name>Nexus Snapshots Repository</name>
    </snapshotRepository>
    -->
</distributionManagement>


3 将maven工程发布到maven-repo/releases/仓库目录下

执行mvn-Dmaven.test.skip=true -DaltDeploymentRepository=maven-repo-public-releases::default::file:E:/developer/maven-repo/releases/ clean deploy
4 将maven工程发布到maven-repo/snapshots/仓库目录下

执行mvn-Dmaven.test.skip=true -DaltDeploymentRepository=maven-repo-public-releases::default::file:E:/developer/maven-repo/snapshots/ clean deploy


5 提交

$> git commit -m "MESSAGE"
$> git push origin master
注:

1 mvn-Dmaven.test.skip=true 为执行时跳过单元测试

2 -DaltDeploymentRepository=maven-repo-public-releases maven-repo-public-releases为pom中配置的repository的id

maven-repo-public-releases为github上maven-repo仓库releases目录的id

maven-repo-public-snapshots为github上maven-repo仓库snapshots目录的id

参考

http://www.ikrady.com/2011/09/github上搭建maven仓库/

http://stackoverflow.com/questions/14013644/hosting-a-maven-repository-on-github

https://github.com/Ekito/maven-repo

https://github.com/sxyx2008/hibernate-search-example/blob/master/pom.xml
