# for-else

* for 문이 정상적으로 수행이 되면, else에 있는 구문이 수행됨
* 중간에 break가 되면, else는 출력안됨

```python
for x in [1,2,3,4]:
    print(x)
else:
    print('완료')
```

➡️![](<../.gitbook/assets/image (6).png>)

```python
for x in [1,2,3,4]:
    print(x)
    if x == 4:
        break
else:
    print('완료')
```

➡️ ![](<../.gitbook/assets/image (5).png>)
