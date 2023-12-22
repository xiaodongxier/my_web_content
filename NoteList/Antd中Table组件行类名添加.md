# Antd中Table组件行类名添加

> 关键词： rowClassName
> 文档： https://1x.antdv.com/components/table-cn/


案例：用rowClassName隔行换色

```html
<a-table :columns="columns" :data-source="dataSource" size="middle" row-key="id" :pagination="false" :row-class-name="rowClassName" />
```


```js
rowClassName(record, index) {
  console.log(record, index);
  let className = "light-row";
  if (index % 2 === 1) className = "dark-row";
  return className;
}
```