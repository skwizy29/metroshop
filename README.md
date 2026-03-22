# metroshop
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <meta name="theme-color" content="#0a0f1e">
    <title>SkwizyShop | Metro Royale — Покупка предметов и сопровождение</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: radial-gradient(circle at 10% 20%, #0a0f1e, #03060c);
            color: #eef2ff;
            padding: 12px;
            min-height: 100vh;
            font-family: system-ui, -apple-system, 'Segoe UI', 'Poppins', 'Inter', 'Roboto', sans-serif;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        /* Header - улучшенная адаптация */
        .header {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 16px;
            margin-bottom: 20px;
            background: rgba(10, 20, 30, 0.75);
            backdrop-filter: blur(12px);
            border-radius: 2rem;
            padding: 12px 20px;
            border: 1px solid rgba(255, 215, 0, 0.3);
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
        }

        .logo h1 {
            font-size: clamp(1.4rem, 5vw, 2rem);
            background: linear-gradient(135deg, #F5AF19, #f0c45a);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 0.5px;
        }
        .logo p {
            font-size: 0.7rem;
            color: #b9c7d9;
        }

        .cart-icon {
            background: #11161f;
            padding: 8px 16px;
            border-radius: 40px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: all 0.2s;
            border: 1px solid #2a3a44;
            touch-action: manipulation;
        }
        .cart-icon:active { transform: scale(0.97); }
        .cart-count {
            background: #f5b81b;
            color: #0a0c15;
            font-weight: bold;
            border-radius: 30px;
            padding: 2px 10px;
            font-size: 0.9rem;
            min-width: 28px;
            text-align: center;
        }
        .cart-price {
            font-weight: 600;
            background: #00000066;
            padding: 4px 12px;
            border-radius: 32px;
            font-size: 0.9rem;
        }

        /* Support bar - мобильная адаптация */
        .support-bar {
            display: flex;
            justify-content: flex-end;
            margin-bottom: 16px;
            gap: 10px;
            flex-wrap: wrap;
        }
        .support-card {
            background: rgba(15, 23, 34, 0.85);
            backdrop-filter: blur(8px);
            padding: 6px 14px;
            border-radius: 50px;
            font-size: 0.75rem;
            border: 1px solid #f5b81b55;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }
        .phone-num, .card-number {
            font-weight: bold;
            color: #f5c542;
            font-family: monospace;
            font-size: 0.8rem;
        }
        .copy-btn {
            background: #2a3a44;
            border: none;
            padding: 4px 10px;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-size: 0.65rem;
            touch-action: manipulation;
        }
        .copy-btn:active { background: #f5b81b; color: #000; }

        /* Products grid - адаптивная сетка */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin: 24px 0;
        }

        .product-card {

Сиська, [23.03.2026 01:45]
background: linear-gradient(145deg, #11171f, #0b1017);
            border-radius: 1.5rem;
            overflow: hidden;
            transition: all 0.2s ease;
            border: 1px solid #2a3743;
            cursor: pointer;
        }
        .product-card:active { transform: scale(0.98); }
        .product-img {
            height: 150px;
            background: #1f2a33;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            border-bottom: 1px solid #2f3e4a;
        }
        .product-info {
            padding: 1rem;
        }
        .product-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 6px;
        }
        .product-category {
            font-size: 0.65rem;
            text-transform: uppercase;
            background: #1e2a32;
            display: inline-block;
            padding: 2px 10px;
            border-radius: 20px;
            color: #cddcec;
            margin-bottom: 8px;
        }
        .product-desc {
            font-size: 0.8rem;
            color: #b0c4de;
            margin: 8px 0;
            line-height: 1.3;
        }
        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #f5c542;
            margin: 10px 0;
        }
        .btn-add {
            background: #f5b81b;
            border: none;
            width: 100%;
            padding: 12px;
            font-weight: bold;
            font-size: 0.95rem;
            border-radius: 60px;
            color: #0b0f17;
            cursor: pointer;
            transition: 0.1s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            touch-action: manipulation;
        }
        .btn-add:active {
            background: #ffce4a;
            transform: scale(0.97);
        }

        /* Modal cart */
        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(8px);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        .cart-modal.active { display: flex; }
        .cart-panel {
            background: #0e141f;
            width: 92%;
            max-width: 650px;
            max-height: 88vh;
            border-radius: 1.8rem;
            padding: 1.2rem;
            border: 1px solid #ffd966;
            overflow-y: auto;
            box-shadow: 0 30px 40px black;
        }

        /* Payment modal */
        .payment-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.96);
            backdrop-filter: blur(12px);
            z-index: 1100;
            justify-content: center;
            align-items: center;
        }
        .payment-modal.active { display: flex; }
        .payment-panel {
            background: linear-gradient(145deg, #111a24, #0a0f18);
            width: 92%;
            max-width: 480px;
            border-radius: 2rem;
            padding: 1.5rem;
            border: 1px solid #f5c542;
            text-align: center;
        }
        .payment-panel h2 {
            color: #f5c542;
            margin-bottom: 16px;
            font-size: 1.6rem;
        }
        .payment-amount {
            font-size: 2rem;
            font-weight: bold;
            background: #00000055;
            padding: 12px;
            border-radius: 1.2rem;
            margin: 16px 0;
            color: #ffdf8c;
        }
        .payment-card-details {
            background: #071017;
            border-radius: 1rem;
            padding: 16px;
            margin: 16px 0;
            border: 1px solid #f5b81b55;
        }
        .payment-card-number {
            font-size: 1.

Сиська, [23.03.2026 01:45]
3rem;
            font-family: monospace;
            font-weight: bold;
            letter-spacing: 1px;
            background: #00000066;
            padding: 10px;
            border-radius: 1rem;
            margin: 10px 0;
            color: #ffde9c;
            word-break: break-all;
        }
        .payment-support {
            background: #1a2530;
            border-radius: 1rem;
            padding: 10px;
            margin: 12px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        .copy-big-btn, .paid-btn, .close-payment-btn {
            border: none;
            padding: 12px 20px;
            border-radius: 60px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.1s;
            touch-action: manipulation;
        }
        .copy-big-btn { background: #f5b81b; color: #0a0c15; margin-top: 8px; }
        .paid-btn { background: #27ae60; color: white; width: 100%; margin-top: 12px; font-size: 1rem; }
        .close-payment-btn { background: #2c3e44; color: white; margin-top: 12px; width: 100%; }
        .copy-big-btn:active, .paid-btn:active, .close-payment-btn:active { transform: scale(0.97); }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #2d3e4e;
            padding-bottom: 12px;
            margin-bottom: 16px;
        }
        .close-cart {
            background: none;
            border: none;
            font-size: 2rem;
            cursor: pointer;
            color: #f0c45a;
            padding: 0 8px;
        }
        .cart-items-list {
            max-height: 45vh;
            overflow-y: auto;
            margin: 12px 0;
        }
        .cart-item {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            background: #0a111a;
            margin: 8px 0;
            padding: 10px;
            border-radius: 1rem;
            border-left: 4px solid #f5b81b;
            gap: 8px;
        }
        .item-info h4 { font-size: 0.9rem; }
        .item-price { font-weight: bold; color: #f5c542; font-size: 0.9rem; }
        .item-actions button {
            background: #2c3e44;
            border: none;
            color: white;
            font-weight: bold;
            width: 32px;
            height: 32px;
            border-radius: 30px;
            margin: 0 3px;
            cursor: pointer;
            font-size: 1rem;
        }
        .cart-total {
            text-align: right;
            font-size: 1.3rem;
            border-top: 1px solid #2e4a5a;
            padding-top: 12px;
            margin-top: 8px;
        }
        .payment-section {
            background: #071017;
            border-radius: 1.2rem;
            padding: 1rem;
            margin-top: 16px;
        }
        .pay-methods {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin: 12px 0;
        }
        .method-btn {
            background: #1b2a33;
            border: none;
            padding: 8px 14px;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-size: 0.85rem;
            touch-action: manipulation;
        }
        .method-btn.active {
            background: #f5b81b;
            color: #0a0c15;
            font-weight: bold;
        }
        .order-btn {
            background: #27ae60;
            width: 100%;
            padding: 12px;
            font-weight: bold;
            border: none;
            border-radius: 60px;
            font-size: 1rem;
            color: white;
            cursor: pointer;
            margin-top: 12px;
        }
        .toast-msg {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: #1f2c38e6;

Сиська, [23.03.2026 01:45]
backdrop-filter: blur(12px);
            padding: 10px 20px;
            border-radius: 60px;
            color: #ffdf8c;
            font-weight: bold;
            z-index: 1200;
            border-left: 4px solid gold;
            pointer-events: none;
            font-size: 0.85rem;
            text-align: center;
            max-width: 90vw;
        }
        .empty-cart {
            text-align: center;
            padding: 30px 20px;
            color: #9aaec2;
        }
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 16px;
            font-size: 0.7rem;
            opacity: 0.7;
        }
        button { cursor: pointer; }
        
        @media (max-width: 550px) {
            body { padding: 8px; }
            .header { padding: 10px 16px; }
            .product-title { font-size: 1rem; }
            .product-price { font-size: 1.3rem; }
            .cart-item { flex-direction: column; align-items: flex-start; }
            .item-actions { align-self: flex-end; }
            .payment-card-number { font-size: 1rem; }
            .support-card { font-size: 0.7rem; padding: 4px 12px; }
        }
        
        /* Для планшетов */
        @media (min-width: 768px) and (max-width: 1024px) {
            .products-grid { grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 18px; }
        }
        
        /* Стили для скролла */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #1e2a32; border-radius: 10px; }
        ::-webkit-scrollbar-thumb { background: #f5b81b; border-radius: 10px; }
    </style>
</head>
<body>
<div class="container">
    <div class="support-bar">
        <div class="support-card">
            <span>📞</span> Поддержка: <span class="phone-num">+79997818232</span>
            <button class="copy-btn" data-copy="+79997818232">📋</button>
        </div>
        <div class="support-card">
            <span>💳</span> Карта: <span class="card-number">2200701230844117</span>
            <button class="copy-btn" data-copy="2200701230844117">📋</button>
        </div>
    </div>

    <div class="header">
        <div class="logo">
            <h1>⚡ SKWIZYSHOP</h1>
            <p>Metro Royale • Сопровождение • Оружие • Реликвии</p>
        </div>
        <div class="cart-icon" id="openCartBtn">
            <span>🛒</span>
            <span class="cart-count" id="cartCount">0</span>
            <span class="cart-price" id="cartTotalPreview">0₽</span>
        </div>
    </div>

    <div class="products-grid" id="productsGrid"></div>
    <footer>© SkwizyShop — официальный трансфер Metro Royale. Мгновенная доставка после подтверждения оплаты.</footer>
</div>

<!-- Корзина -->
<div id="cartModal" class="cart-modal">
    <div class="cart-panel">
        <div class="cart-header">
            <h2>🧾 Корзина</h2>
            <button class="close-cart" id="closeCartBtn">&times;</button>
        </div>
        <div id="cartItemsContainer" class="cart-items-list"></div>
        <div class="cart-total" id="cartTotalAmount">Итого: 0₽</div>
        <div class="payment-section">
            <h3>💳 Способ оплаты</h3>
            <div class="pay-methods" id="payMethodsContainer">
                <button data-method="card" class="method-btn active">💳 Карта</button>
                <button data-method="qiwi" class="method-btn">🟣 QIWI</button>
                <button data-method="crypto" class="method-btn">₿ Crypto</button>
            </div>
            <div id="paymentInfoMsg" style="font-size:0.75rem; margin: 6px 0; color:#c0d4f0;">💳 Оплата картой 2200701230844117</div>
            <button class="order-btn" id="checkoutBtn">✅ Оформить заказ</button>
        </div>
    </div>
</div>

<!-- Модалка оплаты -->
<div id="paymentModal" class="payment-modal">
    <div class="payment-panel">
        <h2>💸 ОПЛАТА</h2>
        <p>Переведите сумму на карту</p>
        <div class="payment-amount" id="paymentAmountDisplay">0 ₽</div>
        <div class="payment-card-details">

Сиська, [23.03.2026 01:45]
<span>💳 Карта получателя:</span>
            <div class="payment-card-number">2200701230844117</div>
            <button class="copy-big-btn" id="copyCardFromPayment">📋 Копировать карту</button>
        </div>
        <div class="payment-support">
            <span>📞 Поддержка:</span>
            <strong>+79997818232</strong>
            <button class="copy-btn" data-copy="+79997818232" style="background:#1f2a33;">Копировать</button>
        </div>
        <p style="font-size:0.7rem; margin: 8px 0;">После оплаты нажмите "Я оплатил(а)"</p>
        <button class="paid-btn" id="confirmPaymentBtn">✅ Я оплатил(а)</button>
        <button class="close-payment-btn" id="closePaymentBtn">✖️ Закрыть</button>
    </div>
</div>

<div id="toast" class="toast-msg" style="display: none;"></div>

<script>
    (function(){
        // Товары: первые 3 - дешевые сопроводы
        const PRODUCTS = [
            { id: 1, name: "🛡️ Сопровод 'Стальной Страж'", category: "Сопровождение", desc: "Опытный телохранитель на 1 рейд", price: 199, icon: "🛡️" },
            { id: 2, name: "🔍 Сопровод 'Теневой Разведчик'", category: "Сопровождение", desc: "Сканирует тайники, 2 рейда", price: 299, icon: "🔍" },
            { id: 3, name: "⚡ Сопровод 'Быстрый Курьер'", category: "Сопровождение", desc: "Ускоряет сбор лута", price: 249, icon: "⚡" },
            { id: 4, name: "MK14 'Метро Легенда'", category: "Оружие", desc: "Винтовка + бронепробитие", price: 1290, icon: "🔫" },
            { id: 5, name: "Бронекостюм 'Стальной Шторм'", category: "Снаряжение", desc: "Lv.6 броня + шлем", price: 890, icon: "🛡️" },
            { id: 6, name: "Рюкзак 'Сектор 7'", category: "Снаряжение", desc: "+ защита от мародеров", price: 490, icon: "🎒" },
            { id: 7, name: "Аптечка 'Феникс' x5", category: "Расходники", desc: "Мгновенное восстановление", price: 350, icon: "💊" },
            { id: 8, name: "M762 'Золотой Тигр'", category: "Оружие", desc: "Легендарный скин + урон", price: 1590, icon: "🐅" },
            { id: 9, name: "Подавитель нового поколения", category: "Модули", desc: "+15% урона, бесшумный", price: 720, icon: "🔇" },
            { id: 10, name: "Баллистический щит", category: "Снаряжение", desc: "Экзощит для штурма", price: 1100, icon: "🛡️" },
            { id: 11, name: "Редкий ящик 'Метро Реликвия'", category: "Контейнер", desc: "Легендарный лут", price: 2490, icon: "🎁" }
        ];

        let cart = [];
        let currentPaymentMethod = "card";
        let pendingOrderTotal = 0;

        // Загрузка из localStorage
        function loadCart() {
            try {
                const saved = localStorage.getItem("skwizy_cart_v2");
                if(saved) {
                    cart = JSON.parse(saved);
                    if(!Array.isArray(cart)) cart = [];
                }
            } catch(e) { cart = []; }
            cart = cart.filter(item => item && typeof item.id === 'number' && item.quantity > 0);
            updateBadge();
        }

        function saveCart() {
            localStorage.setItem("skwizy_cart_v2", JSON.stringify(cart));
            updateBadge();
        }

        function updateBadge() {
            const count = cart.reduce((s, i) => s + i.quantity, 0);
            const total = cart.reduce((s, i) => s + (i.price * i.quantity), 0);
            document.getElementById('cartCount').innerText = count;
            document.getElementById('cartTotalPreview').innerHTML = total + "₽";
        }

        function getTotal() {
            return cart.reduce((s, i) => s + (i.price * i.quantity), 0);
        }

        function showToast(msg, dur = 2200) {
            const toast = document.getElementById('toast');
            toast.innerText = msg;
            toast.style.display = 'block';
            setTimeout(() => { toast.style.display = 'none'; }, dur);
        }

        function addToCart(product) {
            const existing = cart.find(i => i.id === product.id);
            if(existing) existing.quantity++;
            else cart.push({ id: product.id, name: product.name, price: product.

Сиська, [23.03.2026 01:45]
price, quantity: 1 });
            saveCart();
            showToast(`✅ ${product.name.split(' ').slice(0,3).join(' ')} + в корзину`, 1300);
            if(document.getElementById('cartModal').classList.contains('active')) renderCartModal();
        }

        function updateQty(id, delta) {
            const idx = cart.findIndex(i => i.id === id);
            if(idx === -1) return;
            const newQty = cart[idx].quantity + delta;
            if(newQty <= 0) cart.splice(idx,1);
            else cart[idx].quantity = newQty;
            saveCart();
            renderCartModal();
            if(cart.length === 0 && document.getElementById('cartModal').classList.contains('active')) renderCartModal();
        }

        function renderCartModal() {
            const container = document.getElementById('cartItemsContainer');
            if(!container) return;
            if(cart.length === 0) {
                container.innerHTML = '<div class="empty-cart">🛒 Корзина пуста. Добавьте сопровождение или снаряжение!</div>';
                document.getElementById('cartTotalAmount').innerHTML = 'Итого: 0₽';
                return;
            }
            let html = '<ul style="list-style:none;">';
            cart.forEach(item => {
                const itemTotal = item.price * item.quantity;
                html += `<li class="cart-item">
                    <div class="item-info"><h4>${item.name}</h4><small>${item.price}₽ × ${item.quantity}</small></div>
                    <div class="item-price">${itemTotal}₽</div>
                    <div class="item-actions">
                        <button class="qty-minus" data-id="${item.id}">−</button>
                        <span style="margin:0 6px;">${item.quantity}</span>
                        <button class="qty-plus" data-id="${item.id}">+</button>
                        <button class="qty-remove" data-id="${item.id}" style="background:#aa2e2e;">🗑</button>
                    </div>
                </li>`;
            });
            html += '</ul>';
            container.innerHTML = html;
            document.getElementById('cartTotalAmount').innerHTML = Итого: ${getTotal()}₽;

            document.querySelectorAll('.qty-plus').forEach(btn => btn.onclick = () => updateQty(parseInt(btn.dataset.id), 1));
            document.querySelectorAll('.qty-minus').forEach(btn => btn.onclick = () => updateQty(parseInt(btn.dataset.id), -1));
            document.querySelectorAll('.qty-remove').forEach(btn => btn.onclick = () => {
                const id = parseInt(btn.dataset.id);
                const idx = cart.findIndex(i => i.id === id);
                if(idx !== -1) cart.splice(idx,1);
                saveCart();
                renderCartModal();
                updateBadge();
            });
        }

        function openPaymentModal(amount) {
            pendingOrderTotal = amount;
            document.getElementById('paymentAmountDisplay').innerHTML = ${amount} ₽;
            document.getElementById('paymentModal').classList.add('active');
        }

        function closePaymentModal() {
            document.getElementById('paymentModal').classList.remove('active');
            pendingOrderTotal = 0;
        }

        function confirmPayment() {
            if(pendingOrderTotal <= 0) {
                showToast("Нет активного заказа", 1200);
                closePaymentModal();
                return;
            }
            // Очищаем корзину
            cart = [];
            saveCart();
            updateBadge();
            renderCartModal();
            closePaymentModal();
            const cartModal = document.getElementById('cartModal');
            if(cartModal.classList.contains('active')) cartModal.classList.remove('active');
            showToast(`✅ Оплата ${pendingOrderTotal}₽ подтверждена! Предметы доставлены в игру. Спасибо!`, 4500);
            pendingOrderTotal = 0;
        }

        function processOrder() {
            if(cart.length === 0) {
                showToast("⚠️ Корзина пуста! Добавьте товары.", 1800);
                return;

Сиська, [23.03.2026 01:45]
}
            const total = getTotal();
            let methodText = currentPaymentMethod === 'card' ? 'Банковская карта' : (currentPaymentMethod === 'qiwi' ? 'QIWI' : 'Криптовалюта');
            // Закрываем корзину
            document.getElementById('cartModal').classList.remove('active');
            openPaymentModal(total);
            showToast(`💸 Заказ на ${total}₽. Оплатите по реквизитам. Способ: ${methodText}`, 3500);
        }

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            if(!grid) return;
            grid.innerHTML = '';
            PRODUCTS.forEach(prod => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.innerHTML = `
                    <div class="product-img">${prod.icon}</div>
                    <div class="product-info">
                        <div class="product-title">${prod.name}</div>
                        <div class="product-category">${prod.category}</div>
                        <div class="product-desc">${prod.desc}</div>
                        <div class="product-price">${prod.price} ₽</div>
                        <button class="btn-add" data-id="${prod.id}">➕ В корзину</button>
                    </div>
                `;
                grid.appendChild(card);
                const btn = card.querySelector('.btn-add');
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    addToCart(prod);
                });
            });
        }

        function initEventListeners() {
            // Корзина
            document.getElementById('openCartBtn').onclick = () => {
                renderCartModal();
                document.getElementById('cartModal').classList.add('active');
            };
            document.getElementById('closeCartBtn').onclick = () => document.getElementById('cartModal').classList.remove('active');
            document.getElementById('cartModal').onclick = (e) => { if(e.target === document.getElementById('cartModal')) e.target.classList.remove('active'); };
            document.getElementById('checkoutBtn').onclick = processOrder;
            
            // Оплата
            document.getElementById('closePaymentBtn').onclick = closePaymentModal;
            document.getElementById('confirmPaymentBtn').onclick = confirmPayment;
            document.getElementById('paymentModal').onclick = (e) => { if(e.target === document.getElementById('paymentModal')) closePaymentModal(); };
            document.getElementById('copyCardFromPayment').onclick = () => {
                navigator.clipboard.writeText('2200701230844117').then(() => showToast('💳 Номер карты скопирован!', 1200));
            };
            
            // Способы оплаты
            const methods = document.querySelectorAll('.method-btn');
            methods.forEach(btn => {
                btn.onclick = () => {
                    methods.forEach(m => m.classList.remove('active'));
                    btn.classList.add('active');
                    currentPaymentMethod = btn.dataset.method;
                    const msg = document.getElementById('paymentInfoMsg');
                    if(currentPaymentMethod === 'card') msg.innerHTML = '💳 Оплата картой 2200701230844117';
                    else if(currentPaymentMethod === 'qiwi') msg.innerHTML = '🟣 Оплата через QIWI на карту 2200701230844117';
                    else msg.innerHTML = '₿ Криптовалюта USDT, реквизиты в поддержке';
                };
            });
            
            // Кнопки копирования
            document.querySelectorAll('.copy-btn').forEach(btn => {
                btn.onclick = (e) => {
                    e.stopPropagation();
                    const text = btn.getAttribute('data-copy');
                    if(text) navigator.clipboard.writeText(text).then(() => showToast(`📋 Скопировано`, 1000));
                };
            });
        }

        function init() {
            loadCart();

Сиська, [23.03.2026 01:45]
renderProducts();
            initEventListeners();
            console.log("SkwizyShop v2 — адаптирован для GitHub Pages и мобильных устройств");
        }
        
        init();
    })();
</script>
</body>
</html>
