# 碰撞检测

## 外接矩形判定

#### 矩形是否碰撞

```js
const checkRect = (rectA, rectB) => {
  return !(
    rectA.x + rectA.width < rectB.x ||
    rectB.x + rectB.width < rectA.x ||
    rectA.y + rectA.height < rectB.y ||
    rectB.y + rectB.height < rectA.y
  );
};
```

## 外接圆判定

```js
const checkCircle = (circleA, circleB) => {
  const dx = circleA.x - circleB.x;
  const dy = circleA.y - circleB.y;
  const distance = Math.sqrt(dx * dx + dy * dy);
  if (distance < (circleA.radius = circleB.radius)) {
    return true;
  } else {
    return false;
  }
};
```
