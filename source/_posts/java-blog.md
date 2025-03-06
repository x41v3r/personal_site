---
title: java-blog
date: 2025-03-06 20:46:06
categories:
- Java
tags:
---

Convert a JSONObject instance to a JSON string.

```java
String str1 = jsonObject.toString();  // str1 doesn't contain the key-values whose is null

String str2 = JSONObject.toJSONString(jsonObject, SerializerFeature.WriteMapNullValue);  //the key-values with a null value is contained in str2
```

