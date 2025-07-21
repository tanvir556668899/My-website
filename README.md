<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Earn Points</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">

    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #ffcc00 0%, #ffaa00 100%);
            --secondary-color: #fff9e6;
            --text-dark: #2c2c2c;
            --text-light: #000000;
            --success-color: #1e7e34;
            --card-bg: #ffffff;
            --shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--secondary-color);
            color: var(--text-dark);
            display: flex;
            flex-direction: column;
            height: 100vh;
        }

        main {
            flex-grow: 1;
            overflow-y: auto;
            padding: 20px;
        }

        .profile-section {
            background: var(--primary-gradient);
            color: var(--text-light);
            padding: 30px 25px;
            border-radius: 20px;
            margin-bottom: 25px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .profile-icon {
            font-size: 48px;
            background: rgba(0, 0, 0, 0.1);
            border-radius: 50%;
            width: 75px;
            height: 75px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .profile-info h3 {
            margin: 0;
            font-size: 22px;
            font-weight: 700;
        }

        .profile-info p {
            margin: 5px 0 0;
            font-size: 16px;
            font-weight: 600;
            background: rgba(255, 255, 255, 0.9);
            color: #ffaa00;
            padding: 6px 14px;
            border-radius: 20px;
            display: inline-block;
        }

        .card {
            background: #fffdf5;
            border: 2px solid #ffe58f;
            padding: 25px;
            border-radius: 20px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        .card h2 {
            margin-top: 0;
            font-weight: 700;
            color: var(--text-dark);
        }

        #monetag-ad-placeholder {
            min-height: 50px;
            margin: 20px 0;
            border-radius: 12px;
            background: #fff3cd;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            color: #555;
        }

        .action-button {
            background: var(--primary-gradient);
            color: var(--text-dark);
            border: 2px solid #ffaa00;
            padding: 15px 30px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 18px;
            font-weight: 700;
            width: 100%;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            box-shadow: 0 4px 15px rgba(255, 170, 0, 0.4);
        }

        .action-button:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 170, 0, 0.5);
        }

        .action-button:disabled {
            background: #ccc;
            cursor: not-allowed;
            box-shadow: none;
        }

        #ad-message {
            color: var(--success-color);
            margin-top: 15px;
            font-weight: 500;
        }

        .withdraw-form .form-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .withdraw-form label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            font-size: 14px;
        }

        .withdraw-form input,
        .withdraw-form select {
            width: 100%;
            padding: 15px;
            border-radius: 12px;
            border: 1px solid #ddd;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            font-size: 16px;
        }

        .withdraw-form input:focus,
        .withdraw-form select:focus {
            outline: none;
            border-color: #ffaa00;
            box-shadow: 0 0 0 3px rgba(255, 204, 0, 0.3);
        }

        footer {
            display: flex;
            background-color: var(--card-bg);
            box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.05);
            border-top-left-radius: 20px;
            border-top-right-radius: 20px;
            padding: 10px 0;
        }

        .nav-button {
            flex: 1;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            font-weight: 600;
            background: none;
            border: none;
            font-size: 16px;
            color: #999;
            position: relative;
        }

        .nav-button.active {
            color: #ffaa00;
        }

        .nav-button.active::after {
            content: '';
            position: absolute;
            bottom: 5px;
            left: 50%;
            transform: translateX(-50%);
            width: 8px;
            height: 8px;
            background: #ffaa00;
            border-radius: 50%;
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>

<main id="home-section">
    <section class="profile-section">
        <div class="profile-icon">👤</div>
        <div class="profile-info">
            <h3 id="user-name">Welcome User</h3>
            <p>Points: <span id="points-display">0</span></p>
        </div>
    </section>

    <section class="card">
        <h2>🎬 Watch Ad to Earn</h2>
        <p style="color: #666; margin-top: -10px; margin-bottom: 20px;">প্রতিটি বিজ্ঞাপনের জন্য ১০০ পয়েন্ট জিতুন!</p>
        <div id="monetag-ad-placeholder">
            <p><script src='//libtl.com/sdk.js' data-zone='9599191' data-sdk='show_9599191'></script></p>
        </div>
        <button id="watch-ad-btn" class="action-button">⚡ Watch Ad</button>
        <p id="ad-message"></p>
    </section>
</main>

<main id="withdraw-section" class="hidden">
    <section class="card withdraw-form">
        <h2>💵 Withdraw Points</h2>
        <p style="color: #666; font-size: 14px;">20000 পয়েন্ট = 100 টাকা</p>
        <form id="withdraw-form" style="margin-top: 25px;">
            <div class="form-group">
                <label for="points-to-withdraw">Points to Withdraw</label>
                <input type="number" id="points-to-withdraw" placeholder="Minimum 20000" required>
            </div>
            <div class="form-group">
                <label for="payment-method">Payment Method</label>
                <select id="payment-method" required>
                    <option value="bkash">bKash</option>
                    <option value="nagad">Nagad</option>
                </select>
            </div>
            <div class="form-group">
                <label for="account-number">Account Number</label>
                <input type="text" id="account-number" placeholder=  required>
            </div>
            <button type="submit" class="action-button">✅ Submit Request</button>
        </form>
    </section>
</main>

<footer>
    <button id="home-btn" class="nav-button active">🏠 Home</button>
    <button id="withdraw-btn" class="nav-button">💰 Withdraw</button>
</footer>

<script>
    document.addEventListener('DOMContentLoaded', () => {
        const tg = window.Telegram.WebApp;
        tg.ready();

        const userNameElement = document.getElementById('user-name');
        const pointsDisplay = document.getElementById('points-display');
        const watchAdBtn = document.getElementById('watch-ad-btn');
        const adMessage = document.getElementById('ad-message');
        
        const homeSection = document.getElementById('home-section');
        const withdrawSection = document.getElementById('withdraw-section');
        const homeBtn = document.getElementById('home-btn');
        const withdrawBtn = document.getElementById('withdraw-btn');
        const withdrawForm = document.getElementById('withdraw-form');
        const pointsToWithdrawInput = document.getElementById('points-to-withdraw');
        
        let currentUser = { points: 0 };

        if (tg.initDataUnsafe?.user) {
            userNameElement.textContent = tg.initDataUnsafe.user.first_name || 'Welcome User';
        }
        
        const monetagPlaceholder = document.getElementById('monetag-ad-placeholder');
        monetagPlaceholder.innerHTML = `<p>Monetag Ad (ID: 9599191) will show here.</p>`;

        watchAdBtn.addEventListener('click', () => {
            watchAdBtn.disabled = true;
            adMessage.textContent = 'Ad is loading...';

            setTimeout(() => {
                const reward = 150;
                currentUser.points += reward;
                pointsDisplay.textContent = currentUser.points;
                adMessage.textContent = `🎉 Congratulations! You earned ${reward} points.`;

                setTimeout(() => {
                    watchAdBtn.disabled = false;
                    adMessage.textContent = '';
                }, 2000);

            }, 3000);
        });

        homeBtn.addEventListener('click', () => {
            homeSection.classList.remove('hidden');
            withdrawSection.classList.add('hidden');
            homeBtn.classList.add('active');
            withdrawBtn.classList.remove('active');
        });

        withdrawBtn.addEventListener('click', () => {
            homeSection.classList.add('hidden');
            withdrawSection.classList.remove('hidden');
            homeBtn.classList.remove('active');
            withdrawBtn.classList.add('active');
        });

        withdrawForm.addEventListener('submit', (event) => {
            event.preventDefault();

            const pointsToWithdraw = parseInt(pointsToWithdrawInput.value, 10);
            const paymentMethod = document.getElementById('payment-method').value;
            const accountNumber = document.getElementById('account-number').value;

            if (pointsToWithdraw < 7
               000) {
                alert('Error: Minimum 20000 points required to withdraw.');
                return;
            }
            if (pointsToWithdraw > currentUser.points) {
                alert('Error: You do not have enough points.');
                return;
            }

            console.log({
                points: pointsToWithdraw,
                method: paymentMethod,
                number: accountNumber
            });

            currentUser.points -= pointsToWithdraw;
            pointsDisplay.textContent = currentUser.points;

            alert('✅ Success! Your withdrawal request has been submitted.');
            withdrawForm.reset();
            homeBtn.click();
        });
    });
</script>
</body>
</html>p
