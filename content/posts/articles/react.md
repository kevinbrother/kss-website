---
title: react
date: 2025-11-12 
---

## 原因

react 一直处于会用的阶段，但是由于不懂他的内部原理，个人对他的 hooks 吐槽颇多，比如各种 useMemo, useCallback, useEffect 等各种需要手动优化的方式。hooks 不能在条件中写等限制。个人其实是不太能接受的，所以想深入学习下，并分析下他的设计架构，主要参考网上的资料和官方文档

## React

## 老架构（v15） 与新架构 （v16+）

### 老架构的状况

#### 未中断

![alt text](../../images/react/v15_render.png)

- Reconciler和Renderer是交替工作的，当第一个li在页面上已经变化后，第二个li再进入Reconciler。
- 由于整个过程都是同步的，所以在用户看来所有 DOM 是同时更新的。

#### 被中断

![alt text](../../images/react/v15_render_interupt.png)

- 当第一个li完成更新时中断更新，即步骤 3 完成后中断更新，此时后面的步骤都还未执行。
- 用户本来期望123变为246。实际却看见更新不完全的 DOM！（即223）
- 基于这个原因，React决定重写整个架构。

### 架构对比

- 老架构：基于同步渲染，单线程阻塞式渲染，更新时会阻塞主线程，用户交互会有卡顿
  - Reconciler(协调器): 负责比较新旧虚拟 DOM 树的差异，生成更新补丁
    - 递归处理虚拟 DOM
  - Renderer(渲染器): 负责将更新补丁应用到真实 DOM 上，完成 UI 更新

- 新架构：基于异步渲染，采用了协作式调度，能够将渲染任务拆分成多个小任务，避免阻塞主线程，提高用户交互的流畅度
  - Scheduler（调度器）: 负责调度任务的执行顺序和优先级，高优先级任务（如用户交互）会优先进入 Reconciler，低优先级任务（如数据加载）会在空闲时间执行
  - Reconciler（协调器）： 负责比较新旧虚拟 DOM 树的差异，生成更新补丁
  - Renderer（渲染器）： 负责将更新补丁应用到真实 DOM 上，完成 UI 更新

## React V16 架构深入分析

### 更新流程

![alt text](../../images/react/v16_render.png)

- 其中红框中的步骤随时可能由于以下原因被中断：
  - 有其他更高优任务需要先更新
  - 当前帧没有剩余时间
  - 由于红框中的工作都在内存中进行，不会更新页面上的 DOM，所以即使反复中断，用户也不会看见更新不完全的 DOM。

### Scheduler（调度器）

- 以浏览器是否有空闲时间为依据，决定何时执行渲染任务
  - requestIdleCallback API： 浏览器提供的 API，但由于稳定性与兼容问题，React 16 并未直接使用，而是实现了自己的调度机制就是 `Scheduler`

### Reconciler（协调器）

- 可中断的循环过程
- 基于 Fiber 架构，采用增量渲染和优先级调度
  - 增量渲染： 将渲染任务拆分成多个小任务，逐步完成渲染，避免阻塞主线程
  - 优先级调度： 根据任务的优先级，决定任务的执行顺序，高优先级

## 参考文档

[React技术揭秘](https://react.iamkasong.com/)
[React Versions](https://reactjs.org/versions)
[React Official Doc](https://react.dev/)

(<https://codesandbox.io/s/fervent-sutherland-pf7sg?file=/src/App.js>)
(<https://codesandbox.io/s/concurrent-3h48s?file=/src/index.js>)
