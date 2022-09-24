# 高级动画

## 缓动动画

- 1.定义一个 0-1 的缓动系数 easing
- 2.计算出物体与终点之间的距离
- 3.计算出当前速度 速度=距离 ✖️ 缓动系数
- 4.计算新的位置 新的位置 = 当前位置 + 当前速度
- 5.重复 2-4

缓动动画中 速度和距离成正比

```js
const easing = number;
const tragetX = number;
const tragetY = number;
const vx = (tragetX - object.x) * easing;
const vy = (tragetY - object.y) * easing;
```

```js
const ball = new Ball(20, 20, 20);

const tragetX = 500;
const tragetY = 500;
const easing = 0.05;

const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  const vx = (tragetX - ball.x) * easing;
  const vy = (tragetY - ball.y) * easing;
  ball.x += vx;
  ball.y += vy;
  ball.fill();
};
frame();
```

## 弹性动画

- 1.设置一个终点
- 2.确定物体到终点的距离
- 3.运动和距离成正比

弹性动画中 加速度和距离成正比

```js
const ax = (tragetX - object.x) * easing;
const ay = (tragetY - object.y) * easing;
vx += ax;
vy == vy;
vx *= friction;
vy *= friction;
object.x += vx;
object.y += vy;
```

```js
const ball = new Ball(10, 300, 20);
let vx = 0;
const tragetX = 400;
const spring = 0.02;
const friction = 0.95;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  const ax = (tragetX - ball.x) * spring;
  vx += ax;
  vx *= friction;
  ball.x += vx;
  ball.fill();
};
frame();
```
