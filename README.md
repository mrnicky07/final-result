<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BTE Result - Nikhil Kumar</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:sans-serif;
}

body{
min-height:100vh;
display:flex;
justify-content:center;
align-items:center;
background:linear-gradient(135deg,#0f172a,#1e293b);
color:white;
}

.container{
width:90%;
max-width:380px;
padding:25px;
border-radius:20px;
background:rgba(255,255,255,0.05);
backdrop-filter:blur(10px);
text-align:center;
}

h1{
margin-bottom:10px;
}

input{
width:100%;
padding:14px;
margin:8px 0;
border:none;
border-radius:10px;
outline:none;
background:rgba(255,255,255,0.1);
color:white;
}

button{
width:100%;
padding:14px;
margin-top:10px;
border:none;
border-radius:10px;
font-weight:bold;
cursor:pointer;
}

.main{background:#22c55e;}
.copy{background:#3b82f6;}
.toggle{background:#f59e0b;}

.footer{
margin-top:15px;
font-size:13px;
opacity:0.7;
}

.light{
background:#f1f5f9;
color:black;
}

.light input{
color:black;
}
</style>
</head>

<body>

<div class="container">
<h1>BTE Result</h1>
<p>Enter your details</p>

<input type="text" id="enroll" placeholder="Enrollment Number">
<input type="text" id="dob" placeholder="DD/MM/YYYY">

<button class="main" onclick="generate()">Generate & Open</button>
<button class="copy" onclick="copyLink()">Copy Link</button>
<button class="toggle" onclick="toggleMode()">Dark/Light</button>

<div class="footer">
Developed by Nikhil Kumar
</div>
</div>

<script>
let link="";

// auto fill
window.onload=()=>{
if(localStorage.enroll){
document.getElementById("enroll").value=localStorage.enroll;
document.getElementById("dob").value=localStorage.dob;
}
}

// DOB format
document.getElementById("dob").addEventListener("input",function(){
let v=this.value.replace(/\D/g,'');
if(v.length>=2 && v.length<=4)
this.value=v.slice(0,2)+"/"+v.slice(2);
else if(v.length>4)
this.value=v.slice(0,2)+"/"+v.slice(2,4)+"/"+v.slice(4,8);
});

// generate link
function generate(){
let e=document.getElementById("enroll").value.trim();
let d=document.getElementById("dob").value.trim();

if(!e || !d){
alert("Fill all details");
return;
}

localStorage.enroll=e;
localStorage.dob=d;

let encE=btoa(e);
let encD=btoa(d).replace(/=/g,"%3D");

link="https://result.bteexam.com/Odd_Semester/main/result.aspx?id="+encE+"&id2="+encD;

window.open(link,"_blank");
}

// copy
function copyLink(){
if(!link){
alert("Generate first");
return;
}
navigator.clipboard.writeText(link);
alert("Copied!");
}

// dark mode
function toggleMode(){
document.body.classList.toggle("light");
}
</script>

</body>
</html>
