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