<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>إحصائيات الصفقات</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        body {
            background: linear-gradient(140deg, #18182d 60%, #3794ff 100%);
            font-family: 'Cairo', 'Tajawal', sans-serif;
            color: #fff;
            text-align: center;
            margin: 0;
            padding: 0;
            direction: rtl;
        }
        .header-img {
            width: 100%;
            max-height: 260px;
            object-fit: cover;
            border-bottom: 6px solid #3794ff;
            box-shadow: 0 8px 24px rgba(0,0,0,0.15);
            margin-bottom: 0;
            display: block;
        }
        .tg-link {
            margin: 28px auto 10px auto;
            display: flex;
            justify-content: center;
        }
        .tg-link img {
            width: 90px;
            height: 90px;
            border-radius: 18px;
            box-shadow: 0 2px 14px rgba(55,148,255,0.25);
            transition: transform 0.18s;
            border: 3px solid #3794ff;
            background: #111;
        }
        .tg-link img:hover {
            transform: scale(1.07) rotate(-4deg);
            box-shadow: 0 4px 24px #3794ff70;
        }
        .tg-caption {
            margin-top: 10px;
            color: #3794ff;
            font-size: 1.12em;
            font-weight: 600;
        }
        .card {
            background: rgba(20,20,40,0.92);
            border-radius: 20px;
            padding: 40px 20px;
            margin: 40px auto 60px auto;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.25);
        }
        h1 {
            font-size: 2.1em;
            margin-bottom: 20px;
            letter-spacing: 1px;
        }
        .stats {
            display: flex;
            justify-content: space-between;
            margin: 30px 0;
            font-size: 1.3em;
        }
        .stats div {
            background: #2d2d42;
            border-radius: 10px;
            padding: 15px 10px;
            flex: 1;
            margin: 0 5px;
            min-width: 90px;
        }
        .win { color: #2dcc70; }
        .lose { color: #e74c3c; }
        .rate {
            background: #3794ff;
            border-radius: 10px;
            padding: 10px;
            margin: 10px 0 0 0;
            font-size: 1.15em;
            font-weight: bold;
        }
        .footer {
            margin-top: 40px;
            color: #bbb;
            font-size: 1em;
        }
        .controls {
            margin-top: 30px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        .controls button {
            background: #3794ff;
            border: none;
            color: #fff;
            padding: 12px 25px;
            border-radius: 12px;
            font-size: 1.1em;
            cursor: pointer;
            transition: background 0.2s;
        }
        .controls button:hover {
            background: #2d2d42;
        }
    </style>
</head>
<body>
    <!-- صورة الهيدر -->
    <img src="header.jpg" alt="الهيدر" class="header-img">

    <!-- رابط قناة التليجرام كصورة قابلة للضغط -->
    <div class="tg-link">
        <a href="https://t.me/orderfilllled" target="_blank" title="انضم للقناة">
            <img src="whale.png" alt="قناة التليجرام">
        </a>
    </div>
    <div class="tg-caption">اضغط على صورة القناة للانضمام 👈</div>

    <div class="card">
        <h1>📊 إحصائيات الصفقات</h1>
        <div class="stats">
            <div class="win">✅ ناجحة<br><span id="win">0</span></div>
            <div class="lose">❌ خاسرة<br><span id="lose">0</span></div>
        </div>
        <div class="rate">🏆 نسبة النجاح: <span id="winRate">0.00</span>%</div>
        <div class="controls">
            <button onclick="addWin()">صفقة ناجحة</button>
            <button onclick="addLose()">صفقة خاسرة</button>
            <button onclick="resetStats()">إعادة تعيين</button>
        </div>
        <div class="footer">
            مجموع الصفقات: <b id="total">0</b><br>
            يمكنك تعديل الإحصائيات عبر الأزرار.<br>
        </div>
    </div>

    <script>
        let win = 0;
        let lose = 0;

        function updateStats() {
            document.getElementById('win').textContent = win;
            document.getElementById('lose').textContent = lose;
            let total = win + lose;
            document.getElementById('total').textContent = total;
            let winRate = total > 0 ? (win / total * 100).toFixed(2) : '0.00';
            document.getElementById('winRate').textContent = winRate;
        }

        function addWin() {
            win++;
            updateStats();
        }

        function addLose() {
            lose++;
            updateStats();
        }

        function resetStats() {
            win = 0;
            lose = 0;
            updateStats();
        }

        updateStats();
    </script>
</body>
</html>
