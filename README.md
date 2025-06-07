<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings - Premium Fishing Lures</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* All CSS remains the same */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f5f5f5; color: #333; line-height: 1.6; }
        .header { background-color: #1a365d; padding: 1rem 2rem; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .nav { display: flex; justify-content: space-between; align-items: center; max-width: 1200px; margin: 0 auto; }
        .logo { font-size: 2rem; font-weight: bold; color: white; display: flex; align-items: center; gap: 0.5rem; cursor: pointer; }
        #logoText { display: flex; align-items: center; gap: 0.5rem; }
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
        .product-card { background: white; border: 1px solid #ddd; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); display: flex; flex-direction: column; }
        .product-card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .product-image { width: 100%; height: 200px; object-fit: cover; border-bottom: 1px solid #ddd; }
        .product-info { padding: 1rem; flex-grow: 1; display: flex; flex-direction: column; }
        .product-title { font-size: 1.1rem; font-weight: bold; margin-bottom: 0.5rem; color: #1a365d; }
        .product-price { font-size: 1.2rem; font-weight: bold; color: #e74c3c; margin-bottom: 1rem; }
        .product-description { color: #666; margin-bottom: 1rem; font-size: 0.9rem; flex-grow: 1; }
        .add-to-cart { width: 100%; background-color: #1a365d; color: white; border: none; padding: 0.5rem; border-radius: 4px; cursor: pointer; font-weight: 600; transition: all 0.2s ease; margin-top: auto; }
        .add-to-cart:hover { background-color: #142a4a; }
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.5); z-index: 2000; }
        .modal-content { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background: white; border-radius: 8px; padding: 2rem; max-width: 90%; width: 600px; max-height: 90%; overflow-y: auto; box-shadow: 0 5px 15px rgba(0,0,0,0.2); color: #333; }
        .close { position: absolute; top: 1rem; right: 1rem; font-size: 1.5rem; cursor: pointer; color: #666; }
        .close:hover { color: #333; }
        .admin-form { background: white; border: 1px solid #ddd; padding: 1.5rem; border-radius: 8px; margin-bottom: 2rem; }
        .form-group { margin-bottom: 1rem; }
        .form-group label { display: block; margin-bottom: 0.5rem; font-weight: 600; color: #1a365d; }
        .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 0.5rem; border: 1px solid #ddd; border-radius: 4px; font-size: 1rem; }
        .hidden { display: none !important; }
        .toast { position: fixed; bottom: 20px; right: 20px; background: #1a365d; color: white; padding: 1rem; border-radius: 4px; box-shadow: 0 2px 10px rgba(0,0,0,0.2); z-index: 3000; opacity: 0; visibility: hidden; transition: opacity 0.3s, visibility 0.3s; }
        .toast.show { opacity: 1; visibility: visible; }
        #exportData { width: 100%; height: 250px; font-family: monospace; margin-top: 1rem; white-space: pre; overflow-wrap: normal; overflow-x: scroll; }
        .admin-note { background-color: #eef2f7; border-left: 4px solid #1a365d; padding: 1rem; margin-bottom: 1rem; border-radius: 4px; }
        .image-preview-container { margin-top: 1rem; }
        .image-preview { max-width: 200px; max-height: 200px; border-radius: 8px; border: 1px solid #ddd; }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <div class="logo" id="logo">
                <span id="logoText">Lure Kings</span>
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
            <div class="products-grid" id="productsGrid"></div>
        </div>

        <div id="adminView" class="hidden"></div>
    </div>

    <div id="cartModal" class="modal"></div>
    <div id="checkoutModal" class="modal"></div>
    
    <script>
    // #############################################################################
    // ####################  START OF YOUR PRODUCT DATABASE  #######################
    // #############################################################################
    
    // This is the permanent list of products for your website.
    // To update it, use the Admin Panel's "Code Generator" and paste the
    // new code block here, replacing this one.
    
    let products = [
      {
        "id": 1,
        "name": "Bass Pro Jig Head",
        "category": "jigs",
        "price": 12.99,
        "description": "Premium jig head perfect for bass fishing with realistic action.",
        "image": "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop"
      },
      {
        "id": 2,
        "name": "Soft Plastic Worm",
        "category": "soft-plastics",
        "price": 8.49,
        "description": "Lifelike soft plastic worm that attracts fish with its natural movement.",
        "image": "https://images.unsplash.com/photo-1559827260-dc66d52bef19?w=400&h=300&fit=crop"
      }
    ];
    
    // #############################################################################
    // #####################  END OF YOUR PRODUCT DATABASE  ########################
    // #############################################################################


    // --- GLOBAL STATE ---
    let isAdminLoggedIn = false;
    const ADMIN_PASSWORD = "Maxchingershambo08";
    let clickCount = 0;
    let clickTimeout;
    let cart = [];
    let currentFilter = 'all';
    let tempProductImage = null; // Holds Base64 image data for the form

    // --- APP INITIALIZATION ---
    document.addEventListener('DOMContentLoaded', init);

    function init() {
        const storedCart = localStorage.getItem('cart');
        cart = storedCart ? JSON.parse(storedCart) : [];

        createAdminView();
        createModals();
        renderProducts();
        updateCartCount();
        renderAdminProducts();
        setupEventListeners();
    }

    function createModals() {
        document.getElementById('cartModal').innerHTML = `<div class="modal-content"><span class="close" onclick="closeCart()">&times;</span><h2 style="margin-bottom: 1rem; color: #1a365d;">Shopping Cart</h2><div id="cartItems"></div><div class="cart-total" id="cartTotalDisplay">Total: $0.00</div><button class="btn btn-primary" onclick="showCheckout()" style="width: 100%; margin-top: 1rem;">Proceed to Checkout</button></div>`;
        document.getElementById('checkoutModal').innerHTML = `<div class="modal-content"><span class="close" onclick="closeCheckout()">&times;</span><h2 style="margin-bottom: 1rem; color: #1a365d;">Secure Checkout</h2><p>Checkout functionality is currently under development.</p></div>`;
    }

    function createAdminView() {
        const adminViewContainer = document.getElementById('adminView');
        adminViewContainer.innerHTML = `
            <div class="hero"><h1>Admin: Product Manager</h1></div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;" id="form-title">Add New Product</h2>
                <form id="productForm">
                    <input type="hidden" id="productId">
                    <div class="form-group"><label for="productName">Product Name</label><input type="text" id="productName" required></div>
                    <div class="form-group"><label for="productCategory">Category</label><select id="productCategory" required><option value="">Select Category</option><option value="jigs">Jigs</option><option value="soft-plastics">Soft Plastics</option><option value="topwaters">Topwaters</option><option value="spinnerbaits">Spinnerbaits</option></select></div>
                    <div class="form-group"><label for="productPrice">Price ($)</label><input type="number" id="productPrice" step="0.01" min="0" required></div>
                    <div class="form-group"><label for="productDescription">Description</label><textarea id="productDescription" rows="3" required></textarea></div>
                    <div class="form-group">
                        <label for="productImageFile">Upload Image From Computer</label>
                        <input type="file" id="productImageFile" accept="image/*">
                        <div class="image-preview-container"><img id="imagePreview" class="image-preview" style="display:none;"></div>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;" id="save-btn">Add Product to List</button>
                    <button type="button" class="btn btn-secondary" style="width: 100%; margin-top: 10px; display: none;" id="cancel-edit-btn" onclick="cancelEdit()">Cancel Edit</button>
                </form>
            </div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Final Step: Generate Code to Update Website</h2>
                <div class="admin-note">
                    <p>After managing your product list below, click the button to generate the final code. You must copy this code and paste it into the "PRODUCT DATABASE" section in your <strong>index.html</strong> file to make your changes live for everyone.</p>
                </div>
                <button onclick="generateProductCode()" class="btn btn-primary" style="width:100%; margin: 1rem 0;">Generate & Copy Final Product Code</button>
                <textarea id="exportData" readonly placeholder="Your generated code will appear here..."></textarea>
            </div>
            <div class="admin-form">
                <h2 style="margin-bottom: 1rem; color: #1a365d;">Current Product List</h2>
                <div id="adminProductsList"></div>
            </div>
        `;
    }

    function setupEventListeners() {
        document.getElementById('logo').addEventListener('click', handleLogoClick);
        document.getElementById('productForm').addEventListener('submit', handleFormSubmit);
        document.getElementById('productImageFile').addEventListener('change', handleImageFileChange);
    }
    
    function handleLogoClick() {
        clickCount++;
        clearTimeout(clickTimeout);
        clickTimeout = setTimeout(() => { clickCount = 0; }, 1500);
        if (clickCount >= 5) {
            clickCount = 0;
            showAdminLogin();
        }
    }

    function handleImageFileChange(event) {
        const file = event.target.files[0];
        if (!file) {
            tempProductImage = null;
            document.getElementById('imagePreview').style.display = 'none';
            return;
        }
        const reader = new FileReader();
        reader.onload = function(e) {
            tempProductImage = e.target.result; // This is the Base64 string
            const preview = document.getElementById('imagePreview');
            preview.src = tempProductImage;
            preview.style.display = 'block';
        }
        reader.readAsDataURL(file);
    }
    
    function handleFormSubmit(e) {
        e.preventDefault();
        const idInput = document.getElementById('productId').value;
        const id = idInput ? parseInt(idInput) : null;

        const newProductData = {
            id: id || Date.now(),
            name: document.getElementById('productName').value,
            category: document.getElementById('productCategory').value,
            price: parseFloat(document.getElementById('productPrice').value),
            description: document.getElementById('productDescription').value,
            image: tempProductImage, // Use the Base64 data from the uploaded file
        };

        if (!newProductData.name || !newProductData.category || isNaN(newProductData.price) || !newProductData.image) {
            alert('Please fill all fields and upload an image.');
            return;
        }

        const index = products.findIndex(p => p.id === id);

        if (index > -1) {
            products[index] = newProductData;
        } else {
            products.push(newProductData);
        }
        
        renderProducts();
        renderAdminProducts();
        cancelEdit(); // Resets the form
        showToast(id ? 'Product updated in the list!' : 'Product added to the list!');
    }

    function editProduct(id) {
        const product = products.find(p => p.id === id);
        if (!product) return;

        document.getElementById('form-title').innerText = 'Edit Product';
        document.getElementById('save-btn').innerText = 'Save Changes to List';
        document.getElementById('cancel-edit-btn').style.display = 'block';

        document.getElementById('productId').value = product.id;
        document.getElementById('productName').value = product.name;
        document.getElementById('productCategory').value = product.category;
        document.getElementById('productPrice').value = product.price;
        document.getElementById('productDescription').value = product.description;
        
        const preview = document.getElementById('imagePreview');
        preview.src = product.image;
        preview.style.display = 'block';
        tempProductImage = product.image; // IMPORTANT: Pre-fill the image data

        document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' });
    }

    function cancelEdit() {
        document.getElementById('form-title').innerText = 'Add New Product';
        document.getElementById('save-btn').innerText = 'Add Product to List';
        document.getElementById('cancel-edit-btn').style.display = 'none';
        document.getElementById('productForm').reset();
        document.getElementById('productId').value = '';
        document.getElementById('imagePreview').style.display = 'none';
        tempProductImage = null;
    }

    function deleteProduct(id) {
        if (!confirm('Are you sure you want to remove this product from the list?')) return;
        products = products.filter(p => p.id !== id);
        renderProducts();
        renderAdminProducts();
        showToast('Product removed from the list.');
    }

    function generateProductCode() {
        const exportTextArea = document.getElementById('exportData');
        const productCode = `let products = ${JSON.stringify(products, null, 2)};`;
        exportTextArea.value = productCode;
        exportTextArea.select();
        try {
            document.execCommand('copy');
            showToast('Final code copied to clipboard!');
        } catch (err) {
            showToast('Could not copy automatically. Please copy manually.');
        }
    }

    function showToast(message) {
        const t = document.getElementById('toast');
        t.textContent = message;
        t.classList.add('show');
        setTimeout(() => { t.classList.remove('show'); }, 3000);
    }
    
    // --- RENDER AND UTILITY FUNCTIONS ---
    function renderProducts() { const grid = document.getElementById('productsGrid'); if (!grid) return; grid.innerHTML = ''; const filtered = currentFilter === 'all' ? products : products.filter(p => p.category === currentFilter); if (filtered.length === 0) { grid.innerHTML = '<p>No products found in this category.</p>'; return; } filtered.forEach(p => { const card = document.createElement('div'); card.className = 'product-card'; card.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><div class="product-price">$${p.price.toFixed(2)}</div><p class="product-description">${p.description}</p><button class="add-to-cart" onclick="addToCart(${p.id})">Add to Cart</button></div>`; grid.appendChild(card); }); }
    function renderAdminProducts() { const cont = document.getElementById('adminProductsList'); if (!cont) return; cont.innerHTML = ''; if (!products.length) { cont.innerHTML = '<p>No products in the list.</p>'; return; } [...products].slice().reverse().forEach(p => { const el = document.createElement('div'); el.className = 'product-card'; el.innerHTML = `<img src="${p.image}" alt="${p.name}" class="product-image"><div class="product-info"><h3 class="product-title">${p.name}</h3><div style="margin-top:1rem; display: flex; gap: 10px;"><button onclick="editProduct(${p.id})" class="btn btn-secondary" style="flex:1;">Edit</button><button onclick="deleteProduct(${p.id})" class="btn btn-danger" style="flex:1;">Remove</button></div></div>`; cont.appendChild(el); }); }
    function showView(view) { if (view === 'admin' && !isAdminLoggedIn) { showAdminLogin(); return; } document.getElementById('storeView').classList.toggle('hidden', view !== 'store'); document.getElementById('adminView').classList.toggle('hidden', view !== 'admin'); }
    function filterByCategory(category) { currentFilter = category; renderProducts(); document.querySelectorAll('.category-btn').forEach(btn => { btn.classList.remove('active'); const btnText = btn.textContent.toLowerCase().replace(' ', '-'); if (btnText.includes(category) || (category === 'all' && btnText.includes('all'))) { btn.classList.add('active'); } }); }
    function addToCart(productId) { const product = products.find(p => p.id === productId); if (!product) return; const item = cart.find(i => i.id === productId); if (item) { item.quantity++; } else { cart.push({...product, quantity: 1}); } localStorage.setItem('cart', JSON.stringify(cart)); updateCartCount(); showToast(`${product.name} added to cart`); }
    function updateCartCount() { document.getElementById('cartCount').textContent = cart.reduce((t, i) => t + i.quantity, 0); }
    function showCart() { updateCartDisplay(); document.getElementById('cartModal').style.display = 'block'; }
    function closeCart() { document.getElementById('cartModal').style.display = 'none'; }
    function showCheckout() { updateCheckoutDisplay(); document.getElementById('checkoutModal').style.display = 'block'; closeCart();}
    function closeCheckout() { document.getElementById('checkoutModal').style.display = 'none'; }
    function showAdminLogin() { const pw = prompt("Enter admin password:"); if (pw === ADMIN_PASSWORD) { isAdminLoggedIn = true; showView('admin'); } else if (pw !== null) { alert('Incorrect password!'); } }
    function updateCartDisplay() { const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0); const cartItemsEl = document.getElementById('cartItems'); if (cartItemsEl) { cartItemsEl.innerHTML = cart.length ? cart.map(item => `<div class="cart-item" style="display:flex; align-items:center; gap:1rem; padding:1rem; border-bottom:1px solid #ddd;"><img src="${item.image}" style="width:60px; height:60px; object-fit:cover;"><div style="flex-grow:1;"><div style="font-weight:bold;">${item.name}</div><div>$${item.price.toFixed(2)}</div></div><div>x ${item.quantity}</div></div>`).join('') : '<p>Your cart is empty.</p>'; document.getElementById('cartTotalDisplay').textContent = `Total: $${total.toFixed(2)}`; }}
    function updateCheckoutDisplay() { /* Future implementation */ }
    
    </script>
</body>
</html>
