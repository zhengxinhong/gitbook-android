### Java集合框架

![](/assets/java集合框架.gif)

Java 集合框架主要包括两种类型的容器，一种是集合（Collection），存储一个元素集合，另一种是图（Map），存储键/值对映射。Collection 接口又有 3 种子类型，List、Set 和 Queue，再下面是一些抽象类，最后是具体实现类，常用的有 ArrayList、LinkedList、HashSet、LinkedHashSet、HashMap、LinkedHashMap 等等。


##### List

```java
List<String>  result = new ArrayList<>();  //新建数组
for (int i=0 ;i<jsonArray.length();i++){
   jsonObject = jsonArray.getJSONObject(i);
   String phone_number = jsonObject.getString("pHONE_ID");
   result.add(phone_number); //添加值
}

```