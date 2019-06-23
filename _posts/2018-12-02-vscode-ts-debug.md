---
title: VS Code 配置 TypeScript 调试
---

在调试之前先安装 typescript 和 ts-node。

在项目目录运行以下命令。

```
npm init -y
npm i -D ts-node typescript
```

在项目目录创建 `.vscode` 文件夹，在里面创建 `launch.json` 文件，内容如下

```json
{
  "configurations": [
    {
      "name": "ts-node",
      "type": "node",
      "request": "launch",
      "program": "${workspaceRoot}/node_modules/ts-node/dist/bin.js",
      "args": ["${relativeFile}"],
      "cwd": "${workspaceRoot}",
      "protocol": "inspector"
    }
  ]
}
```

然后打开整个项目时，就能使用 vscode 来 debug 了。

如果是 Mac 用户的话，上面配置的内容要改一下：

在命令行输入

```
which 项目的目录
```

得到的可能是 `/usr/local/bin/ts-node`

把上面的 program 属性改为 which 命令得出的内容。

```json
{
  "program": "/usr/local/bin/ts-node"
}
```
