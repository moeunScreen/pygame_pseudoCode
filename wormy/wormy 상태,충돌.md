
## wormy 상태저장
```
startx = random.randint(5, CELLWIDTH - 6)  
starty = random.randint(5, CELLHEIGHT - 6)  
wormCoords = [ {'x': startx, 'y': starty},  
               {'x': startx - 1, 'y': starty},  
               {'x': startx - 2, 'y': starty} ]
```
*리스트 안에 딕셔너리 형태로 
머리랑 몸체 꼬리 저장*

## 충돌판정
```
▶ if ◀ wormCoords[HEAD]['x'] == -1 or
    wormCoords[HEAD]['x'] == CELLWIDTH or   
    wormCoords[HEAD]['y'] == -1 or
    wormCoords[HEAD]['y'] == CELLHEIGHT:
            return                 # game over
```
*머리가 왼쪽 바깥을 벗어났을때
머리가 오른쪽 바깥을 벗어났을때
머리가 위로 벗어났을때
머리가 아래로 벗어났을때*
```
 ▶ for wormBody in wormCoords[1:]: ◀
	 if wormBody['x'] == wormCoords[HEAD]['x'] and     
		wormBody['y'] == wormCoords[HEAD]['y']:
			return                  # game over
```
*몸체가 머리랑 부딪혔을때*