# Android UTS扩展开发

> 版本要求: HBuilderX 3.6.9+

HBuilderX 3.6.9+， 新增 uts插件 Android平台 真机运行支持三方 Gradle 仓储。

运行带有uts插件的项目到Android设备，如果您遇到以下提示，请配置[运行环境](#Android环境配置)

<img src="https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/ea6943e1-d2c1-4c27-99b4-ed2550abd6fd.jpg" style="zoom: 50%;" />

## uts扩展插件

当您运行带有uts插件的项目到Android设备时，会自动安装【uts开发扩展 - Android】插件，请务必安装。具体如下：

<img src="https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/411b69b4-e77e-4b1f-ad3d-880908619119.jpg" style="zoom: 50%" />

## 环境配置
> 下载插件后打开 HBuilderX到 【设置 - 插件配置】：如图

![image](https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/c7057273-2477-4b23-9046-dcfb3c73c3dc.png)

#### 上面的截图展示了以下配置：

##### 配置Gradle

1. 点击图标1的下载地址进入下载页面。如图所示，点击红圈部分下载工具包。

 ![image](https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/278d63c2-f1fe-4aac-a340-d63e0a10d8f8.png)
 
2. 将步骤1下载的内容解压后，找到bin目录下的执行脚本，填入图标3处。

**注意** mac为`%解压路径%/bin/gradle`；window为`%解压路径%\bin\gradle.bat`。

##### 配置SDK

点击图标2的下载地址进入安卓官网，提供如下两种形式。

###### ◇ 下载Android Studio
1. 如图所示，根据平台下载Android Studio

![image](https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/a6831fd6-931d-4b4a-91e6-de07bd56e082.png)

2. 安装后获取Android Studio中sdk的路径地址填入到图标4处。

**注意** 默认路径 mac为`/Users/用户名/Library/Android/sdk`；window为`C:\Users\用户名\AppData\Local\Android\Sdk`

###### ◇ 如不需要安装Android Studio可通过下载Command line tools only
1. 如图所示，根据平台下载Command line tools only。

![image](https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/cd46e8f5-e9b9-431b-a686-921bc75cdde6.png)
 
2. 下载解压后通过`%解压目录%/bin/sdkmanager脚本安装build-tools和platforms
```
sdkmanager --sdk_root=%sdk路径% --install "build-tools;30.0.0"

sdkmanager --sdk_root=%sdk路径% --install "platforms;android-30"
```

4. 将`%sdk路径%`配置到图标4处。

5. [sdkmanager使用文档](https://developer.android.google.cn/studio/command-line/sdkmanager)

**注意** 下载Android Studio和下载Command line tools only选择一种形式下载sdk即可。

##### 配置示例
配置后如下图（根据本地目录结构有所不同）

 ![image](https://f184e7c3-1912-41b2-b81f-435d1b37c7b4.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/dc253f26-1523-4bf6-a5f3-2cc4c5690a44.png)

**注意**

- 如果环境已存在可以直接设置本地的工具包路径
- 此插件依赖sdk目录下build-tools版本不低于30.0.0
- 此插件依赖sdk目录下platforms版本不低于android-30
