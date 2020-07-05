学习笔记

//860. 柠檬水找零
//贪心算法
var lemonadeChange = function(bills) {
	let five	= 0;
	let ten		= 0;
	let total	= 0;
	for (let i = 0; i < bills.length; i++) {
		let money	= bills[i];
		switch(money) {
			case 5:
				five++;
				break;
			case 10:
				if (five === 0) {
					return false;
				}
				five--;
				ten++;
				break;
			case 20:
				if (five >= 1 && ten >= 1 ) {
					five--;
					ten--;
				} else if (five >= 3 ) {
					five	-= 3;
				} else {
					return false;
				}
				break;
		}
	}
	return true;
}

//122. 买卖股票的最佳时机 II
var maxProfit = function(prices) {
	let total	= 0;
	for (let i = 0; i <prices.length; i++) {
		if (prices[i + 1] > prices[i])total	+=  prices[i + 1] - prices[i];
	}
	return total;
}
