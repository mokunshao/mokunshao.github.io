---
title: yarn 与 npm
---

## yarn 国内加速

```
yarn config set registry https://registry.npm.taobao.org
```

## 初始化

```
yarn init
// npm init

yarn init -y
// npm init -y
```

## 安装到 "dependencies"

```
yarn add [package]
// npm install [package] --save 
```

## 安装到 "devDependencies"

```
yarn add [package] --dev
// npm install [package] --save-dev
```

## 安装全局依赖 

```
yarn global add [package]
// npm install -g [package]
```

## 安装 package.json 里的所有依赖包

```
yarn install
// npm install
```

## 删除依赖

```
yarn remove [package]
// npm uninstall [package]
```

## 列出依赖

```
yarn list
// npm list
```

## 运行 script

```
yarn run [script]
// npm run [script]
```

## 更新依赖

```
yarn upgrade [package]
// npm update [package]
```