### uni.onUserCaptureScreen(CALLBACK)

监听用户主动截屏事件，用户使用系统截屏按键截屏时触发此事件。
 
**平台差异说明**

|App|H5|微信小程序|支付宝小程序|百度小程序|字节跳动小程序、飞书小程序|QQ小程序|快手小程序|京东小程序|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|√|x|√|√|√|√|√|√|√|

> 在 App 平台本 API 是 [uni ext api](https://uniapp.dcloud.net.cn/api/extapi.html)，需下载插件：[uni-usercapturescreen](https://ext.dcloud.net.cn/plugin?name=uni-usercapturescreen)

**CALLBACK返回参数：**

无

**代码示例**

```javascript
uni.onUserCaptureScreen(function() {
    console.log('用户截屏了')
});
```

**注意**

Android的截屏监听原理是监听相册中截屏目录的文件新增，需赋予App本地文件读取权限。

### uni.offUserCaptureScreen(function callback)

用户主动截屏事件。取消事件监听。


**平台差异说明**

|App|H5|微信小程序|支付宝小程序|百度小程序|字节跳动小程序、飞书小程序|QQ小程序|快手小程序|京东小程序|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|√|x|√|√|√|√|x|√|√|

> 在 App 平台本 API 是 [uni ext api](https://uniapp.dcloud.net.cn/api/extapi.html)，需下载插件：[uni-usercapturescreen](https://ext.dcloud.net.cn/plugin?name=uni-usercapturescreen)

**参数**

|属性	|	类型|说明|
|--	|--	|--	|
|回调函数|	Function|用户主动截屏事件的回调函数|
