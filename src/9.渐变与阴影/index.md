# 渐变与阴影

## 线性渐变

### createLinearGradient

```js
// x1,y1 渐变开始
// x2,y2 渐变结束
// x1,y1 ---- x2,y1
//   |   \
//   |     \
// x1,y2     x2,y2

const gnt = ctx.createLinearGradient(x1, y1, x2, y2);
```

### addColorStop

```js
// value 0 - 1
gnt.addColorStop(value, color);
```

## 经向渐变

从起点到终点 颜色从内到外进行圆形渐变

### createRadialGradient

```js
// x1,y1 渐变开始圆心坐标 r1 渐变开始圆心半径
// x2,y2 渐变开始圆心坐标 r2 渐变开始圆心半径
const gnt = ctx.createRadialGradient(x1, y1, r1, x2, y2, r2);
```

## 阴影

### shadowOffsetX

阴影与图形的水平距离
默认 0
大于 0 向右偏移
小于 0 向左偏移

```js
ctx.shadowOffsetX = number;
```

### shadowOffsetY

阴影与图形的垂直距离
默认 0
大于 0 向下偏移
小于 0 向上偏移

```js
ctx.shadowOffsetY = number;
```

### shadowColor

阴影颜色
默认黑色

```js
ctx.shadowColor = color;
```

### shadowBlur

阴影的模糊值
值越大 模糊度越强

```js
ctx.shadowBlur = number;
```
