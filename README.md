<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BilalJanGG</title>
<style>
body {font-family: Arial; margin:0; background:#0f172a; color:white;}
.header {padding:15px; text-align:center; font-size:24px; font-weight:bold;}
.container {padding:20px;}
input, textarea {width:100%; padding:10px; margin:5px 0; border-radius:8px; border:none;}
button {padding:10px; border:none; border-radius:8px; background:#22c55e; color:white; cursor:pointer;}
.card {background:#1e293b; padding:15px; margin-top:10px; border-radius:10px;}
.hidden {display:none;}
.bottom-btn {position:fixed; bottom:20px; right:20px; background:#3b82f6;}
</style>
</head>
<body><div class="header">BilalJanGG</div><!-- LOGIN / SIGNUP --><div id="auth" class="container">
<h2>Login</h2>
<input id="loginEmail" placeholder="Email">
<input id="loginPass" type="password" placeholder="Password">
<button onclick="login()">Login</button><h2>Sign Up</h2>
<button onclick="alert('Google Sign Up (Demo)')">Sign up with Google</button>
<input id="signupEmail" placeholder="Email">
<input id="signupPass" type="password" placeholder="Password">
<button onclick="signup()">Sign Up</button>
</div><!-- MAIN APP --><div id="app" class="container hidden">
<input id="search" placeholder="Search scripts..." onkeyup="searchScripts()">
<div id="scripts"></div>
</div><!-- CREATE --><div id="create" class="container hidden">
<h2>Create Script</h2>
<input type="file" id="image">
<input id="game" placeholder="Game Name">
<textarea id="desc" placeholder="Description"></textarea>
<textarea id="script" placeholder="Script"></textarea>
<button onclick="createScript()">Done</button>
</div><button class="bottom-btn hidden" id="createBtn" onclick="openCreate()">Create</button>

<script>
let user = null;
let scripts = [];

function signup(){
  let email = document.getElementById('signupEmail').value;
  let pass = document.getElementById('signupPass').value;
  localStorage.setItem(email, pass);
  alert('Signed Up! Now login');
}

function login(){
  let email = document.getElementById('loginEmail').value;
  let pass = document.getElementById('loginPass').value;
  if(localStorage.getItem(email) === pass){
    user = email;
    document.getElementById('auth').classList.add('hidden');
    document.getElementById('app').classList.remove('hidden');
    document.getElementById('createBtn').classList.remove('hidden');
  } else {
    alert('Wrong login');
  }
}

function openCreate(){
  document.getElementById('create').classList.toggle('hidden');
}

function createScript(){
  let game = document.getElementById('game').value;
  let desc = document.getElementById('desc').value;
  let script = document.getElementById('script').value;

  let obj = {game, desc, script};
  scripts.push(obj);
  displayScripts();
  alert('Created!');
}

function displayScripts(){
  let container = document.getElementById('scripts');
  container.innerHTML = '';
  scripts.forEach(s => {
    container.innerHTML += `
    <div class="card">
      <h3>${s.game}</h3>
      <p>${s.desc}</p>
      <pre>${s.script}</pre></div>`;

}); }

function searchScripts(){ let val = document.getElementById('search').value.toLowerCase(); let container = document.getElementById('scripts'); container.innerHTML = ''; scripts.filter(s => s.game.toLowerCase().includes(val)).forEach(s => { container.innerHTML +=  <div class="card"> <h3>${s.game}</h3> <p>${s.desc}</p> <pre>${s.script}</pre> </div>; }); } </script>

</body>
</html>
