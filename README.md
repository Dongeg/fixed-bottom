# fixed-bottom
解决fixed定位在底部移动端软键盘弹出部分手机错位问题

项目中遇到一个问题，老板的  小米mix  和 iphone6s ，在弹出软键盘时，底部fixed定位的导航条会错位，和美工商量后，决定

软键盘弹出时底部导航条隐藏，收起显示
```js
if($(".footer-menu") && $("input[type=text]")){     //如果页面既有底部fixed，又有可输入表单时执行	
var h= document.documentElement.clientHeight|| document.body.clientHeight;//获取一次初始页面高度
setInterval(function(){   //每秒判断10次   页面高度是否发生改变，对应显示和隐藏导航条    
var newH= document.documentElement.clientHeight|| document.body.clientHeight;
		if(newH != h){
			$(".footer-menu").css('display','none')
		}
		else{
			$(".footer-menu").css('display','block')
		}
	},100)
}
```
这样做牺牲了一些性能，但在符合需求的项目中兼容移动端效果极好，每秒10次对现代移动设备负担也不大
