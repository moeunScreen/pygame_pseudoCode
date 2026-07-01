
삭제를 할때
기본적 for 구문으로 리스트를 앞부분에서 검사해서
`animals = ['cat', 'mouse', 'dog', 'horse']`
dog를 삭제하고 싶어서 for i in range(len())을 쓰면(증가시키면서 검사)
len(4)이기 때문에 for 는 i = 3 일때까지 검사하게되고
```text
for i in range(len(animals)):
if animals[i] == 'dog':
del animals[i]
```
i=2일때 dog가 삭제되지만 
그 순간 리스트는 앞으로 밀리고
`animals = ['cat', 'mouse', 'horse']` 
i=3을 검사할때 
인덱스 에러남(dog가 삭제되고 그 자리에 horse가 와서 값이 없기때문에)

그러나 for i in range(len(),-1,-1)으로 리스트를 뒷부분에서 부터 검사하면
삭제하면
`animals = ['cat', 'mouse', 'horse']`
다음 검사는 i=1이기 때문에
인덱스 에러가 나지 않음

