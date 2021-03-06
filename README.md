LeanCloud JavaScript SDK
====
[![Build Status](https://img.shields.io/travis/leancloud/javascript-sdk.svg?style=flat-square)](https://travis-ci.org/leancloud/javascript-sdk)
[![Codecov](https://img.shields.io/codecov/c/github/leancloud/javascript-sdk.svg?style=flat-square)](https://codecov.io/github/leancloud/javascript-sdk)
[![David](https://img.shields.io/david/leancloud/javascript-sdk.svg?style=flat-square)](https://david-dm.org/leancloud/javascript-sdk)
[![npm](https://img.shields.io/npm/v/leancloud-storage.svg?style=flat-square)](https://www.npmjs.com/package/leancloud-storage)


JavaScript SDK for [LeanCloud](http://leancloud.cn/).

## 安装

```
// npm 安装
npm install leancloud-storage --save
// npm 安装 pre-release 版本
npm install leancloud-storage@next --save

// bower 安装
bower install leancloud-storage --save
```
文档
----
- [安装文档](https://leancloud.cn/docs/sdk_setup-js.html)
- [使用文档](https://leancloud.cn/docs/leanstorage_guide-js.html)
- [API 文档](https://leancloud.github.io/javascript-sdk/docs/)

支持
----
* 如果你发现了新的 bug，或者有新的 feature request，请新建一个 issue
* 在使用过程中遇到了问题时
  * 如果你购买了技术支持服务，请新建一个 ticket。
  * 也可以在 [论坛](https://forum.leancloud.cn/) 提问、讨论。

贡献
----
如果你希望为这个项目贡献代码，请按以下步骤进行：

* `fork` 这个项目
* `npm install` 安装相关依赖
* 开发和调试
  * 浏览器环境执行 `gulp dev`，会自动启动 `demo` 目录，可在 `test-es6.js` 中修改和测试，`test-es5.js` 为自动生成的代码
  * Nodejs 环境同样在 `demo` 目录中，通过执行 `node test-es6.js` 开发与调试。推荐安装 `node inspector` 来调试，安装后执行 `node-debug test-es6.js`。每次修改代码后，如果开发代码引用的是 dist 目录中的代码，需要执行 `gulp release`
* 确保测试全部通过 `npm run test`，浏览器环境打开 `test/test.html`
* 提交并发起 `Pull Request`

项目的目录结构说明如下：

```
├── dist                               // 编译之后生成的文件将会在此目录下
│   ├── av-es6.js                      // 合并后的完整源码（ES6 版本）
│   ├── av.js                          // 合并并编译后的完整源码（ES5 版本）
│   ├── av-min.js                      // 合并、压缩并编译后的源码（ES5 版本）
│   ├── node                           // 目录中为生成的 nodejs 版本代码
│   └── ...
├── src
│   ├── index.js                          // node.js 环境入口文件
│   ├── browserify-wrapper             // 目录中为针对 node.js 与浏览器环境之间差异的不同实现
│   └── ...
└── test                               // 单元测试
```

## 发布流程

0. 遵循 semver 提升版本号
  * src/version.js
  * package.json
  * bower.json
0. 对照 commit 历史写 changelog
0. 提交当前所有改动
0. 等待持续集成 pass
0. 使用 GitHub 基于 dist 分支发布一个 release（for bower）
0. Fetch and checkout remote `dist` branch 并确认该提交的内容是即将发布的版本
0. npm publish（`npm publish`，需 npm 协作者身份），如果是 pre-release 版本需要带 next tag
0. 发布到 CDN，需要七牛权限（执行 `gulp upload`）
