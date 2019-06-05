# dim

封装的一个腾讯云im，以便于flutter开发者可以方便继承im到自己的应用中

## 使用之前注意事项

如果你之前没有使用过腾讯云，请仔细阅读这段文字，如果你已经对腾讯云im了如指掌，可以越过，但建议还是熟悉以下。

因为这个库是基于腾讯云im的，因此需要去云im申请一个应用，阅读这篇[文章](https://github.com/tencentyun/TIMSDK/tree/master/Android)可以获得以下知识：

1、`appid`怎么来的

2、`账号`及其对应的`sig`如何来的，已经推荐的sig的生成方式（当然这个是后台同学关注的）。

弄清楚这些之后，就可以开始使用`dim`了。

## 使用 dim
dim的使用非常简单，只需引入这个库就可以使用了。

```dart
dependencies:
  dim: ^0.2.3
```

不需要像我之前实现的版本那样进行一些繁琐的配置，因为云im升级之后，支持`maven`以及`pod`的引用方式啦。那么Android端


### Android端需要注意什么？

1、混淆配置，在你的flutter的Android工程中配置混淆。

```java
-keep class com.tencent.** { *; }
```

### IOS端需要注意什么？

1、请注意在你的flutter工程的ios项目根目录执行`pod update`[**非必须，如果报错建议执行一次**]

2、随后在执行一次`pod install`


### demo截图

![截图](https://raw.githubusercontent.com/bravekingzhang/pic_go/master/20190603113634.png)


![构建](https://raw.githubusercontent.com/bravekingzhang/pic_go/master/20190603113619.png)


## 已有的功能

1. 初始化

    建议整个应用生命周期只执行一次。
2. 登录
3. 登出
4. 获取会话列表
5. 删除一个会话
6. 获取私信会话消息[群聊消息目前没有封装]

    注意，私信发送方的资料云im改成了异步的方式，因此，这个版本不在返回！
    建议用户自己查询一次，最好的方式是将用户资料存储在本地db中，并
7. 发送图片消息
    
      注意，图片消息中图片云im需要的是图片的`本地路径`。
8. 发送文本消息
9. 发送地理位置消息
10. 获取用户资料
11. 设置用户资料

    目前仅仅提供了设置`nick`，`gender`，`faceUrl`，有需要在补充。
    
## todo

根据需要，可以提issue，或者接受pr来实现更多的接口，主要是体力活。