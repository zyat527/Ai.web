<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>zyat AI</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0;
      padding: 0;
      height: 100vh;
    }
    h1 {
      margin-top: 20px;
      font-size: 28px;
      background: linear-gradient(90deg, #00f2fe, #4facfe);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    p {
      margin: 5px 0 15px;
      opacity: 0.8;
    }
    #chatBox {
      flex: 1;
      width: 90%;
      max-width: 500px;
      background: rgba(255, 255, 255, 0.05);
      border-radius: 15px;
      padding: 15px;
      margin: 10px 0;
      overflow-y: auto;
      backdrop-filter: blur(5px);
      display: flex;
      flex-direction: column;
    }
    .bubble {
      max-width: 80%;
      padding: 10px 15px;
      margin: 8px 0;
      border-radius: 15px;
      animation: fadeIn 0.3s ease;
      word-wrap: break-word;
    }
    .user {
      background: linear-gradient(90deg, #4facfe, #00f2fe);
      align-self: flex-end;
      color: #000;
      border-bottom-right-radius: 0;
    }
    .ai {
      background: rgba(255, 255, 255, 0.1);
      align-self: flex-start;
      border-bottom-left-radius: 0;
    }
    .typing {
      font-style: italic;
      opacity: 0.7;
    }
    #inputArea {
      display: flex;
      gap: 10px;
      width: 90%;
      max-width: 500px;
      margin-bottom: 20px;
    }
    input {
      flex: 1;
      padding: 12px;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      outline: none;
      background: rgba(255, 255, 255, 0.1);
      color: #fff;
    }
    button {
      padding: 12px 20px;
      border: none;
      border-radius: 10px;
      background: linear-gradient(90deg, #4facfe, #00f2fe);
      font-size: 16px;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      transform: scale(1.05);
    }
    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(5px);}
      to {opacity: 1; transform: translateY(0);}
    }
  </style>
</head>
<body>

  <h1>🤖 AI ZYAT</h1>
  <p>LU NANYA GUA JAWAB!</p>

  <div id="chatBox">
    <div class="bubble ai"><strong>AI:</strong> oi gua AI yang baik kok gua akan jadi teman lu ok!!</div>
  </div>

  <div id="inputArea">
    <input type="text" id="userInput" placeholder="Tulis pesan..." />
    <button onclick="kirimPesan()">Kirim</button>
  </div>

  <!-- Suara kirim pesan -->
  <audio id="sendSound" src="https://assets.mixkit.co/active_storage/sfx/2577/2577-preview.mp3"></audio>

  <script>
    function kirimPesan() {
      const inputText = document.getElementById("userInput").value.trim();
      const chatBox = document.getElementById("chatBox");
      const sendSound = document.getElementById("sendSound");

      if (!inputText) return;

      const input = inputText.toLowerCase();
      let jawaban = "Aku nggak ngerti maksudmu kerena aku sudah di perogram untuk menjawab pertanyaan seperti apa kabarmu,hai,nama kamu siapa,siapa aku siapaterima kasih,dan game serta dadah,bye.";

      if (input.includes("halo") || input.includes("hai")) {
        jawaban = "iya ada yang bisa saya bantu?";
      } else if (input.includes("nama")) {
        jawaban = "Namaku zyat, AI versi ringan dari ai yang lain 😄";
      } else if (input.includes("kabarmu") || input.includes("apa kabar")) {
        jawaban = "pagi pagi mentarik, selalu baik.";
      } else if (input.includes("siapa aku")) {
        jawaban = "saya tebak kamu adalah titisan albert instein!";
      } else if (input.includes("terima kasih")) {
        jawaban = "Sama-sama kalah ada perlu kesini lagi aja ya.";
      } else if (input.includes("game")) {
        jawaban = "jika saya mengecewakan anda mohon maaf karena ini bukan game tetapi saya pasti akan mengubah kekecewaan menjadi hilang dengan cara bercanda dengan saya!";
      } else if (input.includes("bye") || input.includes("dadah")) {
        jawaban = "dadah and bye sampai jumpa dan jangan lupa mampir lagi yaa 😊";
      }

      // Mainkan suara
      sendSound.play();

      // Pesan user
      const userBubble = document.createElement("div");
      userBubble.className = "bubble user";
      userBubble.innerHTML = `<strong>Kamu:</strong> ${inputText}`;
      chatBox.appendChild(userBubble);

      // Animasi mengetik
      const typingBubble = document.createElement("div");
      typingBubble.className = "bubble ai typing";
      typingBubble.textContent = "AI sedang mengetik...";
      chatBox.appendChild(typingBubble);
      chatBox.scrollTop = chatBox.scrollHeight;

      // Delay sebelum jawaban muncul
      setTimeout(() => {
        typingBubble.remove();
        const aiBubble = document.createElement("div");
        aiBubble.className = "bubble ai";
        aiBubble.innerHTML = `<strong>AI:</strong> ${jawaban}`;
        chatBox.appendChild(aiBubble);
        chatBox.scrollTop = chatBox.scrollHeight;
      }, 1000);

      document.getElementById("userInput").value = "";
    }
  </script>

</body>
</html>
