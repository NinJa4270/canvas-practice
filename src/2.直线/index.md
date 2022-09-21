# 直线图形

## 直线

### 单直线

```js
ctx.moveTo(x1, y1);
ctx.lineTo(x2, y2);
ctx.stroke();
```

### 多条直线

```js
ctx.moveTo(x1, y1);
ctx.lineTo(x2, y2);
ctx.moveTo(x3, y3);
ctx.lineTo(x4, y4);
ctx.stroke();
```

### 多条直线 - 三角形

```js
ctx.moveTo(x1, y1);
ctx.lineTo(x2, y2);
ctx.lineTo(x3, y3);
ctx.lineTo(x1, y1);
ctx.stroke();
```

### 多条直线 - 矩形

```js
ctx.moveTo(x1, y1);
ctx.lineTo(x2, y1);
ctx.lineTo(x2, y2);
ctx.lineTo(x1, y2);
ctx.lineTo(x1, y1);
ctx.stroke();
```

## 矩形

### “描边”矩形

```js
ctx.strokeStyle = "属性"; // #FFF000 yellow rgb(255,255,0) rgba(255,255,0,0.5) 图像
ctx.strokeRect(x, y, width, height);
```

### “填充”矩形

```js
ctx.fillStyle = "属性"; // #FFF000 yellow rgb(255,255,0) rgba(255,255,0,0.5) 图像
ctx.fillRect(x, y, width, height);
```

#### “填充”“描边”矩形

```js
ctx.strokeStyle = "属性";
ctx.strokeRect(x, y, width, height);
ctx.fillStyle = "属性";
ctx.fillRect(x, y, width, height);
```

### rect 方法 fill/stroke

```js
ctx.strokeStyle = "属性";
ctx.rect(x, y, width, height);
ctx.stroke();

ctx.fillStyle = "属性";
ctx.rect(x, y, width, height);
ctx.fill();
```

### 清空矩形

```js
ctx.clearRect(x, y, width, height);
```

## 多边形

### 绘制箭头

```js
ctx.moveTo(100, 100);
ctx.lineTo(400, 100);
ctx.lineTo(400, 50);
ctx.lineTo(500, 125);
ctx.lineTo(400, 200);
ctx.lineTo(400, 150);
ctx.lineTo(100, 150);
ctx.lineTo(100, 100);
ctx.stroke();
```

### 绘制正多边形

```js
function drawPolygon(n, x, y, size) {
  if (n < 3) throw new Error(`n 不能小于3。n 为 ${n}`);
  ctx.beginPath();
  const degree = (Math.PI * 2) / n; // 每一个内角
  for (let i = 0; i < n; i++) {
    const dx = Math.cos(i * degree);
    const dy = Math.sin(i * degree);
    ctx.lineTo(x + size * dx, y + size * dy);
  }
  ctx.closePath();
}
```

### 绘制五角星

外圈相邻点角度 360/5 = 72
内圈相邻点角度 360/5 = 72
相邻点之间角度 72 /2 = 36
最右侧外圈点 x 轴坐标的角度 90 - 36 - 36 = 18
最右侧外圈点逆时针方向的相邻内圈点距离 x 轴坐标为 36 + 18 = 54
所以从最小角度起以此为 18 54 90 126 ...

```js
function drawPentagram(dx, dy, R = 100, r = 50) {
  const wDegree = 18;
  const nDegree = 54;
  const getDegree = (n) => (Math.PI / 180) * n;
  const getX = (v) => Math.cos(getDegree(v));
  const getY = (v) => -Math.sin(getDegree(v));
  ctx.beginPath();
  for (let i = 0; i < 5; i++) {
    // 外
    const wx = R * getX(wDegree + i * 72) + dx;
    const wy = R * getY(wDegree + i * 72) + dy;
    ctx.lineTo(wx, wy);
    // 内
    const nx = r * getX(nDegree + i * 72) + dx;
    const ny = r * getY(nDegree + i * 72) + dy;
    ctx.lineTo(nx, ny);
  }
  ctx.closePath();
}
```

### 绘制调色板

```js
function drawPalette(w, h) {
  let r = 255,
    g = 0,
    b = 0;
  const size = w / 150;
  for (let i = 0; i < 150; i++) {
    if (i < 25) {
      g += 10;
    } else if (i > 25 && i < 50) {
      r -= 10;
    } else if (i > 50 && i < 75) {
      g -= 10;
      b += 10;
    } else if (i > 75 && i < 100) {
      r += 10;
    } else {
      b -= 10;
    }
    ctx.fillStyle = `rgb(${r},${g},${b})`;
    ctx.fillRect(size * i, 0, size, h);
  }
}
```
