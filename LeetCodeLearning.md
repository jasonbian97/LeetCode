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

双指针：firstindex为第一个指针，j为第二个指针，两个指针追逐前行，j先去探路，然后firstindex追上�?

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

字符串操作：

1. Slice 的使�?
2. 怎样判断某一个字符是数字？间接使用ASCII
3. 使用str.find()操作快速定位，如果没有找到，返回值为-1而不�?！！�?

# 833
```python
class Solution(object):
    def ReplaceString(self,i , Slist, indexes, sources, targets):
        temp=indexes[i]
        sourcelist=list(sources[i])
        length=len(sourcelist)
        for j in range(0,length):
            if Slist[temp+j] is not sourcelist[j]:
                return 
        Slist[temp:temp+length]=targets[i]
        return

    def quicksort(self,indexes, sources, targets):
        length = len(indexes)
        for i in range(0,length-1):
            largest = i
            for j in range(i+1,length):
                if indexes[j]>indexes[largest]:
                    tmp = indexes[j]
                    indexes[j] = indexes[largest]
                    indexes[largest]=tmp
                    tmp = sources[j]
                    sources[j] = sources[largest]
                    sources[largest]=tmp                    
                    tmp = targets[j]
                    targets[j] = targets[largest]
                    targets[largest]=tmp
                    
    def findReplaceString(self, S, indexes, sources, targets):
        num=len(indexes)
        Slist=list(S)
        Solution.quicksort(self,indexes, sources, targets)
        for i in range(0,num):
            Solution.ReplaceString(self,i , Slist, indexes, sources, targets)
        return ''.join(Slist)
```
1.先通过排序将index索引和字符串索引来进行从高到低的排序，然后对在index的位置对字符串进行逐一替换，使用双指针的方式进行比较和替换。
2.由于使用了排序，替换后的索引不会影响字符串前部的索引

