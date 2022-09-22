# 图片操作

## drawImage

```js
ctx.drawImage(image, dx, dy);
ctx.drawImage(image, dx, dy, dw, dh);
ctx.drawImage(image, sx, sy, sw, sh, dx, dy, dw, dh);
```

### ctx.drawImage(image, dx, dy)

```js
// image 图片
// dx，dy 绘制左上角坐标
ctx.drawImage(image, dx, dy);
```

### ctx.drawImage(image, dx, dy, dw, dh)

```js
// image 图片
// dx，dy 绘制左上角坐标
// dw,dh 图片的宽高
ctx.drawImage(image, dx, dy, dw, dh);
```

### ctx.drawImage(image, sx, sy, sw, sh, dx, dy, dw, dh)

```js
// image 图片
// sx sy 图片截取 坐标
// sw sh 图片截取宽高
// dx，dy 绘制左上角坐标
// dw,dh 图片的宽高
ctx.drawImage(image, sx, sy, sw, sh, dx, dy, dw, dh);
```

## 平铺

### createPattern

```js
// type : repeat repeat-x repeat-y no-repeat
ctx.createPattern(image, type);
```

## 切割

### clip

```js
ctx.clip();
```
