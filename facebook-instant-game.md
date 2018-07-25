# Facebook Instant Game 调查

内容: 发布，推广相关

## 文档资料

**Instant Games**  <https://developers.facebook.com/docs/games/instant-games/>

**Our Demo game** <https://apps.facebook.com/1852379284782298/> （需授权访问）


## DEV Guides

* SDK
  * 根目录包含 index.html
  * index.html中要引用 https://connect.facebook.net/en_US/fbinstant.6.0.js
  * 通过Promise enabled fucntion:  
    FBInstant.initializeAsync() 加载资源
    FBInstant.startGameAsync() 启动游戏
  * 注：不使用SDK的话，游戏上传会被拒
  

* Bundle configuration
  * fbapp-config.json 是必须文件，位于项目根目录 

## 发布

* 开发者无需准备服务器，FB 提供了Instant games的存储
* 将游戏项目打包成zip (index.html 必须在压缩包根目录下)
* 游戏上传
  * 后台上传: 登陆App后台在 Instant Games > Web Hosting 页面进行游戏上传
  * API 上传: https://graph-video.facebook.com/{App ID}/assets
    FB提供了Demo项目展示如何利用gulp将项目打包及上传脚本话
* 在Web Hosting 页面可以看到游戏的历史版本，也可以进行版本切换操作
* 限制: 项目文件总体积不能超200M, 总文件数不能超500
* 发布需要提审 (5张Image 素材，1个Vedio)
  * 当前经验:调查用的Demo游戏鉴于质量不高没有尝试发布；据了解海哥组第一版游戏已提交尚未通过审核

## 推广

* Entry Points: FB 为 instant game 提供了许多入口点如: app_center,custom_share,game_share,game_search 等，详细列表：
<https://developers.facebook.com/docs/games/instant-games/guides/analytics/>

* getEntryPointData: SDK 中提供了该 method 可以获取游戏启动入口，可用来作统计
  * 不过目前实测拿到的数据是 null ,可能与游戏处于未发布状态有关
  * SDK中没有发现获取推广信息相关的方法

* 广告推广：Instant game 主要依靠社交推广，及由FB控制的排行榜推广；在Facebook Instant game 文档中未找到关于广告买量方面的信息

* 交叉推广： 通过参考Zynga游戏发现FB SDK提供了游戏交叉推广的API：
  *  switchGameAsync()
     *  可以自定义entrypoint信息，便于追踪  
     *  限制了互相推广的游戏必须在一个business 内
  * 也尝试了用游戏URl的方式进行推广，发现是被禁止的

     ![MacDown Screenshot](https://xuchang-stat.oasgames.com/doc/img/z2.png)


  