mybatis-generator-gui
==============

mybatis-generator-gui是基于[mybatis generator](http://www.mybatis.org/generator/index.html)开发一款界面工具, 本工具可以使你非常容易及快速生成Mybatis的Java POJO文件及数据库Mapping文件。


### 核心特性
* 按照界面步骤轻松生成代码，省去XML繁琐的学习与配置过程
* 保存数据库连接与配置，每次代码生成轻松搞定
* 内置常用插件，比如offset
* 可选的去除掉对版本管理不友好的注释，这样新增或删除字段重新生成的文件比较过来清楚
* 目前仅支持Mysql

### 要求
本工具由于使用了Java 8的众多特性，所以要求 JRE或者JDK 8.0以上版本，对于JDK版本还没有升级的童鞋表示歉意。

### 下载
你可以从本链接下载本工具: https://github.com/wangxh89/mybatis-generator-gui/releases

### 自助构建
    git clone https://github.com/wangxh89/mybatis-generator-gui
    cd mybatis-generator-gui
    mvn jfx:jar
### 启动本软件
* 下载的zip包

解压zip包，如果安装好了JRE或者JDK 8，直接cd至软件目录运行

    java -jar mybatis-generator-gui.jar

* 自助构建


    cd target/jfx/app/

    "c:\Program Files\Java\jdk1.8.0_91\bin\java.exe" -jar mybatis-generator-gui.jar

* Eclipse or IntelliJ IDEA中启动, 找到MainUI类并运行就可以了


### 贡献
目前本工具只是本人项目人使用到了并且觉得非常有用所以把它开源，如果你觉得有用并且想改进本软件，你可以：
* 对于你认为有用的功能，你可以在Issue提，我可以开发的尽量满足
* 对于有Bug的地方，请按如下方式在Issue中提bug
    * 如何重现你的bug，包括你使用的系统，JDK版本，数据库类型及版本
    * 如果有任何的错误截图会更好

### 修改参考配置：
http://blog.csdn.net/isea533/article/details/42102297

generatorConfig.xml:

        <?xml version="1.0" encoding="UTF-8"?>
        <!DOCTYPE generatorConfiguration
          PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
          "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">
        <generatorConfiguration>
        <!-- 数据库驱动-->
            <classPathEntry  location="mysql-connector-java-5.1.38.jar"/>
            <context id="DB2Tables"  targetRuntime="MyBatis3Simple" defaultModelType="flat">
                <property name="beginningDelimiter" value="`"/>
                <property name="endingDelimiter" value="`"/>
                <property name="javaFileEncoding" value="UTF-8"/>
                <commentGenerator >
                    <property name="suppressDate" value="true"/>
                    <!-- 是否去除自动生成的注释 true：是 ： false:否 -->
                    <property name="suppressAllComments" value="true"/>
                </commentGenerator>
                <!--数据库链接URL，用户名、密码 -->
                <jdbcConnection driverClass="com.mysql.jdbc.Driver" connectionURL="jdbc:mysql://localhost/qytstock" userId="root" password="wxh123">
                </jdbcConnection>
                <javaTypeResolver>
                    <property name="forceBigDecimals" value="false"/>
                </javaTypeResolver>
                <!-- 生成模型的包名和位置-->
                <javaModelGenerator targetPackage="test.model" targetProject="src">
                    <property name="enableSubPackages" value="true"/>
                    <property name="trimStrings" value="true"/>
                </javaModelGenerator>
                <!-- 生成映射文件的包名和位置-->
                <sqlMapGenerator targetPackage="test.mapping" targetProject="src">
                    <property name="enableSubPackages" value="true"/>
                </sqlMapGenerator>
                <!-- 生成DAO的包名和位置-->
                <javaClientGenerator type="XMLMAPPER" targetPackage="test.dao" targetProject="src">
                    <property name="enableSubPackages" value="true"/>
                </javaClientGenerator>
                <!-- 要生成哪些表 MyBatis3Simple 可以避免在后面的<table>中逐个进行配置 enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false">-->
                <table tableName="vendor" domainObjectName="Vendor">
                     <generatedKey column="id" sqlStatement="Mysql"/>
                </table>
            </context>
        </generatorConfiguration>
