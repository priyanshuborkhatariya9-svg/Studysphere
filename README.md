<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>MiniGPT</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Arial, sans-serif;
      background: #0f1117;
      color: white;
      height: 100vh;
      overflow: hidden;
    }

    .app {
      display: flex;
      height: 100vh;
    }

    /* SIDEBAR */

    .sidebar {
      width: 250px;
      background: #171923;
      border-right: 1px solid #292c38;
      padding: 15px;
      display: flex;
      flex-direction: column;
    }

    .logo {
      font-size: 22px;
      font-weight: bold;
      padding: 15px 10px;
      margin-bottom: 15px;
    }

    .new-chat {
      width: 100%;
      padding: 12px;
      background: #6c5ce7;
      border: none;
      border-radius: 10px;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }

    .new-chat:hover {
      background: #5848d6;
    }

    /* MAIN */

    .main {
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .header {
      height: 60px;
      border-bottom: 1px solid #292c38;
      display: flex;
      align-items: center;
      padding: 0 20px;
      font-weight: bold;
    }

    /* CHAT */

    .chat {
      flex: 1;
      overflow-y: auto;
      padding: 30px 20px;
    }

    .message {
      max-width: 800px;
      margin: 0 auto 25px;
      display: flex;
      gap: 15px;
      line-height: 1.6;
    }

    .avatar {
      width: 36px;
      height: 36px;
      min-width: 36px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      font-weight: bold;
    }

    .user .avatar {
      background: #6c5ce7;
    }

    .ai .avatar {
      background: #20b486;
    }

    .text {
      padding-top: 5px;
      white-space: pre-wrap;
    }

    /* INPUT */

    .input-area {
      padding: 15px 20px 20px;
      border-top: 1px solid #292c38;
    }

    .input-box {
      max-width: 800px;
      margin: auto;
      display: flex;
      gap: 10px;
      background: #191c27;
      border: 1px solid #343746;
      border-radius: 14px;
      padding: 8px;
    }

    .input-box input {
      flex: 1;
      background: transparent;
      border: none;
      outline: none;
      color: white;
      padding: 10px;
      font-size: 16px;
    }

    .send {
      background: #6c5ce7;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 10px 16px;
      cursor: pointer;
      font-weight: bold;
    }

    .send:hover {
      background: #5848d6;
    }

    /* MOBILE */

    @media (max-width: 700px) {

      .sidebar {
        display: none;
      }

      .chat {
        padding: 20px 12px;
      }

      .message {
        margin-bottom: 20px;
      }

      .input-area {
        padding: 10px;
      }
    }
  </style>
</head>

<body>

<div class="app">

  <aside class="sidebar">

    <div class="logo">
      🤖 MiniGPT
    </div>

    <button class="new-chat" onclick="newChat()">
      ＋ New Chat
    </button>

  </aside>


  <main class="main">

    <header class="header">
      MiniGPT
    </header>


    <section class="chat" id="chat">

      <div class="message ai">

        <div class="avatar">
          AI
        </div>

        <div class="text">
          Hello! 👋 I'm MiniGPT.

          Ask me anything!
        </div>

      </div>

    </section>


    <div class="input-area">

      <div class="input-box">

        <input
          id="messageInput"
          type="text"
          placeholder="Message MiniGPT..."
          onkeydown="handleKey(event)"
        >

        <button class="send" onclick="sendMessage()">
          Send
        </button>

      </div>

    </div>

  </main>

</div>


<script>

function addMessage(text, type) {

  const chat = document.getElementById("chat");

  const message = document.createElement("div");

  message.className = "message " + type;

  message.innerHTML = `
    <div class="avatar">
      ${type === "user" ? "You" : "AI"}
    </div>

    <div class="text">
      ${escapeHTML(text)}
    </div>
  `;

  chat.appendChild(message);

  chat.scrollTop = chat.scrollHeight;
}


function escapeHTML(text) {

  return text
    .replace(/&/g, "&amp;")
    .replace(/</g, "&lt;")
    .replace(/>/g, "&gt;")
    .replace(/"/g, "&quot;")
    .replace(/'/g, "&#039;");

}


function sendMessage() {

  const input = document.getElementById("messageInput");

  const message = input.value.trim();

  if (!message) return;

  addMessage(message, "user");

  input.value = "";

  setTimeout(() => {

    const reply = getAIResponse(message);

    addMessage(reply, "ai");

  }, 500);

}


function getAIResponse(message) {

  const text = message.toLowerCase();

  if (text.includes("hello") || text.includes("hi")) {

    return "Hello! 👋 Nice to meet you!";

  }

  if (text.includes("who are you")) {

    return "I'm MiniGPT, your simple AI assistant.";

  }

  if (text.includes("study")) {

    return "A good study session can be split into focused blocks with short breaks. 📚";

  }

  if (text.includes("html")) {

    return "HTML is used to create the structure of a webpage. 🌐";

  }

  return "I'm still a basic MiniGPT right now 🤖. Soon we'll connect me to a real AI model so I can understand much more!";
}


function handleKey(event) {

  if (event.key === "Enter") {

    sendMessage();

  }

}


function newChat() {

  document.getElementById("chat").innerHTML = `

    <div class="message ai">

      <div class="avatar">
        AI
      </div>

      <div class="text">
        New chat started! 👋
        What would you like to talk about?
      </div>

    </div>

  `;

}

</script>

</body>
</html>
