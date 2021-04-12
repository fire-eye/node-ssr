# 简介
  > nodejs搭建多页面服务端渲染
  * 技术点
    1. Koa入门
    2. koa脚手架 ：koa-generator的用法
      * 安装生成器
      * 创建hello World
      * 目录解析
      * 路由
      * 模板引擎
      * 代码调试
      * 项目测试
    3. koa核心:中间件

  > 项目源码 git clone https://github.com/fire-eye/node-ssr.git
  
  * 运行
    - npm i 
    - npm start

-----
  
## 一、 现代服务端渲染的由来
  > 服务端渲染概念： 是指，浏览器向服务器发出请求页面，服务端将准备好的模板和数据组装成完整的HTML返回给浏览器展示
  * 1、前端后端分离
    > 早在七八年前，几乎所有网站都使用 ASP、Java、PHP做后端渲染，随着网络的加快，客户端性能提高以及js本身的性能提高，我们开始往客户端增加更多的功能逻辑和交互，前端不再是简单的html+css更多的是交互，前端页在这是从后端分离出来「前后端正式分家」

  * 2、客户端渲染
    > 随着ajax技术的普及以及前端框架的崛起(jq、Angular、React、Vue) 框架的崛起，开始转向了前端渲染,使用 JS 来渲染页面大部分内容达到局部刷新的作用
    * 优势
      - 局部刷新，用户体验优
      - 富交互 
      - 节约服务器成本
    * 缺点
      - 不利于SEO(爬虫无法爬取ajax)请求回来的数据
      - 受浏览器性能限制、增加手机端的耗电
      - 首屏渲染需要等js运行才能展示数据

  * 3、现在服务端渲染
    > 为了解决上面客户端渲染的缺点，然前后端分离后必不能合，如果要把前后端部门合并，拆掉的肯定是前端部门
    * 现在服务端渲染的特点
      - 前端开发人员编写html+css模板
      - node中间服务负责前端模板和后台数据的组合
      - 数据依然由java等前服务端语言提供
    * 优势
      - 前后端分工明确
      - SEO问题解决

  * 4、前、后端渲染相关讨论参考
    - [知乎问答：为什么现在又流行服务器端渲染html](https://blog.csdn.net/b9q8e64lo6mm/article/details/79418969)
    - [精读前后端渲染之争](https://github.com/camsong/blog/issues/8)
    - [服务端渲染 vs 客户端渲染](https://jkchao.cn/article/5a11155fb520d115154c8fa1)

---

## 二、 项目开始
> 确保你安装node

  ### 第一步 koa脚手架
  > 目标: 创建node服务,通过浏览器访问,返回'hello node!'(html页面其实就是一串字符串)

    
