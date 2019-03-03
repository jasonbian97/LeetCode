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

# 831

```python
class Solution(object):
    def maskPII(self, S):
        """
        :type S: str
        :rtype: str
        """
        if (S.find('@')!=-1):
            S1=S.lower()
            name1=S1[0]
            name2=S1[S1.find('@')-1]
            res=name1+'*****'+name2+S1[S.find('@'):]
        else:
            clean=""
            for i in S:
                if (i>="0") and (i<="9"):
                    clean=clean+i
            if len(clean)==10:
                res="***-***-"+clean[-4:]
            else:
                num=len(clean)-10
                res="+"+"*"*num+"-***-***-"+clean[-4:]
        return res
```

