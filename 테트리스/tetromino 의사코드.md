
## 상태변수
보드 = board 
마지막키아래시간 = lastMoveDownTime 
마지막키옆시간 = lastMoveSidewaysTime
마지막떨어진시간 = lastFallTime 
아래이동 = movingDown
왼쪽이동 = movingLeft
오른쪽이동 = movingRight
score
level, fallFreq 
  
지금모양 = fallingPiece 
다음모양 = nextPiece

## 테트리스 의사코드
```text
❗while 구문 안
    ✅if 지금모양 == None:
        지금모양 = 다음모양
        다음모양 = 만들기()
        마지막떨어진시간 = time.time()
        
        if not 가능한가()
           return 
    ✅끝내기확인()
    ✅for 이벤트 in pygame.event.get():
        1️⃣if 버튼업
			if K_p:
				디스플레이 색칠
				텍스트('Paused')
				마지막떨어진시간 = time.time()
				마지막키아래시간 = time.time()
				마지막키옆시간 = time.time()
			elif K_LEFT or K_a:
				왼쪽이동 = False
			elif K_RIGHT or K_d:
				오른쪽이동 = False
			elif K_DOWN or K_s:
				 아래이동 = False
        2️⃣elif 버튼다운
			if 왼쪽키 and 가능한가(,,adjX=-1)
				지금모양['x'] -= 1
				왼쪽이동 = True
				오른쪽이동 = False
				마지막키옆시간 = time.time()
			elif 오른쪽키 and 가능한가(,,adjX=1)
				지금모양['x'] += 1
				오른쪽이동 = True
				왼쪽이동 = False
				마지막키옆시간 = time.time()
			elif 윗키 
				(지금모양['회전']+1) % len(모양[지금모양['shape']])
				if not 가능한가()
					(지금모양['회전']-1) % len(모양[지금모양['shape']])
			elif K_q
				(지금모양['회전']-1) % len(모양[지금모양['shape']])
				if not 가능한가()
					(지금모양['회전']+1) % len(모양[지금모양['shape']])
			
			elif 아래키
				아래이동 = True
				if 가능한가(,,adjY=1)
					지금모양['y'] += 1
				마지막떨어진시간 = time.time()
			elif 스페이스키
				아래이동 = False
				왼쪽이동 = False
				오른쪽이동 = False
				for i in range(1, 보드높이)
					if not 가능한가(,,adjY = i)
						break
				지금모양['y'] += i - 1
		
		#키를 계속 누르고 있을때(버튼다운(KEYDOWN)이벤트가 발생하지 않음)
	✅if (왼쪽이동 or 오른쪽이동) and 왼쪽이동가능시간(0.15초)
		if 왼쪽이동 and 가능한가(,,adjX = -1)
			지금모양['x'] -= 1
		elif 오른쪽이동 and 가능한가(,,adjX = 1)
			지금모양['x'] += 1 
		마지막키옆시간 = time.time()
		
	✅if 아래이동 and 아래이동가능시간(0.1초) and 가능한가(,,adjY = 1)
		지금모양['y'] += 1
		마지막키아래시간 = time.time()
	
	✅if 자동떨어지는시간
		if not 가능한가(,,adjY = 1)
			보드더하기(보드,지금모양)
			score += 완성된라인정리(board)
			level, 자동떨어지는시간 = 레벨과시간계산(score)
			지금모양 = None
		else 
			지금모양['y'] += 1
			마지막떨어진시간 = time.time()
	
	✅디스플레이.칠하기(컬러) 
		보드그리기(보드) 
		스코어레벨표시(score,level)
	✅다음모양표시(다음모양)
	✅if 지금모양 != None
		 모양그리기(지금모양)
	
	✅pygame.display.update()
	✅FPS설정(FPS)     

while 구문 끝❗
```
