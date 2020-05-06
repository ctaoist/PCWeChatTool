# Wechat Hook TO Restful API

这个项目的目的是要把微信pc端的所有hook变成 restful api，免费使用，暂不开源

谢Hezone的教程
https://study.163.com/course/courseMain.htm?courseId=1006486010

这个dll只适合微信版本 2.6.8.52

## 使用方法

把 Release 文件夹里的 WechatDllCpp.dll 注入到微信就可以，如果想要获取联系人列表，则需要登录前注入。

注入后 http 服务自动开启 地址为 `127.0.0.1:5710`，并支持 Websocket 连接

如果 dll 同目录下的 `config.ini` 中存在字段 `auth/access_token` 的话，会自动开启验证功能，则所有连接都需要加上`token`参数。

如：`http://127.0.0.1/SendText?wxid=xxxx&msg=xxxxx&token=xxxxxx`

如果注入后想卸载 dll，需要先停止 http server (`http://127.0.0.1/Stop`)，否则微信会崩溃

ps: 求在 Linux Wine 环境下注入 Dll 的方法，感觉好多 Win32 API 都用不了。（本注入工具和dll支持 win server 2003、xp及以上系统 ）

## 功能

API 暂时只有这么多，新功能的话，估计会很缓慢添加。

### 发送文本消息

`http://127.0.0.1/SendText?wxid=xxxx&msg=xxxxx`

```
{
    "wxid" : "微信id"
    "msg"  : "要发的信息"
}
```

### 获取联系人

此功能需要在登录前注入或者注入后重新登录

`http://127.0.0.1/GetContacts`

返回微信联系人列表

### Hook 接收到消息

`接收消息监听.html` 提供了一个简单的 demo

### 获取个人信息

`http://127.0.0.1/GetInformation` 返回个人信息

### Hook 二维码

`http://127.0.0.1/qrcode.png` 获取到二维码后保存在这里


如果觉得本项目对你有帮助，欢迎打赏


![](alipay.png)