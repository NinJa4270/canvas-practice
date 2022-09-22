# 文本操作

## 属性

### font 样式 大小粗细

```
// 默认值 10px sans-serif
ctx.font = "font-style font-weight font-size/line-height font-family";
```

### textAlign 水平对齐方式

```js
// start
// end
// left
// right
// center
ctx.textAlign = "属性";
```

### textBaseline 垂直对齐方式

```js
// alphabetic 文本基线是标准的字母基线 默认值
// top 文本基线在文本块的顶部
// middle 文本基线在文本块的中间
// bottom 文本基线在文本块的底部
// hanging 文本基线是悬挂基线
// ideographic 文字基线是表意字基线 不需要考虑下行字母
ctx.textBaseline = "属性";
```

### fillStyle 填充路径颜色

### strokeStyle 描边路径颜色

## 方法

### fillText 填充文本

```js
// text 文字
// x 文本最左侧坐标
// y 文本最【 下侧 】 坐标
// maxWidth 最大宽度
ctx.fillText(text, x, y, maxWidth);
```

### strokeText 描边文本

```js
// text 文字
// x 文本最左侧坐标
// y 文本最【 下侧 】 坐标
// maxWidth 最大宽度
ctx.strokeText(text, x, y, maxWidth);
```

### measureText 获取文本属性

```js
ctx.measureText(text);
// width 内联字符串宽度
// actualBoundingBoxLeft 平行于基线 从textAlign属性确定的对齐点到文本矩形【左侧】距离
// actualBoundingBoxRight 平行于基线 从textAlign属性确定的对齐点到文本矩形【右侧】距离
// fontBoundingBoxAscent textBaseline 水平线到【渲染文本】的所有字体的矩形最高边界顶部的距离
// fontBoundingBoxDescent textBaseline 水平线到【渲染文本】的所有字体的矩形最底部的距离
// actualBoundingBoxAscent textBaseline 水平线到  渲染文本的矩形边界顶部的距离
// actualBoundingBoxDescent textBaseline 水平线到 渲染文本的矩形边界底部距离

// 其他属性 https://developer.mozilla.org/zh-CN/docs/Web/API/TextMetrics
```
