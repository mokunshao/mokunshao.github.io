---
title: 项目部署到 Github Pages 前的配置
---

## parcel-bundler

在 package.json 里添加。

```json
{
  "scripts": {
    "build": "parcel build index.html --public-url ./"
  }
}
```

## vue-cli

新建 vue.config.js 的内容如下。

```javaScript
module.exports = {
  baseUrl: process.env.NODE_ENV === "production" ? "./" : "/"
};
```

## create-react-app

在 package.json 里添加。

```json
{
  "homepage": "//username.github.io/project/build",
}
```