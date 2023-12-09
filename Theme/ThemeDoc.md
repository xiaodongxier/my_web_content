# 主题文档


## 开发思路

> 纯前端技术开发, 技术上使用 `vue2` + `antd@1.7.8`, 文件以 `markdown` 格式存储, 所有数据文件存储在 `GitHub` 仓库, 通过 `GitHub` 开发 `API` 进行数据的获取, 然后通过前端渲染到页面上。

- Vue2
- Ant Design of Vue
- vue-markdown


## 发布流程

本程序为一个 GitHub 仓库, 并开启 `GitHub page` 作为前端访问页面, 网站数据存放在**该仓库其他分支**或者**新建一个仓库**作为数据存放都可以, 相关 `md` 文件数据我是通过 `VS Code` 编辑的, 然后配合 `VS Code` 中的 `Note Sync` 插件进行保存自动发布。


## 源码结构

```shell
src                        
├─ assets                  
│  └─ logo.png             
├─ components              
│  ├─ About                
│  │  └─ About.vue         
│  ├─ NoteList             
│  │  └─ NoteList.vue      
│  ├─ Theme                
│  │  ├─ modules           
│  │  │  ├─ ThemeDoc.vue   
│  │  │  ├─ ThemeLog.vue   
│  │  │  └─ ThemePlan.vue  
│  │  └─ Theme.vue         
│  ├─ TodoList             
│  │  └─ TodoList.vue      
│  ├─ WishList             
│  │  └─ WishList.vue      
│  ├─ HomePage.vue       
├─ mixins                  
│  └─ commonMixin.js       
├─ App.vue                 
└─ main.js                 
```


## md文档渲染


- 渲染markdown
  - 使用 `vue-markdown` 渲染
  - github-markdown-css
- 代码高亮，行号：https://juejin.cn/post/6844904004452007943
  - [highlightjs-line-numbers.js](https://www.npmjs.com/package/highlightjs-line-numbers.js)


### 代码高亮 [highlight.js](https://github.com/highlightjs/highlight.js)

使用 `highlight.js` 进行代码高亮, 所有高亮的样式可以在这里 [查看](https://highlightjs.org/demo)

```js
import "github-markdown-css/github-markdown.css";
// import "github-markdown-css/github-markdown-dark.css";
// import "github-markdown-css/github-markdown-light.css";

import highlightPlugin from "@highlightjs/vue-plugin";
import "highlight.js/styles/a11y-dark.css"; // 引入内置样式, 样式有很多可以在npm里面看
Vue.use(highlightPlugin);
ount("#app");

```

参考文章：https://juejin.cn/post/7139344870539264036




> 下面代码未生效原因，是因为DOM结构未渲染

```html
<script>
import hljs from 'highlight.js';
export default {
  name: 'ThemePlan',
  mounted() {
      console.log(this.$refs.mdContent.$el.querySelectorAll("*"))
      this.$el.querySelectorAll('pre code').forEach((block) => {
        hljs.highlightBlock(block);
      });
  }
}
</script>
```


## markdown 语法参考

- [菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)


