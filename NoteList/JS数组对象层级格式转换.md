# JS数组对象层级格式转换

**案例**

```js
var a = [
  {
      "projectReview": {
          "verifyMode": "审查会",
      },
      "verifyMemberList": []
  },
  {
      "projectReview": {
          "verifyMode": "审查会",
      },
      "verifyMemberList": []
  }
];

var b = [
  {
    "verifyMode": "审查会",
    "verifyMemberList": []
  },
  {
    "verifyMode": "审查会",
    "verifyMemberList": []
  }
]
```

## a 格式转 b 格式

- 方法1

```js
var c = a.map(function(element) {
  return {
    verifyMode: element.projectReview.verifyMode,
    verifyMember: element.projectReview.verifyMember,
    record: element.projectReview.record,
    verifyMemberList: element.verifyMemberList
  };
});
console.log(c);
```

- 方法2

```js
const c = a.map(({ projectReview, verifyMemberList }) => ({
  ...projectReview,
  verifyMemberList
}));
console.log(c);
```

## b 格式转 a 格式

- 方法1

```js
var c = b.map(function(element) {
  return {
    projectReview: {
      verifyMode: element.verifyMode,
      verifyMember: element.verifyMember,
      record: element.record
    },
    verifyMemberList: element.verifyMemberList
  };
});
console.log(c);
```

- 方法2

```js
const c = b.map(({ verifyMode, verifyMember, record, verifyMemberList }) => ({
  projectReview: {
    verifyMode,
    verifyMember,
    record
  },
  verifyMemberList
}));
console.log(c);
```
