# 路径

## 方法

### beginPath

stroke/fill 等方法 找到最近的 beginPath 后面定义的状态执行

moveTo/lineTo/strokeRect/fillRect/rect/arc/arcTo/quadricCureTo/bezierCurveTo 并不会开始新路径

```js
ctx.beginPath();
```

### closePath

关闭路径：同一个路径的起点和终点这两点连接起来形成一个封闭图形

```js
ctx.closePath();
```

### isPointInPath

判断某点是否在路径上

不支持 strokeRect 与 fillRect 
支持 rect lineTo

```js
ctx.isPointInPath(x, y);
```
