# 主题文档


## 开发思路

> 纯前端技术开发 `vue2` + `antd@1.7.8`, 文件以 `markdown` 格式存储, 所有数据文件存储在 `GitHub` 仓库, 通过 `GitHub` 开发 `API` 进行数据的获取, 然后通过前端渲染到页面上。

- Vue2
- Ant Design of Vue
- vue-markdown


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


- 主题文档是指在 `src/theme` 目录下，以 `*.md` 结尾的文件。
- 主题文档的作用是为用户提供主题相关的文档，帮助用户更好的使用主题。
- 主题文档的格式是 Markdown 格式，使用 `mdx` 格式。
- 主题文档的命名规则是 `*.md`，其中 `*` 表示任意字符。



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


## 发布流程

配合 `vscode` 的插件 `Note Sync` 进行保存自动发布