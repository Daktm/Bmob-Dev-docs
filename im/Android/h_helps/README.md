## 即时聊天相关问题

### IM的开源地址是什么？

Android：[bmob-android-im-sdk](https://github.com/bmob/bmob-android-im-sdk)   
   iOS : [bmob-iOS-im-sdk](https://github.com/bmob/bmob-iOS-im-sdk)

### 为什么我的手机接收不到信息

请先在Web后台配置包名或者证书。

详情查看IM常见问题部分：[IM常见问题](http://docs.bmob.cn/im/faststart/index.html?menukey=fast_start&key=start_im#index_%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E8%A7%A3%E7%AD%94)

### 消息推送的时候我没开启网络，在推送一段时间后再开启网络，会收到消息吗？

在断网开始的一分钟内发的消息是接收不到的，因为心跳包的默认时间是一分钟，这一分钟内，服务器不认为该链接是断开的，所以消息不会保存成离线消息。

### Bmob可以做群聊吗？

可以利用[数据实时同步](http://docs.bmob.cn/android/developdoc/index.html?menukey=develop_doc&key=develop_android#index_%E6%95%B0%E6%8D%AE%E5%AE%9E%E6%97%B6%E5%90%8C%E6%AD%A5)来实现群聊。

思路可以这样：

1. 创建一个群聊表，包括 群组id信息 发送人信息 聊天信息，这里可以把所有的聊天内容放进去;  
2. 创建一个群组信息表，包括 群组用户列表 创建时间 群组名称等;  
3. 创建一个群组信息变更表，包括 群组id信息，用一个字段记录有消息新增;

当有人在群组中发起聊天时，首先先往群聊表中新增一条记录，然后往群组信息表更表中更新一下记录。所有群组的人都监听自己群组对应的群组信息表更表的几行。 

### 为什么发送位置的时候定位不了

1. 如果你是直接用demo里面的bin目录下的apk的话，是不存在这个问题的。
2. 如果你是下载demo之后直接运行的话，需要去重新去百度地图官网申请key,因为demo里面的可以是和我的eclipse绑定在一起的，相信做过百度地图开发的知道这是为什么。
