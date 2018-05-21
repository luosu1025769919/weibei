# weibei
微贝用于支付
## 1.sdk配置


### 1.将我方提供的weibei_1.0.2.jar 放入你的libs目录,
jar下载地址：https://doc.vvpay.cn/down/android/weibei_1.0.2.jar
### 2.在你的Androidmanifest.xml文件中添加一个activity
```xml
<activity
	android:name="com.weibei.activity.WebActivity"
	android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
</activity>
```


## 2.权限需要：
```xml
<uses-permission android:name="android.permission.INTERNET" />
```

## 3.接口说明：
### 1.游戏初始化
> /\*\*
 \* 
 \* @param appid 我方提供的游戏id
 \* @param appkey  我方提供
 \*/
    public static void init(String appid, String appkey) {}

示例： 
```java
WeibeiSdk.init("112000","6f11c05f21d3a28f64bcbb846e388439");
```

### 2.调起支付接口

> /\*\*
 \* 
 \* @param activity   传入你当前activity
 \* @param jsonMsg    订单数据字符串
 \* @param listener   支付回调
 \*/
    public static void opensyt(Activity activity, String jsonMsg, WeibeiListener listener) {}


示例:
```java
WeibeiSdk.opensyt(MainActivity.this, jo.toString(), new WeibeiListener() {
	@Override
	public void onCancel(String jsonMsg) {
		Toast.makeText(MainActivity.this,"取消："+jsonMsg,Toast.LENGTH_LONG).show();
	}

	@Override
	public void onSuccess(String jsonMsg) {
		Toast.makeText(MainActivity.this,"成功："+jsonMsg,Toast.LENGTH_LONG).show();
	}
	@Override
	public void onFailure(String jsonMsg) {
		Toast.makeText(MainActivity.this,"错误："+jsonMsg,Toast.LENGTH_LONG).show();
	}
});
```


## 4.代码混淆

> **-dontwarn com.weibei.\*\* 
-keep class com.weibei.\*\*{*; }**
