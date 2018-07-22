
# Leetcode: Bitwise AND of Numbers Range     :BLOG:Medium:

---

Bitwise AND a range of numbers  

---

Similar Problems:  

-   [Review: Math Problems,](https://code.dennyzhang.com/review-math) Tag: [math](https://code.dennyzhang.com/tag/math)

---

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.  

For example, given the range [5, 7], you should return 4.  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/problems/bitwise-and-of-numbers-range)  

Credits To: [leetcode.com](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/)  

Leave me comments, if you have better ways to solve.  

---

    ## Blog link: https://code.dennyzhang.com/bitwise-and-of-numbers-range
    class Solution(object):
        def rangeBitwiseAnd(self, m, n):
    	"""
    	:type m: int
    	:type n: int
    	:rtype: int
    	"""
    	## Idea: 2^k is in the middle of [m, n], the result is 0
    	## Complexity:
    	if m < 0:
    	    return 0
    	if m == 0:
    	    return 0
    	if m == n:
    	    return m
    
    	m_log2 = 0
    	pow_m = 1
    	while m > pow_m:
    	    pow_m = pow_m*2
    	    m_log2 += 1
    
    	n_log2 = 0
    	pow_n = 1
    	while n > pow_n:
    	    pow_n = pow_n*2
    	    n_log2 += 1
    
    	if n == pow_n:
    	    return 0
    
    	if m == pow_m:
    	    if n >= pow_m*2:
    		return 0
    	    else:
    		return m
    	if n_log2 > m_log2:
    	    return 0
    
    	# print("m: %d, pow_m: %d" % (m, pow_m))
    	res = pow_m/2
    	res += self.rangeBitwiseAnd(m-res, n-res)
    	return res
