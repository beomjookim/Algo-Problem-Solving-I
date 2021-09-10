- python code

```python
def solution(s):
    return s.lower().count('p') == s.lower().count('y')
```

- cpp code

```cpp
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    int b = 0;
    for(char c: s) 
    {
        if(c == 'p' || c == 'P') b++; 
        else if(c == 'y' || c == 'Y') b--;
    }
    return !b;
}
```
