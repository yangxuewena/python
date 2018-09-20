#题目
三数之和
## 问题： 
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。
## 编程实现：
class Solution(object):

    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """      
        ans = []
        nums.sort()
        for i in range(len(nums)-2):
            if i == 0 or nums[i] > nums[i-1]:
                left = i+1
                right = len(nums)-1
                while left < right:
                    ident = nums[left] + nums[right] + nums[i]
                    if ident == 0:      
                        ans.append([nums[i], nums[left], nums[right]])
                        left += 1; right -= 1
                        while left < right and nums[left] == nums[left-1]:  # 去重
                            left += 1
                        while left < right and nums[right] == nums[right+1]:
                            right -= 1
                        
                    elif ident < 0:
                        left += 1
                    else:
                        right -= 1
        return ans
        
##总结
首先对数组进行排序，再确定a,b,c 中的第一个数i，剩下两个数从i以后寻找，找到之后存入ans，继续寻找下一个，若遇到与上一个重复的则跳过。