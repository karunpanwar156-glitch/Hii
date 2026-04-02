# Hii






<!DOCTYPE html>
<html>
<head>
<title>For You ❤️</title>

<style>
body{
  font-family: Arial;
  text-align:center;
  background: linear-gradient(to bottom,#ff9a9e,#fad0c4);
  padding-top:60px;
  overflow:hidden;
}

h1,h2{color:#b30059;}

button{
  padding:14px 30px;
  font-size:20px;
  border:none;
  border-radius:30px;
  margin:10px;
  cursor:pointer;
  transition:0.3s;
}

.yes{background:#ff3366;color:white;}
.no{background:white;color:#ff3366;border:2px solid #ff3366;}

button:hover{transform:scale(1.1);}

/* LOVE SCREEN */
.loveScreen{
  position:fixed;
  top:0;left:0;
  width:100%;height:100%;
  background:linear-gradient(to bottom,#ff4e50,#ff6a88);
  display:none;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  color:white;
  z-index:999;
}

.loveScreen h1{
  font-size:50px;
  animation:zoom 1s infinite alternate;
}

@keyframes zoom{
  from{transform:scale(1);}
  to{transform:scale(1.2);}
}

/* ❤️ HEART RAIN */
.heart{
  position:fixed;
  top:-10px;
  animation:fall 4s linear;
}

@keyframes fall{
  0%{transform:translateY(0);opacity:1;}
  100%{transform:translateY(100vh);opacity:0;}
}

</style>
</head>

<body>

<div id="content"></div>

<div class="loveScreen" id="loveScreen">
  <h1>I Love You ❤️</h1>
  <p>Tum meri life ki sabse special person ho 💖</p>
</div>

<script>

let step = 0;
let noCount = 0;

function next(){
  const c = document.getElementById("content");

  if(step === 0){
    c.innerHTML = `
      <h1>Seju❤️</h1>
      <h2>Mujhe tumse kuch kehna hai...</h2>
      <button class="yes" onclick="next()">Next</button>
    `;
    step++;
  }

  else if(step === 1){
    c.innerHTML = `
      <h2>Jab bhi tumse baat hoti hai na... 😊</h2>
      <button class="yes" onclick="next()">Next</button>
    `;
    step++;
  }

  else if(step === 2){
    c.innerHTML = `
      <h2>Din thoda aur special lagne lagta hai 💖</h2>
      <button class="yes" onclick="next()">Next</button>
    `;
    step++;
  }

  else if(step === 3){
    c.innerHTML = `
      <h2>I really like you ❤️</h2>
      <button class="yes" onclick="showFinal()">Next</button>
    `;
  }
}

function showFinal(){
  document.getElementById("content").innerHTML = `
    <h1>Do you like me? 💖</h1>
    <button class="yes" onclick="yes()">Haa 💕</button>
    <button class="no" onclick="noClick()">Nahi 🙈</button>
  `;
}

// 💖 YES CLICK EFFECT
function yes(){
  document.getElementById("loveScreen").style.display="flex";
  startHeartRain();
}

// ❤️ HEART RAIN FUNCTION
function startHeartRain(){
  setInterval(()=>{
    const h = document.createElement("div");
    h.className="heart";
    h.innerHTML="❤️";
    h.style.left=Math.random()*100+"vw";
    h.style.fontSize=(Math.random()*20+10)+"px";

    document.body.appendChild(h);

    setTimeout(()=>h.remove(),4000);
  },200);
}

// ❌ NO FLOW
function noClick(){
  noCount++;

  const c = document.getElementById("content");

  if(noCount === 1){
    c.innerHTML = `
      <h2>Sach me? 😔</h2>
      <button class="no" onclick="noClick()">Nahi</button>
      <button class="yes" onclick="yes()">Haa 💕</button>
    `;
  }

  else if(noCount === 2){
    c.innerHTML = `
      <h2>Ek baar aur soch lo 💔</h2>
      <button class="no" onclick="noClick()">Nahi</button>
      <button class="yes" onclick="yes()">Haa 💕</button>
    `;
  }

  else if(noCount === 3){
    c.innerHTML = `
      <h2>Please maan ja yarr 🥺</h2>
      <button class="no" onclick="noClick()">Nahi</button>
      <button class="yes" onclick="yes()">Haa 💕</button>
    `;
  }

  else{
    c.innerHTML = `
      <h2>Okay... I understand 💔</h2>
      <button class="yes" onclick="yes()">Wait… Haa 💕</button>
    `;
  }
}

next();

</script>

</body>
</html>
