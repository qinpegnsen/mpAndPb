# 小程序学习笔记（小程序官方开发文档 起步 中的 小程序开封指南 （5,6,7，8章暂时没看） ）

# 小程序为啥受欢迎
* 组件 小程序内置了很多组件地图 比如 轮播图啊 摄像头啊 button按钮的开放能力等 ，省的我们自己写
* api  小程序基友微信，有很多api可以调用 微信支付，转发， 基本的微信客户 等
* 云开发 不需要后台了 前端单独搞定

## 学习注意事项
- 组件学习的时候有在开发者工具打开，如果可以打开就打开学习，或者新建项目粘贴复制过去
- 如果打不开，那么就说明必须得，报错，那就说明必须得在真机才能预览。比如说 page-meta 页面属性节点配置

## 微信开放平台？
> 企业去注册，开发软件，供行业使用，为移动应用、PC端网站、公众号第三方平台（为各行各业公众号运营者提供服务）的开发（这句话来自官网，请开发者注意 1， https://developers.weixin.qq.com/doc/offiaccount/Getting_Started/Overview.html）
> 个人没有办法注册，必须得以企业来注册，最后一步就是完善开发者资料（开发者资料里面首先就是企业的信息）。我用的钉钉的邮箱（qinpengsen4756@dingtalk.com）注册到这一步走不下去了。

## 微信开放平台和微信公众平台都是干啥的？
> 微信公众平台（https://mp.weixin.qq.com/）（里面是一些后台的配置），也可以注册公众号，大众登录的，官方乘作  小程序后台
> 微信开放平台https://open.weixin.qq.com/  是为行业提供解决方案的，其中的资源就是微信官方文档中的开发平台  具体包括
    1. 移动应用开发  接入微信开放平台，让你的移动应用支持微信分享、微信收藏和微信支付。（android ios wp） wp 及时windosphone
    2. 网站应用开发   接入微信开放平台，让你的网站支持使用微信帐号来登录      
    3. 公众帐号开发接入微信开放平台公众帐号开发，为亿万微信用户提供轻便的服务   就是微信公众平台 说白了就是公众号
    4. 第三方平台开发 成为第三方平台，为广大公众号提供运营服务和行业解决方案    通俗地讲就是利用微信公众平台给出的开发文档，经过后期的开发，形成一套功能相对完善的系统，可以给提供增值服务的计算机程序。  比如说 有赞
    5. 还有一些资料的下载 

## 小程序  开放能力  开放接口啥意思？
> 我不清楚，有的人说是微信本身的接口(我在社区提问有人回答的)，其实不重要，h5网页调用的是公众号的接口（因为只有公众号才需要h5网页）
- 后来我想是：开放能力  开放接口 都是微信依据自身特色开发的新的功能（功能是新的概念，比如：api 开放接口的 登录，支付，授权，微信运动等，像路由，缓存，画布，媒体等 都是 已经有的概念）

## 小程序和h5 的区别？
> 小程序的运行环境是微信（app），能够调动微信的很多功能，比如 转发，获取通信状态

## 小程序的通讯模型是啥？
> 小程序的渲染层(wxml,wxss)和逻辑层(js)分别由2个线程管理：渲染层的界面使用了WebView 进行渲染；逻辑层采用JsCore线程运行JS脚本。一个小程序存在多个界面，所以渲染层存在多个WebView线程，这两个线程的通信会经由微信客户端（下文中也会采用Native来代指微信客户端）做中转，逻辑层发送网络请求也经由Native转发
https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/framework.html#%E6%B8%B2%E6%9F%93%E5%B1%82%E5%92%8C%E9%80%BB%E8%BE%91%E5%B1%82

## 小程序的josn的key必须得双引号并且不能是undefined
## wxml  必须得有结束标签
## wxml2种引用？
> import引用  引用template 
> include引用 引用除了template 和 wxs 之外的所有 

## wxs 是是啥？跟小程序中的js一样吗？
- wxs 也是属于渲染层的，因为你只能在wxml里面使用
- wxs是专门用于wxml页面的，如果你有在页面中使用js脚本的需求可以使用，但是wxs是不能被其他js文件引用的。语法跟js不一样，一般很少用到。https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxs/

## wxml 和 wxss 简写？
> wxml: WeiXin Markup Language    wxss:WeiXin Style Sheets

## wxss 的单位？
> rpx 会根据屏幕的不同，做不同的编译适配（小程序编译后，rpx会做一次px换算）

## wxss 引用？
>  在CSS中：@import url('./test_0.css'),这种方法在请求上不会把test_0.css合并到index.css中，也就是请求index.css的时候，会多一个test_0.css的请求。
>  wxss 引用 : @import './test_0.wxss'

## 小程序中的 js 是由什么组成的？为什么小程序用jquery不能操作dom https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000a8806958588cb00862bd5851c0a
> 小程序js=ECMAScript+小程序框架+小程序Api   (没有组件，组件是在wxml中，不是js中)
> 浏览器中的js=ECMAScript+Bom+Dom
> NOdejs=ECMAScript+npm+native
> 同浏览器中的JavaScript 相比没有 BOM 以及 DOM 对象，所以类似 JQuery、Zepto这种浏览器类库是无法在小程序中运行起来的，同样的缺少 Native 模块和NPM包管理的机制，小程序中无法加载原生库，也无法直接使用大部分的 NPM 包。

## 小程序运行的平台和有啥不同？
> iOS平台，包括iOS9、iOS10、iOS11             Android平台                        小程序IDE
> OS9和iOS10 所使用的运行环境并没有完全的兼容到 ECMAScript 6 标准，所以最好不用es6 或者是用 然后 转化成es5（现在在新建项目的时候默认勾选了）   https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000a8806958588cb00862bd5851c0a

## 小程序的js模块化是啥？
> 浏览器中，所有 JavaScript 是在运行在同一个作用域下的，定义的参数或者方法可以被后续加载的脚本访问或者改写。同浏览器不同，小程序中可以将任何一个JavaScript 文件作为一个模块，通过module.exports 或者 exports 对外暴露接口。
## 小程序js的执行顺序？
> 总的来说是从上到下，首先执行app.js 的代码从上到下，如果遇到require先执行requie里面的js，然后在往下执行
> app.js 执行以后会依次执行 开发者在 app.json 中定义的 pages 的顺序，逐一执行相对应的js
## js作用域？
> 小程序的脚本的作用域同 NodeJS 更为相似。在文件中声明的变量和函数只在该文件中有效，不同的文件中可以声明相同名字的变量和函数，不会互相影响.
> 当需要使用全局变量的时，通过使用全局函数 getApp() 获取全局的实例，并设置相关属性值，来达到设置全局变量的目的
## 宿主是啥（native）？
> 宿主是微信客户端 简称 native
## 运行的环境？
> 小程序的运行环境分成渲染层和逻辑层，第2章提到过 WXML 模板和 WXSS 样式工作在渲染层（wxs也是工作在渲染层），JS 脚本工作在逻辑层
## 渲染层和逻辑层都是干啥的，渲染的基本原理？
> 逻辑层产生 ，处理，数据
> 渲染层呈现数据
> 基本原理：逻辑层通过 Page 实例的 setData 方法传递数据到渲染层。
## 跳转到其他页面时当前页面的定时器会清楚吗?
> 所有页面的脚本逻辑都跑在同一个JsCore线程，页面使用setTimeout或者setInterval的定时器，然后跳转到其他页面时，这些定时器并没有被清除，需要开发者自己在页面离开的时候进行清理。navigateTo 的话当前页面还在栈中没有销毁，所以回调函数还在，如果是navigateBack和redirectTo应该就不在了，没试过。

## 页面的组成和那些是必须的？
> 一个页面是分三部分组成：界面、配置和逻辑。界面由WXML文件和WXSS文件来负责描述，配置由JSON文件进行描述，页面逻辑则是由JS脚本文件负责。
> 一个页面的文件需要放置在同一个目录下，其中WXML文件和JS文件是必须存在的，JSON和WXSS文件是可选的。

## 小程序的首页在哪里定义的？
> 根目录app.json中默认pages字段的第一个页面路径为小程序的首页。

## app（小程序）构造器4个参数都是啥？
> onLaunch  当小程序初始化完成时，会触发 onLaunch（全局只触发一次）
> onShow	Function	当小程序启动，或从后台进入前台显示，会触发 onShow
> onHide	Function	当小程序从前台进入后台，会触发 onHide
> onError	Function	当小程序发生脚本错误，或者 API 调用失败时，会触发 onError 并带上错误信息

## 页面构造器有几参数？
> 总共以后10个参数 ，5个回调是Page实例的生命周期函数，4个回调是页面的用户行为，还有data属性绑定的初始数据

## 生命周期的顺序？
> onLoad-- onShow---onReady(onReady触发时，表示页面已经准备妥当，在逻辑层就可以和视图层进行交互了)。还有这两个生命周期函数onHide，onUnload 总共5个。

## onUnload函数触发的条件？
> 当前页面使用wx.redirectTo或wx.navigateBack返回到其他页时，当前页面会被微信客户端销毁回收，此时Page构造器参数所定义的onUnload方法会被调用。

## 页面用户的行为有哪些？（页面跟用户的手指滑动的额上下方向是一致得）
> 下拉刷新 onPullDownRefresh
> 上拉触底 onReachBottom
> 页面滚动 onPageScroll
> 用户转发 onShareAppMessage

## 页面的跳转和路由？页面栈[ pageA, pageB, pageC ]
> 页面在文档编写的时候是最多10层，不知道现在是几层？
> 使用 wx.navigateTo({ url: 'pageD' }) 可以往当前页面栈多推入一个 pageD，此时页面栈变成 [ pageA, pageB, pageC, pageD ]。
> 使用 wx.navigateBack() 可以退出当前页面栈的最顶上页面，此时页面栈变成 [ pageA, pageB, pageC ]。
> 使用wx.redirectTo({ url: 'pageE' }) 是替换当前页变成pageE，此时页面栈变成 [ pageA, pageB, pageE ]，当页面栈到达10层没法再新增的时候，往往就是使用redirectTo这个API进行页面跳转。

## wx.navigateTo,wx.redirectTo和wx.switchTab的区别？
> wx.navigateTo和wx.redirectTo只能打开非TabBar页面，wx.switchTab只能打开Tabbar页面。
> 使用wx.switchTab({ url: 'pageF' })，此时原来的页面栈会被清空（除了已经声明为Tabbar页pageA外其他页面会被销毁），然后会切到pageF所在的tab页面，页面栈变成 [ pageF ]，此时点击Tab1切回到pageA时，pageA不会再触发onLoad，因为pageA没有被销毁。

## 如何重启小程序?
> 我们还可以使用 wx. reLaunch({ url: 'pageH' }) 重启小程序，并且打开pageH，此时页面栈为 [ pageH ]

## 事件对象属性currentTarget和target的区别？这跟js中是一样的
> currentTarget 是绑定的事件的组件
> target 是触发事件的源头组件

## 事件绑定与冒泡捕获？
> 先捕获后冒泡   跟原生js一样(因为捕获从上到下，上是视图层，肯定是视图层传下来)
> bindtap和capture-bind的含义分别代表事件的冒泡阶段和捕获阶段
> capture-catch:事件绑定不会事件传播，可以中断捕获阶段和取消冒泡阶段
> catchtap :阻止事件冒泡
> 列举的事件类型之外的其他组件自定义事件，如无特殊声明都是非冒泡事件，如<form/>的submit事件，<input/>的input事件，<scroll-view/>的scroll事件。

## 兼容微信版本的处理？https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html
> 通过判断API是否存在做兼容
> 小程序还提供了wx.canIUse这个API，用于判断接口或者组件在当前宿主环境是否可用
> 还可以通过在小程序管理后台设置“基础库最低版本设置”来达到不向前兼容的目的   ---  微信公众号平台-设置-基本设置  

### appid 是啥？
> appid （小程序可以理解为一个app）是小程序在微信中的唯一标识，AppId（小程序ID）和AppSecret（小程序密钥）是微信鉴别开发者身份的重要信息（可以登录后在开发-开发设置看到（开发者秘钥https://mp.weixin.qq.com/wxamp/devprofile/get_profile?token=1342486239&lang=zh_CN ）），AppId是公开信息，泄露AppId不会带来安全风险，但是AppSecret是开发者的隐私数据不应该泄露

### openid和session_key是啥？
> openid （是当前⽤户在⼩程序⾥的唯⼀标识，open 打开的意思的嘛，只有用户才打开，所以就是用户的id）就是前文一直提到的微信用户id，可以用这个id来区分不同的微信用户。session_key则是微信服务器给开发者服务器颁发的身份凭证(是开发者服务器和微信服务器的会话密钥)，开发者可以用session_key请求微信服务器其他接口来获取一些其他信息，由此可以看到，session_key不应该泄露或者下发到小程序前端。

### SessionId 是啥？
> session_key是开发者服务器和微信服务器的会话密钥，同样道理，开发者服务器和开发者的小程序应该也有会话密钥，在本书中我们就把它称之为SessionId

## wxs 是啥？
> WXS（WeiXin Script）是小程序的一套脚本语言，结合 WXML，可以构建出页面的结构。就是小程序的js

## 小程序的hidden
> 小程序的if 直接删除节点，hidden该表样式 display

## 小程序的block是啥？
> 小程序中的block，相当于vue中的temolate ，不出现在页面中，处理多个的时候使用

# 小程序实战笔记
  
## 小程序跨段框架的比较

 ui-app >taro >其他  https://www.cnblogs.com/hupingzui/p/10760545.html 这篇文章也是这结论

 1. ui-app 是hbuilder 开发 ，还有专门的编辑器，用vue开发的
 2. taro 是京东开发，用的的reactive 开发的

## 为什么说的跨段框架有时候在查看性能的时候比原生的小程序还快呢？
> 一般来讲，都是编译到小程序的源码，多了一步应该会比较慢的，但是原因如下
1. 小程序的setdate 多次重复渲染
2. 跨端框架的话会进行性diff比较，然后在setDate，所以有的时候比较快

## 微信登录   https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000cc48f96c5989b0086ddc7e56c0a

## 微信支付的业务流程

## 微信的客服消息（设计到内网穿透 和 哈希算法（ sha1 sha256等））
* 微信有自动回复，但是自动回复都比较简单，如果遇到复杂的提问怎么版？这就需要用微信客客服消息了
* 用户的提问首先会给微信服务器，如果太复杂微信服务器可以给我们的服务器，我们的服务器处理完以后再返回给微信服务器，然后微信服务在回答
* 这里其中有一个问题是，微信服务器是外网的，但是我们的服务器是在内网的（在开发的时候），外网是访问不内网的，这就需要内网穿透（钉钉有，花生壳，ngrok等）

## 网页授权（采用oAuth2.0认证方式）有啥用？
>  网页授权就是为了获取用户的信息（其他授权）或者是是用户的openid（静默授权）
>  获取到用户的信息或者是openid后可以调用 菜单栏 用户管理里面的接口

## 授权的两种方式
> 静默授权  **snsapi_base为scope发起的网页授权，是用来获取进入页面的用户的openid的**，并且是静默授权并自动跳转到回调页的。用户感知的就是直接进入了回调页（往往是业务页面）
> **以snsapi_userinfo为scope发起的网页授权，是用来获取用户的基本信息的**。但这种授权需要用户手动同意，并且由于用户同意过，所以无须关注，就可在授权后获取该用户的基本信息。

## 小程序的场景值是什么？
> 就是进入小程序的方式

## 小程序模板消息在哪里可以看到？
> 服务通知，微信搜索服务通知  可以看到跟订阅中心一样，所有的东西都在这个服务通知的文件夹里面

## 小程序消息卡片是啥？
> 通过转发给别人或者群里生成的卡片

## 小程序原生组件是啥意思？
> 小程序的原生组件的意思是，小程序从头到尾自己开发的组件并且运行在natvie上，比如map ，video 等，，大部分的组件都是对html的封装，看下面就知道
- 原生运行在native上 https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/framework.html#%E6%B8%B2%E6%9F%93%E5%B1%82%E5%92%8C%E9%80%BB%E8%BE%91%E5%B1%82
- 非原生运行在webview上
（https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/code.html#WXML-%E6%A8%A1%E6%9D%BF）（往往写 HTML 的时候，经常会用到的标签是 div, p, span，开发者在写一个页面的时候可以根据这些基础的标签组合出不一样的组件，例如日历、弹窗等等。换个思路，既然大家都需要这些组件，为什么我们不能把这些常用的组件包装起来，大大提高我们的开发效率。），

## 小程序插件和第三方组件有啥不同？
- 小程序插件，在后台找插件，然后通过json引入插件
- 第三方组件，是基于npm 的，可以用npm 安装使用   https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/trdparty.html

## UnionID是啥？有啥用？
- 定义：同一用户，对同一个微信开放平台下的不同应用，UnionID是相同的
- 作用：比如一个品牌有很多的公众号，他想统计所有平台粉丝的总数（一个粉丝如果关注了多个公众号只算一个），那么就用到了unionId





