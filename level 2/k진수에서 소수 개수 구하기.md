- 브레인 스토밍

각각을 모듈화 하면 쉬운 문제인데, 생각할 거리를 정말 많이 던져준다.  
1. n -> 10으로의 진법 변환은 int(대상, 진수)를 쓰면 한 방 컷이지만, 반대의 경우 while loop을 시전해줘야 하는 것 잊지 말자.
2. 소수(prime number) 구하기: 두 가지 방법이 있다. brute force 시전하거나, 에라토스테네스의 체 시전하거나. 나는 그간 에라토스테네스의 시간복잡도적 성능 때문에 소수 구하기 == 에라토스테네스의 체라고 생각했다. 그런데 이 문제에서는 오히려 에라토스테네스의 체를 썼더니 런타임 에러(메모리 초과)가 떴다. 에라토스테네스의 체는 시간복잡도를 이득보는 대신, 공간복잡도를 극단적으로 잡아먹는 녀석이다. 즉, 한 번에 범위 안에 있는 모든 수를 소수 판정하기 때문에 이렇게 한 번에 다 판정하는 게 필요할 때 쓰면 좋다. 적절한 방법을 골라서 쓰는 방법을 익히자.  
3. 또한 min, max 같은 python 내장 메소드에도 역시나 option 활용 가능하다. 두 번째 인자로 key = lambda x: something 시전해주면 됨!

- python code

```python
from math import sqrt
from math import floor

def solution(n, k):
    cvtd = ''
    while n:
        cvtd = str(n%k) + cvtd
        n //= k
    cands = list(map(int, [temp for temp in cvtd.split('0') if temp]))
    # 진법변환 결과
    
    def isPrime(num):
        for i in range(2, floor(sqrt(num)) + 1):
            if not num%i: return False
        return True if num != 1 else False
    # 소수판별
    
    return sum([isPrime(cand) for cand in cands])
```
