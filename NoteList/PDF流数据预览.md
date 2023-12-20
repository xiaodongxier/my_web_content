# PDF流数据预览


```html
<a-modal
  v-model="visible"
  :title="pdfTitle"
  on-ok="handleOk"
  :footer="null"
  width="50%"
  centered
  class="pdf-wraper"
  :body-style="{height:'80vh'}"
>
  <div class="pdf-content">
    <object :data="pdfUrl" type="application/pdf" width="100%" height="100%" />
  </div>
</a-modal>
```

```js
getFile(params, { responseType: "blob" }).then((res) => {
  const blob = new window.Blob([res], {
    type: "application/pdf;charset-UTF-8"
  });
  // 参数：用于创建 URL 的 File 对象、Blob 对象或者 MediaSource 对象。​
  // 返回值：一个DOMString包含了一个对象URL，该URL可用于指定源 object的内容。
  const href = URL.createObjectURL(blob);
  this.pdfUrl = href; 
  // 新窗口打开
  // window.open(href);
});
```