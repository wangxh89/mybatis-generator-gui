mybatis-generator-gui
==============

fork自   https://github.com/astarring/mybatis-generator-gui


### 为了符合我的要求，修改内容如下
* MybatisGeneratorBridge.java  context.addProperty("javaFileEncoding", "UTF-8");强制生成文件格式为UTF-8

* MybatisGeneratorBridge.java Context context = new Context(ModelType.FLAT); context.setTargetRuntime("MyBatis3Simple"); 采用FLAT、MyBatis3Simple模式

### 要求
本工具由于使用了Java 8的众多特性，所以要求 JRE或者JDK 8.0以上版本，对于JDK版本还没有升级的童鞋表示歉意。

### 自助构建
    git clone https://github.com/wangxh89/mybatis-generator-gui
    cd mybatis-generator-gui
    mvn jfx:jar

    cd target/jfx/app/

    "c:\Program Files\Java\jdk1.8.0_91\bin\java.exe" -jar mybatis-generator-gui.jar

* Eclipse or IntelliJ IDEA中启动, 找到MainUI类并运行就可以了


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
