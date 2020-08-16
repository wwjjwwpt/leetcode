# leetcode
## 数组中重复的数字
```
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        c = dict()
        for i in nums:
            if i in c:
                return i
            else:
                c[i] = 1
```
## 二维数组中的查找
### 利用in算法
```
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        for i in matrix:
            if target in i:
                return True
            else:
                continue
        return False
```
### 利用二分查找
```
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        for i in matrix:
            low = 0
            high = len(i)-1
            if(high<0):
                return False
            else:
                while(low <= high):
                    mid = (high+low)//2
                    if(target==i[mid]):
                        return True
                    elif(target>i[mid]):
                        low = mid + 1
                    else:
                        high = mid - 1
        return False
```
## 替换空格
replace函数无法使用
```
class Solution:
    def replaceSpace(self, s: str) -> str:
        res = []
        for ch in s:
            if( ch == ' '):
                res.append("%20")
            else:
                res.append(ch)
        return "".join(res)
```
## 从尾打印链表60ms
利用链表逆序
pqm三个参数
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reversePrint(self, head: ListNode) -> List[int]:
        a= []
        p = head
        if(p==None):
            return a
        q = head.next
        if(q ==None):
            a.append(p.val)
            return a
        m = q.next
        while(q!=None):
            q.next = p
            p = q
            if(m ==None):
                break
            q = m
            m = m.next
        head.next = None
        while(q!=None):
            a.append(q.val)
            q = q.next
        return a
```
### 利用insert80ms
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reversePrint(self, head: ListNode) -> List[int]:
        a = []
        while(head):
            a.insert(0,head.val)
            head = head.next
        return a
```
### 利用切片倒序
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reversePrint(self, head: ListNode) -> List[int]:
        res = []
        p = head
        while p:
            res.append(p.val)
            p = p.next
        return res[::-1]
```
## 二叉树的重建

## 剑指 Offer 15. 二进制中1的个数
```
class Solution:
    def hammingWeight(self, n: int) -> int:
        b = []  # 存储余数
        while True:  # 一直循环，商为0时利用break退出循环
            s = n // 2  # 商
            y = n % 2  # 余数
            b = b + [y]  # 每一个余数存储到b中
            if s == 0:
                break  # 商为0时结束循环
            n = s
        #这里不需要倒序
        count = 0
        for i in b:
            if i ==1:
                count+=1
        return count
```
