字符串格JSON与JSON互转

- 字符串转JSON

```js
JSON.parse(str)
```

- JSON转字符串

```js
JSON.stringify(obj)
```

- 字符串转JSON字符串

```js
JSON.stringify(JSON.parse(str))
```

- JSON字符串转字符串

```js
JSON.stringify(JSON.parse(JSON.stringify(obj)))
```
