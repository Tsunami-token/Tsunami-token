<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tsunami Airdrop Countdown</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #countdown {
            font-size: 2em;
            margin-bottom: 20px;
        }
        #invite-link {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Tsunami Airdrop</h1>
    <div id="countdown"></div>
    <div id="invite-link">
        <button onclick="shareLink()">Invite Friends</button>
    </div>

    <script>
        // شمارش معکوس
        const airdropStartTime = new Date().getTime() + (30 * 24 * 60 * 60 * 1000); // 30 روز
        const countdownElem = document.getElementById('countdown');

        function updateCountdown() {
            const now = new Date().getTime();
            const distance = airdropStartTime - now;

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            countdownElem.innerHTML = ${days}d ${hours}h ${minutes}m ${seconds}s;

            if (distance < 0) {
                countdownElem.innerHTML = "Airdrop has started!";
            }
        }

        setInterval(updateCountdown, 1000);

        // تابع برای اشتراک گذاری لینک دعوت
        function shareLink() {
            const userId = window.Telegram.WebApp.initDataUnsafe.user.id;  // گرفتن ID کاربر از تلگرام
            const inviteLink = https://t.me/Tsunami_token_bot?start=${userId};
            alert(Invite your friends with this link: ${inviteLink});
        }
    </script>
</body>
</html>
