---
title: 配置 typescript 调试
---

在调试之前先安装 typescript 和 ts-node。

在项目目录运行以下命令。

```
npm init -y
npm i -D ts-node typescript
```

在项目目录创建 `.vscode` 文件夹，在里面创建 `launch.json` 文件，内容如下

```javascript
{
    "configurations": [
        {
        "name": "ts-node",
        "type": "node",
        "request": "launch",
        "program": ${workspaceRoot}/node_modules/ts-node/dist/bin.js",
        "args": ["${relativeFile}"],
        "cwd": "${workspaceRoot}",
        "protocol": "inspector"
        }
    ]
}
```

然后打开整个项目时，就能使用 vscode 来 debug 了。