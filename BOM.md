## BOM

### 1. 全局对象

> 全局变量不能通过delete操作符删除，定义在window对象上的可以。

```javascript
var a = 1;
console.log(window.a);// 1
delete window.a;
console.log(window.a);// 1
```

```javascript
window.a = 1;
console.log(window.a); //1
delete window.a;
console.log(window.a);// undefined
```

通过var为全局变量window添加属性时，window对象的[[Configurable]]为false。所以无法使用delete删除该属性。

### 2.窗口位置

`window.screenLeft`窗口到屏幕左侧的距离。

`window.screenTop`窗口到屏幕上方的距离。

`window.screenX`窗口到屏幕左侧的距离。FirFox浏览器

`window.screenY`窗口到屏幕上方的距离。FirFox浏览器

移动窗口

window.moveTo(x,y) 移动窗口到指定坐标(x,y)

window.moveBy(x,y) 相对于窗口的原位置移动指定距离。例如原位置坐标(a,b)那么现位置坐标(a+x,b+y)；

移动窗口这个方法大部分是被浏览器禁用的。

### 3、打开一个连接

location = url

location.assign(url)

location.href=url

> 上面这三种方法都会向历史中添加一条新纪录，可以退回到原地址

location.replace(url);

> 当前页面被替换。退回不到替换前的页面

4、重新加载页面

location.reload(); // 普通刷新可能去缓存

location.reload(true); // 强制刷新，重新从服务器获取

5、浏览器前进后退

history.go(1) // 前进1页

history.go(-1); // 后退1页

history.forward(); // 前进

history.back();