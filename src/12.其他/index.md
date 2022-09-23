# 其他

## width/height

```js
const canvas = document.getElementById(id);
const { height, width } = canvas;
```

## getContext()

```js
const ctx = canvas.getContext("2d");
```

## toDataURL()

```js
// type MIME 默认值 image/png
canvas.toDataURL(type);
```

## globalAlpha

定义 canvas 环境的透明度

```js
ctx.globalAlpha = number;
```

## globalCompositeOperation

// https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation
source-over 默认值 新图形覆盖旧图形
destination-over 与 source-over 相反 旧覆盖新的

darker 【移除】 都显示 重叠部分由两个图形的颜色值相减形成
lighter 都显示 重叠部分由两个图形的颜色值相加形成

destination-atop 显示重叠部分 与 新图形的其余部分
source-atop 显示重叠部分 与 旧图形的其余部分

destination-in 显示重叠部分
source-in 显示重叠部分

destination-out 显示不重叠部分
source-out 显示不重叠部分

copy 只显示新图形 旧图形做透明处理

xor 两种图形都绘制 重叠部分透明

multiply
screen
overlay
darken
lighten
color-dodge
color-burn
hard-light
soft-light
difference
exclusion
hue
saturation
color
luminosity

```js
ctx.globalCompositeOperation = "属性值";
```

## stroke/fill
