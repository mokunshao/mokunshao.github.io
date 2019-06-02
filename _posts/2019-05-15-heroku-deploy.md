---
title: 部署前后端连载项目到 Heroku
---

适用于前后端连载的项目。

这是说的前后端连载指的是：根目录是 node.js 的后端项目，根目录中的 client 文件夹是前端项目。

前端项目 build 完后删除除了 dist/build 目录以外的文件。

在根目录的 `server.js` 文件添加以下内容。

对于 Vue 项目：

```javascript
const path = require("path");

if (process.env.NODE_ENV === "production") {
  app.use(express.static("client/dist"));
  app.get("*", (req, res) => {
    res.sendFile(path.resolve(__dirname, "client", "dist", "index.html"));
  });
}
```

对于 React 项目：

```javascript
const path = require("path");

if (process.env.NODE_ENV === "production") {
  app.use(express.static("client/dist"));
  app.get("*", (req, res) => {
    res.sendFile(path.resolve(__dirname, "client", "build", "index.html"));
  });
}
```

对于前后端连载的项目，可以的使用在 heroku 上对前端部分进行 build。首先删除在前端部分的 `node_modules`，然后在 `package.json` 文件添加名为 `heroku-postbuild` 的 script。

```json
"scripts": {
  "start": "node server.js",
  "client-install": "yarn --cwd client install",
  "client": "yarn --cwd client start",
  "server": "nodemon server.js",
  "dev": "concurrently \"yarn server\" \"yarn client\"",
  "heroku-postbuild":" YARN_PRODUCTION=false yarn --cwd client install && yarn --cwd client build"
}
````

yarn 与 npm 的配置略有不同。

```json
YARN_PRODUCTION=false
NPM_CONFIG_PRODUCTION=false
```

```json
yarn --cwd client install && yarn --cwd client build
npm install --prefix client && npm run build --prefix client
```