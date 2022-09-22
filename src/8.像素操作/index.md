# 像素操作

## 方法

### getImageData

```js
// 返回 ImageData 对象 data：Uint8ClampedArra height与width
ctx.getImageData(x, y, w, h);
```

### putImageData

```js
ctx.putImageData(image, x, y);
```

### createImageData

创建一个区域 可以进行像素操作
getImageData/putImageData 是对一张图片进行像素操作
createImageData 是对一个区域进行像素操作
```js
ctx.createImageData(sw, sh);
ctx.createImageData(imageData);
```

## 效果

### 反转效果

```js
for (let i = 0; i < data2.length; i += 4) {
  // const average = (data2[i] + data2[i + 1] + data2[i + 2]) / 3; // 普通平均值
  const average =
    (data2[i] * 0.3 + data2[i + 1] * 0.6 + data2[i + 2] * 0.1) / 3; // 加权平均值
  data2[i] = average;
  data2[i + 1] = average;
  data2[i + 2] = average;
}
```

### 黑白效果

```js
for (let i = 0; i < data3.length; i += 4) {
  const a = 50;
  data3[i] += a;
  data3[i + 1] += a;
  data3[i + 2] += a;
}
```

### 亮度效果

```js
for (let i = 0; i < data3.length; i += 4) {
  const a = 50;
  data3[i] += a;
  data3[i + 1] += a;
  data3[i + 2] += a;
}
```

### 复古效果

```js
for (let i = 0; i < data4.length; i += 4) {
  const r = data4[i];
  const g = data4[i + 1];
  const b = data4[i + 2];
  data4[i] = r * 0.39 + g * 0.76 + b * 0.18;
  data4[i + 1] = r * 0.35 + g * 0.68 + b * 0.16;
  data4[i + 2] = r * 0.27 + g * 0.53 + b * 0.13;
}
```

### 红色蒙版

```js
for (let i = 0; i < data5.length; i += 4) {
  const average = (data5[i] + data5[i + 1] + data5[i + 2]) / 3;
  data5[i] = average;
  data5[i + 1] = 0;
  data5[i + 2] = 0;
}
```

### 透明处理

```js
for (let i = 0; i < data6.length; i += 4) {
  data6[i + 3] *= 0.3;
}
```
