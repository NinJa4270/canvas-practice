# 边界检测

```js
if (ball.x < ball.radius) {
  // 左侧边界
} else if (ball.x > canvas.width - ball.radius) {
  // 右侧边界
} else if (ball.y < ball.radius) {
  // 上侧边界
} else if (ball.y > canvas.height - ball.radius) {
  // 下侧边界
} else {
  // 内部
}
```

## 边界限制

```js
const checkBorder = (ball) => {
  if (ball.x < ball.radius) {
    // 左侧边界
    ball.x = ball.radius;
  } else if (ball.x > canvas.width - ball.radius) {
    // 右侧边界
    ball.x = canvas.width - ball.radius;
  }

  if (ball.y < ball.radius) {
    // 上侧边界
    ball.y = ball.radius;
  } else if (ball.y > canvas.height - ball.radius) {
    // 下侧边界
    ball.y = canvas.height - ball.radius;
  }
};
```

## 边界生成

```js
const getRandomColor = () => {
  const r = Math.floor(Math.random() * 255);
  const g = Math.floor(Math.random() * 255);
  const b = Math.floor(Math.random() * 255);
  return `rgba(${r},${g},${b},1)`;
};

const balls = [];
const n = 200;
const gravity = 0.15;

for (let i = 0; i < 50; i++) {
  const ball = new Ball(300, 500, Math.random() * 20, getRandomColor());
  ball.vx = (Math.random() * 2 - 1) * 3;
  ball.vy = (Math.random() * 2 - 1) * 10;
  balls.push(ball);
}
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  balls.forEach((ball) => {
    if (
      (ball.x < -ball.radius) |
      (ball.x > canvas.width + ball.radius) |
      (ball.y < -ball.radius) |
      (ball.y > canvas.height + ball.radius)
    ) {
      ball.x = 300;
      ball.y = 500;
      ball.vx = (Math.random() * 2 - 1) * 3;
      ball.vy = (Math.random() * 2 - 1) * 10;
    }
    ball.fill();
    ball.x += ball.vx;
    ball.y += ball.vy;
    ball.vy += gravity;
  });
};
frame();
```

## 边界环绕

```js
const ball = new Ball(0, 300);
const vx = 2;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  ball.x += vx;
  if (ball.x > canvas.width + ball.radius) {
    // 右侧边界
    ball.x = -ball.radius;
  }

  ball.fill();
};
frame();
```

## 边界反弹

```js
const ball = new Ball(0, 300);
let vx = (Math.random() * 2 - 1) * 3;
let vy = (Math.random() * 2 - 1) * 3;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  ball.x += vx;
  ball.y += vy;

  if (ball.x < ball.radius) {
    ball.x = ball.radius;
    vx = -vx;
  } else if (ball.x > canvas.width - ball.radius) {
    ball.x = canvas.width - ball.radius;
    vx = -vx;
  }

  if (ball.y < ball.radius) {
    ball.y = ball.radius;
    vy = -vy;
  } else if (ball.y > canvas.height - ball.radius) {
    ball.y = canvas.height - ball.radius;
    vy = -vy;
  }

  ball.fill();
};
frame();
```
