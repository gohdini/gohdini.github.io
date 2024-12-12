<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Study Help - Customer Support</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      line-height: 1.6;
    }
    #support-widget {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #f5f5f5;
      border: 1px solid #ccc;
      padding: 10px;
      width: 300px;
      display: none; /* Initially hidden */
      box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    }
    #support-header {
      background-color: #0078d4;
      color: white;
      padding: 10px;
      font-weight: bold;
      text-align: center;
      cursor: pointer;
    }
    #support-body {
      display: none; /* Hidden by default */
    }
    #hidden-chat {
      display: none; /* Hidden by default */
    }
    textarea {
      width: 100%;
      height: 100px;
      margin: 5px 0;
      resize: none;
    }
    input {
      width: 80%;
      padding: 5px;
    }
    button {
      padding: 5px;
      background-color: #0078d4;
      color: white;
      border: none;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Study Help Platform</h1>
  <p>Welcome to your personalized study assistant. If you need help with any topic, click the customer support widget in the bottom right corner.</p>

  <div id="support-widget">
    <div id="support-header">Customer Support</div>
    <div id="support-body">
      <p>Welcome to Study Help Support. How can we assist you today?</p>
      <textarea id="support-messages" readonly></textarea>
      <input type="text" id="support-input" placeholder="Type your query..." />
      <button onclick="checkMessage()">Send</button>
    </div>
    <div id="hidden-chat">
      <h3>Private Chat</h3>
      <textarea id="chat-box" readonly></textarea>
      <input type="text" id="chat-input" placeholder="Type your message..." />
      <button onclick="sendMessage()">Send</button>
    </div>
  </div>

  <script>
    // Toggle support widget visibility
    document.getElementById("support-header").addEventListener("click", () => {
      const supportBody = document.getElementById("support-body");
      supportBody.style.display = supportBody.style.display === "none" ? "block" : "none";
    });

    // Check for a secret phrase
    function checkMessage() {
      const input = document.getElementById("support-input").value.trim();
      if (input.toLowerCase() === "open private chat") {
        document.getElementById("hidden-chat").style.display = "block";
        document.getElementById("support-body").style.display = "none"; // Hide support
      } else {
        document.getElementById("support-messages").value += `You: ${input}\nSupport: Thank you for your query. We'll get back to you shortly.\n`;
        document.getElementById("support-input").value = ""; // Clear input
      }
    }

    // Private chat functionality
    const messages = [];
    function sendMessage() {
      const chatInput = document.getElementById("chat-input").value.trim();
      if (chatInput) {
        messages.push(`You: ${chatInput}`);
        document.getElementById("chat-box").value = messages.join("\n");
        document.getElementById("chat-input").value = "";
      }
    }
  </script>
</body>
</html>
