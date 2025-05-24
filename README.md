<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SAii - Powered by Google AI</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: url('your-photo.jpg') no-repeat center center fixed;
      background-size: cover;
      color: white;
      overflow: hidden;
    }.overlay {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(5px);
}

.container {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  text-align: center;
}

.title {
  font-size: 3em;
  text-shadow: 0 0 20px #00f0ff;
  animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
  from { text-shadow: 0 0 10px #00f0ff; }
  to { text-shadow: 0 0 20px #00f0ff, 0 0 30px #00f0ff; }
}

.chat-box {
  margin-top: 30px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  padding: 20px;
  width: 80%;
  max-width: 600px;
  backdrop-filter: blur(10px);
}

.input-area {
  margin-top: 20px;
  display: flex;
}

.input-area input {
  flex: 1;
  padding: 10px;
  border-radius: 10px 0 0 10px;
  border: none;
}

.input-area button {
  padding: 10px 20px;
  background: #00f0ff;
  color: black;
  border: none;
  border-radius: 0 10px 10px 0;
  cursor: pointer;
}

.response {
  margin-top: 15px;
  text-align: left;
  font-size: 1.1em;
  animation: fadeIn 1s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

footer {
  position: absolute;
  bottom: 10px;
  width: 100%;
  text-align: center;
  font-size: 0.9em;
  color: #00f0ff;
  text-shadow: 0 0 10px #00f0ff;
}

  </style>
</head>
<body>
  <div class="overlay"></div>
  <div class="container">
    <div class="title">SAii - Speak with Google AI</div>
    <div class="chat-box">
      <div id="chat-output" class="response">Hello! Ask me anything.</div>
      <div class="input-area">
        <input type="text" id="user-input" placeholder="Type your message..." />
        <button onclick="sendMessage()">Send</button>
      </div>
    </div>
  </div>  <footer>SAii is designed by Siyam Khan</footer>  <script>
    async function sendMessage() {
      const input = document.getElementById('user-input');
      const chatOutput = document.getElementById('chat-output');
      const userMessage = input.value.trim();
      if (!userMessage) return;
      
      chatOutput.innerHTML = '<i>Thinking...</i>';

      // Send to Gemini (you must replace with your actual Gemini API logic)
      try {
        const response = await fetch('https://your-backend-api.com/gemini', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ prompt: userMessage })
        });
        const data = await response.json();
        chatOutput.innerHTML = data.reply || 'No response.';
      } catch (e) {
        chatOutput.innerHTML = 'Error: Could not reach AI server.';
      }

      input.value = '';
    }
  </script></body>
</html>
