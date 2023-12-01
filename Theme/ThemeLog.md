# 更新日志

> ["dot", "type", "spin", color", "font-size"]
>  是否自定义, icon字符class, icon是否动态旋转, 圈颜色,字体大小(暂时忽略) 



<!-- 
#### 测速时间轴UI

>< {%["", "", true, "green", ""]%}

- ["", "", "green", ""]


#### 测速时间轴UI

>< {%["", "", true,"red", ""]%}

- ["", "", "red", ""]


#### 测速时间轴UI

>< {%["", "", true, "gray", ""]%}

- ["", "", "gray", ""]


#### 测速时间轴UI

>< {%["dot", "clock-circle-o", false, "blue", "font-size: 16px;"]%}

- ["dot", "clock-circle-o", "blue", "font-size: 16px;"]


 -->







#### 2023-11-25 周六

>< {%["dot", "heart", false,"red", ""]%}

突发灵感, 项目创建, 画了草图原型
确定基本实现思路：单页面应用vue2 + antd; 纯前端项目,没有数据库; 数据全部存储在GitHub仓库, 通过开放 API 进行数据的获取, 成本低不需要进行服务器等相关的部署

#### 2023-11-26 周日

>< {%["", "", false, "blue", "font-size"]%}

完成页面的整体框架, 完成待办事项模块 [效果图](https://gitcdn.xiaodongxier.com/obsidian/202311272349210.webp)



#### 2023-11-27

<!-- >< {%["dot", "alert", false, "", "font-size"]%} -->
>< {%["", "", false, "blue", "font-size"]%}

主题记录模块开发,完成历史时间轴模块 [效果图](https://gitcdn.xiaodongxier.com/obsidian/202311272352787.webp)



#### 2023-11-28

<!-- >< {%["dot", "bug", false, "blie", "font-size"]%} -->
>< {%["", "", false, "blue", "font-size"]%}

文章笔记模块优化
文章接入数据仓库
完整markdown文档渲染样式,代码高亮主题



#### 2023-11-29

>< {%["", "", false, "blue", "font-size"]%}

解决 `md` 文件渲染问题, 前期一直选择 `markdown-vue` 感觉没有问题, 但是现在还要考虑目录的生成貌似它不支持, 所以 `markdown-it` / `marked` 要在选择一个

解决代码主题色渲染问题, 使用的 `highlight.js`  库解决











