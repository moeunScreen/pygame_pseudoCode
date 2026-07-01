
```text
> 저자: "이제 `map[playerX][playerY]`로 직관적으로 접근할 수 있습니다."
  ㄴ독자 : "그 전에 제가 직관을 잃었습니다."
  ㄴ독자2: "그 과정에서 독자도 전치(Transpose)됐습니다."
  ㄴAI : "열을 append하는 겁니다."  
  ㄴ독자: "아 씨 그걸 왜 이제 말해."
```

### levels ###
```text
레벨들 = [레벨,레벨,레벨]
```

### level
```text
레벨 =  {    'width' : maxWidth ,
			'height' : len(맵객체) ,
			'mapObj' : 맵객체 ,
			'goals' : [(x,y),(x,y)...] ,
			'startState' : 게임시작상태객채 , 
		}
```
### mapObj
```text
list of strings
맵객체 = [ ' #####   ','##    #    ','# .$@$. #'... ]
 
        #각 기호의의미
        '#' 나무벽
		'x' 모서리벽
		'@' 플레이어시작점
		'.' 별도착점
		'$' 별
		'+' 플레이어시작점이 목표점이랑 같을때
		'*' 별시작점이 별도착점이랑 같을때
		' ' 밖에있는바닥
		'o' 안에있는바닥
		'1' 풀위에 돌
		'2' 풀위에 작은나무
		'3' 풀위에 큰나무
		'4' 풀위에 이상한나무
```
### startState
```text
게임시작상태객체 = {  'player' (x,y): ,
                    'stepCounter' : int ,
	                'stars' : [(x,y),(x,y)...]
	              }
```


```text
#파일찾기
def readLevelsFile(filename)

assert os.path.exists(filename), '못찾음: %s' % (filename)
mapFile = open(filename, 'r')
모든내용 = mapFile.readlines() + ['\r\n']
mapFile.close()

레벨들 = [] #모든 레벨의 리스트를 포함
levelNum = 0
맵텍스트라인 = [] #하나의 맵만 있음(행기반)
맵객체 = [] #맵텍스트라인에서 따옴(열기반)

#
for lineNum in range(len(모든내용))
    라인 = 모든내용[lineNum],rstrip('\r\n')
    
    #줄에 ;가 있으면, ;부터 뒤에있는내용은 전부 버림 
    if ';' in 라인
        라인 = 라인[:라인.find(';')]
        
	#빈줄이아니면 추가 2.뭔가 3. 4.써져있음, 3아니면 추가
	 빈줄이라면 하나의맵이 끝난거임
    if 라인 != ''
        맵텍스트라인.append(line)
    elif 라인=='' and len(맵텍스트라인) > 0
        #하나의맵에서 가장긴 가로줄 찾기
         그 가로줄에 맞춰서 정사각형으로 만들어야함
         다른줄들 끝에다가 ' '(스페이스) 붙여주기
        maxWidth = -1
        for i in range(len(맵텍스트라인))
            if len(맵텍스트라인[i] > maxWidth
                maxWidth = len(맵텍스트라인[i])
        for i in range(len(맵텍스트라인))
            맵텍스트라인[i] += ' ' * (maxWidth - len(맵텍스트라인[i])
        #맵텍스트라인을 맵객체로 변환
         맵객체는 list of lists 이기 때문에 
         열의 크기만큼 만들기위해 len(맵텍스트라인[0])을 씀
         그리고 행->열로 전치를 할거임
        for x in range(len(맵텍스트라인[0]))
            맵객체.append([])
            
        # 행기반 데이터를 열기반 데이터로 전치시켜 차곡차곡 쌓는 코드
        for y in range(len(맵텍스트라인))
            for x in range(maxWidth)
                맵객체[x].append(맵텍스트라인[y][x])
                
        # @(플레이어), .(목표점), $(별) 을 리스트에 넣어주기
          +(플레이어+목표점), *(별+목표점)
          goals = [] ,는 안에 (x,y)튜플들 들어감
          stars = [] ,도 안에 (x,y)튜플들 들어감
        for x in range(maxWidth)
            for y in range(len(맵객체[x]))
                if 맵객체[x][y] in ('@','+')
                    시작x = x
                    시작y = y
                if 맵객체[x][y] in ('.','+','*')
                    goals.append((x,y))
                if 맵객체[x][y] in ('$','*')
                    stars.append((x,y))
        
        assert 시작x != None and 시작y != None, ' '
        assert len(goals) > 0, ' '
        assert len(starts) >= len(goals) ' ''
        
        게임시작상태객채 = { '플레이어' : (시작x,시작y),
				            '스텝숫자' : 0,
				            'stars' : stars
				      }
		레벨객체 = { '너비' : maxWidht,
				    '높이' : len(맵객체),
				    '맵객체' : 맵객체,
				    'goals' : goals,
				    '시작게임상태' : 게임시작상태객체
				  }
	    레벨들.append(레벨객체)
	    
	    #다음맵을 위해 변수리셋
	    맵택스트라인 = []
	    맵객체 = []
	    게임상태객체 = {}
	    levelNum += 1
                
return 레벨들        
```


