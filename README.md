## Hi there 👋

<!--
**Aucgpt/Aucgpt** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>AUCGpt - AUC Chatbot</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #121212;
      color: #fff;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      height: 100vh;
    }

    header {
      background-color: #1f1f1f;
      padding: 15px;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
      border-bottom: 2px solid #333;
    }

    #nav {
      background: #222;
      padding: 10px;
      text-align: center;
    }

    #nav button {
      background-color: #00b894;
      border: none;
      color: white;
      padding: 8px 15px;
      margin: 0 5px;
      border-radius: 5px;
      cursor: pointer;
    }

    #nav button:hover {
      background-color: #019875;
    }

    #chat {
      flex: 1;
      padding: 20px;
      overflow-y: auto;
    }

    .message {
      margin: 10px 0;
      padding: 10px;
      border-radius: 8px;
      max-width: 80%;
    }

    .user {
      background-color: #007bff;
      align-self: flex-end;
      text-align: right;
    }

    .bot {
      background-color: #444;
      align-self: flex-start;
    }

    #inputArea {
      display: flex;
      border-top: 2px solid #333;
    }

    #userInput {
      flex: 1;
      padding: 15px;
      font-size: 16px;
      border: none;
      outline: none;
    }

    #sendBtn {
      padding: 15px;
      background-color: #00b894;
      color: white;
      font-size: 16px;
      border: none;
      cursor: pointer;
    }

    #sendBtn:hover {
      background-color: #019875;
    }

    #chat, .message {
      display: flex;
      flex-direction: column;
    }

    #aucInfo {
      display: none;
      background-color: #1f1f1f;
      padding: 15px;
      margin: 10px;
      border-top: 2px solid #333;
    }
  </style>
</head>
<body>
  <header>AUCGpt</header>
  <div id="nav">
    <button onclick="showAUCInfo()">About AUC</button>
  </div>

  <div id="aucInfo">
    <h2>Agricultural University College (AUC)</h2>
    <p>ময়মনসিংহে অবস্থিত AUC হচ্ছে একটি ঐতিহ্যবাহী শিক্ষা প্রতিষ্ঠান। এটি বাংলাদেশ কৃষি বিশ্ববিদ্যালয় ক্যাম্পাসে অবস্থিত।</p>
    <ul>
      <li>স্থাপিত: ১৯৮৫</li>
      <li>অর্জন: জাতীয় পর্যায়ে বিজ্ঞান মেলা, বিতর্ক প্রতিযোগিতা ও বিভিন্ন ক্লাব অ্যাক্টিভিটি</li>
      <li>বিশেষত্ব: শিক্ষার মান, ছাত্র-ছাত্রীদের শৃঙ্খলা, এবং সংস্কৃতি চর্চা</li>
    </ul>
  </div>

  <div id="chat"></div>
  <div id="inputArea">
    <input type="text" id="userInput" placeholder="Type your message..."/>
    <button id="sendBtn">Send</button>
  </div>

  <script>
    const chat = document.getElementById('chat');
    const userInput = document.getElementById('userInput');
    const sendBtn = document.getElementById('sendBtn');
    const aucInfo = document.getElementById('aucInfo');

    function showAUCInfo() {
      aucInfo.style.display = aucInfo.style.display === 'none' ? 'block' : 'none';
    }

    function fakeAIResponse(input) {
      input = input.toLowerCase();
      if (input.includes("auc") && input.includes("কি")) {
        return "AUC মানে Agricultural University College, এটি ময়মনসিংহে অবস্থিত একটি ঐতিহ্যবাহী কলেজ।";
      }
      if (input.includes("auc") && input.includes("অর্জন")) {
        return "AUC বিভিন্ন জাতীয় পর্যায়ের প্রতিযোগিতায় অংশগ্রহণ করে এবং বহু পুরস্কার অর্জন করেছে।";
      }
      return "আমি এখনো শেখার পর্যায়ে আছি। তুমি AUC সম্পর্কেও জানতে পারো উপরের বাটন থেকে!";
    }

    function appendMessage(text, sender) {
      const msg = document.createElement('div');
      msg.classList.add('message', sender);
      msg.innerText = text;
      chat.appendChild(msg);
      chat.scrollTop = chat.scrollHeight;
    }

    function sendMessage() {
      const text = userInput.value.trim();
      if (!text) return;
      appendMessage(text, 'user');
      userInput.value = '';
      setTimeout(() => {
        const reply = fakeAIResponse(text);
        appendMessage(reply, 'bot');
      }, 700);
    }

    sendBtn.addEventListener('click', sendMessage);
    userInput.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') sendMessage();
    });
  </script>
</body>
</html>
