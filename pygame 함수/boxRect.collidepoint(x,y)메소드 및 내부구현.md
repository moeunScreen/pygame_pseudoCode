
```text
boxRect.collidepoint(x,y)메소드는
boxRect = pygame.Rect 객체 안에
x,y가 Rect객체 안에 있는 좌표면
True 반환

조건문으로 
     if boxRect.collidepoint(x, y):
          return (boxx, boxy)
이런식로 박스의 위치를 알아냄
```

---

## 충돌검사(Rect, x, y)
```text
메소드내부구현구조
bool collidepoint(Rect r, int x, int y) {  
return (x >= r.left &&  
x < r.right &&  
y >= r.top &&  
y < r.bottom);  
}
```

## 사각형(x,y,w,h)
```text
class Rect:
    def __init__(self, x, y, w, h):
        self.left = x
        self.top = y
        self.right = x + w
        self.bottom = y + h

    def collidepoint(self, x, y):
        return self.left <= x < self.right and self.top <= y < self.bottom
```