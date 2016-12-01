
# 临时指定淘宝 npm 源
```js
$ npm i node-sass@3.8.0 --registry=https://registry.npm.taobao.org
```


# 更新NPM包
npm-check是用来检查npm依赖包是否有更新，错误以及不在使用的，我们也可以使用npm-check进行包的更新。
安装[npm-check](https://github.com/dylang/npm-check)：
```
npm install -g npm-check
```
检查npm包的状态:
```
npm-check -u -g
```
![](https://segmentfault.com/image?src=http://upload-images.jianshu.io/upload_images/22188-aef0b264869c5366.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240&objectId=1190000005857342&token=621ff08a92f8cd8e6f0e6c3e7d67526f)
通过上下键可以移动光标，使用空格键可以选择需要处理的包，回车直接进行处理。
选择npm@3.10.2包升级到3.10.3：
```
? Choose which packages to update. npm@3.10.3

$ npm install --global npm@3.10.3 --color=always
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
/usr/local/lib
└─┬ npm@3.10.3
  ├── aproba@1.0.4
  ├── has-unicode@2.0.1
  └── read-package-tree@5.1.5

[npm-check] Update complete!
[npm-check] npm@3.10.3
[npm-check] You should re-run your tests to make sure everything works with the updates.
```