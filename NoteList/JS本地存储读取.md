# JS本地存储读取

> 在JavaScript中，可以使用本地存储技术，如localStorage或sessionStorage，来读取和写入对象。

1. 写入对象：
   ```javascript
   // 定义一个对象
   var obj = { name: 'John', age: 25 };

   // 将对象转换为字符串
   var objStr = JSON.stringify(obj);

   // 使用localStorage写入对象
   localStorage.setItem('myObj', objStr);
   ```

2. 读取对象：
   ```javascript
   // 使用localStorage读取对象
   var objStr = localStorage.getItem('myObj');

   // 将字符串转换为对象
   var obj = JSON.parse(objStr);

   // 现在可以访问对象的属性
   console.log(obj.name); // 输出: John
   console.log(obj.age); // 输出: 25
   ```

请注意，`localStorage` 和 `sessionStorage` 只能存储字符串类型的数据，因此需要使用 `JSON.stringify()` 将对象转换为字符串，使用 `JSON.parse()` 将字符串转换为对象。