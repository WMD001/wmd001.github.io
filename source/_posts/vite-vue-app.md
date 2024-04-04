---
title: 使用vite创建vue项目
date: 2024-04-04 23:37:34
tags: [vite, vuejs]
categories: [前端]
description: 
cover: 
banner: 
poster: # 海报（可选，全图封面卡片）
  topic: 标题上方的小字 # 可选
  headline: 大标题 # 必选
  caption: 标题下方的小字 # 可选
  color: 标题颜色 # 可选
---

## 安装`pnpm`

这次尝试使用`pnpm` 创建项目，所以首先需要安装`pnpm`

```powershell
npm install -g pnpm
```

## 创建项目

```powershell
pnpm create vite vite-vue-app --template vue-ts
```

使用`vue-ts` 模板创建项目

启动

```powershell
cd vite-vue-app
pnpm install
pnpm run dev
```

启动成功后，浏览器访问可以看到一下主页面

![](Untitled.png)

此时的项目目录

## 启用`vue-router`

### 安装

```powershell
pnpm add vue-router@4
```

### 配置路由

在src下创建router文件夹，文件夹内创建`index.ts`文件如下

```tsx router/index.ts
import {createRouter, createWebHistory, RouteRecordRaw} from "vue-router";

import HelloWorld from "../components/HelloWorld.vue";

const routes:RouteRecordRaw[] = [
    {
        path: '/hello',
        component: HelloWorld
    }
]

export const router = createRouter({
    history: createWebHistory(),
    routes,
})
```

修改`main.ts`文件

```tsx mian.ts
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'
import {router} from "./router";

const app = createApp(App);

// 使用路由
app.use(router);
app.mount('#app')

```

修改原有的`App.vue` 文件

```tsx App.vue
<template>
  <!-- 路由跳转处理 -->
  <router-view />
</template>
```

此时，我们在浏览器访问 `[localhost:5137](http://localhost:5137)` 时，不能访问到任何页面，因为没有配置根路径转发，而访问`localhost:5137/hello` 可以访问到`HelloWorld.vue` 组件中的内容，如图

![](Untitled1.png)

配置根路由

在components目录下新建Index.vue

```tsx Index.vue
<template>
  <div>
    <h1>This is index view.</h1>
  </div>
</template>

```

修改router/index.ts

```tsx router/index.ts
import {createRouter, createWebHistory, RouteRecordRaw} from "vue-router";

import HelloWorld from "../components/HelloWorld.vue";
import Index from "../components/Index.vue";

const routes:RouteRecordRaw[] = [
    {
        path: '/',
        component: Index,
    },
    {
        path: '/hello',
        component: HelloWorld
    }
]

export const router = createRouter({
    history: createWebHistory(),
    routes,
})
```

不需要重新启动，浏览器访问`localhost:5137` ，此时显示：

![](Untitled2.png)

至此，一个使用了TypeScript，vue-router的vue项目已经搭建成功，后续在src新增vue组件，并在router/index.ts中配置相对于的路由，即可实现新增组件页面的访问