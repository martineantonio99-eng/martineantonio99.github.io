# martineantonio99.github.io
ewanewaeanwenaw
[index.html](https://github.com/user-attachments/files/28588220/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Courting Message</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #fff0f5;
      font-family: sans-serif;
      text-align: center;
      overflow: hidden;
    }

    #app {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 2rem;
    }

    .bear {
      font-size: 80px;
      margin-bottom: 1rem;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .question {
      font-size: 24px;
      font-weight: 600;
      color: #333;
      margin-bottom: 0.4rem;
    }

    .sub {
      font-size: 16px;
      color: #888;
      margin-bottom: 2rem;
    }

    .btns {
      display: flex;
      gap: 20px;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
    }

    .yes-btn {
      background: #D4537E;
      color: white;
      border: none;
      border-radius: 50px;
      padding: 13px 34px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
      white-space: nowrap;
    }

    .yes-btn:hover { background: #993556; transform: scale(1.05); }

    .no-btn {
      background: #f5f5f5;
      color: #888;
      border: 1px solid #ddd;
      border-radius: 50px;
      padding: 13px 34px;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
      white-space: nowrap;
    }

    .heart {
      position: fixed;
      pointer-events: none;
      font-size: 28px;
      animation: rise 1.8s forwards;
    }

    @keyframes rise {
      0%   { opacity: 1; transform: translateY(0) scale(1); }
      100% { opacity: 0; transform: translateY(-120px) scale(1.5); }
    }

    .accepted {
      font-size: 20px;
      font-weight: 600;
      color: #D4537E;
      animation: pop 0.5s ease;
    }

    @keyframes pop {
      0%   { transform: scale(0.5); opacity: 0; }
      60%  { transform: scale(1.15); }
      100% { transform: scale(1); opacity: 1; }
    }
  </style>
</head>
<body>

<div id="app">
  <div class="bear" id="bear">🐻</div>
  <p class="question" id="qtxt">Can I court you? 💕</p>
  <p class="sub" id="stxt">Please????</p>
  <div class="btns" id="btns">
    <button class="yes-btn" id="yes-btn" onclick="sayYes()">Yes 💗</button>
    <button class="no-btn" id="no-btn" onclick="pressNo()">No 😔</button>
  </div>
</div>

<script>
  let n = 0;

  const stages = [
    { no: "No 😔",          q: "Can I court you?",               sub: "Please...." },
    { no: "Still no 😢",    q: "NO",         sub: "💔" },
    { no: "HUYY? 😭",  q: "NO",     sub: "🙏" },
    { no: "Wag kasi",   q: "LUH....",       sub: "......" },
    { no: "PLEASE 😤",      q: "AYAW???",       sub: "WAG." },
    { no: "Ouch... 😞", q: "HUHUHUHUHU ",       sub: "huhuhuhuhuhuhuhuh" },
    { no: "Yes 🥰",         q: "HHAHAHAHHAHAHAHHAHAHAHHAHAHAH",  sub: "PLEASEEEEEE" },
  ];

  function pressNo() {
    n++;
    const noBtn = document.getElementById('no-btn');

    if (n >= stages.length) {
      sayYes();
      return;
    }

    const stage = stages[n];
    document.getElementById('qtxt').textContent = stage.q;
    document.getElementById('stxt').textContent = stage.sub;
    noBtn.textContent = stage.no;

    const newSize = 16 + n * 5;
    const padV = 13 + n * 5;
    const padH = 34 + n * 10;
    noBtn.style.fontSize = newSize + 'px';
    noBtn.style.padding = padV + 'px ' + padH + 'px';

    if (n >= stages.length - 1) {
      noBtn.style.background = '#D4537E';
      noBtn.style.color = 'white';
      noBtn.style.borderColor = '#D4537E';
    }
  }

  function sayYes() {
    document.getElementById('no-btn').style.display = 'none';

    for (let i = 0; i < 14; i++) {
      setTimeout(() => {
        const el = document.createElement('div');
        el.className = 'heart';
        el.textContent = ['💕','💗','💖','💓','🌹','❤️'][Math.floor(Math.random() * 6)];
        el.style.left = Math.random() * window.innerWidth + 'px';
        el.style.top  = Math.random() * window.innerHeight * 0.8 + 'px';
        document.body.appendChild(el);
        setTimeout(() => el.remove(), 1800);
      }, i * 120);
    }

    document.getElementById('bear').textContent = '🥰';
    document.getElementById('qtxt').textContent = 'Yuhuuuu 🎉';
    document.getElementById('stxt').textContent = '';
    document.getElementById('btns').innerHTML = '<p class="accepted">Araw araw na kita iinisin HAHHAHAH 💕</p>';
  }
</script>

</body>
</html>
