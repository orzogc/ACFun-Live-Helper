# ACFun-Live-Helper
OBS直播助手

## 组件开发指北
* 弹幕获取
```
this.$store.watch((state) => state.roomInfo.danmakuList, async (newValue, oldValue) => {
  var danmaku = newValue[0]
  console.log('助手组件：xxxx：弹幕状态变更')
}).bind(this)
```

## 感谢使用
念念不忘，必有回响？

## 支持的功能
* 房间观众管理
* 拉黑观众
* 房管管理
* 弹幕透明置顶显示
* 弹幕发送
* 弹幕发送置顶窗
* 直播开关播
* 开播时封面和标题修改
* GIF封面
* 弹幕播报
* 弹幕互动
* OBS推流码修改
* 投喂列表
* 下播后的直播详情

## 更新日志
* 0.2.35 修复复读问题，优化播报队列处理
* 0.2.34 修复重连机制
* 0.2.33 加入简单的动态读取
* 0.2.32 关闭HTTP缓存
* 0.2.31 合并礼物
* 0.2.30 修复重复播报的问题
* 0.2.29 加入关注检测，加入延迟关播
* 0.2.28 取消弹幕显示的合并
* 0.2.27 修复TTS的不存在配置项导致报错停止播报
* 0.2.26 自信的加了Log输出来查错。
* 0.2.25 修复TTS小问题。
* 0.2.24 修复历史遗留问题。
* 0.2.23 确实是没睡醒。
* 0.2.22 可能是没睡醒。
* 0.2.21 修复播报顺序。
* 0.2.20 优化语音播报。
* 0.2.19 集成主站工具，修改弹幕播报的配置位置。
* 0.2.18 优化直播开播，加入封面缓存。
* 0.2.17 优化OBS控制，加入分区检测。
* 0.2.16 修复配置文件保存和读取的bug，加入流检测。
* 0.2.15 加入播报句式，方便自定义化。
* 0.2.14 加入投喂列表，修复OBS控制的错误提示输出。
* 0.2.13 修复点歌命令bug，加入OBS控制，移除OBS配置文件写入。
* 0.2.12 修复尺寸bug。
* 0.2.11 加入OBS配置文件写入。
* 0.2.10 修复一个小bug。
* 0.2.9 加入TTS队列，加入直播GIF封面，优化项目构造。
* 0.2.8 加入直播后详情获取，优化更新检查逻辑。
* 0.2.7 整合部分组件，加入更新检查。
* 0.2.6 小功能修复。
* 0.2.5 加入弹幕获取。
* 0.2.4 修改部分逻辑。
* 0.2.3 加入直播标题和封面修改（独家！我先找到的接口！）。
* 0.2.2 修复关闭直播的bug。
* 0.2.1 全部重构！业务逻辑重新优化。

## 下载
1. [Releases](https://github.com/ShigemoriHakura/ACFun-Live-Helper/releases)

## 发布文章
* [网页开播的超方便小工具发布！](https://www.acfun.cn/a/ac19231355)

## 给点给点
* [茂森白咲](https://www.acfun.cn/u/35119946)

## 截图
![使用截图1](https://raw.githubusercontent.com/ShigemoriHakura/ACFun-Live-Helper/master/screenshots/1.png) 
![使用截图2](https://raw.githubusercontent.com/ShigemoriHakura/ACFun-Live-Helper/master/screenshots/2.png) 
![使用截图3](https://raw.githubusercontent.com/ShigemoriHakura/ACFun-Live-Helper/master/screenshots/3.png) 

## 编译
* npm install
* npm run electron:build 

## 网页开播逻辑
* 上传封面：
* https://member.acfun.cn/common/api/getQiniuToken 获取token
* https://upload.qiniup.com/ token用base64解码，直接axios就ok
* 上传封面完成
* 开播流检测：
* https://api.kuaishouzt.com/rest/zt/live/web/obs/transcodeInfo 获取转码信息,可以忽略
* https://api.kuaishouzt.com/rest/zt/live/web/obs/config 获取推流地址和密钥
* https://api.kuaishouzt.com/rest/zt/live/web/obs/startpush 开始推流，需要用got的buffer（暂时没找到更方便的）
* 关播：
* https://api.kuaishouzt.com/rest/zt/live/web/obs/stoppush 关闭推流
