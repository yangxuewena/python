#题目
Z字形变换
## 问题： 
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
## 编程实现：
class Solution(object):

    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """

        if numRows == 1:
            return s

        result = []
        r = 0
        flag = 1
        l = len(s)
        res = [[] for _ in range(numRows)]
        for i in range(l):
            res[r].append(s[i])
            if flag == 1:
                r = r + 1
                if r == (numRows - 1):
                    flag = -1
            elif flag == -1:
                r = r - 1
                if r == 0:
                    flag = 1
        for i in range(numRows):
            result = result + res[i]
        result = ''.join(result)#将单个字符串连接成新的字符串
        return result
##总结
若只有一行返回原字符串，
若大于一行，定义一个flag，标志填充方向，若flag等于1，从第0行向最后一行的方向填充；若flag等于-1，从最后一行向第一行的方向填充，
最后将每行的字符连接起来，再将单个字符串连接成整个字符串。