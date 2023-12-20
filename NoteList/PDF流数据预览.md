# PDF流数据预览

```js
getFile(params, { responseType: "blob" }).then((res) => {
  const blob = new window.Blob([res], {
    type: "application/pdf;charset-UTF-8"
  });
  const href = URL.createObjectURL(blob);
  this.pdfUrl = href;
  // 新窗口打开
  // window.open(href);
});
```