# JS筛选指定后缀文件


> 找出下面数据中name值的后缀为md的数据

```js
const  files = [
  {
      "name": "test.txt",
  },
  {
      "name": "text.md",
  },
  {
      "name": "text.js",
  }
]
```

```js
const result = files.filter(file => file.name.endsWith(".md"));
console.log(result);
```

`.endsWith(".md")` 是 JavaScript 字符串的内置方法之一。它用于判断一个字符串是否以指定的后缀结尾。在这个例子中，".md" 是要判断的后缀，如果字符串以 ".md" 结尾，那么返回 true，否则返回 false。