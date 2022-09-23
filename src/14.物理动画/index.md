# 物理动画

clearRect 清除画布
requestAnimationFrame 重绘

## 三角函数

sin0 = x/r
cos0 = y/r
tan0 = x/y
0 = arcsin(x/r)
0 = arccos(y/r)
0 = arctan(x/y)

```js
Math.sin((0 * Math.PI) / 180);
Math.cos((0 * Math.PI) / 180);
Math.tan((0 * Math.PI) / 180);
Math.asin(x / r) * (180 / Math.PI);
Math.acos(x / r) * (180 / Math.PI);
Math.atan(x / r) * (180 / Math.PI);
```

### Math.atan2(y,x) 追随鼠标旋转

x 邻边边长
y 对边边长

```js
class Arrow {
  constructor(x = 0, y = 0, angle = 0) {
    this.x = x;
    this.y = y;
    this.angle = angle;
  }
  fill(ctx) {
    ctx.save();
    ctx.translate(this.x, this.y);
    ctx.rotate(this.angle);
    ctx.fillStyle = "#F00";
    ctx.beginPath();
    ctx.moveTo(-20, -10);
    ctx.lineTo(0, -10);
    ctx.lineTo(0, -20);
    ctx.lineTo(20, 0);
    ctx.lineTo(0, 20);
    ctx.lineTo(0, 10);
    ctx.lineTo(-20, 10);
    ctx.closePath();
    ctx.fill();
    ctx.restore();
  }
}

const arrow = new Arrow(300, 300);
const getMouse = (element) => {
  const mouse = { x: 0, y: 0 };
  element.addEventListener("mousemove", function (e) {
    e = e || window.event;
    let { pageX: x, pageY: y } = e;
    x -= element.offsetLeft;
    y -= element.offsetTop;
    mouse.x = x;
    mouse.y = y;
  });
  return mouse;
};
const mouse = getMouse(canvas);
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  const dx = mouse.x - 300;
  const dy = mouse.y - 300;
  arrow.angle = Math.atan2(dy, dx);
  arrow.fill(ctx);
};
frame();
```

### 两点间距离

```js
const point1 = { x: 100, y: 100 };
const point2 = { x: 300, y: 0 };
const dx = point2.x - point1.x;
const dy = point2.y - point1.y;
const distance = Math.sqrt(dx * dx + dy * dy);
```

### 圆周运动

#### 正圆

```js
// 获取正圆上坐标
x = centerX + Math.cos(angle) * radius;
y = centery + Math.sin(angle) * radius;
```

```js
class Ball {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  fill() {
    ctx.save();
    ctx.fillStyle = "red";
    ctx.beginPath();
    ctx.arc(this.x, this.y, 10, 0, Math.PI * 2);
    ctx.closePath();
    ctx.fill();
    ctx.restore();
  }
}
const ball = new Ball(500, 300);
let angle = 0;
const center = { x: 300, y: 300 };
const radius = 200;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);

  ctx.beginPath();
  ctx.arc(center.x, center.y, 200, 0, Math.PI * 2);
  ctx.closePath();
  ctx.fillStyle = "#669";
  ctx.fill();

  ball.x = center.x + Math.cos(angle) * radius;
  ball.y = center.y + Math.sin(angle) * radius;
  ball.fill();
  angle += 0.01;
};
frame();
```

#### 椭圆

```js
// 获取正圆上坐标
x = centerX + Math.cos(angle) * radiusX;
y = centery + Math.sin(angle) * radiusY;
```

```js
function drawOval(x, y, radiusX, radiusY) {
  const step = radiusX > radiusY ? 1 / radiusX : 1 / radiusY;
  ctx.beginPath();
  ctx.strokeStyle = "#669";
  ctx.moveTo(x + radiusX, y);
  for (let i = 0; i < Math.PI * 2; i += step) {
    ctx.lineTo(x + radiusX * Math.cos(i), y + radiusY * Math.sin(i));
  }
  ctx.closePath();
  ctx.stroke();
}
```

```js
const center = { x: 300, y: 300 };
const radiusX = 200;
const radiusY = 100;
let angle = 0;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  drawOval(center.x, center.y, radiusX, radiusY);
  ball.x = center.x + Math.cos(angle) * radiusX;
  ball.y = center.y + Math.sin(angle) * radiusY;
  ball.fill();
  angle += 0.01;
};
frame();
```

### 波形运动

## 匀速运动

## 加速运动

## 重力

## 摩擦力
