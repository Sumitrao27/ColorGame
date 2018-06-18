<!DOCTYPE html>
<html>
<head>
<style type="text/css">
body {
	background-color: #232323;
	margin: 0;
	font-family: "Montserrat", "Avenir";
}
#rgb1{
font-size:50px;

}
#mid{
background-color:white;
text-align:center;
color:black;
}
button{
background-color:white;
color:rgb(64,128,128);
margin-left:50px;
padding:5px;
}
button:hover{
background-color:rgb(64,128,128);
color:white;
}
#space{
margin-left:200px;
}
H1{
text-align:center;
background-color:rgb(64,128,128);
margin:0;
color:white;
padding:15px;
}
#boxes{
margin:20px auto;
max-width:80%;
}
.different{
width:20%;
background-color:purple;
border-radius:5%;
padding-bottom:20%;
float:left;
margin:0.5%;
margin-left:10%;
}

</style>
</head>
<body>
<H1> THE GREAT <br>
<span id="rgb1"> RGB</span> <br>
COLOR GAME
</H1>
<Div id="mid">
<button id="news" >NEW COLOR</button>
<span id="space"></span>
<button class="level">EASY</button>
<button class="level">MEDIUM</button>
<button class="level">HARD</button>
</Div>
<Div id="boxes">
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
<Div class="different"></Div>
</Div>
<script type="text/javascript">

var nSquares=9;
var colors=[];
var selectedColor;
var h1=document.querySelector("h1");
var colorD = document.getElementById("rgb1");
var result=document.querySelector("#space");
var resetWay=document.querySelector("#news");
var levelSet=document.querySelectorAll(".level");
var different=document.querySelectorAll(".different");
letStart();

function letStart(){
setLevel();
newS();
setDifferentS();
}
function setLevel(){
for(var i=0;i<levelSet.length;i++){
levelSet[i].addEventListener("click",function() {

 switch(this.textContent){
 case "EASY":
  nSquares=3;
  break;
  
  case "MEDIUM":
  nSquares=6;
  break;
  
  default:
  nSquares=9;
 
 }  
  
  newS();
});
}
}
function setDifferentS(){
for(var i=0;i<different.length;i++){
different[i].addEventListener("click",function(){
  var clickedColor=this.style.backgroundColor;
  console.log(clickedColor==selectedColor);
  console.log(clickedColor);
  console.log(selectedColor);
  if(clickedColor===selectedColor){
   result.textContent="CORRECT";
   resetWay.textContent="PLAY_AGAIN ?";
   showColor(clickedColor);
   h1.style.background=clickedColor;
  }
  else{
    result.textContent="SORRY TRY AGAIN";
    this.style.background="rgb(35,35,35)";
	}
});
}
}

function newS(){
colors=newColors(nSquares);
selectedColor=selectColor();
colorD.textContent=selectedColor;
resetWay.textContent="NEW COLOR";
for(var i=0;i<different.length;i++){
if(colors[i]){
different[i].style.display="block"
different[i].style.background=colors[i];
}
else {
		different[i].style.display = "none";
	}
}
h1.style.background="rgb(64,128,128)";
}

resetWay.addEventListener("click",function(){
newS();
})

function showColor(color){
for(var i=0;i< different.length;i++){
different[i].style.background=color;
}
}
function selectColor(){
var selectit=Math.floor(Math.random()* colors.length);
return colors[selectit];
}

function newColors(n){
var arr=[]
for(var i=0;i<n;i++){
arr.push(randomColor())
}
return arr;
}
function randomColor(){
var r=Math.floor(Math.random()*256);
var g=Math.floor(Math.random()*256);
var b=Math.floor(Math.random()*256);
return "rgb(" + r + ", " + g + ", " + b + ")"
}

</script>
</body>
</html>
