# Front-end-engineering

How to build an engineered front-end library, combined with Github Actions, that automatically publishes to the full flow of Github and NPM

作者：molvqingtai
链接：https://juejin.cn/post/6971812117993226248

`package.json` 生成之后，我需要添加如下配置项:

```diff
   "main": "index.js",
+  "type": "module",
   "scripts": {
     "test": "echo \"Error: no test specified\" && exit 1"
   },
+  "publishConfig": {
+    "access": "public"
+  }
```

我们将项目定义为[ESM](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FJavaScript%2FGuide%2FModules "https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules")规范,前端社区正逐渐向[ESM](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FJavaScript%2FGuide%2FModules "https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules")标准迁移，从[Node v12.0.0](https://link.juejin.cn?target=https%3A%2F%2Fnodejs.org%2Ffr%2Fblog%2Frelease%2Fv12.0.0%2F "https://nodejs.org/fr/blog/release/v12.0.0/")开始，只要设置了 `"type": "module"`, Node 会将整个项目视为[ESM](https://link.juejin.cn?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2Fdocs%2FWeb%2FJavaScript%2FGuide%2FModules "https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules")规范，我们就可以直接写裸写 `import/export`。

`publishConfig.access`表示当前项目发布到[NPM](https://link.juejin.cn?target=https%3A%2F%2Fwww.npmjs.com%2F "https://www.npmjs.com/")的访问级别，它有 `restricted`和 `public`两个选项,`restricted`表示我们发布到[NPM](https://link.juejin.cn?target=https%3A%2F%2Fwww.npmjs.com%2F "https://www.npmjs.com/")上的是私有包（收费），访问级别默认为 `restricted`,因为我们是开源项目所以标记为 `public`。
