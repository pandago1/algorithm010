
课后罪业
70. 爬楼梯
var climbStairs = function(n) {
  if(n===1) return 1
  let f = 1, s = 2
  for(let i = 3; i <= n; i++) {
    let t = f + s
    f = s
    s = t
  }
  return s
};

//////////////////////////////////
22. 括号生成
var generateParenthesis = function(n) {
    var arr = [];
    _generate(0, 0 , n, "");

    function _generate(left, right, n, s) {
        if (left >= n && right >= n) {
        arr.push(s);
        return;
    }

    if (left < n) {
        _generate(left + 1, right, n, s + '(');
    }
    if (right < left) {
        _generate(left, right + 1, n, s + ')');
    }
}
    return arr;
};
