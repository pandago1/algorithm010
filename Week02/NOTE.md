学习笔记
学习了树结构 中序遍历 前序遍历 后序遍历 N叉树

///////////////////////////////////////////
242. 有效的字母异位词
var isAnagram = function(s, t) {
	if (s.length !== t.length) return false; 
	var map	= {};
	for (var i = 0; i < s.length; i++) {
		if (!map[s[i]]) {
			map[s[i]]	= 0;
		}
		if (!map[t[i]] ) {
			map[t[i]]	= 0;
		}
		map[s[i]]++;
		map[t[i]]--;
	}
	for (var v in map) {
		if (map[v] != 0)  {
			return false; 
		}
	}
	return true;
}

//////////////////////////////////////////
94. 二叉树的中序遍历
递归
var inorderTraversal = function(root) {
    let nums    = [];
    let fun     = (root) =>{
        root.left && fun(root.left);
        nums.push(root.val);
        root.right && fun(root.right);
    }
    root && fun(root);
    return nums;
};
递归2
var inorderTraversal = function(root) {
  if (root) {
    return [...inorderTraversal(root.left), root.val, ...inorderTraversal(root.right)]
  } else {
    return []
  }
};

栈遍历
var inorderTraversal = function(root) {
	let nums	= [];
	let stack	= [];
	while (root || stack.length) {
		while (root) {
			stack.push(root);
			root	= root.left;
		}
		root	= stack.pop();
		nums.push(root.val);
		root	= root.right;
	}
	return nums;
};

//////////////////////////////////////////
144. 二叉树的前序遍历
前序递归
var preorderTraversal = function(root) {
	return root ? [root.val, ...preorderTraversal(root.left), ...preorderTraversal(root.right)] : []
};
前序栈
var preorderTraversal = function(root) {
		var arr		= [];
		var nums	= [];
	root && arr.push(root);
	while (arr.length > 0) {
		let cur	= arr.pop();
		nums.push(cur.val);

		cur.left && arr.push(cur.left);
		cur.right && arr.push(cur.right);
	}
	return nums;
};
//////////////////////////////////////////
590. N叉树的后序遍历
var postorder = function(root) {
    if(!root) return[];
    var res =[];
    helper(root);
    function helper(root){
        if(!root) return;
        for(var i=0;i<root.children.length;i++){
            helper(root.children[i])
        }
        res.push(root.val);   
    }
    return res;
}
//////////////////////////////////////////
591. N叉树的后序遍历
var preorder = function(root) {
   	if (!root) return [];
	var nums	= [];
	helper(root);
	function helper(root) {
		if (!root) return;
		nums.push(root.val);
		for (var i = 0; i < root.children.length;i++){
			helper(root.children[i]);
		}
	}
	return nums;
 
}
//////////////////////////////////////////
429. N叉树的层序遍历

var levelOrder = function(root) {
	var nums	= [];
	search(root, nums, 0);
	return nums;
};
function search(root, nums, k) {
	if (root == null) return ;
	if (!nums[k]) nums[k]	= [];
	nums[k].push(root.val);
	for (var i = 0; i < root.children.length; i++) {
		search(root.children[i], nums, k + 1);
	}
}

//////////////////////////////////////////
剑指 Offer 49. 丑数

var nthUglyNumber = function(n) {
	var arr	= [1];
	let n2	=0,n3	=0,n5=0;
	for (var i = 1; i < n;i++) {
		var result2	=arr[n2] * 2;
		var result3	=arr[n3] * 3;
		var result5	=arr[n5] * 5;
		arr[i]	= Math.min(result2, result3, result5);
		if (arr[i] === result2) {
			n2++;
		}
		if (arr[i] === result3) {
			n3++;
		}
		if (arr[i] === result5) {
			n5++;
		}
	}
	return arr[n - 1];
}
