# 曲线图形

## 圆

```js
// 绘制方向 true 逆时针 false 顺时针
ctx.beginPath();
ctx.arc(x, y, 起始角度, 结束角度, 绘制方向);
ctx.closePath();
```

### 圆 - 描边圆

```js
// 绘制方向 true 逆时针 false 顺时针
ctx.beginPath();
ctx.arc(x, y, 起始角度, 结束角度, 绘制方向);
ctx.closePath();
ctx.stroke();
```

### 圆 - 描边圆 半圆

```js
// 绘制方向 true 逆时针 false 顺时针
ctx.beginPath();
ctx.arc(x, y, 起始角度, 结束角度, 绘制方向);
ctx.closePath();
ctx.stroke();
```

### 圆 - 填充圆

```js
// 绘制方向 true 逆时针 false 顺时针
ctx.beginPath();
ctx.arc(x, y, 起始角度, 结束角度, 绘制方向);
ctx.closePath();
ctx.fill();
```

## 弧线

### 弧线 - arc

```js
ctx.arc(x, y, 起始角度, 结束角度, 绘制方向);
```

### 弧线 - arcTo

```js
// cx,cy 控制点坐标
// x，y 结束点坐标
// radius 圆弧半径
ctx.arcTo(cx, cy, x, y, radius);
```

### 弧线 - 圆角矩形

```js
function drawRoundRect(x, y, w, h, r) {
  ctx.beginPath();
  ctx.moveTo(x + r, y);
  ctx.lineTo(x - r * 2 + w, y);
  ctx.arcTo(x + w, y, x + w, y + r, r);
  ctx.lineTo(x + w, y + h - r * 2);
  ctx.arcTo(x + w, y + h, x + w - r * 2, y + h, r);
  ctx.lineTo(x + r, y + h);
  ctx.arcTo(x, y + h, x, y + h - r * 2, r);
  ctx.lineTo(x, y + r);
  ctx.arcTo(x, y, x + r, y, r);
  ctx.closePath();
  ctx.stroke();
}
```

## 二次贝塞尔曲线

```js
// cx,cy 控制点坐标
// x，y 结束点坐标
ctx.quadraticCurveTo(cx, cy, x, y);
```

## 三次贝塞尔曲线

```js
// cx1,cy1 控制点1坐标
// cx2,cy2 控制点2坐标
// x，y 结束点坐标
ctx.bezierCurveTo(cx1, cy1, cx2, cy2, x, y);
```

## 扇形

```js
function drawSector(x, y, r, startRadius, endRadius) {
  ctx.beginPath();
  ctx.moveTo(x, y);
  ctx.arc(x, y, r, startRadius, endRadius, false);
  ctx.closePath();
}
```
