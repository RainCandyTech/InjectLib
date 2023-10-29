<p align="center" style="font-size: 21px">QiuChenly InjectShell</p>
<p align="center">Creative & Design</p>
<p align="center">2023@MacBook Pro</p>


# 概览

<!-- TOC -->

- [概览](#概览)
- [关注我](#关注我)
- [免责声明](#免责声明)
    - [让你们看看原神的力量 去吧 芭芭拉](#让你们看看原神的力量-去吧-芭芭拉)
- [使用](#使用)
- [问题](#问题)
- [环境](#环境)
- [兼容](#兼容)
- [激活注意](#激活注意)
  - [Emby Server 破解](#emby-server-破解)
  - [Sublime Text Dev](#sublime-text-dev)
  - [PD 19](#pd-19)
  - [Stash](#stash)
  - [ELPass](#elpass)
  - [Surge](#surge)
  - [拦截激活部分App](#拦截激活部分app)
- [提示](#提示)
- [警告](#警告)
- [目的](#目的)
- [交流](#交流)
- [~~停更~~](#停更)

<!-- TOC -->

# 关注我

关注我的Twitter (X) 平台 ID OK？关注落叶喵，关注 QiuChenly 谢谢喵

[QiuChenly](https://twitter.com/QiuChenly)


# 免责声明

致来自中国大陆的各位学习研究爱好者:<br>
   根据大陆中华人民共和国《计算机软件保护条例》第十七条规定：“为了学习和研究软件内含的设计思想和原理，通过安装、显示、传输或者存储软件等方式使用软件的，可以不经软件著作权人许可，不向其支付报酬。”您需知晓本仓库所有内容资源均来源于网络，仅供用户交流学习与研究使用，版权归属原版权方所有，版权争议与本仓库本作者无关，用户本人下载后不能用作商业或非法用途，需在24小时之内删除，否则后果均由用户承担责任。如果你不删,请发邮件到 qiuchenly@outlook.com, 我做个登记, 然后让这些喜欢发律师函的事务所一对一指导你。

我是来自北美的独立 iOS 应用开发者, 是二次元南桐. 从早稻田毕业的那一天, 我的青春也永远留在了京都.

对了,下次发律师函的时候记得发往我住的地方: 华盛顿特区第35大道林肯大街15号-501, John Albet 收.

### 让你们看看原神的力量 去吧 芭芭拉

[![启动](https://i2.hdslb.com/bfs/archive/966fe6fe2c1329919bb8972d69fb8c09d17047cc.jpg@100w_100h_1c.png)](https://ipfs.lanyundev.com/ipfs/bafybeigpm6ocaba2wlgi7zgio3lu7hzqxgrviiicuwc5xbddlo77leabcy/6e51fccaeb5343bda366d42e68c3c705.MP4)

# 使用

1. 下载整个仓库并解压，双击运行"原神_启动.command"并输入密码，按照提示操作。
   <br>
   小白不知道点哪里下载整个仓库？[点我下载](https://github.com/QiuChenlyOpenSource/InjectLib/archive/refs/heads/main.zip)
2. 要是你不差这几分钟时间，从头到尾先认真读一遍这个readme，可能你看完之后会解决你的部分疑惑。

纯小白另可参见:[小白参考](https://github.com/wolffya/InjectLib/tree/secondary)

# 问题

这里列举一下可能会遇到的问题。

1. 遇到"xxx 想要访问你的机密信息"<br>
   ![img.png](img.png)<br>
   原因:<br>
   补丁对某些 App 会自动签名以保证能在 SIP 打开的情况下使用。但是保存在钥匙串里的信息只能被官方签名的 App 读取
   自己签名 App 后会造成丢失权限<br><br>
   解决方案:<br>
   在钥匙串删除该 App 使用的相关“机密信息”。

2. 需要移到废纸篓
   
   应该是 App 没有打开过就直接执行注入了。这可能会导致检查不通过，不过影响不是很大。建议 App 在注入前先运行一次。

   ![移到废纸篓](image-3.png)

   这是正常的，因为 SIP 打开的情况下如果修改了 App 会导致校验不通过，你只需要手动从访达中右击点开一次就好了:<br>
   ![打开](image-4.png)
   ![进一步打开](image-5.png)

   此时就能正常打开。如果还出现问题，请检查自己的注入操作有没有问题。

4. Operation not permitted<br>
   如下所示。<br>
   ![simple](image-7.png)<br>
   ```
   开始注入App: com.nssurge.surge-mac
   /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/fileutils.rb:1387:in `initialize': Operation not permitted @ rb_sysopen - /Applications/Surge.app/Contents/Frameworks/Bugsnag.framework/Versions/A/Bugsnag_backup (Errno::EPERM)
   ```
   这是很多人会遇到的问题。<br>Operation not permitted 意味着终端 App 在修改目标 App 时由于没有权限所导致的崩溃。<br>
   原因：终端没有给操作权限<br>
   解决办法：<br>
   1. 打开设置<br>
   2. 隐私和安全性<br>
   3. 开发者工具 和 App 管理<br>
   4. 两个地方都要打开终端开关，重启终端即可正常执行。<br>
   ![terminal](image-6.png)<br>
   ![还有这个](image-8.png)

# 环境

代码运行最低操作系统要求&此代码编译环境

- 最低运行 macOS High Sierra 10.13
- 编译SDK macOS 14.0
- 目标部署平台 macOS 10.13
- CMakeLists 环境变量
  - set(CMAKE_OSX_DEPLOYMENT_TARGET "10.13")
- 检查二进制文件的最低macOS版本兼容性
  - ```find . -name "*.*" | xargs otool -l | grep -E "(minos|sdk)"```

# 兼容

新增的SIP栏说明:<br>

- ❌: 只能关闭SIP使用<br>
- ✅: 可以在打开SIP的机器上使用<br>

| App                                            | 版本                                                                                        | ARM64 | Intel | SIP | 特殊要求                                                                                                                                                                            |
|:-----------------------------------------------|:------------------------------------------------------------------------------------------|:-----:|:-----:|-----|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| iShot                                          | 通杀                                                                                        |   ✅   |   ✅   | ✅   | 交个朋友 不杀了 大家支持正版吧 又不贵                                                                                                                                                            | 
| Infuse Pro                                     | 通杀                                                                                        |   ✅   |   ✅   | ✅   |                                                                                                                                                                                 | 
| MWEB Pro                                       | 通杀                                                                                        |   ✅   |   ✅   | ✅   |                                                                                                                                                                                 | 
| 解优2                                            | 通杀                                                                                        |   ✅   |   ✅   | ✅   |                                                                                                                                                                                 | 
| Omi录屏专家                                        | 通杀                                                                                        |   ✅   |   ✅   | ❌   | 需要从Mac App Store 下载                                                                                                                                                              | 
| OmniPlayer                                     | 通杀                                                                                        |   ✅   |   ✅   | ✅   | 需要从Mac App Store 下载                                                                                                                                                              |
| Navicat Premium                                | 通杀                                                                                        |   ✅   |   ✅   | ✅   | 需要从Mac App Store 下载                                                                                                                                                              |
| Navicat 16 ForOracle                           | 通杀                                                                                        |   ❌   |   ✅   | ✅   | 需要从Mac App Store 下载 我下不到 ARM64 的版本                                                                                                                                                 |
| Sublime Text                                   | [通杀](https://download.sublimetext.com/sublime_text_build_4154_mac.zip)                    |   ✅   |   ✅   | ✅   | 授权信息下面找。                                                                                                                                                                        |
| Elpass                                         | [通杀](https://elpass.app/macos/Elpass-1.5.6-490.zip)                                       |   ✅   |   ✅   | ✅   | 无法使用云同步 签名后的 App 通病 无解 搭配 Surge 脚本可以做到5138年授权                                                                                                                                       |
| Surge 5                                        | [通杀](https://dl.nssurge.com/mac/v5/Surge-5.4.0-2417-5fbf4315352d3132015458910d121712.zip) |   ✅   |   ✅   | ✅   | 年度好戏我愿称之为 《窃听风云8:赛博卧底》                                                                                                                                                          | 
| CleanMyMac X                                   | 通杀                                                                                        |   ✅   |   ✅   | ✅   | com.macpaw.CleanMyMac4.Menu 单独也要注入 Helper 每个版本不一样还是需要单独处理 暂时不弄了 不要下大陆特供版 更新地址: https://s3-us-west-2.amazonaws.com/updateinfo.devmate.com/com.macpaw.CleanMyMac4/beta/updates.xml | 
| Microsoft Office Word/PowerPoint/Excel/Outlook | 通杀                                                                                        |   ✅   |   ✅   | ✅   | 365订阅版 需要从 Mac App Store 下载                                                                                                                                                       |
| Stash                                          | [2.3.0](https://mac-release-static.stash.ws/Stash-build-221.zip)                          |   ❌   |   ✅   | ❌   | 无法设置全局代理 不知道哪里有问题 总体体验较差 不如 Surge                                                                                                                                                |
| Paste                                          | 4.0.9                                                                                        |   ✅   |   ✅   | ✅   |     通杀特征码变了 下次再说                                                                                                                                                                            | 
| App Cleaner & Uninstaller                      | 8.2.2                                                                                     |   ✅   |   ✅   | ✅   | 因为签名会导致提示盗版，有空在再弄。                                                                                                                                                              | 
| Affinity Photo 2/Designer 2/Publisher 2 全家桶    | 2.1.1                                                                                     |   ✅   |   ✅   | ✅   | 需要从Mac App Store 下载                                                                                                                                                              |
| ProxyMan                                       | [通杀](https://download.proxyman.io/49100/Proxyman_4.10.0.dmg)                            |   ✅   |   ✅   | ✅   | 更新地址: https://proxyman.io/osx/version.xml                                                                                                                                       |
| BuhoCleaner                                    | [通杀](https://www.drbuho.com/buho-public-files/buhocleaner/buhocleaner197150.dmg)       |   ✅   |   ✅   | ✅   | 更新地址：https://www.drbuho.com/buho-public-files/buhocleaner/appcast.xml                                                                                                           |
| Macs Fan Control                                    | [通杀](https://crystalidea.com/downloads/macsfancontrol.zip)       |   ✅   |   ✅   | ✅   | |
| TablePlus                                    | [通杀](https://tableplus.com/release/osx/tableplus_latest)       |   ✅   |   ✅   | ✅   |  |
|Transmit 5|5.9.2|✅|✅|✅| 需要从App Store下载
|DevUtils|[1.17.0](https://devutils.com/archives/DevUtils-1.17.0.dmg)|✅|✅|✅| 功能可用 但是激活状态我懒得改了 作者写的这个 App 代码质量之烂令人无语 不想多说什么了
|MP3Tag|[1.8.6 (86)](https://updates.mp3tag.app/Mp3tag-1.8.6.zip)|❌|✅|✅| 序列号随便输入 全部激活
|Widgetter|[通杀](https://apps.apple.com/cn/app/widgetter-%E5%B0%8F%E5%B7%A5%E5%85%B7-%E6%A1%8C%E9%9D%A2%E5%A3%81%E7%BA%B8-%E4%B8%BB%E9%A2%98-%E5%B1%8F%E4%BF%9D/id1553223588?mt=12)|✅|✅|✅| MAS 下载 激活全部功能
|Bartender 5|[5.0.36-通杀](https://macbartender.com/B2/updates/5-0-31/Bartender%205.zip)|✅|✅|✅| 更新地址 https://www.macbartender.com/B2/updates/AppcastB5.xml
|Parallels Desktop|[19.1.0](https://download.parallels.com/desktop/v19/19.1.0-54729/ParallelsDesktop-19.1.0-54729.dmg) |   ✅   |   ✅   | ✅   |  谁会想到会有人以全家除他以外(含亲妈)全部暴毙的代价冒名顶替别人给我发恐吓律师函呢？
|QCAD-Intel|[3.28.2](https://www.qcad.org/archives/qcad/qcad-3.28.2-trial-macos-10.14-13.dmg)|❌|✅|✅| ARM懒得弄

| Adobe 全家桶               | 版本           | ARM64 | Intel | 特殊说明 全家桶全部支持打开SIP下使用                         |
|:------------------------|:-------------|:-----:|:-----:|:-----------------------------|
| Adobe PhotoShop         | 通杀           |   ✅   |   ✅   | PS：Intel 上的神经滤镜已经完美可用 ARM64 的暂时不行                |
| Adobe Acrobat Pro           | 23.006.20320 |   ✅   |   ✅   |                              |
| Adobe Illustrator       | 28.0.0       |   ✅   |   ✅   | ARM64 测试通过 X86 没有测试过 大家自行测试   |
| Adobe Lightroom      | 7.0         |   ❌    |   ✅   | 注入后先点试用 然后过期后可以正常使用 |
| Adobe Lightroom Classic | 13.0.1         |   ❌   |   ✅   | 注入后先点试用 然后过期后可以正常使用                 |
| Adobe InCopy 2024      | 19.0.0.151         |   ✅    |   ❌   | 在 M1 Mac Mini 中测试通过 |
| Adobe InDesign 2024      | 19.0.0.151         |   ✅    |   ❌   | 在 M1 Mac Mini 中测试通过 |
| Adobe Premiere Pro 2024     | 24.0.0         |   ✅    |   ✅   | 在 M1 Mac Mini 中测试通过 |
| Adobe After Effects 2024      | 24.0.0         |   ✅    |   ✅   | 在 M1 Mac Mini 中测试通过 |
| Adobe Animate 2024      | 24.0         |   ✅   |   ✅   | 在 M1 Mac Mini 中测试通过 |
| Adobe Audition 2024      | 24.0.0.46         |   ✅    |   ✅   | 在 M1 Mac Mini 中测试通过 |
| Adobe Media Encoder 2024      | 24.0         |   ✅    |   ✅   | 在 M1 Mac Mini 中测试通过 |

另请参见: [Adobe激活产品说明](./Adobe说明.md)

# 激活注意

## Emby Server 破解
参见 [EmbyServer 破解说明](./EmbyServer)

## Sublime Text Dev

```
----- BEGIN LICENSE -----
秋城落叶@52pojie.com
Unlimited User License
EA7E-8888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
88888888888888888888888888888888
------ END LICENSE ------
```

## PD 19

PD 19 说明与注意事项:<br>

1. 注入后先不要打开PD, 去运行"Parallels_原始人_起洞.command", PD将会自动启动。
2. 每次打开PD都要重复步骤1才能完美使用。步骤1执行一次之后只要PD你没有退出, 就可以直接使用PD不需要再去执行步骤1。
3. 总结: 原始人，起洞！

灵感和解决思路来自于:<br>
仓库: https://github.com/trueToastedCode/ParallelsLab/tree/main<br>
非常感谢 trueToastedCode 提出的想法和美妙设计！

非常感谢 @trueToastedCode，PD 19.1 的破解正是由 @trueToastedCode 的努力研究成果！

## Stash

https://mac-release.stash.ws/appcast.xml

## ELPass

hey,bro,what's up?

ElPass: https://elpass.app/macos/appcast-beta.xml

## Surge

目前最新支持 Surge 5.4.0 2417 版本.

laoliu，good morning. not good also fine, follow u.

Surge 盗版用户请支持正版。<br>
对开发者团队我无意冒犯，早上好。<br>

Surge 更新地址: https://www.nssurge.com/mac/v5/appcast-signed-beta.xml <br>

一切完美。感谢QQ 302***3398 用户无偿提供授权信息。<br>
目前错误已全部修正。<br>
之前安装过旧版本的用户进Surge后先卸载一遍Helper帮助程序才能正常安装帮助程序挂上代理。点击安装帮助程序没反应的不是破解的问题，能不能先去点一下卸载帮助程序呢？<br>

## 拦截激活部分 App

Surge 可以利用拦截修改 http 返回值的方式破解下面的 App 而无需修改原始 App。下面是脚本破解步骤，如果你不需要用下面的 App，看到这里就可以关闭网页了。

Surge 开启 MitM 和脚本功能，然后: <br>

1. 在你的配置文件中加入例子中提供文件中的 Script 字段信息:
   [Surge脚本配置例子.conf](Surge%E6%BF%80%E6%B4%BB%E8%84%9A%E6%9C%AC%2FSurge%E8%84%9A%E6%9C%AC%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90.conf)
   ![img.png](imgs/img.png)
   ![img_1.png](imgs/img_1.png)
   ![img_1.png](imgs/img_2.png)

2. [paddle_act.js](Surge%E6%BF%80%E6%B4%BB%E8%84%9A%E6%9C%AC%2Fpaddle_act.js)这个文件一定要复制到conf文件所在目录中。

3. 记得 https 解密打开，并且信任证书，MitM 域名加入 *.paddleapi.com 保存即可。<br>
   如果要实现五千年授权需要打开增强模式并加入新的域名: api.elpass.app<br>
   ![img.png](imgs/img3.png)

4. 在 App 中随意输入序列号和邮箱，点击激活后秒激活。

已测试支持以下App:

| App           | 版本     | 特殊说明                                           |
|:--------------|:-------|:-----------------------------------------------|
| AlDente Pro   | 1.22   |                                                |
| AirBuddy      | 2.7.1  |                                                |
| Downie 4      | 4.6.27 | `B7EE3D3C-B7EE3D3C-B7EE3D3C-B7EE3D3C-B7EE3D3C` |
| One Switch    | 1.31   |                                                |
| Rectangle Pro | 3.0.8  |                                                |
| Swish         | 1.10.2 |                                                |
| TG Pro        | 2.8.2  |                                                |
| Timemator     | 3.0.3  |                                                |

# 提示

1. 会自动扫描本地安装的 App，你只需要在想注入的 App 后面输入y即可。
2. Adobe App 如果不想让官方 ACC 乱拉屎，可以用这个仓库下载 v6 版本的离线安装包: https://github.com/Drovosek01/adobe-packager,
   然后配合 AntiCC 之类的组件运行 Adobe 产品。
3. 激活之后由于 App 还需要依赖我的注入代码，所以不要移动注入文件夹或者删除注入文件夹。
4. 脚本如果没有权限执行注入操作终端报错类似于下面这样:<br>
   ![示例](image-2.png)
   那是因为 SIP 的安全策略限制不允许运行不符合安全策略的代码执行，所以你需要先打开:<br>
   设置 - 隐私与安全性 - 开发者工具:<br>
   ![开发者工具](image.png)<br>
   并打开终端执行代码策略:<br>
   ![策略](image-1.png)<br>

   最后重新执行即可正常注入。这是 macOS 的安全策略。


# 警告

一定要关闭 SIP，因为我使用的注入方式依赖于关闭 SIP。
但是有例外，上方表格中 App 的 SIP 状态为"✅"则可以不用关闭 SIP 即可使用,并且注入下载文件夹不需要保留，注入后可以删除。
本库中几乎所有的 App 都建议你在打开 SIP 状态下使用，不建议用户关闭 SIP，除非你很懂这块。

# 目的

本项目是 Free 的、开源的、基于互联网最原始的共享精神的、不接受任何打赏的、无所不包的、令人感叹的、无与伦比的、精妙绝伦的、化腐朽为神奇的、逆天的、养生的、抽象的、二次元的、OP的。

在 2023 年，所有人都逐渐觉得打赏、付费才是理所应当的，哪怕是某些人只做了一件从外网搬运到国内的工作，也应该得到鼓励。
我不能说这种行为是完全错误的，只能说有些人恬不知耻见利忘义。哪怕是打赏也应该基于双方意愿的基础上，而不是用“打赏后才能下载”这种理由强奸用户的使用习惯，把用户变成必须付费的蠢驴，并辅以几十元的超低价注册会员费用钝刀割肉式的强奸用户。

当然，这种用户也确实是个蠢货。有这种钱你买正版得了，别跟我说太贵，你出去跟朋友吃一顿好点的饭 200 起步，大部分好软件正版才不到 100 块钱。抽包烟软中煊赫门起步，面对 19.9 年费会员时却面露难色。相信我，你也并不是真的需要这些软件，只是人云亦云盲目从众罢了。

我认为，共享精神不应该建立在物质上，我深刻的理解金钱对人的吸引和动力，但这种精神本身就超越了物质。


# ~~停更~~

~~最近想追个19岁的小妹妹。<br>
项目基本上不会更新了，增加的新项目基本上是工作💻需要才做的。<br>
也不会去维护下面App的新版本了，等我追到手🧑‍🤝‍🧑再说罢！<br>~~

~~为了追💗妹妹👧，MD，跟米哈游原神铁道星穹崩坏王者荣耀蛋仔二次元拼了😡👊！<br>
这下不得不成为农P/原P/穹P了🙏🙏<br>~~

~~无知时诋毁原神🫤🙏<br>
成熟时理解原神😭🙏<br>
恋爱时成为原神😋🙏<br>~~

~~原神助我！喝唉！🖐大荒天陨！️<br>
任何邪恶！终将绳之以法👮！<br>~~

~~原神，启动！~~

失败了，大家别问了。 <br>
她不是不喜欢玩游戏，她只是不想和不喜欢的人玩游戏。<br/>

这段Repo不会删，警钟长鸣。但是你要问我如果再给我一次机会还会不会选18岁妹妹，我的回答是“yes i do.”
