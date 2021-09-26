- python code

```python
def solution(x, n):
    ans = []
    for i in range(n):
        ans.append(x*(i+1))
    return ans

```

- cpp code

```cpp
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) 
{
    vector<long long> answer;
    int a = 0;
    for(n; n>0; n--) 
    {
        answer.push_back(a += x);
    }
    return answer;
}
```
