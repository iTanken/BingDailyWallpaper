# BingDailyWallpaper

🖼 全新必应每日桌面壁纸设置工具，支持 Windows 及 macOS。自动保存图片，一键设置壁纸。**Write once, run anywhere！**
![必应每日桌面壁纸设置工具](https://user-images.githubusercontent.com/23544702/59973479-066dad80-95d3-11e9-8602-5f58efd27d4c.png)

最近发现了一个可以设置 macOS 壁纸图片的终端命令，闲来无事，在前作（参见 [Java 版下载必应每日壁纸并自动设置 Windows 系统桌面](https://zixizixi.cn/articles/2017/09/01/1504264675391.html) ）基础上针对 macOS 进行了支持优化，支持设置 macOS 桌面壁纸。并且根据官方数据接口，可以查看、设置最近 14 天的壁纸图片。本次更新还添加了命令行支持和右键功能菜单，以增强实用性。

由于历史遗留原因，本次依旧使用以前的 XML 格式的数据接口，后续闲的蛋疼的时候可能会改用 json 格式的接口：
> [https://cn.bing.com/HPImageArchive.aspx?idx=0&n=1](https://cn.bing.com/HPImageArchive.aspx?idx=0&n=1)

同时发现，每日故事接口已被移除，无任何响应内容：
> ~~https://cn.bing.com/cnhp/coverstory/~~

好怕怕呀，以后微软要是把每日图片的接口也砍掉的话就真的蛋疼了 🤣

## 下载
* 直接下载： [iWallpaper.jar](https://img.hacpai.com/file/2019/06/iWallpaper-4b7e0443.jar)

* 项目地址： [https://github.com/iTanken/BingDailyWallpaper](https://github.com/iTanken/BingDailyWallpaper)

* 发行地址： [https://github.com/iTanken/BingDailyWallpaper/releases](https://github.com/iTanken/BingDailyWallpaper/releases)

🤔 由于源码较乱，暂时还没有兴致开源，以后也许某天闲的蛋疼了就开源了。有兴趣的小伙伴可以自行反编译哟～

## 使用方法
由于本工具基于 Java 开发，故需要系统安装 [Java 运行环境](https://www.java.com/en/download/)，要求最低版本为 Java8。正确安装 JRE 或 JDK 后，您可以直接双击本工具的可执行 jar 文件运行，或者执行以下 CLI 命令来启动程序：
```
java -jar iWallpaper.jar
```
在 macOS 系统上，由于平台限制问题，不会显示实际程序名称，可以通过命令行启动来自定义左上角的显示名称：
```
java -Xdock:name=必应每日桌面壁纸 -jar iWallpaper.jar
```

### 使用 CLI
目前只支持 4 个参数，实际有用的只有 3 个，在终端或命令行窗口中输入 `java -jar iWallpaper.jar --help` 显示 CLI 帮助信息：
![image.png](https://img.hacpai.com/file/2019/06/image-de2bf8fe.png)

**path** ：自定义壁纸图片文件的保存位置，必须是合法的本地路径，不指定默认为 **$USER_HOME/Pictures/BingWallpaper** 目录 ：
```
java -jar iWallpaper.jar --path  D:\Files\images\bing
```

**size** ：自定义壁纸图片分辨率大小，可选值：**1366x768**、**1920x1080**（默认），只支持这两种分辨率：
```
java -jar iWallpaper.jar --size 1366x768
```

**view** ：不显示主界面，包含此参数启动软件时设置当天的壁纸后将直接退出程序：
```
java -jar iWallpaper.jar --view
```

**help**：显示 CLI 帮助信息，不重要...
```
java -jar iWallpaper.jar --help
```

### 特别说明
在 macOS 下通过终端设置桌面壁纸的命令为：
```
osascript -e 'tell application "Finder" to set desktop picture to POSIX file "替换为图片路径"'
```
设置桌面壁纸时会在控制台中显示对应的命令执行日志：
![命令执行日志](https://img.hacpai.com/file/2019/06/image-39afae7b.png)

## 运行效果
在 Windows 系统的运行效果相对于 macOS 更接近于原生程序，由于本次更新主要针对 macOS，且两种系统运行效果基本一致，故不再对 Windows 系统运行效果进行单独说明。

### 启动界面：
![TomLoveJerry.gif](https://img.hacpai.com/file/2019/06/TomLoveJerry-57225131.gif)

嗯...听说最近很流行，Tom Love Jerry。

### 主界面：
![主界面](https://img.hacpai.com/file/2019/06/image-f5e731ab.png)
看到没，那一对扎眼的左右方向按钮，就是用来切换上一张和下一张必应壁纸图片的，就像前面说过的，只支持查看最近两周的图片。

单击底部的图片信息，会直接复制说明信息到剪贴板并提示，提示框会自动消失：

![复制说明信息到剪贴板](https://img.hacpai.com/file/2019/06/7-c1844330.gif)

双击底部的图片信息，会直接使用默认浏览器打开数据接口返回的 copyrightlink，也就是必应的搜索地址：

![打开 copyrightlink](https://img.hacpai.com/file/2019/06/8-11eafeb3.gif)


启动后，会默认显示并直接设置当天的必应图片为桌面壁纸：

![image.png](https://img.hacpai.com/file/2019/06/image-2b2a3a5a.png)

到达最后一张，也就是今天，再切换下一张，就会很温馨的提示你：

![image.png](https://img.hacpai.com/file/2019/06/image-8b708e00.png)

同样，在到达第一张时，也就是两周前的那一天：

![image.png](https://img.hacpai.com/file/2019/06/image-516b6fa0.png)

* 提示框会自动消失哟～

### 右键菜单
在图片区域单击鼠标右键，弹出右键功能菜单，支持以下 10 个快捷功能，右侧提示的快捷键仅在唤出右键菜单的前提下可用：
![image.png](https://img.hacpai.com/file/2019/06/image-792b4bac.png)

1. 刷新：重新下载并刷新当前图片：
![刷新](https://img.hacpai.com/file/2019/06/admin1-6f6d6e45.gif)

2. 重启：重启软件，macOS 下重启后会更新应用标题：
![重启](https://img.hacpai.com/file/2019/06/admin2-ba7fd4cf.gif)
![重启后mac标题](https://img.hacpai.com/file/2019/06/image-19e0f2ad.png)

3. 另存为：保存当前图片到其他位置：
![另存为](https://img.hacpai.com/file/2019/06/image-03e94440.png)

4. 设为桌面壁纸：顾名思义，设置当前图片为壁纸，即支持设置两周内任意一天的图片为壁纸：
![设为桌面壁纸](https://img.hacpai.com/file/2019/06/admin3-9c724156.gif)

5. 打开文件位置：打开当前壁纸图片本地保存位置，默认保存到 **$USER_HOME/Pictures/BingWallpaper** 目录中，可通过命令行参数自定义保存目录：
![打开文件位置](https://img.hacpai.com/file/2019/06/4-147556b8.gif)

6. 用默认程序打开：使用系统默认 jpg 图片查看工具打开当前图片；
![用默认程序打开](https://img.hacpai.com/file/2019/06/5-478a7e1d.gif)

7. 查看日志：打开调试控制台日志，包含**信息** 💚、**调试** 💙、**警告** 💛、**错误** ❤️ 4 种类型的日志，也可以通过快捷键 **Alt（Windows）/Option（macOS）+ F12** 打开：
![日志调试控制台](https://img.hacpai.com/file/2019/06/image-384672e2.png)

8. 获取帮助：使用系统默认浏览器打开项目地址：

![获取帮助](https://img.hacpai.com/file/2019/06/6-9d035918.gif)

9. 关于：打开程序的关于信息窗口，厚颜无耻的放了三个自己的链接：

![关于](https://img.hacpai.com/file/2019/06/image-7fcf4b15.png)

10. 退出：退出软件，也可以通过快捷键 **Ctrl + W** 关闭程序：

![退出](https://img.hacpai.com/file/2019/06/image-2f4e7011.png)

## 鸣谢

本工具主要使用了以下几个三方库：

* [AppleJavaExtensions-1.6.jar](https://repo1.maven.org/maven2/com/apple/AppleJavaExtensions/)
	>  Mac OS X 上用于 Java 的新 Apple eAWT 和 eIO API，以允许在 Mac OS X 以外的平台上编译 eAWT 或 eIO 引用代码。

* [commons.cli-1.2.0.jar](https://repo1.maven.org/maven2/commons-cli/commons-cli/)：
	> Apache Commons CLI 库提供了一个 API，用于解析传递给程序的命令行选项。它还能够打印详细说明命令行工具可用选项的帮助消息。

* [dom4j-1.6.1.jar](https://repo1.maven.org/maven2/dom4j/dom4j/)
	> dom4j 是一个易于使用的开源库，用于在 Java 平台上使用 Java Collections Framework 处理 XML、XPath 和 XSLT，并完全支持 DOM，SAX 和 JAXP。

* [jna-4.4.0.jar](https://repo1.maven.org/maven2/com/sun/jna/jna/)
	> 为 [Java](https://en.wikipedia.org/wiki/Java_(software_platform) "Java（软件平台）") 程序提供了对[本机共享库的](https://en.wikipedia.org/wiki/Shared_library "共享库")轻松访问，而无需使用 [Java Native Interface](https://en.wikipedia.org/wiki/Java_Native_Interface "Java Native Interface")。

## 授权
本作品采用[知识共享署名-相同方式共享 4.0 国际许可协议](https://creativecommons.org/licenses/by-sa/4.0/deed.zh)进行许可。
