# Vue导出PDF

## html2pdf.js

```shell
sudo cnpm install --save html2pdf.js
```




## print-js

```shell
sudo cnpm install print-js   
```






## html2canvas & jspdf

```shell
sudo cnpm install --save html2canvas;
sudo cnpm install --save jspdf
```

```
html2canvas插件有很多参数，以下是其中一些常用的参数及其默认值：

1. `allowTaint`（默认值：false）：是否允许污染跨源图像。如果设置为true，插件将尝试绘制跨源图像。

2. `backgroundColor`（默认值：null）：指定导出图像的背景颜色。可以是颜色名称、十六进制值或rgba值。

3. `canvas`（默认值：null）：使用现有的canvas元素来绘制图像。如果指定了canvas元素，插件将在该canvas上绘制图像，而不会创建新的canvas。

4. `foreignObjectRendering`（默认值：false）：是否启用foreignObject渲染。如果设置为true，插件将尝试使用foreignObject来渲染文本。

5. `height`（默认值：null）：指定导出图像的高度。如果未指定，插件将自动计算高度以适应导出的内容。

6. `ignoreElements`（默认值：(el) => false）：指定要忽略的元素。可以是一个函数，接受一个元素作为参数并返回一个布尔值，或是一个CSS选择器字符串。

7. `logging`（默认值：false）：是否启用日志记录。如果设置为true，插件将在控制台输出日志。

8. `scale`（默认值：window.devicePixelRatio）：指定导出图像的缩放比例。可以是一个数字或一个函数，接受一个canvas元素作为参数并返回一个数字。

9. `useCORS`（默认值：false）：是否使用CORS来加载图像。如果设置为true，插件将尝试使用CORS来加载跨源图像。

10. `width`（默认值：null）：指定导出图像的宽度。如果未指定，插件将自动计算宽度以适应导出的内容。

这些只是html2canvas插件的一部分参数，还有其他参数可供使用。您可以根据需要查看html2canvas文档以获取更详细的参数列表。
```





## 参考

- [vue-pdf实现pdf预览、分页、下载、打印](https://cloud.tencent.com/developer/article/1864231)