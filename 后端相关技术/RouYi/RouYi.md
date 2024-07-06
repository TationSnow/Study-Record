# **Rou Yi** 

零代码平台：宜搭、Noohle（怒吼）、简道云

低代码平台：若依 / RuoYi、jeecg-boot、人人开源 / renren-fast

- RuoYi - Vue 是一个JavaEE 轻量级快速开发平台，毫无保留的给个人及企业免费使用
- 基于经典技术组合（Spring Boot、Spring Security、MyBatis、Jwt、Vue、Element）

若依官网：http://ruoyi.vip/



## 后端环境搭建运行

1. 下载 git 代码：通过IDEA下载git源码：https://gitee.com/y_project/RuoYi-Vue.git
2. 初始化工程：初始化工程：IDEA会自动加载Maven包
3. Mysql配置：
   1. 创建数据库 test-ry
   2. 执行若依目录下的SQL语句
   3. 导入数据库 
   4.  在rouyi-admin模块下，修改数据库连接，编辑Resource目录下的Application-druid.yml
4. Redis配置
   1. [Redis安装和基本使用（windows版） - SpongeD - 博客园 (cnblogs.com)](https://www.cnblogs.com/tester-D/p/15958183.html)
   2. [Releases · microsoftarchive/redis (github.com)](https://github.com/microsoftarchive/redis/releases)
   3. 解压后在该目录下进入cmd命令行界面 输入 redis-server.exe redis.windows.conf
5. 启动项目 - rouyi-admin目录下



| 模块名称        | 功能        |
| --------------- | ----------- |
| rouyi-admin     | Web服务入口 |
| rouyi-common    | 通用工具    |
| rouyi-generator | 框架核心    |
| rouyi-generator | 代码生成    |
| rouyi-quartz    | 定时任务    |
| rouyi-system    | 系统模块    |







## 前端环境搭建运行

1. 打开前端工程
   1. 进入项目目录：rouyi-ui
   2. 可选步骤（替换3）更换镜像解决npm下载速度慢的问题：npm install --registry=https://registry.npmmirror.com
2. 安装依赖：npm install
3. 启动部署：npm run dev



跨域问题：若依前端是基于代理转发来解决跨域问题的

vue.config.js中

```js
devServer: {
    host: '0.0.0.0',
    port: port,
    open: true,
    proxy: {
      // detail: https://cli.vuejs.org/config/#devserver-proxy
      [process.env.VUE_APP_BASE_API]: {
        target: `http://localhost:8080`,
        changeOrigin: true,
        pathRewrite: {
            // http://localhost:8080/login
          ['^' + process.env.VUE_APP_BASE_API]: ''
        }
      }
    },
    disableHostCheck: true
  },
```

## 功能列表

| 功能                 | 描述                                                         | 快捷键    |
| -------------------- | ------------------------------------------------------------ | --------- |
| 热部署               | 若依自带了热部署插件，只要没有新文件创建都可以使用           | Ctrl + F9 |
| Spring Security 加密 |                                                              |           |
| MyBatis              | MyBatis提供了嵌套查询功能 |           |



### MyBatis 



1. resultMap 手动封装映射

   1. ```xml
      <resultMap id="映射名称" type="实体类类型">
      	<result property="实体类属性名1" column="数据库查询返回的字段列1" />
      	<result property="实体类属性名2" column="数据库查询返回的字段列2" />
      	<result property="实体类属性名3" column="数据库查询返回的字段列3" />
      	<result property="实体类属性名4" column="数据库查询返回的字段列4" />
      	<result property="实体类属性名5" column="数据库查询返回的字段列5" />
      </resultMap>
      ```

2. association 多对一查询

   1. ```xml
      <resultMap id="映射名称" type="实体类类型">
      	<result property="实体类属性名1" column="数据库查询返回的字段列1" />
      	<result property="实体类属性名2" column="数据库查询返回的字段列2" />
          <association property="实体类属性对象名1" javaType="实体类属性对象类型1" column="要查询的实体类属性对象中的外键属性名1" select="要查询的Mapper接口的全名+方法名">
      </resultMap>
      ```

3. collection 一对多查询

   1. ```XML
      
      ```

手动映射封装：<resulutMap></resultMap>

<association></association>

<collection></collection>



## 二次开发

案例业务需求：饿了吗点餐外卖

### 代码生成

1. 准备二次开发的业务表结构和数据
2. 登录系统（系统工具 - 代码生成 - 导入对应表）
3. 代码生成列表中找到需要的表（可预览-编辑同步删除生成配置）	
4. 点击生产代码会得到一个ruoyi.zip执行sql文件，按照包内目录结构复制到自己的项目中即可





### 代码导入







## 项目迁移	

1. 使用npm或yarn全局安装Vite
2. 项目根目录中，使用npm或yarn添加Vite作为开发依赖
3. 删除与Vue CLI相关的配置文件（如`vue.config.js`）
4. 创建一个新的Vite配置文件（通常是`vite.config.js`）
5. 更改`package.json`中的脚本，以使用Vite命令（如`vite serve`来启动开发服务器）。





## 若依框架修改器（一键修改包名等）

 [若依框架修改器V4-20230425 · Ricky/RuoYi-MT - Gitee.com](https://gitee.com/lpf_project/RuoYi-MT/releases/tag/V4-20230425)





## 若依入门项目 帝可得

1. 后端仓库地址：[dkd-parent: 帝可得后台管理系统 (gitee.com)](https://gitee.com/yudian1991/dkd-parent)
2. 前端仓库地址：[dkd-vue: 帝可得前端 (gitee.com)](https://gitee.com/yudian1991/dkd-vue)
3. Git克隆并初始化后端项目
   1. admin - 修改yml文件
4. MySQL导入与配置
5. 启动Redis与配置
6. 运行后端项目
7. Git克隆并初始化前端项目
8. 安装依赖
9. 运行前端项目





### 区域改造

1. 确定关联查询方案，并编写SQL
2. 创建RegionVo
3. 在RegionMapper和xml文件中添加查询Vo方法和sql
4. 在RegionService接口和实现类中添加查询Vo方法
5. 修改RegionController查询方法
6. 修改前端视图组件 



