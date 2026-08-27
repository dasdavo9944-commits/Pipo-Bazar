<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>pipoBaZaR - User Panel</title>
    <style>
        :root { --primary: #6366f1; --main: #7b1fa2; --bg: #f8fafc; --text: #1e293b; --accent: #e11d48; }
        * { box-sizing: border-box; font-family: 'Inter', sans-serif; -webkit-tap-highlight-color: transparent; }
        body { background: #eff6ff; margin: 0; padding: 0; color: var(--text); overflow-x: hidden; }
        
        .container { max-width: 480px; margin: 0 auto; background: #fff; min-height: 100vh; position: relative; box-shadow: 0 0 20px rgba(0,0,0,0.05); padding-bottom: 70px; }
        .page { display: none; animation: fadeIn 0.3s ease; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .header { display: flex; justify-content: space-between; align-items: center; padding: 15px 20px; background: #fff; border-bottom: 1px solid #f1f5f9; position: sticky; top: 0; z-index: 100; }
        .header b { font-size: 18px; color: var(--main); font-weight: 800; }
        .balance-chip { background: #f3e8ff; color: var(--main); padding: 5px 12px; border-radius: 20px; font-weight: 800; font-size: 13px; }
        .back-btn { font-size: 22px; cursor: pointer; color: var(--main); padding-right: 15px; }

        .notice-board { background: #fff9db; border: 1px solid #ffe066; padding: 10px; border-radius: 10px; margin: 15px; display: flex; align-items: center; gap: 10px; }
        .notice-board marquee { font-size: 13px; font-weight: bold; color: #856404; }

        .auth-container { padding: 40px 20px; text-align: center; }
        .input-box { width: 100%; padding: 15px; border: 1.5px solid #e2e8f0; border-radius: 12px; font-size: 16px; outline: none; margin-bottom: 15px; }
        .btn-large { width: 100%; padding: 16px; background: #6366f1; color: #fff; border: none; border-radius: 12px; font-weight: bold; font-size: 16px; cursor: pointer; }

        .content { padding: 15px; }
        .grid-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-bottom: 15px; }
        
        .cat-box { background: #fff; border: 1.5px solid #e2e8f0; border-radius: 18px; height: 125px; display: flex; flex-direction: column; align-items: center; justify-content: center; cursor: pointer; text-align: center; padding: 10px; transition: 0.2s; }
        .cat-box:active { transform: scale(0.95); background: #f8fafc; }
        .cat-box img { width: 45px; height: 45px; margin-bottom: 5px; object-fit: contain; }
        .cat-box .icon-emoji { font-size: 38px; margin-bottom: 5px; display: block; }
        .cat-box b { font-size: 11px; color: #1e293b; text-transform: uppercase; line-height: 1.2; }
        
        .product-card { background: #fff; border: 1px solid #e2e8f0; border-radius: 12px; padding: 15px 10px; text-align: center; cursor: pointer; position: relative; transition: 0.2s; }
        .product-card.selected { border: 2px solid #6366f1; background: #f0f7ff; }
        .product-card b { color: #1e293b; font-size: 14px; }
        .product-card .price-tag { color: #6366f1; font-weight: bold; font-size: 13px; margin-top: 5px; display: block; }
        .selected-icon { position: absolute; top: -5px; right: -5px; background: #6366f1; color: white; border-radius: 50%; width: 20px; height: 20px; font-size: 12px; display: none; align-items: center; justify-content: center; }
        .product-card.selected .selected-icon { display: flex; }

        .order-box { border: 1px solid #eee; padding: 12px; border-radius: 10px; margin-bottom: 10px; position: relative; background: #fff; }
        .status-badge { position: absolute; right: 10px; top: 10px; font-size: 10px; padding: 3px 8px; border-radius: 10px; font-weight: bold; }
        .st-Pending { background: #fef3c7; color: #d97706; }
        .st-Success, .st-Approved { background: #dcfce7; color: #15803d; }
        .st-Rejected { background: #fee2e2; color: #b91c1c; }

        .nav { position: fixed; bottom: 0; width: 100%; max-width: 480px; background: #fff; border-top: 1px solid #f1f5f9; display: flex; padding: 10px 0; z-index: 1000; }
        .nav-item { flex: 1; text-align: center; color: #94a3b8; cursor: pointer; font-size: 10px; font-weight: bold; }
        .nav-item.active { color: var(--main); }
    </style>
</head>
<body>

<div class="container">

    <div id="loginPage" class="page active">
        <div class="header"><b>Login</b><span></span></div>
        <div class="auth-container">
            <h1>Welcome Back</h1>
            <input type="text" id="lNick" class="input-box" placeholder="আপনার নিকনেম">
            <input type="password" id="lPass" class="input-box" placeholder="পাসওয়ার্ড">
            <button class="btn-large" onclick="handleLogin()">LOGIN</button>
            <p style="margin-top:20px">Account নেই? <b onclick="showPage('regPage')" style="color:var(--main); cursor:pointer">Register</b></p>
        </div>
    </div>

    <div id="regPage" class="page">
        <div class="header"><b>Create Account</b><span></span></div>
        <div class="auth-container">
            <input type="text" id="rName" class="input-box" placeholder="আপনার নাম">
            <input type="text" id="rNick" class="input-box" placeholder="নিকনেম">
            <input type="password" id="rPass" class="input-box" placeholder="পাসওয়ার্ড">
            <button class="btn-large" onclick="handleRegister()">REGISTER NOW</button>
        </div>
    </div>

    <div id="homePage" class="page">
        <div class="header"><b>FF TOP UP</b><div class="balance-chip">৳ <span class="u-bal">0.00</span></div></div>
        <div class="notice-board">
            <span>📢</span><marquee id="noticeText">আমাদের অ্যাপে আপনাকে স্বাগতম!</marquee>
        </div>
        <div class="content">
            <div class="grid-row" style="grid-template-columns: repeat(2, 1fr);">
                <div class="cat-box" onclick="openService('likes')">
                    <img src="https://img.icons8.com/color/96/facebook-like.png" alt="Likes">
                    <b>Likes<br>Services</b>
                </div>
                <div class="cat-box" onclick="openService('diamond')">
                    <span class="icon-emoji">💎</span>
                    <b>FF<br>DIAMONDS</b>
                </div>
            </div>
            
            <div class="grid-row" style="grid-template-columns: repeat(2, 1fr);">
                <div class="cat-box" onclick="openService('weekly_lite')">
                    <img src="https://img.icons8.com/color/96/christmas-star.png" alt="Weekly Lite">
                    <b>WEEKLY<br>LITE</b>
                </div>
                <div class="cat-box" onclick="openService('weekly_monthly')">
                    <img src="https://img.icons8.com/color/96/ticket.png" alt="Weekly/Monthly">
                    <b>WEEKLY /<br>MONTHLY</b>
                </div>
            </div>
        </div>
    </div>

    <div id="servicePage" class="page">
        <div class="header"><span class="back-btn" onclick="showPage('homePage')">←</span><b>Select Package</b></div>
        <div class="content">
            <h4 style="margin-bottom:15px; color:#475569">① Select Package</h4>
            <div id="pkgGrid" style="display:grid; grid-template-columns: 1fr 1fr; gap:12px"></div>
            <div style="margin-top:25px">
                <h4 style="margin-bottom:10px; color:#475569">② Player Info</h4>
                <input type="text" id="gameUID" class="input-box" placeholder="Enter Player ID / UID">
                <button class="btn-large" onclick="handleOrder()">BUY NOW (WALLET)</button>
            </div>
        </div>
    </div>

    <div id="walletPage" class="page">
        <div class="header"><b>My Wallet</b></div>
        <div class="content">
            <div style="background:var(--main); color:#fff; padding:30px; border-radius:20px; text-align:center">
                <small>Current Balance</small>
                <h1 style="margin:5px 0">৳ <span class="u-bal">0.00</span></h1>
            </div>
            <h3 style="margin-top:20px">Deposit Money</h3>
            <div style="border:1px solid #ddd; padding:15px; border-radius:10px; margin-bottom:10px; cursor:pointer" onclick="openPaymentProcess('bKash', '01726761064', 'deposit')">
                <b>bKash Deposit</b> <span style="float:right">→</span>
            </div>
            <div style="border:1px solid #ddd; padding:15px; border-radius:10px; cursor:pointer" onclick="openPaymentProcess('Nagad', '01726761064', 'deposit')">
                <b>Nagad Deposit</b> <span style="float:right">→</span>
            </div>
        </div>
    </div>

    <div id="ordersPage" class="page">
        <div class="header"><b>History</b></div>
        <div class="content" id="orderArea"></div>
    </div>

    <div id="finalStepPage" class="page">
        <div class="header"><span class="back-btn" onclick="showPage('homePage')">←</span><b>Confirm</b><span></span></div>
        <div class="content">
            <div style="background:#334155; color:#fff; padding:20px; border-radius:15px; text-align:center; margin-bottom:20px">
                <small id="finalLabel">Send Money To:</small>
                <h2 id="finalNum">01726761064</h2>
            </div>
            <div id="amountGroup" style="display:none">
                <input type="number" id="finalAmtInput" class="input-box" placeholder="টাকার পরিমাণ (৳)">
            </div>
            <input type="text" id="finalTrxInput" class="input-box" placeholder="TrxID দিন">
            <button class="btn-large" onclick="submitFinalPayment()">SUBMIT REQUEST</button>
        </div>
    </div>

    <div class="nav" id="bottomNav" style="display:none">
        <div class="nav-item" onclick="showPage('homePage')">🏠<br>Home</div>
        <div class="nav-item" onclick="showPage('ordersPage')">📜<br>History</div>
        <div class="nav-item" onclick="showPage('walletPage')">💰<br>Wallet</div>
        <div class="nav-item" onclick="logout()">👤<br>Logout</div>
    </div>

</div>

<!-- Firebase SDK Module -->
<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
    import { getDatabase, ref, set, get, onValue, push, update } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

    const firebaseConfig = {
        apiKey: "AIzaSyAaD3s0Ep0gn_SuS2oLJ9A-E69lUmqkffQ",
        authDomain: "top-up-85e1c.firebaseapp.com",
        databaseURL: "https://top-up-85e1c-default-rtdb.asia-southeast1.firebasedatabase.app",
        projectId: "top-up-85e1c",
        storageBucket: "top-up-85e1c.firebasestorage.app",
        messagingSenderId: "805756548452",
        appId: "1:805756548452:web:e20f3a97092c3096643671",
        measurementId: "G-QVM1GGNDHJ"
    };

    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);

    const data = {
        diamond: [
            { n: '25 Diamond', p: 23 }, { n: '50 Diamond', p: 39 }, { n: '115 Diamond', p: 80 },
            { n: '240 Diamond', p: 158 }, { n: '355 Diamond', p: 235 }, { n: '505 Diamond', p: 333 },
            { n: '610 Diamond', p: 398 }, { n: '850 Diamond', p: 553 }, { n: '1090 Diamond', p: 708 },
            { n: '1240 Diamond', p: 788 }, { n: '2530 Diamond', p: 1573 }, { n: '5060 Diamond', p: 3143 },
            { n: '7590 Diamond', p: 4703 }, { n: '10120 Diamond', p: 6253 }
        ],
        weekly_monthly: [
            { n: 'Weekly', p: 160 }, { n: '2X Weekly', p: 320 }, { n: '3X Weekly', p: 480 },
            { n: '5X Weekly', p: 800 }, { n: 'Monthly', p: 800 }, { n: '2X Monthly', p: 1600 },
            { n: '1Weekly + 1Monthly', p: 960 }, { n: '4Weekly + 1Monthly', p: 1440 }
        ],
        weekly_lite: [
            { n: '1x Weekly Lite', p: 47 }, { n: '2x Weekly Lite', p: 94 },
            { n: '3x Weekly Lite', p: 141 }, { n: '5x Weekly Lite', p: 235 }
        ],
        likes: [{ n: '200 Likes', p: 40 }]
    };

    let currentUser = null;
    let selectedPkg = null;
    let currentProcess = {};

    // Notice Sync fixed to 'app_notice'
    onValue(ref(db, 'app_notice'), (snapshot) => {
        if (snapshot.exists()) {
            document.getElementById('noticeText').innerText = snapshot.val();
        }
    });

    // Check Auto Login Session on App Load
    window.addEventListener('DOMContentLoaded', () => {
        const savedUserNick = localStorage.getItem('userSessionNick');
        if (savedUserNick) {
            autoLogin(savedUserNick);
        }
    });

    async function autoLogin(nk) {
        const userRef = ref(db, 'users/' + nk);
        const snapshot = await get(userRef);
        if (snapshot.exists()) {
            currentUser = snapshot.val();
            listenUserData(nk);
            showPage('homePage');
        } else {
            localStorage.removeItem('userSessionNick');
        }
    }

    window.showPage = function(id) {
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        document.getElementById(id).classList.add('active');
        document.getElementById('bottomNav').style.display = ['loginPage', 'regPage'].includes(id) ? 'none' : 'flex';
        if(id === 'homePage' && currentUser) updateUI();
        if(id === 'ordersPage' && currentUser) renderHistory();
    };

    window.openService = function(type) {
        selectedPkg = null;
        const grid = document.getElementById('pkgGrid');
        grid.innerHTML = data[type].map((i, idx) => `
            <div class="product-card" id="pkg-${idx}" onclick="selectItem('${i.n}', ${i.p}, 'pkg-${idx}')">
                <div class="selected-icon">✓</div>
                <b>${i.n}</b>
                <span class="price-tag">BDT ${i.p}</span>
            </div>
        `).join('');
        showPage('servicePage');
    };

    window.selectItem = function(name, price, id) {
        selectedPkg = { name, price };
        document.querySelectorAll('.product-card').forEach(el => el.classList.remove('selected'));
        document.getElementById(id).classList.add('selected');
    };

    window.handleRegister = async function() {
        const name = document.getElementById('rName').value.trim();
        const nk = document.getElementById('rNick').value.trim().toLowerCase();
        const pass = document.getElementById('rPass').value;

        if(!nk || !pass || !name) return alert("সব তথ্য সঠিকভাবে পূরণ করুন!");

        const userRef = ref(db, 'users/' + nk);
        const snapshot = await get(userRef);

        if(snapshot.exists()) {
            alert("এই নিকনেম অ্যাকাউন্টটি ইতোমধ্যেই বিদ্যমান!");
        } else {
            await set(userRef, {
                name: name,
                nick: nk,
                pass: pass,
                balance: 0
            });
            alert("Account Created Successfully!");
            showPage('loginPage');
        }
    };

    window.handleLogin = async function() {
        const nk = document.getElementById('lNick').value.trim().toLowerCase();
        const pass = document.getElementById('lPass').value;

        if(!nk || !pass) return alert("নিকনেম এবং পাসওয়ার্ড দিন!");

        const userRef = ref(db, 'users/' + nk);
        const snapshot = await get(userRef);

        if(snapshot.exists()) {
            const userData = snapshot.val();
            if(userData.pass === pass) {
                currentUser = userData;
                localStorage.setItem('userSessionNick', nk); // Save session in local storage
                listenUserData(nk);
                showPage('homePage');
            } else {
                alert("ভুল পাসওয়ার্ড দিয়েছেন!");
            }
        } else {
            alert("ব্যবহারকারী পাওয়া যায়নি!");
        }
    };

    function listenUserData(nk) {
        onValue(ref(db, 'users/' + nk), (snapshot) => {
            if(snapshot.exists()){
                currentUser = snapshot.val();
                updateUI();
            }
        });
    }

    function updateUI() {
        if(!currentUser) return;
        const bal = parseFloat(currentUser.balance || 0).toFixed(2);
        document.querySelectorAll('.u-bal').forEach(e => e.innerText = bal);
    }

    window.handleOrder = async function() {
        const uid = document.getElementById('gameUID').value;
        if(!selectedPkg) return alert("প্যাকেজ সিলেক্ট করুন!");
        if(!uid) return alert("Player ID/UID দিন!");
        if((currentUser.balance || 0) < selectedPkg.price) return alert("পর্যাপ্ত ব্যালেন্স নেই!");

        const newBal = currentUser.balance - selectedPkg.price;
        
        await update(ref(db, 'users/' + currentUser.nick), { balance: newBal });

        const orderRef = push(ref(db, 'users/' + currentUser.nick + '/orders'));
        await set(orderRef, {
            id: orderRef.key,
            nick: currentUser.nick,
            n: selectedPkg.name,
            p: selectedPkg.price,
            uid: uid,
            status: "Pending",
            date: new Date().toLocaleString()
        });

        alert("অর্ডার সফল হয়েছে! এডমিন শীঘ্রই সম্পন্ন করবেন।");
        document.getElementById('gameUID').value = '';
        showPage('ordersPage');
    };

    window.openPaymentProcess = function(m, n, t) {
        currentProcess = { type:t, method:m };
        document.getElementById('finalNum').innerText = n;
        document.getElementById('amountGroup').style.display = t === 'deposit' ? 'block' : 'none';
        showPage('finalStepPage');
    };

    window.submitFinalPayment = async function() {
        const trx = document.getElementById('finalTrxInput').value.trim();
        const amt = parseFloat(document.getElementById('finalAmtInput').value);
        if(!trx) return alert("TrxID দিন!");

        if(currentProcess.type === 'deposit') {
            if(isNaN(amt) || amt <= 0) return alert("সঠিক পরিমাণ লিখুন!");
            
            const depRef = push(ref(db, 'users/' + currentUser.nick + '/deposits'));
            await set(depRef, {
                id: depRef.key,
                nick: currentUser.nick,
                method: currentProcess.method,
                price: amt,
                status: "Pending",
                date: new Date().toLocaleString(),
                trx: trx
            });
        }

        alert("রিকোয়েস্ট জমা হয়েছে! এডমিন ভেরিফাই করে অ্যাপ্রুভ করবে।");
        document.getElementById('finalTrxInput').value = '';
        document.getElementById('finalAmtInput').value = '';
        showPage('homePage');
    };

    window.renderHistory = function() {
        const area = document.getElementById('orderArea');
        area.innerHTML = "লোড হচ্ছে...";

        onValue(ref(db, 'users/' + currentUser.nick), (snapshot) => {
            if(snapshot.exists()) {
                const u = snapshot.val();
                let history = [];

                if(u.orders) {
                    Object.values(u.orders).forEach(o => history.push(o));
                }

                if(u.deposits) {
                    Object.values(u.deposits).forEach(d => history.push(d));
                }

                area.innerHTML = history.length ? history.reverse().map(o => `
                    <div class="order-box">
                        <span class="status-badge st-${o.status}">${o.status}</span>
                        <b>${o.n || (o.method + ' Deposit')}</b> - ৳${o.p || o.price}<br>
                        <small>${o.date}</small>
                    </div>`).join('') : "কোন হিস্ট্রি নেই";
            } else {
                area.innerHTML = "কোন হিস্ট্রি নেই";
            }
        });
    };

    window.logout = function() {
        currentUser = null;
        localStorage.removeItem('userSessionNick'); // Clear session on logout
        showPage('loginPage');
    };
</script>
</body>
</html>
