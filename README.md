<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Şaka Zamanı</title>
  <style>
    body { margin:0; padding:0; background:#000; color:#fff; font-family:Arial, sans-serif; overflow:hidden; height:100vh; }
    #container { position:fixed; inset:0; display:flex; flex-direction:column; justify-content:center; align-items:center; text-align:center; }
    h1 { font-size:8vw; margin:0; }
    button { font-size:5vw; padding:2vw 6vw; margin:3vw; border:none; border-radius:15px; cursor:pointer; color:#fff; }
    #evet { background:#2ecc71; }
    #hayir { background:#e74c3c; }
    #msg { font-size:6vw; color:#f1c40f; display:none; margin-top:5vw; }
    #timer { font-size:12vw; display:none; margin-top:5vw; }
  </style>
</head>
<body onload="goFullscreen()">

<div id="container">
  <h1>Beni seviyo musun?</h1>
  <button id="evet" onclick="yes()">Evet</button>
  <button id="hayir" onclick="no()">Hayır</button>
  <div id="msg"></div>
  <div id="timer"></div>
</div>

<script>
function goFullscreen() {
  document.documentElement.requestFullscreen?.() || document.documentElement.webkitRequestFullscreen?.();
}

function no() {
  document.getElementById("msg").textContent = "Yalan söylüyorsun! Tekrar dene 😡";
  document.getElementById("msg").style.display = "block";
  setTimeout(() => document.getElementById("msg").style.display = "none", 3000);
}

function yes() {
  document.getElementById("msg").textContent = "Aferin kankam, şimdi çıkabilirsin 😏";
  document.getElementById("msg").style.display = "block";
  document.getElementById("evet").style.display = "none";
  document.getElementById("hayir").style.display = "none";
  document.getElementById("timer").style.display = "block";
  
  let time = 20;
  document.getElementById("timer").textContent = time;
  const countdown = setInterval(() => {
    time--;
    document.getElementById("timer").textContent = time;
    if (time <= 0) {
      clearInterval(countdown);
      window.location = "https://www.youtube.com/watch?v=dQw4w9WgXcQ";
    }
  }, 1000);
}
</script>
</body>
</html>
