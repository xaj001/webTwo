# webTwo
web2雪梨综合作业
```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>美音词馆</title>
<style type="text/css">
	#box{
		width:718px;
		height:500px;
		border:1px solid black;
		position:relative;
		overflow:hidden;
	}
	.slide{
		width:718px;
		height:500px;
		position:absolute;
	}
</style>
<script type="text/javascript">
	var weeks = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
	var date1 = new Date();
	var d1 = date1.getDay();
	var month = date1.getMonth();
	var year = date1.getFullYear();
	var day = date1.getDate();
	console.log("今天是"+weeks[d1]+year+"年"+(month+1)+"月"+day+"日");
	onload=function(){
		var arr = document.getElementsByClassName("slide");
		for(var i=0;i<arr.length;i++){
			arr[i].style.left = i*718+"px";
		}
	}
	function LeftMove(){
		var arr = document.getElementsByClassName("slide");
		for(var i=0;i<arr.length;i++){
			var left = parseFloat(arr[i].style.left);
			left-=2;
			var width = 718;
			if(left<=-width){
				left=(arr.length-1)*width;
				clearInterval(moveId);
			}
			arr[i].style.left = left+"px";
		}
	}
	function divInterval(){
		moveId=setInterval(LeftMove,10);
	}	
	timeId=setInterval(divInterval,5000);
	function stop(){
		clearInterval(timeId);
	}
	function start(){
		clearInterval(timeId);
		timeId=setInterval(divInterval,5000);
	}	
	onblur = function(){
		stop();
	}
	onfocus = function(){
		start();
	}
	function promptDialog(){
			var t = prompt("请给我们的网页打分吧，1（非常满意）2（满意）3（较满意）4（一般）5（不满意）",[1]);
			console.log(t);
		}
</script>
</head>
<body>
	<div id="box" onmouseover="stop()" onmouseout="start()">
		<div class="slide"><img src="01.jpg" alt="" /></div>
		<div class="slide"><img src="02.jpg" alt="" /></div>
		<div class="slide"><img src="03.jpg" alt="" /></div>
	</div>
	<input type="button" value="发表建议" onclick="promptDialog();" />
</body>
</html>
```
