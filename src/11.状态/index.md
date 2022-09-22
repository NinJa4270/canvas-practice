# 状态

如果使用 beginPath 则不同路径使用不同的状态
如果不使用 beginPath 后面的值会覆盖前面的值

## clip 与状态

clip 也不支持 strokeRect 与 fillRect 方法 请使用 rect 代替

## save restore

使用场景
图形/图片裁剪
图形/图片变形
以下属性改变的时候
fillStyle/font/globalAlpha/globalCompositeOperation/lineCap/lineJoin
lineWidth/miterLimit/shadowBlur/shadowColor/shadowOffsetX/shadowOffsetY/strokeStyle
textAlign/textBaseline

```js
ctx.save();
ctx.restore();
```

## 图形/图片剪切

见 demo

## 图形/图片变形

见 demo

## 状态属性的改变

填充效果 ：fillStyle
描边效果 ：strokeStyle
线条效果 ：lineCap lineJoin lineWidth miterLimit
文本效果 ：font textAlign textBaseline
阴影效果 ：shadowBlur shadowColor shadowOffsetX shadowOffsetY
全局属性 ：globalAlpha globalCompositeOperation
