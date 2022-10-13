> HBuilderX 3.6+ 支持uts插件
> HBuilderX 3.6+ supports uts plugin

## 1 uts插件介绍
## 1 uts plugin introduction

### 什么是uts
### what is uts

uts，全称 uni type script，是一门跨平台的、高性能的、强类型的现代编程语言。
uts, the full name of uni type script, is a cross-platform, high-performance, strongly typed modern programming language.

它可以被编译为不同平台的编程语言，如：
It can be compiled into programming languages for different platforms, such as:
- web平台，编译为JavaScript
- web platform, compiled to JavaScript
- Android平台，编译为Kotlin
- Android platform, compiled to Kotlin
- iOS平台，编译Swift（暂未发布）
- iOS platform, compile Swift (not yet released)

uts 采用了与 ts 基本一致的语法规范，支持绝大部分 ES6 API。
uts adopts the same syntax specification as ts and supports most ES6 APIs.

如需详细了解uts语法，另见[uts语法介绍](../tutorial/syntax-uts.md)
For details on uts syntax, see also [uts syntax introduction](../tutorial/syntax-uts.md)

### 什么是uts插件
### What is uts plugin

现有的uni-app，仍以js引擎为主。但从HBuilderX 3.6.0开始，uni-app支持uts插件（暂时仅支持vue3编译器，后续补充vue2）。
The existing uni-app is still dominated by the js engine. But starting from HBuilderX 3.6.0, uni-app supports the uts plugin (for the time being, only the vue3 compiler is supported, and vue2 will be added later).

也就是uts的第一步不是完整开发一个独立的app，而是作为uni-app的插件。后续uts会持续迭代，达到完整开发app的水平。
That is, the first step of uts is not to develop a complete independent app, but as a plug-in for uni-app. Subsequent uts will continue to iterate to reach the level of complete app development.

uts插件编译到app平台时，在功能上相当于uni-app之前的app原生插件，也就是kotlin和swift开发的插件。
When the uts plugin is compiled into the app platform, it is functionally equivalent to the app native plugin before uni-app, that is, the plugin developed by kotlin and swift.

开发uts插件不需要熟悉kotlin和swift的语法，因为使用的是基于ts的语法。但需要熟悉Android和iOS的系统API，否则无法调用原生能力。
It is not necessary to be familiar with the syntax of kotlin and swift to develop uts plugin, because the syntax based on ts is used. However, you need to be familiar with the system APIs of Android and iOS, otherwise you cannot call native capabilities.

![uts插件结构](https://native-res.dcloud.net.cn/images/uts/UTS%E7%BB%93%E6%9E%84%E7%A4%BA%E6%84%8F%E5%9B%BE1.png)
![uts plugin structure](https://native-res.dcloud.net.cn/images/uts/UTS%E7%BB%93%E6%9E%84%E7%A4%BA%E6%84%8F %E5%9B%BE1.png)

### uts插件与uni原生语言插件的区别
### The difference between uts plugin and uni native language plugin

在HBuilderX 3.6以前，uni-app在App侧只有一种原生插件，即用java或object-c开发的插件。
Before HBuilderX 3.6, uni-app had only one native plug-in on the App side, that is, a plug-in developed with java or object-c.

在uts推出后，原来的“App原生插件”，更名为“App原生语言插件”。
After the launch of uts, the original "App native plugin" was renamed "App native language plugin".

不同的名字，代表它们需要开发者编写语言不同。但殊途同归，最后都编译为原生的二进制代码。
Different names mean that they require developers to write in different languages. But the same results are obtained, and they are finally compiled into native binary code.

|-				|原生语言插件				|uts插件					|
|- |Native language plugin |uts plugin |
|-				|-------					|--------						|
|开发语言		|java/oc					|uts							|
|Development language |java/oc |uts |
|开发环境		|Android Studio/XCode		|HBuilderX						|
|Development Environment |Android Studio/XCode |HBuilderX |
|打包方式		|外挂aar 等产出物			|编译时生成原生代码				|
|Packaging |Plug-in aar and other outputs |Generate native code when compiling |
|js层调用方式	|uni.requireNativePlugin()	|普通的js函数/对象，可以直接import|
|The calling method of the js layer |uni.requireNativePlugin() |Ordinary js functions/objects can be imported directly|

相当于原生语言插件，uts插件的优势：
Equivalent to native language plugins, the advantages of uts plugins:

1. 统一了编程语言（uts），一种语言开发所有平台，真正大前端。
1. Unified programming language (uts), one language to develop all platforms, really big front-end.
2. 统一了开发工具（HBuilderX），免除搭建复杂的原生开发环境。
2. The development tool (HBuilderX) is unified, eliminating the need to build a complex native development environment.
3. 插件封装中要理解的概念更少。 传统原生语言插件需要在js和原生层处理通信，使用各种特殊转换，使用特殊语法导入，注意事项很多。**uts统一为纯前端概念，简单清晰。**
3. There are fewer concepts to understand in plugin packaging. Traditional native language plug-ins need to handle communication at the js and native layers, use various special transformations, import using special syntax, and have many precautions. **uts is unified as a pure front-end concept, simple and clear. **
4. uts下前端和原生可以统一在HBuilderX中联调。而传统原生语言插件需要在多个开发工具间切换，联调复杂。
4. The front-end and native under uts can be jointly debugged in HBuilderX. However, traditional native language plug-ins need to switch between multiple development tools, and the joint debugging is complicated.

但当前的uts插件的完善度还没有达到原生语言插件的水平，虽然会陆续升级解决，但明示如下：
However, the completeness of the current uts plug-in has not yet reached the level of the native language plug-in. Although it will be upgraded one after another, it is clearly stated as follows:
1. uts插件只支持vue3编译器，还不支持vue2
1. The uts plugin only supports the vue3 compiler, not vue2
2. uts插件还不支持iOS
2. The uts plugin does not support iOS yet
3. uts插件无法封装nvue页面组件
3. uts plugin cannot encapsulate nvue page components
4. uts插件还无法在插件市场计费销售
4. The uts plug-in cannot be billed and sold in the plug-in market

### uts插件和Native.js的区别
### Difference between uts plugin and Native.js

- [Native.js](../tutorial/native-js.md)运行在js上，通过反射调用os api。功能和性能都不及真正的原生
- [Native.js](../tutorial/native-js.md) runs on js and calls os api through reflection. Features and performance are not as good as true native
- uts在app上不运行在js引擎里，是真正的原生。
- uts does not run in the js engine on the app, it is truly native.


## 2 创建uts插件
## 2 Create uts plugin

### uts插件目录结构
### uts plugin directory structure

在uni-app的项目工程下，提供了独立的目录`utssdk`，来存放uts插件。
Under the uni-app project, a separate directory `utssdk` is provided to store uts plugins.

当然官方更推荐使用[uni_modules](uni_modules.md)方式，这是更好的包管理方案。
Of course, the official recommendation is to use the [uni_modules](uni_modules.md) method, which is a better package management solution.

首先确保项目根目录存在uni_modules文件夹，如果不存在，需要手动创建一个。
First make sure that the uni_modules folder exists in the project root directory. If it does not exist, you need to create one manually.

![插件目录](https://native-res.dcloud.net.cn/images/uts/uni_modules.jpg)
![Plugin Directory](https://native-res.dcloud.net.cn/images/uts/uni_modules.jpg)

### 新建步骤拆解
### New step disassembly

右键点击`uni_modules`目录 -> 新建插件

![新建插件1](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin.jpg)
![New Plugin 1](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin.jpg)

选择类型 **uts原生插件**

![新建插件2](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin2_1.jpg)
![New Plugin 2](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin2_1.jpg)

为了避免和插件市场的其他插件冲突，建议起一个自己的插件前缀名称。

uts插件目录结构
uts plugin directory structure

![新建插件3](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin3_1.jpg)
![New Plugin 3](https://native-res.dcloud.net.cn/images/uts/new_uts_plugin3_1.jpg)


### package.json

package.json为uni_modules插件配置清单文件，负责描述插件的基本配置。


```json
{
  "id": "uts-helloworld",
  "displayName": "uts插件示例",
  "version": "0.1",
  "description": "uts插件示例",
  "uni_modules": {
    
  }
}
```

上面是一个默认的清单文件示例,关于package.json更多描述[详见](uni_modules.md#package.json)
The above is an example of a default manifest file, more description about package.json [see details](uni_modules.md#package.json)

### 插件的目录结构
### Plugin directory structure

<pre v-pre="" data-lang="">
	<code class="lang-" style="padding:0">
┌─common                          // 可跨端公用的uts代码。推荐，不强制
├─static                          // 静态资源
├─utssdk
│	├─app-android                 //Android平台目录
│	│	├─assets                  //Android原生assets资源目录，可选
│	│	├─libs                    //Android原生库目录，可选
│	│	├─res                     //Android原生res资源目录，可选
│	│	├─AndroidManifest.xml     //Android原生应用清单文件，可选
│	│	├─config.json             //Android原生配置文件
│	│	└─index.uts
│	├─app-ios                     //ios平台目录
│	│	├─config.json             //ios原生配置文件
│	│	└─index.uts
│	├─web                         //web平台目录
│	│	└─index.uts
│	└─mp-xxx                      // 其他平台目录
├─package.json                    // 插件清单文件
├─index.d.ts                      // 插件能力声明，可选
└─index.uts                       // 插件能力实现
</code>
</pre>


index.uts文件是程序主入口。如果插件根目录下没有index.uts，则会在编译到不同平台时，寻找分平台的目录下的index.uts文件。
The index.uts file is the main entry point of the program. If there is no index.uts in the root directory of the plugin, it will look for the index.uts file in the sub-platform directory when compiling to different platforms.

比如编译到app-android平台时，如果uts插件根目录没有index.uts，会寻找utssdk/app-android/index.uts。如果也没有找到，会报错。
For example, when compiling to the app-android platform, if the root directory of the uts plugin does not have index.uts, it will look for utssdk/app-android/index.uts. If it is not found, an error will be reported.

当同时存在分平台目录的index.uts和根目录index.uts时，会优先获取具体的分平台目录。
When the index.uts of the sub-platform directory and the index.uts of the root directory exist at the same time, the specific sub-platform directory will be obtained first.

开发者有多种组织自己代码的方式：
Developers have several ways to organize their code:
1. 在插件根目录的index.uts中写条件编译代码。简单的业务一个文件搞定
1. Write conditional compilation code in index.uts in the root directory of the plugin. Simple business with one file
2. 在插件根目录index.uts中写条件编译，import分平台的文件
2. Write conditional compilation in the plugin root directory index.uts, and import the files of different platforms
3. 不写根目录的index.uts，直接在分平台目录写index.uts。不跨端时，比如只做一个Android插件，这样写比较简单
3. Instead of writing index.uts in the root directory, write index.uts directly in the sub-platform directory. When it is not cross-end, such as only making an Android plug-in, it is relatively simple to write this way

index.d.ts文件是对当前插件能力的**声明**，用于语法提示。它不是必写项。

因为uts写好后，HBuilderX可以自动识别uts api并进行语法提示。它更多的用于后续uts插件加密时给予语法提示。

如果不熟悉d.ts，可以自行网上搜索，它属于ts标准技术。
If you are not familiar with d.ts, you can search online by yourself. It belongs to the standard technology of ts.

### App原生配置
### App native configuration

#### Android平台原生配置
#### Android platform native configuration

app-android 文件夹下存在Android平台原生配置，包括以下目录或文件
The native configuration of the Android platform exists in the app-android folder, including the following directories or files

|目录名/文件名			|用途									|
|directory name/file name |purpose |
|---					|---									|
|assets					|Android平台原生assets资源目录			|
|assets |Android platform native assets resource directory |
|libs					|Android平台原生引用的三方jar/aar目录		|
|libs |The third-party jar/aar directory natively referenced by the Android platform |
|res					|Android平台原生res资源目录				|
|res |Android platform native res resource directory |
|AndroidManifest.xml	|Android平台原生应用清单文件				|
|AndroidManifest.xml |Android platform native application manifest file |
|config.json			|Android平台下的配置文件					|
|index.uts				|主入口，index.d.ts声明的能力在Android平台下的实现	|


##### assets  
Android平台原生assets资源目录，建议只保存UTS插件内置的资源文件。

除了插件下有assets目录，项目下也有。注意2者的区别。
如果需要插件使用者配置（如三方SDK的授权文件），则插件作者应该在插件文档中告诉插件使用者，配置到项目的Android原生应用资源目录，而不是配置在插件目录下。[详见](https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-android)

##### libs  
Android平台原生三方库目录，支持以下类型文件：
The Android platform's native third-party library directory supports the following types of files:
- jar 
- aar

如果封装三方原生sdk为uni-app插件，可以将sdk的jar/aar文件放到此目录，但不推荐这么做，因为多个uts插件引用相同三方原生sdk时可能会产生冲突，如果sdk支持仓储，建议优先使用仓储，参考config.json的[dependencies](#dependencies)。  

如果使用的三方sdk包含了so库，也可以保存到此目录，需按Android的abi类型分目录保存。

关于libs目录的使用，可以参考 [Hello UTS](https://gitcode.net/dcloud/hello-uts/-/tree/master/uni_modules)

> 遗留事项: HBuilderX3.6.2版本对libs目录使用还不完善，[详见](#tempnotice)

##### res  
Android平台原生res资源目录，建议只保存UTS插件内置的资源文件。

除了插件下有res目录，项目下也有。注意2者的区别。一般使用者的配置不放在插件下，而放在自己的项目下。项目下配置[详见](https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-android)

注意：截止到HBuilderX3.6.2，uts插件无法使用res。图片资源建议放在assets目录。

##### AndroidManifest.xml  
Android原生应用清单文件，建议只保存UTS插件内置的清单文件配置。

除了插件下有AndroidManifest.xml，项目下也有。注意2者的区别。一般使用者的配置不放在插件下，而放在自己的项目下。项目下配置[详见](https://uniapp.dcloud.net.cn/tutorial/app-nativeresource-android)

##### config.json
uts插件在Android平台的原生层配置文件，可以在其中配置依赖仓储等gradle相关内容。
The uts plugin is in the native layer configuration file of the Android platform, where you can configure gradle-related content such as dependency repositories.

```json
{
	// 使用NDK时支持的CPU类型，可选
	// CPU type supported when using NDK, optional
	"abis": [
	    "使用NDK时支持的cpu类型, 可取值armeabi-v7a|arm64-v8a|x86|x86_64"
	],
    // 依赖的仓储配置，可选，打包时会合并到原生工程的build.gradle中
	"dependencies": [
		"androidx.core:core-ktx:1.6.0",
		{
			"id": "com.xxx.richtext:richtext",
			"source": "implementation 'com.xxx.richtext:richtext:3.0.7'"
		}
	],
    // Android系统版本要求，最低Android 5.0
    // Android system version requirements, minimum Android 5.0
	"minSdkVersion": 21
}
```

- abis  
当插件使用了NDK开发的so库时配置，描述插件支持CPU类型。  
可取值：armeabi-v7a、arm64-v8a、x86、x86_64

<a id="dependencies"/>

- dependencies  
配置插件依赖的仓储，云端打包时会合并到Android原生工程的build.gradle的  
数组类型，数组中的项可以是字符串类型或JSON对象  
对于字符串类型项，将会作为`implementation`方式依赖添加到build.gradle中，上面示例中"androidx.core:core-ktx:1.6.0"将会添加以下配置  
```
dependencies {
  implementation 'androidx.core:core-ktx:1.6.0'
}
```
对于JSON类型项，将会把source字段值作为gradle源码添加到build.gradle中，上面示例中"id": "com.xxx.richtext:richtext"项将会添加以下配置  
```
dependencies {
  implementation 'com.xxx.richtext:richtext:3.0.7'
}
```

> 遗留事项: HBuilderX3.6.1版本对dependencies配置支持还不完善，[详见](#tempnotice)

- minSdkVersion  
插件支持的Android最低版本，整数类型，取值范围为Android API Level  
默认uni-app最低支持版本为19，即Android4.3.3


**注意：**

Android平台原生配置需提交云端打包才能生效，真机运行时需使用[自定义基座](https://uniapp.dcloud.net.cn/tutorial/run/run-app.html#customplayground)

#### HX3.6.2 临时注意事项@tempnotice

使用HBuilderX 3.6.2版本及更早版本，关于原生依赖的处理有部分不完善，需要注意以下事项：

+ config.json 目前还不支持配置仓库依赖，需要将gradle配置的库手动下载后，放置在libs目录，使用手动添加的方式集成

+ uni-app引擎内置了部分依赖库（比如androidX，清单详见下方），如你的插件需使用相同依赖，请注意：
	
	1. 确保与内置的依赖版本一致。
	
	2. 真机运行时，需将依赖库copy到libs目录下。但注意，打包自定义基座时需先从libs中暂时移除，避免打包类重复报错。生成自定义基座之后再将这些内置依赖库移回libs目录下，否则无法真机运行。
	
[内置依赖清单](https://uniapp.dcloud.net.cn/plugin/androidInnerLib.html)
[Built-in dependency list](https://uniapp.dcloud.net.cn/plugin/androidInnerLib.html)

这些遗留事项会尽快升级完善。

## 3 开发uts原生插件
## 3 Develop uts native plugin

以Android平台获取电量为例，介绍uts原生插件开发步骤
Taking the Android platform to obtain electricity as an example, the development steps of the uts native plug-in are introduced.

![OSAPI示例](https://native-res.dcloud.net.cn/images/uts/uts_osapi_demo_1.jpg)
![OSAPI example](https://native-res.dcloud.net.cn/images/uts/uts_osapi_demo_1.jpg)

在Android平台目录下，编辑index.uts，键入以下内容。
In the Android platform directory, edit index.uts and type the following.


```ts
// index.uts

// 引用android api
// refer to android api
import Context from "android.content.Context";
import BatteryManager from "android.os.BatteryManager";
// 引用uts环境库
// Refer to the uts environment library
import { getAppContext } from "io.dcloud.uts.android";

export function getBatteryCapacity(): string {
	// 获取android系统 application上下文
	// Get the android system application context
    const context = getAppContext();
    if (context != null) {
        const manager = context.getSystemService(
            Context.BATTERY_SERVICE
        ) as BatteryManager;
        const currentLevel: number = manager.getIntProperty(
            BatteryManager.BATTERY_PROPERTY_CAPACITY
        );
        return '' + currentLevel + '%';
    }
    return "0%";
}

```

`io.dcloud.uts.android`库介绍文档[见下](#iodcloudutsandroid)
`io.dcloud.uts.android` library introduction document [see below](#iodcloudutsandroid)

至此，我们已经完成一个Android平台上获取电量的原生能力封装。
So far, we have completed the packaging of the native ability to obtain electricity on the Android platform.

在下一节，将介绍前端如何使用这个插件。

注：HBuilderX的代码提示系统，支持在uts文件中对Android的原生API进行提示。
Note: HBuilderX's code prompt system supports prompting Android's native API in the uts file.


## 4 前端使用插件
## 4 Front-end using plugins

虽然uts插件由uts语法开发，但前端引用插件并不要求一定需要ts，普通js即可引用uts插件。
Although the uts plug-in is developed by uts syntax, the front-end reference plug-in does not necessarily require ts, and ordinary js can reference the uts plug-in.

下面介绍两种常见的引入方式
Two common introduction methods are described below.

 **泛型引用**
 **Generic reference**

作为一个对象全部import进来，然后通过点运算符调用这个对象的方法或属性。
All imported as an object, and then call the method or property of this object through the dot operator.

```js
// 先引用，全部导入，对象起名为UTSHello
// Reference first, import all, and name the object UTSHello
import * as UTSHello from "../../../uni_modules/uts-osapi";

// 然后使用UTSHello的方法
// Then use the method of UTSHello
UTSHello.getBatteryCapacity()
```


**显性引用**
**Explicit references**

从可导出的选项里import 1个或多个（逗号分隔），然后直接使用导出的方法或属性。
Import 1 or more (comma-separated) from the exportable options, and then use the exported methods or properties directly.

```js
//先引用，导入指定方法或属性
//First reference, import the specified method or property
import {
  getBatteryCapacity
} from "../../../uni_modules/uts-osapi";

// 然后使用导入的方法
// then use the imported method
getBatteryCapacity()
```

关于电量这个插件，插件市场已经提供好了现成的插件，除了Android，还同时支持了web和小程序，可以去下载体验。[详见](https://ext.dcloud.net.cn/plugin?id=9295)
Regarding the plug-in of electricity, the plug-in market has already provided ready-made plug-ins. In addition to Android, it also supports web and MiniApp, which can be downloaded and experienced. [See details](https://ext.dcloud.net.cn/plugin?id=9295)

更多开发示例，可以参考 [HelloUTS](https://gitcode.net/dcloud/hello-uts)。
For more development examples, you can refer to [HelloUTS](https://gitcode.net/dcloud/hello-uts).

## 5 真机运行
## 5 Real machine running

### 5.1 UTS支持真机运行
### 5.1 UTS supports real machine operation

**uts虽然是原生代码，但同样具有真机运行功能**
**Although uts is a native code, it also has the function of running on a real machine**

若HBuilderX中没有`uts编译运行插件`，在第一次运行时会自动下载。
If there is no `uts compile and run plugin` in HBuilderX, it will be downloaded automatically when it is run for the first time.

在Android上，运行体验与uni-app基本无差异。一样可以热刷新，打印console.log。
On Android, the running experience is basically the same as uni-app. You can also hot refresh and print console.log.

### 5.2 自定义基座
### 5.2 Custom Dock

自定义基座也支持uts插件。
Custom docks also support uts plugins.

与原生插件一样,涉及以下场景,需要自定义基座后方能生效:
Like native plugins, it involves the following scenarios, which require a custom base to take effect:

- 1 集成三方sdk
- 1 integrated third party sdk
- 2 新增资源(包括res/asset 等)
- 2 New resources (including res/asset, etc.)

总结来说，就是所有 涉及新增依赖/gralde配置/androidManifest.xml/资源 等标准基座不具备的能力时，需要自定义基座
To sum up, all the capabilities that standard docks do not have, such as new dependencies/gralde configuration/androidManifest.xml/resources, require a custom dock


### 5.3 遗留问题
### 5.3 Legacy issues

截止到HBuilderX 3.6.2 时遗留事项：
- 不能debug断点uts源码
- iOS版还未发布
- uts插件还不支持远程仓库依赖，目前添加插件的配置方法参考 [这个章节](#tempnotice)
- uts插件无法使用res。图片资源建议放在assets目录。

遗留事项后续升级完善。
Remaining matters will be upgraded and improved later.

## 6 云端打包
## 6 Cloud Packaging

正常支持云端打包。
Cloud packaging is normally supported.

注意：虽然uts在真机运行时支持热刷，但打包后uts编译为了纯原生二进制代码，不支持wgt热更新。
Note: Although uts supports hot flashing when the real machine is running, after packaging, uts is compiled into pure native binary code and does not support wgt hot update.

打包若包含了已经内置的依赖库，则需注意参考 [这个章节](#tempnotice)

## uni-app的Android内置库@iodcloudutsandroid

在uts里，Android的所有api都可以访问。同时DCloud提供了`io.dcloud.uts.android`库，处理在uni-app下的特殊情况。
In uts, all APIs of Android can be accessed. At the same time, DCloud provides the `io.dcloud.uts.android` library to handle special cases under uni-app.

```ts
import { getAppContext } from "io.dcloud.uts.android";
```

### getAppContext

获取当前应用Application上下文，对应android平台 Context.getApplicationContext 函数实现
Get the application context of the current application, corresponding to the android platform Context.getApplicationContext function implementation

Android开发场景中，调用应用级别的资源/能力，需要使用此上下文。更多用法，参考[Android官方文档](https://developer.android.google.cn/docs)


```ts
// [示例]获取asset下的音频，并且播放
// [Example] Get the audio under the asset and play it
let assetManager = getAppContext()!.getAssets();
let afd = assetManager.openFd("free.mp3");
let mediaPlayer = new MediaPlayer();
mediaPlayer.setDataSource(afd.getFileDescriptor(),afd.getStartOffset(), afd.getLength());
mediaPlayer.prepare();
mediaPlayer.start();
```

### getUniActivity

获取当前插件所属的activity实例，对应android平台 getActivity 函数实现
Get the activity instance to which the current plugin belongs, corresponding to the android platform getActivity function implementation

Android开发场景中，调用活动的级别的资源/能力，需要使用此上下文。更多用法，参考[Android官方文档](https://developer.android.google.cn/docs)

```ts
// [示例]获取当前activity顶层容器
// [Example] Get the current activity top-level container
let frameContent = decorView.findViewById<FrameLayout>(android.R.id.content)
```

### getResourcePath(resourceName:String)

获取指定插件资源的运行期绝对路径
 
```ts
// [示例]获取指定资源路径
// [Example] Get the specified resource path
// 得到文件运行时路径: `/storage/emulated/0/Android/data/io.dcloud.HBuilder/apps/__UNI__3732623/www/uni_modules/test-uts-static/static/logo.png`
// Get the file runtime path: `/storage/emulated/0/Android/data/io.dcloud.HBuilder/apps/__UNI__3732623/www/uni_modules/test-uts-static/static/logo.png`
getResourcePath("uni_modules/test-uts-static/static/logo.png")

```

### onAppActivityPause

App的activity onPause时触发

```ts
onAppActivityPause(() => {
    let eventName = "onAppActivityPause - " + Date.now();
    console.log(eventName);
});
```

### onAppActivityResume

App的activity onResume时触发

```ts
onAppActivityResume(() => {
     let eventName = "onAppActivityResume - " + Date.now();
     console.log(eventName);
});
```

### onAppActivityDestroy

App 的 activity onDestroy时触发

```ts
onAppActivityDestroy(() => {
     let eventName = "onAppActivityDestroy- " + Date.now();
     console.log(eventName);
});
```

### onAppActivityBack

App 的 activity 回退物理按键点击时触发

```ts
onAppActivityBack(() => {
     let eventName = "onAppActivityBack- " + Date.now();
     console.log(eventName);
});
```

### onAppActivityRequestPermissionsResult
App 的 activity 获得权限请求结果的回调

```ts
onAppActivityRequestPermissionsResult((requestCode: number,
                                                     permissions: MutableList<string>,
                                                     grantResults: MutableList<number>) => {
		/**
		 * 0 已同意
		 * -1 已拒绝
		 */
		console.log(grantResults);
		console.log(permissions);   
		console.log(requestCode);
	});

//发起定位权限申请
//Initiate a positioning permission application
ActivityCompat.requestPermissions(getUniActivity()!,
	    arrayOf(Manifest.permission.ACCESS_COARSE_LOCATION), 1001);

```


## 常见问题
## common problem

### 常见报错
### Common errors

- [plugin:vite:resolve] Failed toresolve entry for package "插件路径"
- [plugin:vite:resolve] Failed toresolve entry for package "plugin path"
	HBuilderX 的最低要求为3.6.0，低于此版本无法import uts插件，编译时将报错。
	The minimum requirement of HBuilderX is 3.6.0. The uts plugin cannot be imported below this version, and an error will be reported when compiling.

- 文件查找失败：'uts插件路径'
- file lookup failed: 'uts plugin path'
    目前暂未支持 vue2，vue2 的uni-app项目无法import uts插件，编译时将报错。
    Currently, vue2 is not supported. The uni-app project of vue2 cannot import the uts plugin, and an error will be reported when compiling.

### Float类型传参
### Float type parameter

android很多布局参数强制要求Float，但是ts中没有内置这种类型。可以使用下面的代码实现转换
Float is mandatory for many layout parameters in android, but there is no built-in type of this type in ts. The conversion can be achieved using the following code

```ts
let textSize =  30.0.toFloat();
```

### 匿名内部类

UTS目前还不支持匿名内部类的写法，在android中类似这样的场景

```kotlin
getUniActivity()!!.runOnUiThread(Runnable(){
    // do something
});
```

需要声明一个实现类，再新建实例的方式实现，代码如下

```
class AddUIRunnable extends Runnable {
    override run():void {
		// do something
    }
};
let uiRunable = new AddUIRunnable();
getUniActivity()!.runOnUiThread(uiRunable)
```

### 泛型参数
### Generic parameters

android中UI相关的api，很多会要求泛型，目前uts中可以使用下面的代码实现
Many UI-related APIs in android will require generics. Currently, the following code can be used in uts.

```ts
let frameContent = decorView.findViewById<FrameLayout>(android.R.id.content)
let layoutParam = new FrameLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT,ViewGroup.LayoutParams.WRAP_CONTENT);
```

## 路线图
## route map

uts是一个宏大工程，产品将分阶段发布。近期将陆续发布：
1. iOS相关功能
2. 支持vue2编译器
3. debug
4. UI操作能力
4. UI operation ability
5. 插件市场支持uts插件的加密和计费销售
5. The plug-in market supports encryption and billing sales of uts plug-ins

最终，uts不再是uni-app的插件，而是应用的主体。（现在是以js为主，uts作为插件存在，主引擎仍然在v8或jscore里）
Ultimately, uts is no longer a plugin for uni-app, but the body of the app. (Now it is mainly js, uts exists as a plug-in, and the main engine is still in v8 or jscore)

那时，即便是最复杂的应用，比如微信，也可以使用uts来开发，毫无功能和性能的影响。
At that time, even the most complex applications, such as WeChat, could be developed using uts without any functional or performance impact.


## 示例项目
## Example project

DCloud提供了 Hello UTS示例，[详见](https://gitcode.net/dcloud/hello-uts)。
DCloud provides an example of Hello UTS, [see details](https://gitcode.net/dcloud/hello-uts).

插件市场提供了一个跨Android、web、微信小程序的电量获取封装插件，[详见](https://ext.dcloud.net.cn/plugin?id=9295)
The plug-in market provides a power acquisition package plug-in across Android, web, and WeChat MiniApp, [see details](https://ext.dcloud.net.cn/plugin?id=9295)
