# 云开发

## 三大能力
* 云函数  （相当于后台的代码，因为是一个nodejs的环境，有入口函数）
* 云存储    (上传一些图片的资源)
* 云数据库  （数据库）
* 云调用（还没怎么研究，文档也没有怎么写）

## 如何使用
* project.config.json 声明 miniprogramRoot （小程序端） cloudfunctionRoot （云函数端） 路径
* 云函数端 其实就是一个node js的环境，里面有入口函数，当在小程序端 wx.cloud.callfuncition 的时候就会调用，相当于后台
* 小程序端 就是前端

## 云函数（后台）调用的2种方式？ https://developers.weixin.qq.com/miniprogram/dev/wxcloud/basis/capabilities.html#%E4%BA%91%E5%87%BD%E6%95%B0
- 部署到云端进行调用
- 本地测试调用 

## 云函数调用报错 500 internet server error
- 可能是微信的服务器出错了，等会再试


