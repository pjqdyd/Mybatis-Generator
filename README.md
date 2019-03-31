# Mybatis-Generator
在IDEA中maven插件mybatis-generator的使用

### 注意:

1. 这里在Idea下使用Maven插件mybatis generator来生成
   pojo实体类, dao接口, 以及mapper映射的xml文件

2. 导入项目进Idea后，修改好generatorConfig.xml的生成配置信息后后, 且配置好要生成的表名后, 双击运行maven插件mybatis-genetor:generate
   就可以生成对应的文件了

3. 这些文件就可以拷贝到项目中使用了
```
   (注意:

    1. 在生成的mapper/*.xml文件中,请将实体类的值改为全包名下的，或者直接写实体类的
    如在生成的UserMapper.xml文件中, 将含有"pojo.User"的**type属性值改为"com.pjqdyd.pojo.User"/或"User",
    否则在使用mybatis时会报错找不到实体类**.pojo.User)

    2. 在生成的mapper/*.xml文件中将<mapper namespace="com.pjqdyd.dao.UserMapper">写成全包名

    3. 在使用mybatis时, 如果报错出现无法创建bean/class/sqlSesssionFactor,或者是提示
        Mapped Statements collection already contains value for com.pjqdyd.dao.UserMapper.updateByPrimaryKey,
        可能是因为生成的UserMapper.xml文件里的映射sql操作的语句标签重复生成了, 删除id=updateByPrimaryKey等有重复的标签
        块就行了.
        (可能是多次点击了插件运行生成)


```
(在连接数据库时可能会有错误)
1. mysql 8以上版本的加密用了sha2算法:
    报错caching-sha2-password

解决办法: https://blog.csdn.net/u010026255/article/details/80062153

2. 连接mysql时报错: Unknown system variable 'query_cache_size'

  解决办法: https://www.cnblogs.com/nicknailo/articles/9074804.html
原因是mysql-connector-java的版本还是6.0.6，需要升级版本到8.0.11 ，这个报错就不存在了

3. mysql的时区配置不正确: The server time zone value....

解决办法: https://blog.csdn.net/weixin_39033443/article/details/81711306
Mysql 8 的版本可以: 
在连接数据库的配置上加上参数 ?serverTimezone=GMT%2B8
如: jdbc:mysql://localhost:3306/video?characterEncoding=utf-8&serverTimezone=GMT%2B8&useSSL=false



---
####(我的springboot集成Mybatis使用demo: https://github.com/pjqdyd/Mybatis-demo)
