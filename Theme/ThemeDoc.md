# 主题文档

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