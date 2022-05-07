## 나의 풀이

1. double for loop으로 한 쌍을 brute force로 찾아내기. 최대 O(N^2)의 시간복잡도를 가짐.
2. 우선 정렬하고, brute force를 시전하되 target의 크기보다 큰 값이 나오면 더 빨리 break 가능. 복잡도는 역시 O(N^2).
3. sort를 하고, 맨 앞과 맨 뒤에서 각각 포인터를 활동시킨다. 만약 범위가 벗어나면 앞의 것을, 적다면 뒤의 것을. 복잡도는 O(NlogN).

당연하겠지만, 대부분의 베스트 솔루션은 O(N^2)짜리 풀이다. 이것도 문제는 없겠지만, 가장 좋은 풀이는 세 번째.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        i, j = 0, len(nums)-1
        nums_dic = sorted([[num, k] for k, num in enumerate(nums)])
        
        while True:
            temp = nums_dic[i][0] + nums_dic[j][0]
            if temp == target: return [nums_dic[i][1], nums_dic[j][1]]
            elif temp < target: i += 1
            else: j -= 1
```
