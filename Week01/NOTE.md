学习笔记

学习了 leetcode基本使用，
了解了双指针
复习了递归, 链表操作


数组和链表是最基础的数据结构

心得:
1.梳理思路

2.代码实现落地还有段距离,需要考个各种情况和边界情况的处理
作业题
1. 删除排序数组中的重复项
	（Facebook、字节跳动、微软在半年内面试中考过）
	有序数组,隐含重复数据是相邻的
	画出图中的变化,画图写代码
	双指针中快指针从1开始遍历

	let removeDuplicates = function(nums) {
		let len	= 1;
		for (let i = 1; i < nums.length; i++) {
			if (nums[i] != nums[i - 1]) nums[len++] = nums[i];
		}
		return len;
	}

	console.log(removeDuplicates([1,1,3,3,4,5,5 ,7 ,7]));

	
2.旋转数组
	（微软、亚马逊、PayPal 在半年内面试中考过）
var rotate = function(nums, k) {
	nums.splice(0, 0, ...nums.splice(nums.length - k));
}



3.合并两个有序链表
var mergeTwoLists = function(l1, l2) {
	if (l1 === null) {
		return l2;
	} else if(l2 === null) {
		return l1;
	} else if (l1.val < l2.val) {
		l1.next	= mergeTwoLists(l1.next, l2);
        return l1;
	} else {
		l2.next	= mergeTwoLists(l1, l2.next);
        return l2;
	}
}
