---
title: java-autopoi
date: 2025-03-18 11:19:50
categories:
- Java
tags:
---

# 1 Summary

```java
public void handelImportExcel(MultipartFile file) {
    ImportParams params = new ImportParams();
    params.setTitleRows(0);
    params.setHeadRows(1);
    List<RevenueAnnualForecastTemplate> importList = null;
    List<RevenueAnnualForecastErrorVo> errorVoList = new ArrayList<>();
    RevenueAnnualForecastErrorVo errorVo;
    try {
        importList = ExcelImportUtil.importExcel(
                file.getInputStream(),
                RevenueAnnualForecastTemplate.class, params);  //analize
        if (null == importList || importList.isEmpty()){
            return Result.error("导入文件不能为空");
        }
    } catch (Exception e) {
        throw new JeecgBootException("AnaException");
    }
}
```



