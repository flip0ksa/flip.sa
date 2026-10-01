<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FLIP | تحدي السري</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Tajawal', sans-serif;
        }
        body {
            background-color: #050814;
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
            position: relative;
        }
        body::before {
            content: '';
            position: absolute;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(59, 130, 246, 0.15) 0%, rgba(5, 8, 20, 0) 70%);
            top: -50px;
            right: -50px;
            z-index: -1;
        }
        .container {
            width: 100%;
            max-width: 420px;
            background: rgba(13, 27, 42, 0.7);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 24px;
            padding: 35px 25px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
            animation: fadeIn 0.8s ease-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .logo-area h1 {
            font-size: 38px;
            font-weight: 900;
            letter-spacing: 3px;
            color: #ffffff;
            margin-bottom: 10px;
        }
        .logo-area h1 span {
            color: #3b82f6;
        }
        .game-section h2 {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 10px;
            color: #f8fafc;
        }
        .game-section p {
            font-size: 14px;
            color: #94a3b8;
            line-height: 1.6;
            margin-bottom: 25px;
        }
        .letters-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 20px;
        }
        .letter-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 24px;
            font-weight: 900;
            padding: 20px;
            border-radius: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .letter-btn:hover {
            border-color: #3b82f6;
            background: rgba(59, 130, 246, 0.1);
            transform: translateY(-2px);
        }
        .error-msg {
            color: #ef4444;
            font-size: 14px;
            font-weight: 700;
            margin-top: 15px;
            min-height: 20px;
            transition: opacity 0.3s;
        }
        
        /* Hidden Reward Section */
        .reward-section {
            display: none;
        }
        .welcome-msg h2 {
            font-size: 22px;
            font-weight: 700;
            margin-bottom: 10px;
            color: #f8fafc;
        }
        .welcome-msg p {
            font-size: 14px;
            color: #94a3b8;
            line-height: 1.6;
            margin-bottom: 25px;
        }
        .coupon-box {
            background: rgba(255, 255, 255, 0.05);
            border: 2px dashed rgba(59, 130, 246, 0.5);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 25px;
        }
        .coupon-title {
            font-size: 13px;
            color: #94a3b8;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        .coupon-code {
            font-size: 26px;
            font-weight: 900;
            color: #3b82f6;
            letter-spacing: 2px;
            margin-bottom: 15px;
        }
        .copy-btn {
            background: #3b82f6;
            color: white;
            border: none;
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        .copy-btn.copied {
            background: #10b981;
        }
        .links-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.07);
            color: #ffffff;
            text-decoration: none;
            padding: 14px;
            border-radius: 12px;
            font-size: 15px;
            font-weight: 700;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }
        .social-link:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateY(-2px);
        }
        .footer-note {
            margin-top: 25px;
            font-size: 12px;
            color: #64748b;
            letter-spacing: 1px;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- قسم اللعبة -->
        <div class="game-section" id="gameSection">
            <div class="logo-area">
                <h1>FLIP</h1>
            </div>
            <h2>تحدي البراند 🎮</h2>
            <p>اختر الحرف المميز والأساسي في اسم البراند (حرف I) لفتح كود الخصم الحصري!</p>
            
            <div class="letters-grid">
                <button class="letter-btn" onclick="checkLetter('F')">F</button>
                <button class="letter-btn" onclick="checkLetter('L')">L</button>
                <button class="letter-btn" onclick="checkLetter('I')">I</button>
                <button class="letter-btn" onclick="checkLetter('P')">P</button>
            </div>
            <div class="error-msg" id="errorMsg"></div>
        </div>

        <!-- قسم كود الخصم (يظهر بعد الفوز) -->
        <div class="reward-section" id="rewardSection">
            <div class="logo-area">
                <h1>FL<span>!</span>P</h1>
            </div>

            <div class="welcome-msg">
                <h2>كفو! فزت بالتحدي 🌌</h2>
                <p>شكراً لانضمامك إلى عالمنا. تقديراً لذكائك، جهزنا لك هذا الخصم الحصري لطلبك القادم.</p>
            </div>

            <div class="coupon-box">
                <div class="coupon-title">كود الخصم الخاص بك</div>
                <div class="coupon-code" id="codeText">FLIP15</div>
                <button class="copy-btn" id="copyBtn" onclick="copyCoupon()">
                    <i class="fa-regular fa-copy"></i> نسخ الكود
                </button>
            </div>

            <div class="links-list">
                <a href="https://salla.sa" target="_blank" class="social-link">
                    <i class="fa-solid fa-store"></i> متجرنا الإلكتروني
                </a>
                <a href="https://instagram.com" target="_blank" class="social-link">
                    <i class="fa-brands fa-instagram"></i> انستقرام
                </a>
                <a href="https://tiktok.com" target="_blank" class="social-link">
                    <i class="fa-brands fa-tiktok"></i> تيك توك
                </a>
            </div>

            <div class="footer-note">
                FL!P STREETWEAR © 2026
            </div>
        </div>
    </div>

    <script>
        function checkLetter(letter) {
            const errorMsg = document.getElementById('errorMsg');
            if (letter === 'I') {
                // إخفاء اللعبة وإظهار الهدية بحركة ناعمة
                document.getElementById('gameSection').style.display = 'none';
                document.getElementById('rewardSection').style.display = 'block';
            } else {
                errorMsg.innerText = 'حرف خطأ! حاول مرة أخرى ❌';
                setTimeout(() => {
                    errorMsg.innerText = '';
                }, 2000);
            }
        }

        function copyCoupon() {
            const code = document.getElementById('codeText').innerText;
            navigator.clipboard.writeText(code);
            const btn = document.getElementById('copyBtn');
            btn.innerHTML = '<i class="fa-solid fa-check"></i> تم النسخ بنجاح!';
            btn.classList.add('copied');
            
            setTimeout(() => {
                btn.innerHTML = '<i class="fa-regular fa-copy"></i> نسخ الكود';
                btn.classList.remove('copied');
            }, 2500);
        }
    </script>
</body>
</html>
