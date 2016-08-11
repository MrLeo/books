# web前端命名规范
![](http://p3.pstatp.com/large/ba2000945a2fea407c2)
> web语义化：
> 1. **标签语义化**，如在合适的地方用合适的语义化标签，如头部可用`<header>`、尾部可用`<footer>`；
> 2. **命名语义化**，包括html的id和class的命名，javascript相关命名；如#header{}、.footer{}、等。

*下面是常见的命名参考规范：*

## 主体
- 头部：`header`
- 内容：`content/container`
- 尾部：`footer`
- 导航：`nav`
- 侧栏：`sidebar`
- 栏目：`column`
- 整体布局：`wrapper`
- 左右中：`left / right / center`
- 登录条：`loginbar`
- 标志：`logo`
- 广告：`banner`
- 页面主体：`main`
- 热点：`hot`
- 新闻：`news`
- 下载：`download`
- 子导航：`subnav`
- 菜单：`menu`
- 子菜单：`submenu`
- 搜索：`search`
- 友情链接：`friendlink`
- 页脚：`footer`
- 版权：`copyright`
- 滚动：`scroll`
- 标签页：`tab`
- 文章列表：`list`
- 提示信息：`msg`
- 小技巧：`tips`
- 栏目标题：`title`
- 加入：`join`
- 指南：`guild`
- 服务：`service`
- 注册：`regsiter`
- 状态：`status`
- 投票：`vote`
- 合作伙伴：`partner`

## css注释的写法
如内容区，Html注释的写法 ：`<!--header头部-- >`
![](http://p1.pstatp.com/large/bdc00029cab87400452)

## id的命名规范
1. 页面结构
    - 容器: `container`
    - 页头：`header`
    - 内容：`content/container`
    - 页面主体：`main`
    - 页尾：`footer`
    - 导航：`nav`
    - 侧栏：`sidebar`
    - 栏目：`column`
    - 页面外围控制整体布局宽度：`wrapper`
    - 左右中：`left right center`
2. 导航
    - 导航：`nav`
    - 主导航：`mainnav`
    - 子导航：`subnav`
    - 顶导航：`topnav`
    - 边导航：`sidebar`
    - 左导航：`leftsidebar`
    - 右导航：`rightsidebar`
    - 菜单：`menu`
    - 子菜单：`submenu`
    - 标题：`title`
    - 摘要：`summary`
3. 功能
    - 标志：`logo`
    - 广告：`banner`
    - 登陆：`login`
    - 登录条：`loginbar`
    - 注册：`regsiter`
    - 搜索：`search`
    - 功能区：`shop`
    - 标题：`title`
    - 加入：`joinus`
    - 状态：`status`
    - 按钮：`btn`
    - 滚动：`scroll`
    - 标签页：`tab`
    - 文章列表：`list`
    - 提示信息：`msg`
    - 当前的：`current`
    - 小技巧：`tips`
    - 图标：`icon`
    - 注释：`note`
    - 指南：`guild`
    - 服务：`service`
    - 热点：`hot`
    - 新闻：`news`
    - 下载：`download`
    - 投票：`vote`
    - 合作伙伴：`partner`
    - 友情链接：`link`
    - 版权：`copyright`
4. class的命名:
    - 颜色：使用颜色的名称或者16进制代码，如：
        > .red { color: red; } 
        > .f60 { color: #f60; } 
        > .ff8600 { color: #ff8600; }
    - 字体大小，直接使用“font+字体大小”作为名称，如：
        > .font12px { font-size: 12px; }    
        > .font9pt {font-size: 9pt; }
    - 对齐样式，使用对齐目标的英文名称，如：
        > .left { float:left; } 
        > .bottom { float:bottom; }
    - 标题栏样式，使用“类别+功能”的方式命名，如：
        > .barnews { } 
        > .barproduct { }

## 注意事项：
1. 一律小写；
2. 尽量用英文；
3. 尽量不加中杠和下划线；
4. 尽量不缩写，除非一看就明白的单词，如：wrapper可以写成wrap。
5. css文件命名规范：
    - 主要的 `master.css`
    - 模块 `module.css`
    - 基本共用 `base.css`
    - 布局，版面 `layout.css`
    - 主题 `themes.css`
    - 专栏 `columns.css`
    - 文字 `font.css`
    - 表单 `forms.css`
    - 补丁 `mend.css`
    - 打印 `print.css`