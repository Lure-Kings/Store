<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lure Kings</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            background-color: #f5f5f5; 
            color: #333; 
            line-height: 1.4;
            max-width: 100vw;
            overflow-x: hidden;
        }
        
        /* Header */
        .header { 
            background-color: #1a365d; 
            padding: 0.3rem 0.5rem;
            position: sticky; 
            top: 0; 
            z-index: 1000; 
        }
        .nav { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
        }
        .logo { 
            font-size: 1rem; 
            font-weight: bold; 
            color: white;
        }
        .nav-buttons { 
            display: flex; 
            gap: 0.3rem; 
        }
        .btn { 
            padding: 0.3rem 0.6rem; 
            border: none; 
            border-radius: 3px; 
            font-size: 0.7rem; 
            font-weight: 600; 
        }
        .btn-secondary { 
            background-color: transparent; 
            color: white; 
            border: 1px solid white; 
        }
        .btn-primary { 
            background-color: #1a365d; 
            color: white; 
        }
        .cart-icon { 
            position: relative; 
        }
        .cart-count { 
            position: absolute; 
            top: -5px; 
            right: -5px; 
            background: #e74c3c; 
            color: white; 
            border-radius: 50%; 
            width: 15px; 
            height: 15px; 
            font-size: 0.6rem; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
        }
        
        /* Main Content */
        .container { 
            padding: 0.5rem; 
        }
        .hero { 
            text-align: center; 
            padding: 0.8rem 0.5rem; 
            margin-bottom: 0.8rem;
            background-color: white; 
            border-radius: 5px;
        }
        .hero h1 { 
            font-size: 1.1rem; 
            margin-bottom: 0.3rem; 
            color: #1a365d; 
        }
        .hero p { 
            font-size: 0.8rem; 
            color: #666; 
        }
        
        /* Categories */
        .categories { 
            display: flex; 
            flex-wrap: wrap; 
            gap: 0.3rem; 
            margin-bottom: 0.8rem; 
        }
        .category-btn { 
            padding: 0.3rem 0.6rem; 
            background: white; 
            border: 1px solid #ddd; 
            border-radius: 3px; 
            font-size: 0.7rem; 
        }
        .category-btn.active { 
            background: #1a365d; 
            color: white; 
        }
        
        /* Products */
        .products-grid { 
            display: grid; 
            grid-template-columns: 1fr; 
            gap: 0.8rem; 
            margin-bottom: 1rem; 
        }
        .product-card { 
            background: white; 
            border: 1px solid #ddd; 
            border-radius: 5px;
            overflow: hidden;
        }
        .product-image { 
            width: 100%; 
            height: 100px; 
            object-fit: cover; 
        }
        .product-info { 
            padding: 0.6rem; 
        }
        .product-title { 
            font-size: 0.8rem; 
            font-weight: bold; 
            margin-bottom: 0.2rem; 
        }
        .product-price { 
            font-size: 0.8rem; 
            color: #e74c3c; 
            margin-bottom: 0.3rem; 
        }
        .product-description { 
            font-size: 0.7rem; 
            color: #666; 
            margin-bottom: 0.5rem; 
        }
        .add-to-cart { 
            width: 100%; 
            padding: 0.3rem; 
            background-color: #1a365d; 
            color: white; 
            border: none; 
            border-radius: 3px; 
            font-size: 0.7rem; 
        }
        
        /* Modals */
        .modal { 
            display: none; 
            position: fixed; 
            top: 0; 
            left: 0; 
            width: 100%; 
            height: 100%; 
            background: rgba(0,0,0,0.5); 
            z-index: 2000; 
        }
        .modal-content { 
            position: absolute; 
            top: 50%; 
            left: 50%; 
            transform: translate(-50%, -50%); 
            background: white; 
            border-radius: 5px; 
            padding: 0.8rem; 
            width: 95%; 
            max-height: 90%; 
            overflow-y: auto; 
        }
        .close { 
            position: absolute; 
            top: 0.3rem; 
            right: 0.5rem; 
            font-size: 1.2rem; 
            cursor: pointer; 
        }
        
        /* Cart Items */
        .cart-item { 
            display: flex; 
            padding: 0.5rem 0; 
            border-bottom: 1px solid #eee; 
            align-items: center;
        }
        .cart-item img { 
            width: 40px; 
            height: 40px; 
            object-fit: cover; 
            margin-right: 0.5rem;
        }
        .cart-item-info { 
            flex-grow: 1;
        }
        .cart-item-name { 
            font-size: 0.8rem; 
            font-weight: bold; 
        }
        .cart-item-price { 
            font-size: 0.7rem; 
        }
        .cart-item-remove { 
            color: #c0392b; 
            font-size: 0.6rem; 
            text-decoration: none;
        }
        .cart-item-qty { 
            display: flex; 
            align-items: center; 
            gap: 0.3rem;
        }
        .cart-item-qty button { 
            width: 20px; 
            height: 20px; 
            border: 1px solid #ddd; 
            background: white; 
        }
        
        /* Admin View (hidden by default) */
        .hidden { display: none !important; }
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

    <div class="container">
        <div id="storeView">
            <div class="hero">
                <h1>Australian Owned</h1>
                <p>Serious value for anglers</p>
            </div>
            
            <div class="categories">
                <button class="category-btn active" onclick="filterByCategory('all')">All</button>
                <button class="category-btn" onclick="filterByCategory('jigs')">Jigs</button>
                <button class="category-btn" onclick="filterByCategory('soft-plastics')">Soft Plastics</button>
                <button class="category-btn" onclick="filterByCategory('topwaters')">Topwaters</button>
            </div>
            
            <div class="products-grid" id="productsGrid"></div>
        </div>

        <div id="adminView" class="hidden">
            <!-- Admin content will be generated here -->
        </div>
    </div>

    <!-- Cart Modal -->
    <div id="cartModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCart()">&times;</span>
            <h3>Shopping Cart</h3>
            <div id="cartItems"></div>
            <div style="text-align: right; padding: 0.5rem 0; font-weight: bold;">
                Total: $<span id="cartTotal">0.00</span>
            </div>
            <button class="btn btn-primary" onclick="showCheckout()" style="width: 100%;">Checkout</button>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="checkoutModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeCheckout()">&times;</span>
            <h3>Checkout</h3>
            <div style="background: #f8f9fa; padding: 0.5rem; margin: 0.5rem 0; border-left: 3px solid #1a365d;">
                DM for shipping prices
            </div>
            <div style="background: #f8f9fa; padding: 0.5rem; margin: 0.5rem 0; border-left: 3px solid #1a365d;">
                DM for direct transfer
            </div>
            <form id="checkoutForm" method="POST">
                <input type="hidden" name="_subject" value="New Order">
                <input type="hidden" name="_cc" value="lure.kings.fishing.aus@gmail.com">
                <input type="hidden" name="_next" value="">
                
                <div style="margin-bottom: 0.5rem;">
                    <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Full Name*</label>
                    <input type="text" required style="width: 100%; padding: 0.3rem; border: 1px solid #ddd;">
                </div>
                
                <div style="margin-bottom: 0.5rem;">
                    <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Email*</label>
                    <input type="email" required style="width: 100%; padding: 0.3rem; border: 1px solid #ddd;">
                </div>
                
                <div style="margin-bottom: 0.5rem;">
                    <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Address*</label>
                    <textarea required style="width: 100%; padding: 0.3rem; border: 1px solid #ddd; height: 60px;"></textarea>
                </div>
                
                <div style="margin-bottom: 0.5rem;">
                    <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Order Notes</label>
                    <textarea style="width: 100%; padding: 0.3rem; border: 1px solid #ddd; height: 40px;"></textarea>
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%;">Place Order</button>
            </form>
        </div>
    </div>

    <script>
    // Product database
    let products = [];
    
    // Cart and admin state
    let cart = [];
    let isAdminLoggedIn = false;
    const ADMIN_PASSWORD = "Maxchingershambo08";
    let currentFilter = 'all';
    
    // Initialize the app
    document.addEventListener('DOMContentLoaded', function() {
        loadCart();
        renderProducts();
        setupAdminView();
    });
    
    // Cart functions
    function loadCart() {
        const savedCart = localStorage.getItem('cart');
        if (savedCart) cart = JSON.parse(savedCart);
        updateCartCount();
    }
    
    function saveCart() {
        localStorage.setItem('cart', JSON.stringify(cart));
        updateCartCount();
    }
    
    function updateCartCount() {
        const count = cart.reduce((total, item) => total + item.quantity, 0);
        document.getElementById('cartCount').textContent = count;
    }
    
    function addToCart(productId) {
        const product = products.find(p => p.id === productId);
        if (!product) return;
        
        const existingItem = cart.find(item => item.id === productId);
        if (existingItem) {
            existingItem.quantity++;
        } else {
            cart.push({...product, quantity: 1});
        }
        
        saveCart();
    }
    
    function showCart() {
        const modal = document.getElementById('cartModal');
        const itemsContainer = document.getElementById('cartItems');
        const totalElement = document.getElementById('cartTotal');
        
        itemsContainer.innerHTML = '';
        
        if (cart.length === 0) {
            itemsContainer.innerHTML = '<p>Your cart is empty</p>';
        } else {
            let total = 0;
            
            cart.forEach(item => {
                total += item.price * item.quantity;
                
                const itemElement = document.createElement('div');
                itemElement.className = 'cart-item';
                itemElement.innerHTML = `
                    <img src="${item.image}">
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">$${item.price.toFixed(2)}</div>
                        <a href="#" onclick="removeFromCart(${item.id}); return false;" class="cart-item-remove">Remove</a>
                    </div>
                    <div class="cart-item-qty">
                        <button onclick="changeQuantity(${item.id}, -1)">-</button>
                        <span>${item.quantity}</span>
                        <button onclick="changeQuantity(${item.id}, 1)">+</button>
                    </div>
                `;
                
                itemsContainer.appendChild(itemElement);
            });
            
            totalElement.textContent = total.toFixed(2);
        }
        
        modal.style.display = 'block';
    }
    
    function closeCart() {
        document.getElementById('cartModal').style.display = 'none';
    }
    
    function changeQuantity(productId, change) {
        const item = cart.find(item => item.id === productId);
        if (!item) return;
        
        item.quantity += change;
        
        if (item.quantity <= 0) {
            cart = cart.filter(item => item.id !== productId);
        }
        
        saveCart();
        showCart(); // Refresh cart view
    }
    
    function removeFromCart(productId) {
        cart = cart.filter(item => item.id !== productId);
        saveCart();
        showCart(); // Refresh cart view
    }
    
    function showCheckout() {
        closeCart();
        document.getElementById('checkoutModal').style.display = 'block';
    }
    
    function closeCheckout() {
        document.getElementById('checkoutModal').style.display = 'none';
    }
    
    // Product rendering
    function renderProducts() {
        const grid = document.getElementById('productsGrid');
        grid.innerHTML = '';
        
        const filtered = currentFilter === 'all' 
            ? products 
            : products.filter(p => p.category === currentFilter);
            
        if (filtered.length === 0) {
            grid.innerHTML = '<p>No products found</p>';
            return;
        }
        
        filtered.forEach(product => {
            const card = document.createElement('div');
            card.className = 'product-card';
            card.innerHTML = `
                <img src="${product.image}" class="product-image">
                <div class="product-info">
                    <div class="product-title">${product.name}</div>
                    <div class="product-price">$${product.price.toFixed(2)}</div>
                    <div class="product-description">${product.description}</div>
                    <button class="add-to-cart" onclick="addToCart(${product.id})">Add to Cart</button>
                </div>
            `;
            
            grid.appendChild(card);
        });
    }
    
    function filterByCategory(category) {
        currentFilter = category;
        document.querySelectorAll('.category-btn').forEach(btn => {
            btn.classList.remove('active');
        });
        event.target.classList.add('active');
        renderProducts();
    }
    
    // Admin functions
    function setupAdminView() {
        const adminView = document.getElementById('adminView');
        
        // Setup admin login on logo click
        document.getElementById('logo').addEventListener('click', function() {
            if (++clickCount >= 5) {
                clickCount = 0;
                const password = prompt('Enter admin password:');
                if (password === ADMIN_PASSWORD) {
                    isAdminLoggedIn = true;
                    showAdminView();
                }
            }
        });
    }
    
    function showAdminView() {
        document.getElementById('storeView').classList.add('hidden');
        document.getElementById('adminView').classList.remove('hidden');
        
        const adminView = document.getElementById('adminView');
        adminView.innerHTML = `
            <div class="hero">
                <h1>Admin Panel</h1>
            </div>
            
            <div style="background: white; padding: 0.8rem; border-radius: 5px; margin-bottom: 0.8rem;">
                <h3>Add Product</h3>
                <form id="addProductForm" style="margin-top: 0.5rem;">
                    <div style="margin-bottom: 0.5rem;">
                        <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Name</label>
                        <input type="text" required style="width: 100%; padding: 0.3rem;">
                    </div>
                    
                    <div style="margin-bottom: 0.5rem;">
                        <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Category</label>
                        <select required style="width: 100%; padding: 0.3rem;">
                            <option value="jigs">Jigs</option>
                            <option value="soft-plastics">Soft Plastics</option>
                            <option value="topwaters">Topwaters</option>
                        </select>
                    </div>
                    
                    <div style="margin-bottom: 0.5rem;">
                        <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Price</label>
                        <input type="number" step="0.01" required style="width: 100%; padding: 0.3rem;">
                    </div>
                    
                    <div style="margin-bottom: 0.5rem;">
                        <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Description</label>
                        <textarea required style="width: 100%; padding: 0.3rem; height: 60px;"></textarea>
                    </div>
                    
                    <div style="margin-bottom: 0.5rem;">
                        <label style="display: block; margin-bottom: 0.2rem; font-size: 0.8rem;">Image URL</label>
                        <input type="text" required style="width: 100%; padding: 0.3rem;">
                    </div>
                    
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Add Product</button>
                </form>
            </div>
            
            <div style="background: white; padding: 0.8rem; border-radius: 5px;">
                <h3>Current Products</h3>
                <div id="adminProductsList" style="margin-top: 0.5rem;"></div>
            </div>
        `;
        
        renderAdminProducts();
        
        document.getElementById('addProductForm').addEventListener('submit', function(e) {
            e.preventDefault();
            // Add product logic here
        });
    }
    
    function renderAdminProducts() {
        const container = document.getElementById('adminProductsList');
        if (!container) return;
        
        container.innerHTML = '';
        
        products.forEach(product => {
            const productElement = document.createElement('div');
            productElement.style.marginBottom = '0.5rem';
            productElement.style.padding = '0.5rem';
            productElement.style.border = '1px solid #ddd';
            productElement.style.borderRadius = '3px';
            
            productElement.innerHTML = `
                <div style="display: flex; align-items: center; margin-bottom: 0.3rem;">
                    <img src="${product.image}" style="width: 40px; height: 40px; object-fit: cover; margin-right: 0.5rem;">
                    <div style="flex-grow: 1;">
                        <div style="font-weight: bold; font-size: 0.8rem;">${product.name}</div>
                        <div style="font-size: 0.7rem;">$${product.price.toFixed(2)}</div>
                    </div>
                    <button style="padding: 0.2rem 0.4rem; font-size: 0.7rem; background: #c0392b; color: white; border: none; border-radius: 3px;" onclick="deleteProduct(${product.id})">Delete</button>
                </div>
            `;
            
            container.appendChild(productElement);
        });
    }
    
    function showView(view) {
        if (view === 'admin' && !isAdminLoggedIn) return;
        
        document.getElementById('storeView').classList.toggle('hidden', view !== 'store');
        document.getElementById('adminView').classList.toggle('hidden', view !== 'admin');
    }
    </script>
</body>
</html>
