```python
sort 시에 sort(key = lambda x: blah blah...) 이것 까먹지 말자.
```

그리고, python에서 in operator는 list와 set, dict 모두에서 사용 가능한데, list는 당연히 O(n)이지만 나머지 둘은 해쉬이므로 O(1)이다.  
이걸 사용하면 시간 복잡도를 드라마틱하게 줄일 수 있다. 시간 복잡도를 줄여야 할 때는 해쉬를 첫 번째로 생각해내자.
