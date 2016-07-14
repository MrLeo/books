# web前端规范-JavaScript

标签： 荣智汇通,开发,web前端,javascript

---

# javascript 注释

> [HBuilder官方文档](http://ask.dcloud.net.cn/article/129)


``` javascript
/**
 * 文档注释写在这里
 * @alias aliasName (使用@alias可以给一个变量或者函数指定一个别名，代码提示时会提示该别名)
 * @description 描述内容 (使用@description可以在代码提示时显示被描述变量或者函数的描述信息。)
 * @example 示例内容 (使用@example可以提示代码示例。)
 * @extends {Type} (使用@extends用于标识继承于某个类型。)
 * @param {Type[,Type,...]} ParameterName=[Value1|Value2[|Value3|...]] 参数描述 (使用@param可以描述一个函数的参数以及参数类型，HBuilder扩展了参数值域的写法（目前只支持字符串值域）)
 * @property {Type[,Type,...]} propertyName 属性描述 (使用@property可以描述一个对象的属性)
 * @constructor (使用@constructor可以标识一个函数是构造函数)
 * @type {Type[,Type,...]} (使用@type可以定义某个变量的类型)
 * @return {Type[,Type,...]} (使用@return可以描述一个对象的属性)
 * @throw {TypeError} 参数类型不匹配 (异常信息)
 */
 function add(item){
    if(typeof item === "number"){
        arr.push(item)
    }
    else{
        throw new TypeError();
    }
}
```

