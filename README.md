
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Valentine Invitation 💘</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Comic Sans MS', cursive, sans-serif;
    }

    .card {
      background: white;
      padding: 30px 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      animation: pop 1s ease;
      max-width: 320px;
    }

    h1 {
      color: #ff4d6d;
      margin-bottom: 10px;
    }

    p {
      color: #555;
      font-size: 18px;
    }

    .heart {
      font-size: 40px;
      animation: beat 1s infinite;
      margin: 15px 0;
    }

    button {
      background: #ff4d6d;
      border: none;
      color: white;
      padding: 12px 20px;
      border-radius: 30px;
      font-size: 16px;
      cursor: pointer;
      margin: 8px;
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.1);
    }

    @keyframes beat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.3); }
    }

    @keyframes pop {
      0% { transform: scale(0); }
      100% { transform: scale(1); }
    }
  </style>

<!-- Supabase SDK -->
<script src="https://unpkg.com/@supabase/supabase-js@2"></script>

<script>
  const SUPABASE_URL = "https://xhunxjynsnrmkgabdtjz.supabase.co";
  const SUPABASE_KEY = "sb_publishable_j5y-wN2t5zzgCXtx3RnkGA_rBaF5hry";

  const supabase = supabase.createClient(
    SUPABASE_URL,
    SUPABASE_KEY
  );

  async function sendResponse(answer) {
    const { error } = await supabase
      .from("responses")
      .insert([{ answer: answer }]);

    if (error) {
      document.getElementById("response").innerHTML =
        "Oops 😢 something went wrong";
      console.error(error);
    } else {
      document.getElementById("response").innerHTML =
        answer === "YES"
        ? "Yay! 💖 I got your answer 🥰"
        : "Thank you for being honest 💗";
    }
  }

  function yes() {
    sendResponse("YES");
    console.log("yes");
  }

  function no() {
    sendResponse("NO");
    console.log("no");
  }
</script>
  
</head>
<body>

  <div class="card">
    <h1>hi baby 💕</h1>
    <div class="heart">❤️</div>
    <p>
      Will you be my Valentine?<br>
      Let’s make this day extra special ✨
    </p>
    <button onclick="yes()">Yes 💘</button>
    <button onclick="no()">No 🙈</button>
    <p id="response"></p>
  </div>
</body>

</html>
