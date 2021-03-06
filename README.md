- 记录亲自趟过的各个大厂前端面试题

## 考察点

1. 技术基础
2. 项目深度 ×
3. 产品思维 ×
4. 技术深度与广度

## 阿里面试回顾

### 第一次面试

#### 技术一面与笔试

面试时长 2 小时，笔试时长 1 小时。

技术方面问到： EventLoop, 闭包
项目方面问到： Electron 项目，详细说了单聊，群聊已读未读的实现。Gatsby 服务端状态与首屏前端状态如何对接？

#### 技术二面

技术方面：

1. fs.readFile 异步执行的时机？ ×
2. generator 的实现原理 x （闭包与状态交叠的循环语句）
3. http3 x
4. websocket 如何启动？ socket 是什么？（进程间通信协议）
5. socker 与 http2 差异
6. JIT （编译优化策略，对编译结果按照热度进行缓存）
7. webpack 中 loader 和 plugin 的差异
8. webp 格式，更好的文件压缩

工程方面：

1. SSR 框架的选型原有？（社区繁荣，契合团队现有技术栈，开发效率高）
2. why electron? (跨平台跨操作系统，一套代码 B、C 端同时运行，内嵌 Browser，web 开发可参与)
3. 如何更好的抽离业务 Card?（对不想管业务透明化，环境抽离，基础设施打包提供，简洁的工程项目结构）

##### 技术三面与 HR 面

部门主管与 HR 同时进行面试，主管问到从工作当中的得到的收获?  
HR 问到目前的薪资水平？跳槽的初衷？

#### 反思

1. 不要提自己不熟悉的点
2. 约面试前根据面试时长提前安排要讲的侧重点，时间短时，不要长篇大论讲细节

### 第二次面试

#### 技术一面与笔试

技术方面： 原型链，浏览器从输入 url 到页面加载完的可优化点
笔试： 第一次笔试侧重于简单的算法，此次侧重于对所有技术栈的掌握深度

#### 技术二面

主要考察对于项目（export pdf）的认识，前端功能涉及的前后端知识点(pdf server 实现，server route 的实现)，每个功能的细节（pdf link 是否加密，如何加密），背后原理与选型原因。  
项目难点，项目中的漏洞（限制用户操作是否合理），以及对于产品本身的思考（是否关注用户数据的变化及其带来的价值），细节设计的出发点，有没有考虑过设计本身的问题。

## 总结

技术：

基础 （10%） —— 原型链，闭包，EventLoop,diff  
深度 （20%） —— generator 原理,readFile 时间点,socket 和 websocket  
广度 （10%） —— http3, 图片压缩技术，JIT

项目：

难点 （30%） —— 考察参与度，是否深度思考过功能设计，技术选型思维，架构思路  
产品 （30%） —— 对产品设计的思考，对产品整个链路的关注度，对产品漏洞的分析

## 汇总

1. 技术基础方面留意实现原理，如 diff,generator，浏览器渲染原理
2. 技术广度方面关注 JIT,WebAssembly
3. 项目难点，呈现迭代性思维，对功能的 **逐步优化与改进** ，对涉及到的前后端(**Node**)内容的认识。
4. 产品方面，对于功能的思考，难点在功能设计上的漏洞？功能实现是否到极致（如统计最准确的首屏时间）？
5. 技术选型与架构思维。
6. 可附带工作流管理，团队管理的认识与总结。
7. 做一些后端项目。（error monitor, r2v）

### 第四次面试

#### 技术一面

1. redux 原理，store 切分绑定
2. react-router 原理与 history 模式
3. axios interceptor ？如何保证从 request 拦截到发送请求到接收响应到 response 拦截的次序 ?
4. https，三次握手过程？ssl 加密算法？通过非对称加密来加密传输对内容加密的对称加密公钥
5. webpack loader 是什么？怎么写？写过 plugin 吗？ 写过 cli 吗？  
   问：写 cli 有什么特别的地方？  
   答：1. 运行时不同；2. 面向用户不通 3. 可虑方便性 4. 预留扩展
6. 讲讲项目 error-monitor  
   问：为什么不用 mysql 库？这个在性能上会好写，sql 比较优化
7. 提问：面试表现有那里不足？
   答：回答精炼一些

#### 技术二面

1. React Hooks 不同，增益？
2. Redux 和 Hooks 状态管理的对比？
   回答：在于管理模块的体量，Redux 比较适用于大中型模块，Hooks 适用于小型模块
3. React 和 Vue 源码看过吗？
   回答：Redux, React-Redux 源码简述
4. Webpack 有深入使用过吗？
   回答：讲述到了 Error-Monitor 项目当中，source-map 部分
5. 其他后端项目？
   回答：PDF server
6. 个人性格是怎样的？
7. 有没有在别人认为方案无效或得到答案时依然持续验证自己的猜想？
8. 技术规划是什么样的？

### 第五次面试

#### 技术一面

1. error-monitor

问题：错误有做批量上传吗？批量上传时要考虑什么问题？

```md
1. 数据压缩，避免冗余
2. 用户信息可以通过 token 替代
3. 缓存时间不宜过长或过短
4. 存储量需要进行限制
```

问题：浏览器插件的错误，会被捕捉到吗？

```md
1. 操作工具栏的插件不会被捕捉
2. 注入页面的脚本会被捕捉到
```

问题：用户关闭浏览器，错误还没有上报，怎么处理？

```md
1. 可以通过 localStorage 缓存，下次打开浏览器进行上报
```

问题：捕捉到的错误，有多少能被处理？

```md
大部分包含有效信息，能够被处理，小部分需要结合业务场景和额外信息来定位
```

问题：pdf server 上传 HTML string 会携带脚本进去吗？脚本会执行吗？

```md
上传 HTMl 时会过滤脚本。  
puppeteer 通过打开页签来导出 PDF，会加载脚本
```

问题：前端的优化思路

```md
```

问题：canvas 和 svg 的对比及适用场景？

问题：babel 插件怎么设计？

```md
babel 架构
```

问题：比较擅长哪个方向？

```md
运维，需求设计，研发，架构，团队管理都有参与，比较适合于中后台，倾向于效率工具开发。
```
