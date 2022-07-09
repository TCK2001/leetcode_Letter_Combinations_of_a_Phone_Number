# leetcode_Letter_Combinations_of_a_Phone_Number
+ 숫자를 대입하면 핸드폰에 있는 알파벳으로 모든 조합 가능한 조합을 리턴
+ 輸入一個值，並把所以手機的英文子母組合的可能性全部列出來

-----
+ Example1
```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```
----
+ Example2
```
Input: digits = ""
Output: []
```
----
+ Example3
```
Input: digits = "2"
Output: ["a","b","c"]
```
----
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        key = {                   # 우선 모든 알파벳 저장 해놓기
            '2':['a','b','c'], 
            '3':['d','e','f'],
            '4':['g','h','i'],
            '5':['j','k','l'],
            '6':['m','n','o'],
            '7':['p','q','r','s'],
            '8':['t','u','v'],
            '9':['w','x','y','z']
        }
        ans = []
        if len(digits) > 0:      # 길이가 0 이상일떄 판단식 들어감
            for i in digits:     # input이 23 이면 i=0 -> 2 , i=1 ->3
                if len(ans) == 0:# 만약 처음에 아무것도 없는 상태면
                    ans.extend(key[i]) # key값을 넣어줌
                else: # 1개 이상의 값일때 ...
                    sub = []
                    for j in ans: # 첫번째 값으로
                        for k in key[i]: # 두번째부터 하나하나씩 모든 가능성을 대조해서 
                            sub.append(j + k) # 넣음
                    ans = sub # 모든회문을 돌고나면 마지막 답
        return(ans)
```
---
결론 : 
그냥 매우 간단한 반복문으로 풀기 * extend랑 append 차이점 알아야함 ! extend는 [1,2,3,4] 이렇게 말그래도 추가하는거지만 append 는 [1,2,3,[4]]그냥 통쨰로 넣어버린다
---
結論 : 
應該有更快的方法，但我這一題直接用最單純的for迴圈去處理，但一定要知道extend和append的差別，差別在於[1,2,3,4]和[1,2,3,[4]]前面是extend後面是append感覺到差別嗎? 一個是把iterable裡的東西放進去(extend)，另外一個是把一個元素放進去(append)。

---
### Result
Runtime: 25 ms, faster than 98.96% of Python3 online submissions for Letter Combinations of a Phone Number.\
Memory Usage: 13.8 MB, less than 78.31% of Python3 online submissions for Letter Combinations of a Phone Number.
