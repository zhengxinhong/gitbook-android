* 首先 Android 的权限机制，一直是关系着 Android 的安全问题
* 6.0 以前我们只在安装 Android App 的时候会看到涉及到的权限，但是我们大多都不会注意，而且申请到的权限我们都无法修改禁止
这样子就会给一些坏蛋利用权限来做一些损害用户利益的事情
到 6.0 之后如果我们需要获取一些权限不能仅仅在安装时显示权限了，而是需要通过弹窗来提醒用户，让用户自己来选择


* >###首先我们同样需要在 AndroidManifest.xml 添加需要的权限

```java
   <uses-permission android:name="android.permission.CALL_PHONE"/>
```

* >###这里就是最重要的一点了，我们需要用到在 Api23 中新加入的方法 checkSelfPermission()和requestPermissions()

```java
// 检查是否已经开启通讯录读取权限
   if (ContextCompat.checkSelfPermission(this,Manifest.permission.READ_CONTACTS) != PackageManager.PERMISSION_GRANTED){
      // 请求开启通讯录读取权限
      ActivityCompat.requestPermissions(MainActivity.this, new String[]{Manifest.permission.READ_CONTACTS},123);
      System.out.println("XH-没有权限");
      return;
   }else {
      System.out.println("XH-已经获取权限");
   }
   
   @Override
   public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
   super.onRequestPermissionsResult(requestCode, permissions, grantResults);
      switch (requestCode){
      case 123:{
         if (grantResults.length>0 && grantResults[0] == PackageManager.PERMISSION_GRANTED){
            GetNumber.getNumber(this);
            lv = (ListView)findViewById(R.id.phoneList);
            adapter = new MyAdapter(GetNumber.lists,this);
            lv.setAdapter(adapter);
         }else{
         
            System.out.println("XH-拒绝授权");
         }
      }
   }
}
```