* 首先 Android 的权限机制，一直是关系着 Android 的安全问题
* 6.0 以前我们只在安装 Android App 的时候会看到涉及到的权限，但是我们大多都不会注意，而且申请到的权限我们都无法修改禁止
这样子就会给一些坏蛋利用权限来做一些损害用户利益的事情
到 6.0 之后如果我们需要获取一些权限不能仅仅在安装时显示权限了，而是需要通过弹窗来提醒用户，让用户自己来选择


* >###首先我们同样需要在 AndroidManifest.xml 添加需要的权限

```java
   <uses-permission android:name="android.permission.CALL_PHONE"/>
```

* >###这里就是最重要的一点了，我们需要用到在 Api23 中新加入的方法 checkSelfPermission()和requestPermissions()

