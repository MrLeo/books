# C#开发规范



## 注释

- 类头 注释

```
/*****************************************************************
* ADD:-----------------------------------------------------------
* VER:1.0
* DTE:2015-4-21 10:39:36
* ATU:作者
* DES:说明
* MOD:-----------------------------------------------------------
* VER:1.1
* DTE:2015-4-21 10:39:36
* ATU:作者
* DES:说明
*****************************************************************/
```

- 方法 注释
``` csharp
//#region 获取xxx分页数据
/// <summary>
/// 获取xxx分页数据
/// </summary>
/// <param name="page">页码</param>
/// <returns>返回分页列表</returns>
public void GetPageList(int page){
        //TODO：未完成
        ...
    
        //#region 代码块 - 逻辑操作
        ...
        //#endregion
}
//#endregion
```

- Enumerate / Model 注释
``` csharp
public void BooleanStates{
        /// <summary>
        /// output true value only
        /// </summary>
        True,
        
        /// <summary>
        /// output false value only
        /// </summary>
        False,
        
        /// <summary>
        /// output true and false value both
        /// </summary>
        TrueFalse
}
```


## MVC - C#框架规范

- 
- 
- 