# my_web_content

我的网站数据


## api

- 仓库
  - 仓库分支列表
    - https://api.github.com/repos/xiaodongxier/my_web_content/branches
  - 主分支仓库列表
    - https://api.github.com/repos/xiaodongxier/my_web_content/contents/
  - 其他分支仓库列表
    - https://api.github.com/repos/{owner}/{repo}/contents/{path}?ref={branch}
      - 例如：https://api.github.com/repos/xiaodongxier/my_web_content/contents?ref=dream_data
      - 文件夹：https://api.github.com/repos/xiaodongxier/my_web_content/contents/NoteList?ref=dream_data
      - 文档：https://raw.githubusercontent.com/xiaodongxier/my_web_content/dream_data/Theme/ThemePlan.md
  - 获取仓库其他分支信息
    - https://api.github.com/repos/xiaodongxier/my_web_content/branches/dream_data



- 获取分支文件内容
  - https://raw.githubusercontent.com/xiaodongxier/my_web_content/dream_data/README.md



获取特定分支的文件列表：
GET /repos/{owner}/{repo}/contents/{path}?ref={branch}




## 接口文章


https://blog.csdn.net/weixin_43829154/article/details/120697007

https://www.cnblogs.com/ygunoil/p/13607491.html



















- https://cdn.jsdelivr.net/gh/xiaodongxier/testdata/md.md
- https://cdn.jsdelivr.net/gh/xiaodongxier/testdata@master/md.md
- https://raw.gitmirror.com/xiaodongxier/testdata/main/md.md
- https://api.github.com/repos/xiaodongxier/testdata/contents/md.md







- https://api.github.com/repos/{owner}/{repo}/git/refs/heads/{branch}
- https://api.github.com/repos/xiaodongxier/my_web_content/git/refs/heads/dream_data

- https://api.github.com/repos/xiaodongxier/my_web_content/contents/dream_data

https://api.github.com/repos/xiaodongxier/my_web_content/contents/README.md?ref=dream_data



- https://raw.gitmirror.com/xiaodongxier/testdata/dream_data@main/
- https://gist.gitmirror.com/dimitardanailov/6acdd54ab67d5a25c0229b2fe5bbb42b/raw/397f0873922a6aa48895074cc28d7f71c8261b81/create_user.sh


https://github.com/solstice23/argon-theme