# 变形操作

translate 平移
scale 缩放
rotate 旋转
transform setTransform 变换矩阵

## translate

```js
ctx.translate(x, y);
```

## scale

scale 缩放不只改变图形大小 也改变左上角坐标，线宽等

```js
ctx.scale(x, y);
```

## rotate

根据原点旋转(0,0)

```js
// 计算角度 angle = number * Math.PI/180
// d > 0 顺时针旋转
// d < 0 逆时针旋转
ctx.rotate(angle);
```

## transform

translate scale rotate 本质上都是通过变换矩阵实现的

```js
// a 水平缩放绘图
// b 水平倾斜绘图
// c 垂直倾斜绘图
// d 垂直缩放绘图
// e 水平移动绘图
// f 垂直移动绘图
/*
    a c e
    b d f
    0 0 1
*/
ctx.transform(a, b, c, d, e, f);
```

### 平移

起始坐标 x,y
平移后坐标 x1,y1
在 xy 轴平移量 e f
则有以下公式

```
x1 = x + e
y1 = y = f
```

得到矩阵公式

```
|x1|   |1 0 e| |x|
|y1| = |0 1 f| |y|
|1 |   |0 0 1| |1|
```

translate(e,f) 等价于 transform(1, 0, 0, 1, e, f);

### 缩放

起始坐标 x,y
缩放后坐标 x1,y1
在 xy 轴缩放倍数 a d
则有以下公式

```
x1 = x _ a
y1 = y _ d
```

得到矩阵公式

```
|x1|    |a 0 0| |x|
|y1| =  |0 d 0| |y|
|1 |    |0 0 1| |1|
```

scale(a,d) 等价于 transform(a, 0, 0, d, 0, 0);

### 旋转

起始坐标 x,y
旋转后坐标 x1,y1
旋转角度 𝜃
则有以下公式

```
x1 = x*cos𝜃 - y*sin𝜃
y1 = x*sin𝜃 + y*cos𝜃
```

得到矩阵公式

```
|x1|    |cos𝜃  -sin𝜃 0| |x|
|y1| =  |sin𝜃  cos𝜃  0| |y|
|1 |    |0      0    1| |1|
```

rotate(angle) 等价于 transform(Math.cos(angle), Math.sin(angle), -Math.sin(angle), Math.cos(angle), 0, 0);


### setTransform
与 transform 区别
transform 每次变换参数都是上一次变换后的图形状态
setTransform 重置图形的状态 再进行变换