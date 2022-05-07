## 나의 풀이

1. 가장 첫 번째 string을 가지고 그 다음 string과 비교하여 공통 부분 남기고, 그걸 또 그 다음으로 넘겨서 확인하는 것을 반복한다. 시간복잡도는 O(N^2).
2. zip을 활용해서 하나씩 확인해주기. 이것도 시간복잡도는 O(N^2)으로 같으나, 더 간결하므로 이 방법 사용.

참고로 zip 쓰면 원소 중 길이가 가장 작은 녀석 길이 끝났을 때 멈춘다!  

```python
class Solution:
    def longestCommonPrefix(self, words: List[str]) -> str:
        n = len(words)
        res = ''

        for char_set in zip(*words):
            temp = char_set[0]
            if ''.join(char_set).replace(temp, ''): break
            res += temp

        return res
```
