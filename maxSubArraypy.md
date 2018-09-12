#题目
最大子序和
## 问题： 
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
## 编程实现：
class Solution(object):

    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l = len(nums)
        for i in range(1,l):
            submax = max(nums[i-1]+nums[i],nums[i])
            nums[i] = submax
        return max(nums)
##总结
设以第i个数字结尾的连续子数组的最大和submax,只有两种情况，一种是只包含第i个数字本身；另一种是第i个数字本身加上以i-1项结尾的连续连续子数组的最大和，求这两种情况的最大值，保存在nums数组中，最后求出数组中的最大值。