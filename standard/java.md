# Java开发规范


## 注释
- 类 注释
```java
/** 
 * 类名称：CheckUserController
 * 创建人：lilei
 * 创建时间：2015-05-23
 */
@Controller
@RequestMapping(value="/checkuser")
public class CheckUserController extends BaseController {
	//代码
}
```	

- 方法 注释
```java
/**
 * 处理VIP邀请码利率
 * @param inviteCode 邀请码
 * @param zfUser 当前用户
 * @return 利率
 * @throws Exception 
 */
public BigDecimal operationVipInviteRate(String inviteCode,ZFUser zfUser) throws Exception{
	//代码
}
```

- Enumerate / Model 注释


## JavaFrameWork - Java框架规范

- 非必要情况，不要用一个对象反复保存查询结果
- 代码要对齐，该缩进缩进
- 

