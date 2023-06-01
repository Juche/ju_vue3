# 官方文档笔记

## API

- `createApp`
  > `createSSRApp` 以 SSR 激活模式创建一个应用实例
  > [应用实例 API 的完整列表](https://cn.vuejs.org/api/application.html)

```js
import { createApp } from 'vue';
// const app = createApp({
//   /* 根组件选项 */
// });
// 如果使用单文件组件，可以直接导入根组件
import App from './App.vue';
const app = createApp(App);

/**
 * @应用实例对象
 * mount() 将应用实例挂载在一个容器元素中,每个应用实例仅能调用一次
 * unmount() 卸载一个已挂载的应用实例,会触发该应用所有组件的卸载钩子
 * component() 传组件名和定义,注册全局组件;传组件名,返回该名字注册的组件
 * directive() 传指令名和定义,注册全局指令;传指令名,返回该名字注册的指令
 * use() 安装插件,第一个参数是插件本身,可选的第二个参数是传递给插件的选项
 * mixin() [不推荐]主要是为了向后兼容,全局 mixin 会作用于应用的每个组件实例
 * provide() 提供可以在应用中所有后代组件中注入使用的值
 * runWithContext() ??使用当前应用作为注入上下文执行回调函数
 * version 提供当前应用所使用的 Vue 版本号,这在插件中很有用
 * config 配置应用级选项
 *   errorHandler 用于为应用内抛出的未捕获错误指定一个全局处理函数
 *   warnHandler 用于为 Vue 的运行时警告指定一个自定义处理函数
 *   performance [开发模式]可在浏览器开发工具“性能/时间线”中启用对组件初始化/编译/渲染和修补的性能追踪
 *   compilerOptions 配置运行时编译器的选项
 *     isCustomElement 指定一个检查方法来识别原生自定义元素
 *     whitespace 调整模板中空格的处理行为
 *     delimiters 调整模板内文本插值的分隔符
 *     comments 调整是否移除模板中的 HTML 注释
 *   globalProperties [对 Vue.prototype 的一种替代]注册能被应用内所有组件实例访问的全局属性的对象
 *   optionMergeStrategies 一个用于定义自定义组件选项的合并策略的对象
 */
app.config.errorHandler = (err) => {
  /* 处理错误 */
};
// 这使得 TodoDeleteButton 在应用的任何地方都是可用的
app.component('TodoDeleteButton', TodoDeleteButton);

app.mount('#app');
```

```js
// 多个应用实例
// createApp API 允许在同一个页面中创建多个共存的 Vue 应用
// 而且每个应用都拥有自己的用于配置和全局资源的作用域
const app1 = createApp({
  /* ... */
});
app1.mount('#container-1');

const app2 = createApp({
  /* ... */
});
app2.mount('#container-2');
// 如果使用 Vue 来增强服务端渲染 HTML,且只想 Vue 控制一个大型页面中特殊的一小部分,
// 应避免将一个单独的 Vue 应用实例挂载到整个页面上,
// 而是应该创建多个小的应用实例,将它们分别挂载到所需的元素上去。
```

---

## 关键词

- [ ] 响应式
  - ref
  - reactive
  - computed
  - readonly
  - watch
  - watchEffect
  - watchPostEffect
  - watchSyncEffect
- [ ] 组合式函数: 利用 Vue 的组合式 API 来封装和复用有状态逻辑的函数
  - 相关内容 hooks / mixins
- [ ] 自定义指令: 只有当所需功能只能通过直接的 DOM 操作来实现时，才应该使用自定义指令
- [ ] Plugins: 插件是能为 Vue 添加全局功能的工具代码
  - 插件发挥作用的常见场景主要包括以下几种：
    - 通过 app.component() 和 app.directive() 注册一到多个全局组件或自定义指令。
    - 通过 app.provide() 使一个资源可被注入进整个应用。
    - 向 app.config.globalProperties 中添加一些全局实例属性或方法
    - 一个可能上述三种都包含了的功能库 (例如 vue-router)。
- [ ] Teleport
- [ ] SSR

## 资源

- [Vue 文档](https://cn.vuejs.org)
- [VueUse 文档](https://vueuse.org)
