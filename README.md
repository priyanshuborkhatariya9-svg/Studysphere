<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>MiniGPT | AI Assistant</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family:Arial,Helvetica,sans-serif;
  background:#0f1117;
  color:#fff;
  height:100vh;
  overflow:hidden;
  transition:.3s;
}

body.light{
  background:#f5f6fb;
  color:#171827;
}

.app{
  display:flex;
  height:100vh;
}

/* SIDEBAR */

.sidebar{
  width:250px;
  background:#171923;
  border-right:1px solid #292c38;
  padding:15px;
  display:flex;
  flex-direction:column;
}

body.light .sidebar{
  background:#fff;
  border-color:#e5e6ed;
}

.logo{
  font-size:22px;
  font-weight:bold;
  padding:15px 10px;
  margin-bottom:15px;
}

.logo span{
  color:#8e7cff;
}

.new-chat,
.theme-btn{
  width:100%;
  padding:12px;
  border:none;
  border-radius:10px;
  color:white;
  font-weight:bold;
  cursor:pointer;
  margin-bottom:10px;
}

.new-chat{
  background:#6c5ce7;
}

.new-chat:hover{
  background:#5848d6;
}

.theme-btn{
  background:#292c38;
}

body.light .theme-btn{
  background:#eeeefa;
  color:#333;
}

.sidebar-bottom{
  margin-top:auto;
}

/* MAIN */

.main{
  flex:1;
  display:flex;
  flex-direction:column;
  min-width:0;
}

.header{
  height:60px;
  border-bottom:1px solid #292c38;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:0 20px;
  font-weight:bold;
}

body.light .header{
  border-color:#e5e6ed;
}

.header-title{
  display:flex;
  align-items:center;
  gap:10px;
}

.status{
  width:9px;
  height:9px;
  background:#20b486;
  border-radius:50%;
}

/* CHAT */

.chat{
  flex:1;
  overflow-y:auto;
  padding:30px 20px;
}

.message{
  max-width:800px;
  margin:0 auto 25px;
  display:flex;
  gap:15px;
  line-height:1.6;
}

.avatar{
  width:38px;
  height:38px;
  min-width:38px;
  border-radius:50%;
  display:grid;
  place-items:center;
  font-size:11px;
  font-weight:bold;
}

.user .avatar{
  background:#6c5ce7;
}

.ai .avatar{
  background:#20b486;
}

.text{
  padding-top:5px;
  white-space:pre-wrap;
  word-wrap:break-word;
}

/* WELCOME */

.welcome{
  max-width:800px;
  margin:80px auto;
  text-align:center;
}

.welcome-icon{
  font-size:60px;
  margin-bottom:15px;
}

.welcome h1{
  font-size:36px;
  margin-bottom:10px;
}

.welcome p{
  color:#9a9dae;
  font-size:16px;
}

/* INPUT */

.input-area{
  padding:15px 20px 20px;
  border-top:1px solid #292c38;
}

body.light .input-area{
  border-color:#e5e6ed;
}

.input-box{
  max-width:850px;
  margin:auto;
  display:flex;
  gap:8px;
  background:#191c27;
  border:1px solid #343746;
  border-radius:14px;
  padding:8px;
}

body.light .input-box{
  background:#fff;
  border-color:#dcdde7;
}

.input-box input{
  flex:1;
  background:transparent;
  border:none;
  outline:none;
  color:white;
  padding:11px;
  font-size:16px;
  min-width:0;
}

body.light .input-box input{
  color:#171827;
}

.input-box input::placeholder{
  color:#888b9a;
}

.btn{
  border:none;
  border-radius:10px;
  padding:10px 14px;
  cursor:pointer;
  font-weight:bold;
  color:white;
  white-space:nowrap;
}

.search{
  background:#343746;
}

.search:hover{
  background:#454958;
}

.send{
  background:#6c5ce7;
}

.send:hover{
  background:#5848d6;
}

/* TYPING */

.typing{
  display:flex;
  gap:5px;
  padding-top:8px;
}

.dot{
  width:7px;
  height:7px;
  border-radius:50%;
  background:#aaa;
  animation:bounce 1s infinite;
}

.dot:nth-child(2){
  animation-delay:.15s;
}

.dot:nth-child(3){
  animation-delay:.3s;
}

@keyframes bounce{
  0%,100%{
    transform:translateY(0);
  }
  50%{
    transform:translateY(-5px);
  }
}

/* MOBILE */

@media(max-width:700px){

  .sidebar{
    display:none;
  }

  .chat{
    padding:20px 12px;
  }

  .message{
    margin-bottom:20px;
  }

  .input-area{
    padding:10px;
  }

  .input-box{
    padding:6px;
  }

  .btn{
    padding:10px;
  }

  .welcome{
    margin:70px 15px;
  }

  .welcome h1{
    font-size:28px;
  }

  .search{
    display:none;
  }

}

</style>
</head>

<body>

<div class="app">

  <!-- SIDEBAR -->

  <aside class="sidebar">

    <div class="logo">
      🤖 <span>MiniGPT</span>
    </div>

    <button class="new-chat" onclick="newChat()">
      ＋ New Chat
    </button>

    <div class="sidebar-bottom">

      <button class="theme-btn" onclick="toggleTheme()">
        🌓 Toggle Theme
      </button>

    </div>

  </aside>


  <!-- MAIN -->

  <main class="main">

    <header class="header">

      <div class="header-title">
        <span class="status"></span>
        MiniGPT
      </div>

      <div>
        🤖 AI Assistant
      </div>

    </header>


    <!-- CHAT -->

    <section class="chat" id="chat">

      <div class="welcome" id="welcomeScreen">

        <div class="welcome-icon">
          🤖
        </div>

        <h1>Welcome to MiniGPT</h1>

        <p>
          Your simple AI assistant. Ask me something!
        </p>

      </div>

    </section>


    <!-- INPUT -->

    <div class="input-area">

      <div class="input-box">

        <input
          id="messageInput"
          type="text"
          placeholder="Message MiniGPT..."
          autocomplete="off"
        >

        <button
          class="btn search"
          onclick="searchWeb()"
          title="Search the web"
        >
          🔎 Search
        </button>

        <button
          class="btn send"
          onclick="sendMessage()"
        >
          ➤ Send
        </button>

      </div>

    </div>

  </main>

</div>


<script>

/* =========================
   BASIC AI
========================= */

function getAIResponse(message){

  const text = message.toLowerCase();

  if(
    text.includes("hello") ||
    text.includes("hi") ||
    text.includes("hey")
  ){
    return "Hello! 👋 I'm MiniGPT. How can I help you today?";
  }

  if(text.includes("who are you")){
    return "I'm MiniGPT, a simple AI assistant website created with HTML, CSS and JavaScript. 🤖";
  }

  if(text.includes("html")){
    return "HTML stands for HyperText Markup Language. It creates the structure of webpages. 🌐";
  }

  if(text.includes("css")){
    return "CSS is used to style webpages — colors, layouts, spacing, animations and more. 🎨";
  }

  if(text.includes("javascript")){
    return "JavaScript adds logic and interactivity to websites, such as buttons, forms and dynamic content. ⚡";
  }

  if(text.includes("study")){
    return "Try studying in focused sessions, taking short breaks, and testing yourself with active recall. 📚";
  }

  if(text.includes("math")){
    return "I can help with math questions. Send me the problem you'd like to work through. 🧮";
  }

  if(text.includes("website")){
    return "You can build a website with HTML for structure, CSS for design, and JavaScript for functionality. 🌐";
  }

  if(text.includes("thank")){
    return "You're welcome! 😄";
  }

  return "I'm currently running in basic mode. 🤖 You can use 🔎 Search to look up this question on the web. Later, we can connect MiniGPT to a real AI API so it can generate much smarter answers.";
}


/* =========================
   SEND MESSAGE
========================= */

function sendMessage(){

  const input =
    document.getElementById("messageInput");

  const message =
    input.value.trim();

  if(!message) return;

  removeWelcome();

  addMessage(message,"user");

  input.value="";

  showTyping();

  setTimeout(function(){

    removeTyping();

    const reply =
      getAIResponse(message);

    addMessage(reply,"ai");

    saveChat();

  },700);

}


/* =========================
   ADD MESSAGE
========================= */

function addMessage(text,type){

  const chat =
    document.getElementById("chat");

  const message =
    document.createElement("div");

  message.className =
    "message " + type;

  message.innerHTML=`

    <div class="avatar">
      ${type==="user" ? "YOU" : "AI"}
    </div>

    <div class="text">
      ${escapeHTML(text)}
    </div>

  `;

  chat.appendChild(message);

  chat.scrollTop =
    chat.scrollHeight;
}


/* =========================
   SECURITY
========================= */

function escapeHTML(text){

  return text
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}


/* =========================
   TYPING
========================= */

function showTyping(){

  const chat =
    document.getElementById("chat");

  const typing =
    document.createElement("div");

  typing.className=
    "message ai";

  typing.id="typing";

  typing.innerHTML=`

    <div class="avatar">
      AI
    </div>

    <div class="typing">

      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>

    </div>

  `;

  chat.appendChild(typing);

  chat.scrollTop =
    chat.scrollHeight;
}


function removeTyping(){

  const typing =
    document.getElementById("typing");

  if(typing){
    typing.remove();
  }

}


/* =========================
   REMOVE WELCOME
========================= */

function removeWelcome(){

  const welcome =
    document.getElementById("welcomeScreen");

  if(welcome){
    welcome.remove();
  }

}


/* =========================
   WEB SEARCH
========================= */

function searchWeb(){

  const input =
    document.getElementById("messageInput");

  const query =
    input.value.trim();

  if(!query){

    alert("Type something to search first.");

    input.focus();

    return;
  }

  const url =
    "https://www.google.com/search?q="
    + encodeURIComponent(query);

  window.open(url,"_blank");

}


/* =========================
   NEW CHAT
========================= */

function newChat(){

  const chat =
    document.getElementById("chat");

  chat.innerHTML=`

    <div class="welcome" id="welcomeScreen">

      <div class="welcome-icon">
        🤖
      </div>

      <h1>New Chat</h1>

      <p>
        What would you like to talk about?
      </p>

    </div>

  `;

  localStorage.removeItem("miniGPTChat");

}


/* =========================
   DARK / LIGHT MODE
========================= */

function toggleTheme(){

  document.body.classList.toggle("light");

  localStorage.setItem(
    "miniGPTTheme",
    document.body.classList.contains("light")
      ? "light"
      : "dark"
  );

}


/* =========================
   SAVE CHAT
========================= */

function saveChat(){

  const chat =
    document.getElementById("chat");

  localStorage.setItem(
    "miniGPTChat",
    chat.innerHTML
  );

}


/* =========================
   LOAD CHAT
========================= */

function loadChat(){

  const saved =
    localStorage.getItem("miniGPTChat");

  if(saved){

    document.getElementById("chat").innerHTML =
      saved;

  }

}


/* =========================
   LOAD THEME
========================= */

function loadTheme(){

  const theme =
    localStorage.getItem("miniGPTTheme");

  if(theme==="light"){

    document.body.classList.add("light");

  }

}


/* =========================
   ENTER KEY
========================= */

document
  .getElementById("messageInput")
  .addEventListener("keydown",function(event){

    if(event.key==="Enter"){

      event.preventDefault();

      sendMessage();

    }

  });


/* =========================
   START
========================= */

loadTheme();
loadChat();

</script>

</body>
</html>
