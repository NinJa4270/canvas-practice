# 用户交互

## 捕获物体

矩形捕获
圆捕获
多边形捕获
不规则图形捕获
后两种采用 分离轴定理(SAT) 最小平移向量(MTV)
http://www.demodashi.com/demo/10423.html

### 矩形捕获

```js
if (
  mouse.x > rect.x &&
  mouse.x < rect.x + rect.width &&
  mouse.y > rect.y &&
  mouse.y < rect.y + rect height
) {
}
```

### 圆捕获

```js
const dx = mouse.x - ball.x;
const dy = mouse.y - ball.y;
const distance = Math.sqrt(dx * dx + dy * dy);
if (distance < ball.radius) {
}
```

### 捕获静止物体

```js
class Ball {
  // ...
  checkMouse(mouse) {
    const dx = mouse.x - this.x;
    const dy = mouse.y - this.y;
    const distance = Math.sqrt(dx * dx + dy * dy);
    if (distance < this.radius) {
      return true;
    } else {
      return false;
    }
  }
}

canvas.addEventListener("mousemove", function () {
  if (ball.checkMouse(mouse)) {
    text.innerText = "移入小球";
  } else {
    text.innerText = "移出小球";
  }
});

const mouse = getMouse(canvas);

const ball = new Ball(300, 300, 80);
ball.fill();
```

### 捕获运动物体

```js
const ball = new Ball(300, 300, 20);
ball.vx = 2;
ball.vy = 3;
let isMouseDown = false;

canvas.addEventListener("mousemove", function () {
  if (ball.checkMouse(mouse)) {
    isMouseDown = true;
  } else {
    isMouseDown = false;
  }
});

const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  checkBorder(ball);
  ball.fill();
  if (!isMouseDown) {
    ball.x += ball.vx;
    ball.y += ball.vy;
  }
};
frame();
```

## 拖拽物体

```js
const ball = new Ball(300, 300, 20);
let dx = 0,
  dy = 0;
canvas.addEventListener("mousedown", function () {
  if (ball.checkMouse(mouse)) {
    dx = mouse.x - ball.x;
    dy = mouse.y - ball.y;
    document.addEventListener("mousemove", onMouseMove, false);
    document.addEventListener("mouseup", onMouseUp, false);
  }
});

function onMouseMove() {
  ball.x = mouse.x - dx;
  ball.y = mouse.y - dy;

  // 边界检测
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
}
function onMouseUp() {
  document.removeEventListener("mouseup", onMouseUp, false);
  document.removeEventListener("mousemove", onMouseMove, false);
}

const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  ball.fill();
};

frame();
```

## 抛掷物体

```js
const ball = new Ball(300, 300, 20);
let isMouseDown = false;
let dx = 0,
  dy = 0,
  oldX = 0,
  oldY = 0,
  vx = 0,
  vy = 0;
const gravity = 1.5; // 重力
const bounce = -0.8; // 反弹消耗

canvas.addEventListener("mousedown", function () {
  if (ball.checkMouse(mouse)) {
    isMouseDown = true;
    oldX = ball.x;
    oldY = ball.y;
    dx = mouse.x - ball.x;
    dy = mouse.y - ball.y;
    document.addEventListener("mousemove", onMouseMove, false);
    document.addEventListener("mouseup", onMouseUp, false);
  }
});

function onMouseMove() {
  ball.x = mouse.x - dx;
  ball.y = mouse.y - dy;

  // 边界检测
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
}
function onMouseUp() {
  isMouseDown = false;
  document.removeEventListener("mouseup", onMouseUp, false);
  document.removeEventListener("mousemove", onMouseMove, false);
}
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);

  if (isMouseDown) {
    vx = ball.x - oldX;
    vy = ball.y - oldY;

    oldX = ball.x;
    oldY = ball.y;
  } else {
    vy += gravity;
    ball.x += vx;
    ball.y += vy;
    // 边界检测
    if (ball.x < ball.radius) {
      // 左侧边界
      ball.x = ball.radius;
      vx = vx * bounce;
    } else if (ball.x > canvas.width - ball.radius) {
      // 右侧边界
      ball.x = canvas.width - ball.radius;
      vx = vx * bounce;
    }
    if (ball.y < ball.radius) {
      // 上侧边界
      ball.y = ball.radius;
      vy = vy * bounce;
    } else if (ball.y > canvas.height - ball.radius) {
      // 下侧边界
      ball.y = canvas.height - ball.radius;
      vy = vy * bounce;
    }
  }
  ball.fill();
};
frame();
```
