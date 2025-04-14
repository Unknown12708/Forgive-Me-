
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Forgive Me?</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: #e6f7ff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
    }
    .container {
      background: white;
      border-radius: 16px;
      padding: 30px;
      max-width: 500px;
      text-align: center;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
    }
    .message {
      font-size: 1.2rem;
      margin-bottom: 20px;
      min-height: 100px;
      color: #333;
    }
    .next-btn, .choice-btn {
      background-color: #f39c12;
      border: none;
      padding: 10px 20px;
      font-size: 1rem;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.3s;
    }
    .next-btn:hover, .choice-btn:hover {
      background-color: #d35400;
      color: white;
    }
    .choices {
      display: flex;
      justify-content: space-around;
      margin-top: 20px;
    }
    .emoji {
      font-size: 2rem;
      margin-top: 10px;
    }
    #whatsapp-link button {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      background-color: #25D366;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      font-size: 1rem;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="message" id="message"></div>
    <button class="next-btn" id="nextBtn">Next</button>
    <div class="choices" id="choices" style="display: none;">
      <button class="choice-btn" onclick="showResponse(true)">Yes, I forgive you ❤️</button>
      <button class="choice-btn" onclick="showResponse(false)">No, I’m still mad 😤</button>
    </div>
    <div class="emoji" id="emoji"></div>

    <!-- WhatsApp Button -->
    <a id="whatsapp-link" href="#" style="display: none;" target="_blank">
      <button>Reply on WhatsApp 💬</button>
    </a>
  </div>

  <script>
    const messages = [
      "Hey Aditi... I know this might be the last thing you want to see from me.",
      "But I’ve been thinking about that one hour we talked… it actually meant something to me.",
      "What happened after—that rude stuff? That wasn’t me. My friend used my account and messed up badly.",
      "I should’ve protected that moment. I take full responsibility, and I’m really sorry.",
      "So this is me, doing what I can... hoping you’ll hear the real me. Would you forgive me?"
    ];

    let index = 0;
    const messageDiv = document.getElementById("message");
    const nextBtn = document.getElementById("nextBtn");
    const choices = document.getElementById("choices");
    const emoji = document.getElementById("emoji");
    const whatsappLink = document.getElementById("whatsapp-link");

    function typeMessage(text, callback) {
      let i = 0;
      messageDiv.textContent = "";
      const interval = setInterval(() => {
        messageDiv.textContent += text[i];
        i++;
        if (i === text.length) {
          clearInterval(interval);
          if (callback) callback();
        }
      }, 30);
    }

    function showNextMessage() {
      if (index < messages.length) {
        typeMessage(messages[index], () => {
          index++;
          if (index === messages.length) {
            nextBtn.style.display = "none";
            choices.style.display = "flex";
          }
        });
      }
    }

    function showResponse(forgiven) {
      choices.style.display = "none";
      if (forgiven) {
        typeMessage("Thank you... this means a lot 💖");
        emoji.textContent = "🤗";
        whatsappLink.style.display = "block";
        const phoneNumber = '919041541154';
        const messageText = encodeURIComponent("Hey, I saw your page. Let's talk 🙂");
        whatsappLink.href = `https://wa.me/${phoneNumber}?text=${messageText}`;
      } else {
        typeMessage("It’s okay... I understand 😞");
        emoji.textContent = "💔";
      }
    }

    nextBtn.addEventListener("click", showNextMessage);
    showNextMessage();
  </script>
</body>
</html>
