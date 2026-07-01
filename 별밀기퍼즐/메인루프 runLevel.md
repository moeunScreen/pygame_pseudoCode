
```text
상수
FPS = 30
윈도우너비 = 800 # in pixels  
윈도우높이 = 600 # in pixels  
윈도우너비반 = int(WINWIDTH / 2)  
윈도우높이반 = int(WINHEIGHT / 2)  
  
# The total width and height of each tile in pixels.  
타일너비 = 50  #in pixels
타일높이 = 85  #in pixels
TILEFLOORHEIGHT = 40

```


```text
while구문안
    #runLevel은 'solved','next','back','reset' 문자열반환해줌
    result = runLevel(levels, 지금레벨인덱스)
    
    if result in ('solved','next')
        지금레벨인덱스 += 1
        if 지금레벨인덱스가 레벨보다 크면 0으로 초기화
    elif result == 'back' 
        지금레벨인덱스 -= 1
        if 지금레벨인덱스가 0보다 작으면 마지막으로 초기화
    elif result == 'reset'
        pass
         #while를 다시한번돌음(지금레벨맵초기화)
```

