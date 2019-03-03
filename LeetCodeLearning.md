# 830

```python
class Solution(object):
    def largeGroupPositions(self, S):
        list1=list(S)
        result=[]
        firstindex=0
        while firstindex<len(list1):
            i=list1[firstindex]
            j=0
            while firstindex+j<len(list1) and list1[firstindex+j]==i:
                j+=1
            if j>=3:
                result.append([firstindex,firstindex+j-1])                   
            firstindex+=j
        return result
```

双指针：firstindex为第一个指针，j为第二个指针，两个指针追逐前行，j先去探路，然后firstindex追上。

