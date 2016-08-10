<html>
<head>
<script>
function move(event){
findAdjacent();
var x = event.clientX;
var y = event.clientY;
var a = window.innerHeight;
var b = window.innerWidth;
if (x > b - 15) {x = b - 15;};
if (y > a - 15) {y = a - 15;};
if (x < 15) {x = 15;};
if (y < 15) {y = 15;};
var l = (((b / 2) - 1) - x) * -1; //opposite
var m = ((a / 2) - 1) - y; //adjacent
var r = (Math.atan(l/m)) * (180/Math.PI);
var da = (Math.atan(b/a)) * (180/Math.PI);
var innerAdjacent = findAdjacent(da,r,a,b);
var innerAngle = findAngle(da,r,l,m);
var opposite = innerAdjacent * (Math.tan(innerAngle));
var adjacent = Math.abs(innerAdjacent);
var rsh = ((Math.sqrt( Math.pow(opposite,2) + Math.pow(adjacent,2)))*2)-30;
document.getElementById("display_1").innerHTML= x;
document.getElementById("display_2").innerHTML= y;
document.getElementById("display_3").innerHTML= l;
document.getElementById("display_4").innerHTML= m;
document.getElementById("display_5").innerHTML= r;
document.getElementById("display_6").innerHTML= a;
document.getElementById("display_7").innerHTML= b;
document.getElementById("display_8").innerHTML= da;
document.getElementById("display_9").innerHTML= rsh;
document.getElementById("display_10").innerHTML= opposite;
document.getElementById("display_11").innerHTML= adjacent;
document.getElementById("cuteCircle").style.top = y - 15 + "px";
document.getElementById("cuteCircle").style.left = x - 15 + "px";
document.getElementById("verticalStroke").style.height = a + "px";
document.getElementById("verticalStroke").style.left = (b / 2) - 1 + "px";
document.getElementById("horizontalStroke").style.width = b + "px";
document.getElementById("horizontalStroke").style.top = (a / 2) - 1 + "px";
document.getElementById("rotateStroke").style.WebkitTransform = "rotate(" + r + 90 + "deg)";
document.getElementById("rotateStroke").style.top = (rsh / 2) * -1 + "px";
document.getElementById("rotateStroke").style.height = rsh + "px";
document.getElementById("rotateStrokeHolder").style.top = (a/2) + "px";
document.getElementById("rotateStrokeHolder").style.left = (b/2) + "px";
}
function findAdjacent(da, r, a, b){
if (r < da && -da < r) {
console.log(a/2);
return (a/2);

} else {
return (b/2);
}
}
function findAngle(da, r, l, m){
if (-da < r && r < da) {
return (Math.atan(l/m));
} else {
return (Math.PI/2)-(Math.atan(l/m));
}
}
</script>
<style>
body{
overflow:hidden;
font-size:.8em;
color:#999999;
font-family:sans-serif;
line-height:25px;
margin:0px;
padding:0px;
}
.cuteCircle{
	position:absolute;
	z-index:1;
	top:25px;
	left:100px;
	width:30px;
	height:30px;
	background-color:#6666ff;
	border-radius:15px;
}
.row{
margin-top:10px;
margin-left:20px;
}
.title{
display:inline;
}
.value{
display:inline;
}
.verticalStroke{
position:absolute;
width:25px;
left:0px;
top:0px;
width:2px;
background-color:#6666ff;
}
.horizontalStroke{
position:absolute;
left:0px;
top:0px;
height:2px;
background-color:#6666ff;
}
.rotateStroke{
width:2px;
position:absolute;
background-color:#6666ff;
}
.rotateStrokeHolder{
position:absolute;
}
</style>
</head>
<body onmousemove="move(event)" onload="move(event)" onresize="move(event)">
	<div class="row">
		<div class="title">Position X:</div>
		<div id="display_1" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Position Y:</div>
		<div id="display_2" class="value"></div>
	</div>
	<div class="row">
		<div class="title">X from center:</div>
		<div id="display_3" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Y from center:</div>
		<div id="display_4" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Rotation:</div>
		<div id="display_5" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Window Height:</div>
		<div id="display_6" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Window Width:</div>
		<div id="display_7" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Diagonal Angle:</div>
		<div id="display_8" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Special Line Height:</div>
		<div id="display_9" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Opposite:</div>
		<div id="display_10" class="value"></div>
	</div>
	<div class="row">
		<div class="title">Adjacent:</div>
		<div id="display_11" class="value"></div>
	</div>
	<div id="cuteCircle" class="cuteCircle"></div>
	<div id="verticalStroke" class="verticalStroke"></div>
	<div id="horizontalStroke" class="horizontalStroke"></div>
	<div id="rotateStrokeHolder" class="rotateStrokeHolder">
		<div id="rotateStroke" class="rotateStroke"></div>
	</div>
</body>
</html>
