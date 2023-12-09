# GitHub相关API

> 注意： api地址区分大小写，github偶尔访问不了不要着急，耐心等待一会儿就好


## 获取用户信息


```
API地址：https://api.github.com/users/
请求方式：get
请求参数：path路径： 用户名
返回参数：一个用户对象
例子：https://api.github.com/users/xiaodongxier
```

**返回结果：**

```json
{
    "login": "xiaodongxier",
    "id": 56629378,
    "node_id": "MDQ6VXNlcjU2NjI5Mzc4",
    "avatar_url": "https://avatars.githubusercontent.com/u/56629378?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/xiaodongxier",
    "html_url": "https://github.com/xiaodongxier",
    "followers_url": "https://api.github.com/users/xiaodongxier/followers",
    "following_url": "https://api.github.com/users/xiaodongxier/following{/other_user}",
    "gists_url": "https://api.github.com/users/xiaodongxier/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/xiaodongxier/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/xiaodongxier/subscriptions",
    "organizations_url": "https://api.github.com/users/xiaodongxier/orgs",
    "repos_url": "https://api.github.com/users/xiaodongxier/repos",
    "events_url": "https://api.github.com/users/xiaodongxier/events{/privacy}",
    "received_events_url": "https://api.github.com/users/xiaodongxier/received_events",
    "type": "User",
    "site_admin": false,
    "name": "小东西儿",
    "company": null,
    "blog": "https://xiaodongxier.com",
    "location": null,
    "email": null,
    "hireable": null,
    "bio": null,
    "twitter_username": null,
    "public_repos": 77,
    "public_gists": 3,
    "followers": 20,
    "following": 8,
    "created_at": "2019-10-16T08:28:56Z",
    "updated_at": "2023-12-01T07:36:28Z"
}
```


