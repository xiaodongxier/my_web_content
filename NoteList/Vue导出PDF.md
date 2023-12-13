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
// 导出页面为PDF格式
import html2Canvas from "html2canvas";
import JsPDF from "jspdf";
export default {
  install(Vue, options) {
    Vue.prototype.getPdf = function (name, id) {
      const title = name || "index";
      html2Canvas(document.querySelector(`#${id}`), {
        allowTaint: true,
        // backgroundColor: "red",
        taintTest: false,
        useCORS: true,
        dpi: window.devicePixelRatio * 4, // 将分辨率提高到特定的DPI 提高四倍
        scale: 4, // 按比例增加分辨率
        logging: true // 可以长屏分页导出
      }).then(function (canvas) {
        // 获取canvas的宽度
        const contentWidth = canvas.width;
        // 获取canvas的高度
        const contentHeight = canvas.height;
        // 计算页面的高度
        const pageHeight = contentWidth / 592.28 * 841.89;
        // 初始化leftHeight
        let leftHeight = contentHeight;
        // 初始化position
        let position = 0;
        // 图片宽度
        const imgWidth = 595.28;
        // 图片高度
        const imgHeight = 592.28 / contentWidth * contentHeight;
        // 将canvas转换为图片
        const pageData = canvas.toDataURL("image/jpeg", 1.0);
        // 创建PDF对象
        const PDF = new JsPDF("l", "pt", "a4");
        // 如果leftHeight小于pageHeight，则添加图片
        if (leftHeight < pageHeight) {
          PDF.addImage(pageData, "JPEG", 0, 0, imgWidth, imgHeight);
        // 否则，循环添加图片
        } else {
          while (leftHeight > 0) {
            PDF.addImage(pageData, "JPEG", 0, position, imgWidth, imgHeight);
            leftHeight -= pageHeight;
            position -= 841.89;
            // 如果leftHeight大于0，则添加新页
            if (leftHeight > 0) {
              PDF.addPage();
            }
          }
        }
        PDF.save(title + ".pdf");
      });
    };
  }
};
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

### 版本1

> 调整了居中，但是内容感觉有点小，希望宽带在大一点，高度再高一点，

```js
// 导出页面为PDF格式
import html2Canvas from "html2canvas";
import JsPDF from "jspdf";
export default {
  install(Vue, options) {
    Vue.prototype.getPdf = function (name, id) {
      const title = name || "index";
      html2Canvas(document.querySelector(`#${id}`), {
        allowTaint: true,
        // backgroundColor: "red",
        taintTest: false,
        useCORS: true,
        dpi: window.devicePixelRatio * 4, // 将分辨率提高到特定的DPI 提高四倍
        scale: 4, // 按比例增加分辨率
        logging: true // 可以长屏分页导出
      }).then(function (canvas) {
        const contentWidth = canvas.width;
        const contentHeight = canvas.height;
        const pageHeight = contentWidth / 592.28 * 841.89;
        let leftHeight = contentHeight;
        let position = 0;
        const imgWidth = 595.28;
        const imgHeight = 592.28 / contentWidth * contentHeight;
        const pageData = canvas.toDataURL("image/jpeg", 1.0);
        const PDF = new JsPDF("l", "pt", "a4");

        // 获取页面宽度
        const pageWidth = PDF.internal.pageSize.getWidth();
        // 计算x坐标
        const x = (pageWidth - imgWidth) / 2;
        console.log("pageWidth", pageWidth);
        console.log("contentWidth", contentWidth);
        console.log("x", x);
        if (leftHeight < pageHeight) {
          PDF.addImage(pageData, "JPEG", x, 0, imgWidth, imgHeight);
        // 否则，循环添加图片
        } else {
          while (leftHeight > 0) {
            PDF.addImage(pageData, "JPEG", x, position, imgWidth, imgHeight);
            leftHeight -= pageHeight;
            position -= 841.89;
            // 如果leftHeight大于0，则添加新页
            if (leftHeight > 0) {
              PDF.addPage();
            }
          }
        }
        PDF.save(title + ".pdf");
      });
    };
  }
};
```



## 参考

- [vue-pdf实现pdf预览、分页、下载、打印](https://cloud.tencent.com/developer/article/1864231)
- [jsPDF addHTML 将低质量图像导出为 PDF](https://stackoverflow.com/questions/29166163/jspdf-addhtml-exporting-low-quality-image-to-pdf)


### 网络原始版本

```js
function createPDFObject() {
  html2canvas(document.getElementById("main"), {
   onrendered:function(canvas) {

  var contentWidth = canvas.width;
  var contentHeight = canvas.height;

  //One page pdf shows the height of canvas generated by html page;
  //一页pdf显示html页面生成的画布的高度；
  var pageHeight = contentWidth / 592.28 * 841.89;
  //html page height without pdf generation
  // 不生成pdf的html页面高度
  var leftHeight = contentHeight;
  //Page offset
  // //页面偏移量
  var position = 0;
  //a4 paper size [595.28, 841.89], width and height of image in pdf of canvas generated by html page
  // /a4纸张大小[595.28, 841.89]，html页面生成的画布pdf中图像的宽度和高度
  var imgWidth = 595.28; 
  var imgHeight = 592.28/contentWidth * contentHeight;

  //Return picture dataURL, parameters: picture format and sharpness (0-1)
  // /返回图片数据URL，参数：图片格式和清晰度（0-1）
  var pageData = canvas.toDataURL('image/jpeg', 1.0);

  //Direction is vertical by default, dimension ponits, format A4 [595.28841.89]
  // 默认情况下，方向为垂直，尺寸为小马，格式为A4[595.28, 841.89]
  var pdf = new jsPDF('', 'pt', 'a4');
  
  //There are two heights to distinguish, one is the actual height of the html page, and the height of the generated pdf page (841.89)
  // 有两个高度需要区分，一个是html页面的实际高度，另一个是生成的pdf页面的高度（841.89）
  //When the content does not exceed the display range of one page of pdf, paging is not required
  // 当内容不超过一页pdf的显示范围时，不需要分页
  if (leftHeight < pageHeight) {
      pdf.addImage(pageData, 'JPEG', 0, 0, imgWidth, imgHeight );
  } else {
      while(leftHeight > 0) {
          pdf.addImage(pageData, 'JPEG', 0, position, imgWidth, imgHeight)
          leftHeight -= pageHeight;
          position -= 841.89;
          //Avoid adding blank pages
          // 避免添加空白页
          if(leftHeight > 0) {
            pdf.addPage();
          }
      }
  }
   pdf.save('stone.pdf');

  }
 });
```