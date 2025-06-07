<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* [Your existing CSS remains unchanged] */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f5f5f5; color: #333; line-height: 1.6; }
        .header { background-color: #1a365d; padding: 1rem 2rem; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .nav { display: flex; justify-content: space-between; align-items: center; max-width: 1200px; margin: 0 auto; }
        .logo { font-size: 2rem; font-weight: bold; color: white; display: flex; align-items: center; gap: 0.5rem; cursor: pointer; }
        #mainHeaderLogo { max-height: 50px; display: none; }
        #logoText { display: flex; align-items: center; gap: 0.5rem; }
        /* Crown icon style removed as it's no longer in the HTML */
        .nav-buttons { display: flex; gap: 1rem; align-items: center; }
        .btn { padding: 0.5rem 1rem; border: none; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; }
        .btn-primary { background-color: #1a365d; color: white; }
        .btn-secondary { background-color: transparent; color: white; border: 1px solid white; }
        .btn-danger { background-color: #c0392b; color: white; }
        .btn:hover { opacity: 0.9; }
        .cart-icon { position: relative; }
        .cart-count { position: absolute; top: -8px; right: -8px; background: #e74c3c; color: white; border-radius: 50%; width: 20px; height: 20px; display: flex; align-items: center; justify-content: center; font-size: 0.75rem; font-weight: bold; }
        .container { max-width: 1200px; margin: 2rem auto; padding: 0 1rem; }
        .hero { text-align: center; margin-bottom: 3rem; padding: 2rem 0; background-color: white; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .hero h1 { font-size: 2.5rem; margin-bottom: 1rem; color: #1a365d; }
        .hero p { font-size: 1.1rem; max-width: 600px; margin: 0 auto; color: #666; }
        .categories { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 2rem; justify-content: center; }
        .category-btn { padding: 0.5rem 1rem; background: white; border: 1px solid #ddd; border-radius: 4px; cursor: pointer; transition: all 0.2s ease; }
        .category-btn:hover, .category-btn.active { background: #1a365d; border-color: #1a365d; color: white; }
        .products-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.5rem; margin-bottom: 3rem; }
        .product-card { background: white; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); transition: all 0.2s ease; }
        .product-card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .product-image { width: 100%; height: 200px; object-fit: cover; border-bottom: 1px solid #ddd; }
        .product-info { padding: 1rem; }
        .product-title { font-size: 1.1rem; font-weight: bold; margin-bottom: 0.5rem; color: #1a365d; }
        .product-price { font-size: 1.2rem; font-weight: bold; color: #e74c3c; margin-bottom: 1rem; }
        .product-description { color: #666; margin-bottom: 1rem; font-size: 0.9rem; }
        .add-to-cart { width: 100%; background-color: #1a365d; color: white; border: none; padding: 0.5rem; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; }
        .add-to-cart:hover { background-color: #142a4a; }
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); z-index: 2000; }
        .modal-content { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background: white; border-radius: 8px; padding: 2rem; max-width: 90%; width: 600px; max-height: 90%; overflow-y: auto; box-shadow: 0 5px 15px rgba(0,0,0,0.2); color: #333; }
        .close { position: absolute; top: 1rem; right: 1rem; font-size: 1.5rem; cursor: pointer; color: #666; }
        .close:hover { color: #333; }
        .admin-form { background: white; border: 1px solid #ddd; padding: 1.5rem; border-radius: 8px; margin-bottom: 2rem; }
        .form-group { margin-bottom: 1rem; }
        .form-group label { display: block; margin-bottom: 0.5rem; font-weight: 600; color: #1a365d; }
        .hidden { display: none !important; }
        .toast { position: fixed; bottom: 20px; right: 20px; background: #1a365d; color: white; padding: 1rem; border-radius: 4px; box-shadow: 0 2px 10px rgba(0,0,0,0.2); z-index: 3000; opacity: 0; visibility: hidden; transition: opacity 0.3s, visibility 0.3s; }
        .toast.show { opacity: 1; visibility: visible; }
        #exportData { width: 100%; height: 200px; font-family: monospace; margin-top: 1rem; }
        .admin-note { background-color: #eef2f7; border-left: 4px solid #1a365d; padding: 1rem; margin-bottom: 1rem; border-radius: 4px; }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo" id="logo">
                <img id="mainHeaderLogo" alt="Company Logo">
                <span id="logoText">
                    Lure Kings
                </span>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-secondary" onclick="showView('store')">Store</button>
                <button class="btn btn-primary cart-icon" onclick="showCart()">
                    <i class="fas fa-shopping-cart"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </button>
            </div>
        </nav>
    </header>

    <div class="toast" id="toast"></div>

    <div class="container">
        <div id="storeView">
            <div class="hero">
                <h1>Australian Owned and Operated</h1>
                <p>Serious value for serious anglers</p>
            </div>
             <div class="categories">
                <button class="category-btn active" onclick="filterByCategory('all')">All Lures</button>
                <button class="category-btn" onclick="filterByCategory('jigs')">Jigs</button>
                <button class="category-btn" onclick="filterByCategory('soft-plastics')">Soft Plastics</button>
                <button class="category-btn" onclick="filterByCategory('topwaters')">Topwaters</button>
                <button class="category-btn" onclick="filterByCategory('spinnerbaits')">Spinnerbaits</button>
            </div>
            <div class="products-grid" id="productsGrid">
                <p>Loading products...</p>
            </div>
        </div>

        <div id="adminView" class="hidden">
            </div>
    </div>

    <div id="cartModal" class="modal"></div>
    <div id="checkoutModal" class="modal"></div>
    
    <script>
    // --- GLOBAL STATE ---
    let isAdminLoggedIn = false;
    const ADMIN_PASSWORD = "Maxchingershambo08";
    let clickCount = 0;
    let clickTimeout;
    let products = []; // Master product list. Populated from LIVE data or DRAFT data.
    let cart = [];
    let currentFilter = 'all';

    // --- APP INITIALIZATION ---
    document.addEventListener('DOMContentLoaded', init);

    async function init() {
        let liveProducts = [];
        try {
            const response = await fetch('products.json?v=' + Date.now());
            if (!response.ok) throw new Error('Network response was not ok.');
            liveProducts = await response.json();
        } catch (error) {
            console.error('Failed to fetch live products:', error);
            document.getElementById('productsGrid').innerHTML = '<p>Error loading products. Please try again later.</p>';
        }

        const productDrafts = localStorage.getItem('productDrafts');
        
        if (productDrafts) {
            products = JSON.parse(productDrafts);
        } else {
            products = liveProducts;
        }

        const storedCart = localStorage.getItem('cart');
        cart = storedCart ? JSON.parse(storedCart) : [];

        const savedLogo = localStorage.getItem('companyLogo');
        if (savedLogo) {
            applyLogo(savedLogo);
        }
        
        createAdminView();
        renderProducts();
        updateCartCount();
        renderAdminProducts();
        
        setupEventListeners();

        const urlParams = new URLSearchParams(window.location.search);
        if (urlParams.has('order') && urlParams.get('order') === 'success') {
            showToast("Thank you! Your order has been placed successfully.");
            window.history.replaceState({}, document.title, window.location.pathname);
        }
    }

    function createAdminView() {
        document.getElementById('cartModal').innerHTML = `<div class="modal-content"><span class="close" onclick="closeCart()">&times;</span><h2 style="margin-bottom: 1rem; color: #1a365d;">Shopping Cart</h2><div id="cartItems"></div><div class="cart-total" id="cartTotalDisplay">Total: $0.00</div><button class="btn btn-primary" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">Proceed to Checkout</button></div>`;
        
        const adminViewContainer = document.getElementById('adminView');
        adminViewContainer.innerHTML = `
            <div class="hero"><h1>Admin Dashboard</h1><p>Manage your Lure Kings inventory</p></div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Step 1: Edit Your Product Drafts</h2>
                <div class="admin-note">
                    <p>All changes you make here (adding, editing, deleting) are saved as a <strong>DRAFT</strong> on this computer only. They will NOT be visible to customers until you complete Step 2.</p>
                </div>
                <form id="productForm">
                    <input type="hidden" id="productId">
                    <div class="form-group"><label for="productName">Product Name</label><input type="text" id="productName" required></div>
                    <div class="form-group"><label for="productCategory">Category</label><select id="productCategory" required><option value="">Select Category</option><option value="jigs">Jigs</option><option value="soft-plastics">Soft Plastics</option><option value="topwaters">Topwaters</option><option value="spinnerbaits">Spinnerbaits</option></select></div>
                    <div class="form-group"><label for="productPrice">Price ($)</label><input type="number" id="productPrice" step="0.01" min="0" required></div>
                    <div class="form-group"><label for="productDescription">Description</label><textarea id="productDescription" rows="3" required></textarea></div>
                    <div class="form-group"><label for="productImage">Image URL</label><input type="text" id="productImageURL" placeholder="Enter image URL" required></div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Save Product to Draft</button>
                </form>
            </div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Step 2: Publish Your Drafts</h2>
                 <div class="admin-note">
                    <p>When you are happy with your drafts, click the button below to generate the data. You must then copy this data and paste it into the <strong>products.json</strong> file on GitHub to make your changes live for everyone.</p>
                </div>
                <button onclick="exportProducts()" class="btn btn-primary" style="width:100%; margin: 1rem 0;">Generate & Copy Publish Data</button>
                <textarea id="exportData" readonly placeholder="Your generated JSON data will appear here..."></textarea>
                <button onclick="discardDrafts()" class="btn btn-danger" style="width:100%; margin-top: 1rem;">Discard All Drafts & Reload</button>
            </div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Current Product Drafts</h2>
                <div id="adminProductsList"></div>
            </div>
        `;
    }

    function setupEventListeners() {
        // MODIFICATION: The event listener is now on the main logo element
        document.getElementById('logo').addEventListener('click', handleLogoClick);
        if (document.getElementById('productForm')) {
            document.getElementById('productForm').addEventListener('submit', function(e) {
                e.preventDefault();
                saveProduct();
            });
        }
    }
    
    // NEW: Replaces handleCrownClick. Triggers admin login.
    function handleLogoClick() {
        clickCount++;
        clearTimeout(clickTimeout);
        clickTimeout = setTimeout(() => {
            clickCount = 0;
        }, 1500); // 1.5 second window to complete the clicks

        if (clickCount >= 5) { // Increased to 5 clicks for security
            clickCount = 0;
            showAdminLogin();
        }
    }
    
    function applyLogo(logoUrl) {
        const mainLogoImg = document.getElementById('mainHeaderLogo');
        mainLogoImg.src = logoUrl;
        mainLogoImg.style.display = 'block';
    }

    function discardDrafts() {
        if (confirm("Are you sure? This will delete all your unsaved drafts and reload the page with the current live data from the website.")) {
            localStorage.removeItem('productDrafts');
            showToast('Drafts discarded. Reloading...');
            setTimeout(() => location.reload(), 1500);
        }
    }

    function exportProducts() {
        const exportTextArea = document.getElementById('exportData');
        exportTextArea.value = JSON.stringify(products, null, 2);
        exportTextArea.select();
        try {
            document.execCommand('copy');
            showToast('Publish data copied to clipboard!');
        } catch (err) {
            showToast('Could not copy automatically. Please copy manually.');
        }
    }
    
    function saveProduct() {
        const idInput = document.getElementById('productId').value;
        const id = idInput ? parseInt(idInput) : null;

        const newProductData = {
            id: id || Date.now(),
            name: document.getElementById('productName').value,
            category: document.getElementById('productCategory').value,
            price: parseFloat(document.getElementById('productPrice').value),
            description: document.getElementById('productDescription').value,
            image: document.getElementById('productImageURL').value,
        };

        if (!newProductData.name || !newProductData.category || isNaN(newProductData.price) || !newProductData.description || !newProductData.image) {
            alert('Please fill all required fields.');
            return;
        }

        const index = products.findIndex(p => p.id === id);

        if (index > -1) {
            products[index] = newProductData;
        } else {
            products.push(newProductData);
        }
        
        localStorage.setItem('productDrafts', JSON.stringify(products));

        renderProducts();
        renderAdminProducts();
        
        document.getElementById('productForm').reset();
        document.getElementById('productId').value = '';
        showToast(id ? 'Product draft updated!' : 'Product draft added!');
    }

    function deleteProduct(id) {
        if (!confirm('Are you sure you want to delete this product from your draft?')) return;
        products = products.filter(p => p.id !== id);
        
        localStorage.setItem('productDrafts', JSON.stringify(products));

        renderProducts();
        renderAdminProducts();
        showToast('Product draft deleted. Export to publish the change.');
    }

    function editProduct(id) {
        const p = products.find(prod => prod.id === id);
        if (!p) return;
        document.getElementById('productId').value = p.id;
        document.getElementById('productName').value = p.name;
        document.getElementById('productCategory').value = p.category;
        document.getElementById('productPrice').value = p.price;
        document.getElementById('productDescription').value = p.description;
        document.getElementById('productImageURL').value = p.image;
        document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' });
    }

    function showToast(message) {
        const t = document.getElementById('toast');
        t.textContent = message;
        t.classList.add('show');
        setTimeout(() => { t.classList.remove('show'); }, 3000);
    }
    
    function renderProducts() { const grid = document.getElementById('productsGrid'); if (!grid) return; grid.innerHTML = ''; const filtered = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter); if (filtered.length === 0) { grid.innerHTML = '<p>No products found in this category.</p>'; return; } filtered.forEach(p => { const card = document.createElement('div'); card.className = 'product-card'; card.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><div class="product-price">$${p.price.toFixed(2)}</div><p class="product-description">${p.description}</p><button class="add-to-cart" onclick="addToCart(${p.id})">Add to Cart</button></div>`; grid.appendChild(card); }); }
    function renderAdminProducts() { const cont = document.getElementById('adminProductsList'); if (!cont) return; cont.innerHTML = ''; if (!products.length) { cont.innerHTML = '<p>No product drafts.</p>'; return; } [...products].slice().reverse().forEach(p => { const el = document.createElement('div'); el.className = 'product-card'; el.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><p style="font-size:0.9em;color:#666">${p.category}</p><p style="font-weight:bold;color:#e74c3c">$${p.price.toFixed(2)}</p><div style="margin-top:1rem; display: flex; gap: 10px;"><button onclick="editProduct(${p.id})" class="btn btn-secondary" style="flex:1;">Edit</button><button onclick="deleteProduct(${p.id})" class="btn btn-danger" style="flex:1;">Delete</button></div></div>`; cont.appendChild(el); }); }
    function saveCartToStorage() { localStorage.setItem('cart', JSON.stringify(cart)); }
    function showView(view) { if (view === 'admin' && !isAdminLoggedIn) { showAdminLogin(); return; } document.getElementById('storeView').classList.toggle('hidden', view !== 'store'); document.getElementById('adminView').classList.toggle('hidden', view !== 'admin'); }
    function filterByCategory(category) { currentFilter = category; renderProducts(); document.querySelectorAll('.category-btn').forEach(btn => { btn.classList.remove('active'); const btnText = btn.textContent.toLowerCase().replace(' ', '-'); if (btnText.includes(category) || (category === 'all' && btnText.includes('all'))) { btn.classList.add('active'); } }); }
    function addToCart(productId) { const product = products.find(p => p.id === productId); if (!product) return; const item = cart.find(i => i.id === productId); if (item) { item.quantity++; } else { cart.push({...product, quantity: 1}); } saveCartToStorage(); updateCartCount(); showToast(`${product.name} added to cart`); }
    function updateCartCount() { document.getElementById('cartCount').textContent = cart.reduce((t, i) => t + i.quantity, 0); }
    function showCart() { updateCartDisplay(); document.getElementById('cartModal').style.display = 'block'; }
    function closeCart() { document.getElementById('cartModal').style.display = 'none'; }
    function showAdminLogin() { const pw = prompt("Enter admin password:"); if (pw === ADMIN_PASSWORD) { isAdminLoggedIn = true; showView('admin'); } else if (pw !== null) { alert('Incorrect password!'); } }
    function updateCartDisplay() { const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0); const cartItemsEl = document.getElementById('cartItems'); if (cartItemsEl) { cartItemsEl.innerHTML = cart.length ? cart.map(item => `<div class="cart-item"><img src="${item.image}" alt="${item.name}"><div class="cart-item-info"><div class="cart-item-title">${item.name}</div><div>$${item.price.toFixed(2)} each</div><div class="quantity-controls"><button class="quantity-btn" onclick="updateCartItem(${item.id}, -1)">-</button><span>${item.quantity}</span><button class="quantity-btn" onclick="updateCartItem(${item.id}, 1)">+</button></div></div><div><div style="font-weight: bold; text-align: right;">$${(item.price * item.quantity).toFixed(2)}</div><button class="remove-item" style="margin-top: 5px;" onclick="removeFromCart(${item.id})">Remove</button></div></div>`).join('') : '<p>Your cart is empty.</p>'; document.getElementById('cartTotalDisplay').textContent = `Total: $${total.toFixed(2)}`; }}
    function updateCartItem(productId, change) { const item = cart.find(i => i.id === productId); if (item) { item.quantity += change; if (item.quantity <= 0) { cart = cart.filter(i => i.id !== productId); } } saveCartToStorage(); updateCartCount(); updateCartDisplay(); }
    function removeFromCart(productId) { cart = cart.filter(item => item.id !== productId); saveCartToStorage(); updateCartCount(); updateCartDisplay(); }
    function showCheckout() { /* show checkout modal logic */ }
    
    </script>
</body>
</html>
