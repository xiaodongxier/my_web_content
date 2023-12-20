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
  // 生成链接
  const href = URL.createObjectURL(blob);
  this.pdfUrl = href; 
  // 新窗口打开
  // window.open(href);
});
```