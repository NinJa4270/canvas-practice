# 事件

## 鼠标事件

mousedown/mouseup/mousemove

```js
const canvas = document.getElementById("canvas");
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
canvas.addEventListener("mousemove", function () {
  console.log(mouse.x, mouse.y);
});
```

## 键盘事件

keydown/keyup

```js
const getKey = () => {
  const key = {
    direction: "",
  };
  window.addEventListener("keydown", function (e) {
    switch (e.keyCode) {
      case 38:
      case 87:
        key.direction = "up";
        break;
      case 39:
      case 68:
        key.direction = "right";
        break;
      case 40:
      case 83:
        key.direction = "down";
        break;
      case 37:
      case 65:
        key.direction = "left";
        break;
      default:
        key.direction = "";
        break;
    }
  });
  return key;
};

const key = getKey();
window.addEventListener("keydown", function (e) {
  console.log(key.direction);
});
```

## 循环事件
使用 requestAnimationFrame
```js
let fx = 0;
const frame = () => {
  window.requestAnimationFrame(frame);
  ctx.clearRect(0, 0, 600, 600);
  ctx.beginPath();
  ctx.arc(fx, 70, 20, 0, Math.PI * 2);
  ctx.closePath();
  ctx.fillStyle = "red";
  ctx.fill();
  fx += 2;
  if (fx >= 600) fx = 0;
};
frame();
```
