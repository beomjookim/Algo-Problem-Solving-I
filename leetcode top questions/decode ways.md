##풀이

DP. 계단 오르기 1, 2, 3 처럼 recursion으로 풀 수도 있고, 아래와 같이 for로 활용할 수도 있다. dict가 꼭 없어도 괜찮을 수 있다.  
이게 DP 문제라는 걸 잊지 말자.  

중요한 것은 아웃풋으로 모든 케이스를 나열하는 것이 아니라 최종 개수만 알면 된다는 것이다! 그게 제일 중요함.  
굳이 dict 안 쓰고 간단하게 dp list로 끝낼 수 있는 문제였다.  


```python
    def numDecodings(self, s: str) -> int:
        if not s or s[0]=='0': return 0

        dp = [0 for x in range(len(s) + 1)] 

        # base case initialization
        dp[0:2] = [1,1]

        for i in range(2, len(s) + 1): 
            # One step jump
            if 0 < int(s[i-1:i]):    #(2)
                dp[i] = dp[i - 1]
            # Two step jump
            if 10 <= int(s[i-2:i]) <= 26: #(3)
                dp[i] += dp[i - 2]
                
        return dp[-1]
```
