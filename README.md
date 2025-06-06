<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lure Kings - Premium Fishing Store</title>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Georgia', serif;
    background-color: #e6f0fa;
    color: #1e3a8a;
    line-height: 1.6;
}

.header {
    background: linear-gradient(135deg, #1e3a8a 0%, #60a5fa 100%);
    color: white;
    padding: 1.5rem 2rem;
    position: sticky;
    top: 0;
    z-index: 1000;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.header-content {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    display: flex;
    align-items: center;
    gap: 12px;
    font-size: 1.8rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
}

.logo svg {
    width: 30px;
    height: 30px;
    fill: #93c5fd;
    cursor: pointer;
    transition: transform 0.3s ease;
}

.logo svg:hover {
    transform: scale(1.1);
}

.cart-icon {
    position: relative;
    cursor: pointer;
    font-size: 1.2rem;
}

.cart-count {
    position: absolute;
    top: -8px;
    right: -8px;
    background: #1e40af;
    color: white;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    font-size: 0.7rem;
    display: flex;
    align-items: center;
    justify-content: center;
}

.hero {
    background: linear-gradient(rgba(30, 58, 138, 0.8), rgba(96, 165, 250, 0.8)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><rect fill="%231e3a8a" width="1200" height="600"/><path fill="%23ffffff" opacity="0.1" d="M0,300 Q300,200 600,300 T1200,300 V600 H0 Z"/></svg>');
    color: white;
    padding: 5rem 2rem;
    text-align: center;
}

.hero h1 {
    font-size: 3.5rem;
    margin-bottom: 1.5rem;
    font-weight: 700;
}

.hero p {
    font-size: 1.3rem;
    margin-bottom: 2rem;
    max-width: 800px;
    margin-left: auto;
    margin-right: auto;
}

.filters {
    max-width: 1280px;
    margin: 2rem auto;
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    justify-content: center;
}

.filter-btn {
    background: #bfdbfe;
    color: #1e3a8a;
    border: none;
    padding: 0.5rem 1.5rem;
    border-radius: 20px;
    cursor: pointer;
    font-size: 0.9rem;
    transition: background 0.3s, color 0.3s;
}

.filter-btn.active, .filter-btn:hover {
    background: #1e3a8a;
    color: white;
}

.main-content {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
}

.product-grid {
    display: flex;
    overflow-x: auto;
    gap: 2rem;
    margin-top: 2rem;
    padding-bottom: 1rem;
    scroll-behavior: smooth;
}

.product-grid::-webkit-scrollbar {
    height: 8px;
}

.product-grid::-webkit-scrollbar-thumb {
    background: #60a5fa;
    border-radius: 4px;
}

.product-grid::-webkit-scrollbar-track {
    background: #bfdbfe;
}

.product-card {
    background: white;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    flex: 0 0 300px;
}

.product-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(0,0,0,0.12);
}

.product-images {
    position: relative;
    height: 220px;
    overflow: hidden;
}

.product-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: none;
}

.product-image.active {
    display: block;
}

.image-nav {
    position: absolute;
    bottom: 12px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 6px;
}

.image-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: rgba(255,255,255,0.6);
    cursor: pointer;
    transition: background 0.3s;
}

.image-dot.active {
    background: white;
}

.product-info {
    padding: 1.5rem;
}

.product-title {
    font-size: 1.2rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #1e3a8a;
}

.product-price {
    font-size: 1.3rem;
    font-weight: 700;
    color: #2563eb;
    margin-bottom: 1rem;
}

.rating {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 1rem;
}

.stars {
    display: flex;
    gap: 3px;
}

.star {
    color: #93c5fd;
}

.rating-text {
    font-size: 0.9rem;
    color: #4b5e8e;
}

.add-to-cart-btn {
    width: 100%;
    background: #1e3a8a;
    color: white;
    border: none;
    padding: 12px;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 600;
    transition: background 0.3s;
}

.add-to-cart-btn:hover {
    background: #60a5fa;
}

.modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.6);
    z-index: 2000;
}

.modal-content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    padding: 2rem;
    border-radius: 8px;
    max-width: 90%;
    max-height: 90%;
    overflow-y: auto;
}

.admin-panel {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

.form-group {
    margin-bottom: 1.5rem;
}

.form-group label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: 600;
    color: #1e3a8a;
}

.form-group input, .form-group textarea, .form-group select {
    width: 100%;
    padding: 12px;
    border: 1px solid #bfdbfe;
    border-radius: 6px;
    font-size: 1rem;
}

.form-group input:focus, .form-group textarea:focus, .form-group select:focus {
    outline: none;
    border-color: #1e3a8a;
}

.btn {
    background: #1e3a8a;
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 600;
    transition: background 0.3s;
    margin-right: 12px;
}

.btn:hover {
    background: #60a5fa;
}

.btn-danger {
    background: #1e40af;
}

.btn-danger:hover {
    background: #3b82f6;
}

.notification {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #2563eb;
    color: white;
    padding: 1rem 2rem;
    border-radius: 6px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    transform: translateX(400px);
    transition: transform 0.3s ease;
    z-index: 3000;
}

.notification.show {
    transform: translateX(0);
}

.cart-sidebar {
    position: fixed;
    top: 0;
    right: -400px;
    width: 400px;
    height: 100%;
    background: white;
    box-shadow: -2px 0 10px rgba(0,0,0,0.1);
    transition: right 0.3s ease;
    z-index: 2000;
    overflow-y: auto;
}

.cart-sidebar.open {
    right: 0;
}

.cart-header {
    background: #1e3a8a;
    color: white;
    padding: 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.cart-items {
    padding: 1.5rem;
}

.cart-item {
    display: flex;
    gap: 1rem;
    padding: 1rem 0;
    border-bottom: 1px solid #bfdbfe;
}

.cart-item img {
    width: 70px;
    height: 70px;
    object-fit: cover;
    border-radius: 6px;
}

.cart-item-info {
    flex: 1;
}

.shipping-calculator {
    background: #e6f0fa;
    padding: 1.5rem;
    border-radius: 6px;
    margin: 1rem 0;
}

.checkout-section {
    padding: 1.5rem;
    border-top: 2px solid #bfdbfe;
}

.reviews-section {
    margin-top: 2rem;
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

.review-item {
    padding: 1rem 0;
    border-bottom: 1px solid #bfdbfe;
}

.review-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.5rem;
}

.hidden {
    display: none;
}

@media (max-width: 768px) {
    .header-content {
        flex-direction: column;
        gap: 1.5rem;
    }

    .hero h1 {
        font-size: 2.5rem;
    }

    .product-grid {
        flex-direction: row;
    }

    .cart-sidebar {
        width: 100%;
        right: -100%;
    }

    .filters {
        flex-direction: column;
        align-items: center;
    }
}
</style>
</head>
<body>
<!-- Header -->
<header class="header">
    <div class="header-content">
        <div class="logo">
            <svg onclick="handleLogoClick()" viewBox="0 0 24 24">
                <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm5-9h-3V7h-2v4H7v2h5v4h2v-4h3z"/>
            </svg>
            <span>Lure Kings</span>
        </div>
        <div class="cart-icon" onclick="toggleCart()">
            🛒
            <span class="cart-count" id="cartCount">0</span>
        </div>
    </div>
</header>

<!-- Hero Section -->
<section class="hero" id="home">
    <h1>Premium Fishing Equipment</h1>
    <p>Elevate your fishing experience with our curated selection of high-quality lures, rods, and tackle</p>
</section>

<!-- Filters -->
<div class="filters">
    <button class="filter-btn active" onclick="filterProducts('all')">All</button>
    <button class="filter-btn" onclick="filterProducts('jigs')">Jigs</button>
    <button class="filter-btn" onclick="filterProducts('soft-plastics')">Soft Plastics</button>
    <button class="filter-btn" onclick="filterProducts('topwaters')">Topwaters</button>
    <button class="filter-btn" onclick="filterProducts('spinnerbaits')">Spinnerbaits</button>
    <button class="filter-btn" onclick="filterProducts('vibrating-jigs')">Vibrating/Bladed Jigs</button>
    <button class="filter-btn" onclick="filterProducts('crankbaits')">Crankbaits</button>
    <button class="filter-btn" onclick="filterProducts('jerkbaits')">Jerkbaits</button>
    <button class="filter-btn" onclick="filterProducts('swimbaits')">Swimbaits</button>
    <button class="filter-btn" onclick="filterProducts('flies')">Flies</button>
    <button class="filter-btn" onclick="filterProducts('line')">Line</button>
    <button class="filter-btn" onclick="filterProducts('rods')">Rods</button>
    <button class="filter-btn" onclick="filterProducts('reels')">Reels</button>
</div>

<!-- Main Content -->
<main class="main-content">
    <div id="customer-view">
        <div class="product-grid" id="productGrid"></div>

        <!-- Reviews Section -->
        <div class="reviews-section" id="reviewsSection">
            <h3>Customer Reviews</h3>
            <div class="rating">
                <div class="stars" id="overallRating"></div>
                <span class="rating-text" id="overallRatingText"></span>
            </div>
            <div id="reviewsList"></div>

            <h4 style="margin-top: 2rem;">Leave a Review</h4>
            <form id="reviewForm">
                <div class="form-group">
                    <label>Your Name</label>
                    <input type="text" id="reviewerName" required>
                </div>
                <div class="form-group">
                    <label>Rating</label>
                    <select id="reviewRating" required>
                        <option value="">Select Rating</option>
                        <option value="5">5 Stars</option>
                        <option value="4">4 Stars</option>
                        <option value="3">3 Stars</option>
                        <option value="2">2 Stars</option>
                        <option value="1">1 Star</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Review</label>
                    <textarea id="reviewText" rows="4" required></textarea>
                </div>
                <button type="submit" class="btn">Submit Review</button>
            </form>
        </div>
    </div>

    <!-- Admin Panel -->
    <div id="admin-panel" class="admin-panel hidden">
        <h2>Admin Panel - Lure Kings</h2>
        <div style="margin-bottom: 2rem;">
            <button class="btn" onclick="showSection('product-management')">Product Management</button>
            <button class="btn" onclick="showSection('order-management')">Order Management</button>
            <button class="btn" onclick="showSection('review-management')">Review Management</button>
            <button class="btn" onclick="showCustomerView()">Back to Store</button>
        </div>

        <!-- Product Management -->
        <div id="product-management" class="admin-section">
            <h3>Add New Product</h3>
            <form id="productForm">
                <div class="form-group">
                    <label>Product Name</label>
                    <input type="text" id="productName" required>
                </div>
                <div class="form-group">
                    <label>Price (AUD)</label>
                    <input type="number" id="productPrice" step="0.01" required>
                </div>
                <div class="form-group">
                    <label>Description</label>
                    <textarea id="productDescription" rows="3" required></textarea>
                </div>
                <div class="form-group">
                    <label>Category</label>
                    <select id="productCategory" required>
                        <option value="">Select Category</option>
                        <option value="jigs">Jigs</option>
                        <option value="soft-plastics">Soft Plastics</option>
                        <option value="topwaters">Topwaters</option>
                        <option value="spinnerbaits">Spinnerbaits</option>
                        <option value="vibrating-jigs">Vibrating/Bladed Jigs</option>
                        <option value="crankbaits">Crankbaits</option>
                        <option value="jerkbaits">Jerkbaits</option>
                        <option value="swimbaits">Swimbaits</option>
                        <option value="flies">Flies</option>
                        <option value="line">Line</option>
                        <option value="rods">Rods</option>
                        <option value="reels">Reels</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Product Images</label>
                    <input type="file" id="productImageFiles" accept="image/*" multiple>
                </div>
                <button type="submit" class="btn">Add Product</button>
            </form>

            <h3 style="margin-top: 2rem;">Existing Products</h3>
            <div id="adminProductList"></div>
        </div>

        <!-- Order Management -->
        <div id="order-management" class="admin-section hidden">
            <h3>Recent Orders</h3>
            <div id="ordersList"></div>
        </div>

        <!-- Review Management -->
        <div id="review-management" class="admin-section hidden">
            <h3>Manage Reviews</h3>
            <div id="adminReviewsList"></div>
        </div>
    </div>
</main>

<!-- Cart Sidebar -->
<div class="cart-sidebar" id="cartSidebar">
    <div class="cart-header">
        <h3>Shopping Cart</h3>
        <button onclick="toggleCart()" style="background: none; border: none; color: white; font-size: 1.5rem; cursor: pointer;">×</button>
    </div>
    <div class="cart-items" id="cartItems"></div>
    <div class="shipping-calculator">
        <h4>Shipping Calculator</h4>
        <select id="shippingZone" onchange="calculateShipping()">
            <option value="">Select your location</option>
            <option value="inner">Inner City - $5.00</option>
            <option value="metro">Metro Area - $10.00</option>
            <option value="regional">Regional - $15.00</option>
            <option value="interstate">Interstate - $15.00</option>
        </select>
        <div id="shippingCost" style="margin-top: 10px; font-weight: bold;"></div>
    </div>
    <div class="checkout-section">
        <div id="cartTotal" style="font-size: 1.2rem; font-weight: bold; margin-bottom: 1rem;"></div>
        <button class="btn" onclick="proceedToCheckout()" style="width: 100%;">Proceed to Checkout</button>
    </div>
</div>

<!-- Checkout Modal -->
<div class="modal" id="checkoutModal">
    <div class="modal-content">
        <h2>Checkout</h2>
        <form id="checkoutForm">
            <div class="form-group">
                <label>Full Name</label>
                <input type="text" id="customerName" required>
            </div>
            <div class="form-group">
                <label>Email</label>
                <input type="email" id="customerEmail" required>
            </div>
            <div class="form-group">
                <label>Phone</label>
                <input type="tel" id="customerPhone" required>
            </div>
            <div class="form-group">
                <label>Shipping Address</label>
                <textarea id="shippingAddress" rows="3" required></textarea>
            </div>
            <div class="form-group">
                <label>Payment Method</label>
                <select id="paymentMethod" required>
                    <option value="">Select Payment Method</option>
                    <option value="stripe">Credit Card (Stripe)</option>
                    <option value="paypal">PayPal</option>
                    <option value="bank">Bank Transfer</option>
                </select>
            </div>
            <div id="orderSummary" style="background: #e6f0fa; padding: 1rem; border-radius: 6px; margin: 1rem 0;"></div>
            <div style="display: flex; gap: 1rem;">
                <button type="submit" class="btn">Complete Order</button>
                <button type="button" class="btn" onclick="closeCheckout()">Cancel</button>
            </div>
        </form>
    </div>
</div>

<!-- Admin Password Modal -->
<div class="modal" id="adminPasswordModal">
    <div class="modal-content">
        <h2>Admin Access</h2>
        <form id="adminPasswordForm">
            <div class="form-group">
                <label>Password</label>
                <input type="password" id="adminPassword" required>
            </div>
            <div style="display: flex; gap: 1rem;">
                <button type="submit" class="btn">Submit</button>
                <button type="button" class="btn" onclick="closeAdminPasswordModal()">Cancel</button>
            </div>
        </form>
    </div>
</div>

<!-- Notification -->
<div class="notification" id="notification"></div>

<script>
// Global variables
let products = JSON.parse(localStorage.getItem('products')) || [
    {
        id: 1,
        name: "Premium Spinnerbait Lure Set",
        price: 29.99,
        description: "High-quality spinnerbait lures perfect for bass fishing. Includes 6 different colors.",
        category: "spinnerbaits",
        images: ["data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23e6f3ff' width='200' height='150'/><circle fill='%23ff6b35' cx='100' cy='75' r='30'/><text x='100' y='130' text-anchor='middle' font-family='Arial' font-size='12' fill='%23333'>Spinnerbait Lure</text></svg>", "data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23fff0e6' width='200' height='150'/><circle fill='%23ff6b35' cx='100' cy='75' r='25'/><text x='100' y='130' text-anchor='middle' font-family='Arial' font-size='12' fill='%23333'>Side View</text></svg>"],
        reviews: []
    },
    {
        id: 2,
        name: "Carbon Fiber Fishing Rod",
        price: 159.99,
        description: "Ultra-lightweight carbon fiber rod with excellent sensitivity. Perfect for all fishing conditions.",
        category: "rods",
        images: ["data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23e6f3ff' width='200' height='150'/><line x1='20' y1='130' x2='180' y2='20' stroke='%23333' stroke-width='8'/><text x='100' y='140' text-anchor='middle' font-family='Arial' font-size='12' fill='%23333'>Carbon Fiber Rod</text></svg>"],
        reviews: []
    },
    {
        id: 3,
        name: "Professional Spinning Reel",
        price: 89.99,
        description: "Smooth-action spinning reel with 10 ball bearings. Built for durability and performance.",
        category: "reels",
        images: ["data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23e6f3ff' width='200' height='150'/><circle fill='%23666' cx='100' cy='75' r='40' stroke='%23333' stroke-width='3' fill='none'/><circle fill='%23333' cx='100' cy='75' r='20'/><text x='100' y='140' text-anchor='middle' font-family='Arial' font-size='12' fill='%23333'>Spinning Reel</text></svg>"],
        reviews: []
    },
    {
        id: 4,
        name: "Pro Crankbait Set",
        price: 34.99,
        description: "Set of 5 deep-diving crankbaits designed for targeting large freshwater fish.",
        category: "crankbaits",
        images: ["data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23e6f3ff' width='200' height='150'/><rect fill='%23ff6b35' x='50' y='50' width='100' height='30' rx='15'/><text x='100' y='130' text-anchor='middle' font-family='Arial' font-size='12' fill='%23333'>Crankbait Set</text></svg>"],
        reviews: []
    }
];

let cart = JSON.parse(localStorage.getItem('cart')) || [];
let orders = JSON.parse(localStorage.getItem('orders')) || [];
let websiteReviews = JSON.parse(localStorage.getItem('websiteReviews')) || [];
let isAdminMode = false;
const ADMIN_PASSWORD = 'maxchingerhambo';
let logoClickCount = 0;
let currentFilter = 'all';

// Initialize the application
function init() {
    loadProducts();
    updateCartDisplay();
    loadReviews();
    calculateOverallRating();
    saveData();
}

// Save data to localStorage
function saveData() {
    localStorage.setItem('products', JSON.stringify(products));
    localStorage.setItem('cart', JSON.stringify(cart));
    localStorage.setItem('orders', JSON.stringify(orders));
    localStorage.setItem('websiteReviews', JSON.stringify(websiteReviews));
}

// Handle logo clicks for admin access
function handleLogoClick() {
    logoClickCount++;
    if (logoClickCount >= 3) {
        promptAdminPassword();
        logoClickCount = 0;
    }
}

// Prompt for admin password
function promptAdminPassword() {
    const modal = document.getElementById('adminPasswordModal');
    modal.style.display = 'block';
}

// Handle admin password submission
document.getElementById('adminPasswordForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const password = document.getElementById('adminPassword').value;
    if (password === ADMIN_PASSWORD) {
        toggleAdminMode();
        closeAdminPasswordModal();
    } else {
        showNotification('Incorrect password');
        document.getElementById('adminPassword').value = '';
    }
});

// Close admin password modal
function closeAdminPasswordModal() {
    document.getElementById('adminPasswordModal').style.display = 'none';
    logoClickCount = 0;
}

// Toggle admin mode
function toggleAdminMode() {
    isAdminMode = !isAdminMode;
    const customerView = document.getElementById('customer-view');
    const adminPanel = document.getElementById('admin-panel');

    if (isAdminMode) {
        customerView.classList.add('hidden');
        adminPanel.classList.remove('hidden');
        loadAdminData();
        showNotification('Admin mode activated');
    } else {
        customerView.classList.remove('hidden');
        adminPanel.classList.add('hidden');
        showNotification('Returned to customer view');
    }
}

// Show customer view
function showCustomerView() {
    isAdminMode = false;
    const customerView = document.getElementById('customer-view');
    const adminPanel = document.getElementById('admin-panel');
    customerView.classList.remove('hidden');
    adminPanel.classList.add('hidden');
}

// Show admin section
function showSection(sectionId) {
    const sections = document.querySelectorAll('.admin-section');
    sections.forEach(section => section.classList.add('hidden'));
    document.getElementById(sectionId).classList.remove('hidden');
}

// Filter products
function filterProducts(category) {
    currentFilter = category;
    const buttons = document.querySelectorAll('.filter-btn');
    buttons.forEach(btn => btn.classList.remove('active'));
    const activeBtn = Array.from(buttons).find(btn => btn.onclick.toString().includes(`'${category}'`));
    if (activeBtn) activeBtn.classList.add('active');
    loadProducts();
}

// Load products into the grid
function loadProducts() {
    const grid = document.getElementById('productGrid');
    grid.innerHTML = '';

    const filteredProducts = currentFilter === 'all' 
        ? products 
        : products.filter(product => product.category === currentFilter);

    filteredProducts.forEach(product => {
        const productCard = createProductCard(product);
        grid.appendChild(productCard);
    });
}

// Create product card HTML
function createProductCard(product) {
    const card = document.createElement('div');
    card.className = 'product-card';

    const avgRating = calculateProductRating(product);
    const starDisplay = generateStarDisplay(avgRating);

    card.innerHTML = `
        <div class="product-images">
            ${product.images.map((img, index) =>
                `<img src="${img}" alt="${product.name}" class="product-image ${index === 0 ? 'active' : ''}">`
            ).join('')}
            ${product.images.length > 1 ? `
                <div class="image-nav">
                    ${product.images.map((_, index) =>
                        `<div class="image-dot ${index === 0 ? 'active' : ''}" onclick="switchImage(${product.id}, ${index})"></div>`
                    ).join('')}
                </div>
            ` : ''}
        </div>
        <div class="product-info">
            <h3 class="product-title">${product.name}</h3>
            <div class="product-price">$${product.price}</div>
            <div class="rating">
                <div class="stars">${starDisplay}</div>
                <span class="rating-text">(${product.reviews.length} reviews)</span>
            </div>
            <button class="add-to-cart-btn" onclick="addToCart(${product.id})">Add to Cart</button>
        </div>
    `;

    return card;
}

// Switch product image
function switchImage(productId, imageIndex) {
    const card = document.querySelector(`[data-product-id="${productId}"]`) ||
        Array.from(document.querySelectorAll('.product-card')).find(card =>
            card.querySelector('.product-title').textContent === products.find(p => p.id === productId)?.name
        );

    if (card) {
        const images = card.querySelectorAll('.product-image');
        const dots = card.querySelectorAll('.image-dot');

        images.forEach((img, index) => {
            img.classList.toggle('active', index === imageIndex);
        });

        dots.forEach((dot, index) => {
            dot.classList.toggle('active', index === imageIndex);
        });
    }
}

// Generate star display
function generateStarDisplay(rating) {
    const fullStars = Math.floor(rating);
    const hasHalfStar = rating % 1 >= 0.5;
    let stars = '';

    for (let i = 0; i < fullStars; i++) {
        stars += '<span class="star">★</span>';
    }

    if (hasHalfStar) {
        stars += '<span class="star">☆</span>';
    }

    const remainingStars = 5 - fullStars - (hasHalfStar ? 1 : 0);
    for (let i = 0; i < remainingStars; i++) {
        stars += '<span class="star" style="color: #bfdbfe;">★</span>';
    }

    return stars;
}

// Calculate product rating
function calculateProductRating(product) {
    if (product.reviews.length === 0) return 0;
    const sum = product.reviews.reduce((acc, review) => acc + review.rating, 0);
    return sum / product.reviews.length;
}

// Add to cart
function addToCart(productId) {
    const product = products.find(p => p.id === productId);
    if (product) {
        const existingItem = cart.find(item => item.id === productId);
        if (existingItem) {
            existingItem.quantity += 1;
        } else {
            cart.push({ ...product, quantity: 1 });
        }
        updateCartDisplay();
        saveData();
        showNotification(`${product.name} added to cart`);
    }
}

// Update cart display
function updateCartDisplay() {
    const cartCount = document.getElementById('cartCount');
    const cartItems = document.getElementById('cartItems');
    const cartTotal = document.getElementById('cartTotal');

    const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
    cartCount.textContent = totalItems;

    cartItems.innerHTML = '';
    let subtotal = 0;

    cart.forEach(item => {
        subtotal += item.price * item.quantity;
        const cartItem = document.createElement('div');
        cartItem.className = 'cart-item';
        cartItem.innerHTML = `
            <img src="${item.images[0]}" alt="${item.name}">
            <div class="cart-item-info">
                <div style="font-weight: bold;">${item.name}</div>
                <div>$${item.price} x ${item.quantity}</div>
                <div style="margin-top: 5px;">
                    <button onclick="updateCartQuantity(${item.id}, -1)" style="background: #1e40af; color: white; border: none; padding: 5px 10px; border-radius: 4px; cursor: pointer;">-</button>
                    <span style="margin: 0 10px;">${item.quantity}</span>
                    <button onclick="updateCartQuantity(${item.id}, 1)" style="background: #2563eb; color: white; border: none; padding: 5px 10px; border-radius: 4px; cursor: pointer;">+</button>
                </div>
            </div>
        `;
        cartItems.appendChild(cartItem);
    });

    cartTotal.textContent = `Subtotal: ${subtotal.toFixed(2)}`;
}

// Update cart quantity
function updateCartQuantity(productId, change) {
    const item = cart.find(item => item.id === productId);
    if (item) {
        item.quantity += change;
        if (item.quantity <= 0) {
            cart = cart.filter(cartItem => cartItem.id !== productId);
        }
        updateCartDisplay();
        saveData();
    }
}

// Toggle cart sidebar
function toggleCart() {
    const cartSidebar = document.getElementById('cartSidebar');
    cartSidebar.classList.toggle('open');
}

// Calculate shipping
function calculateShipping() {
    const shippingZone = document.getElementById('shippingZone').value;
    const shippingCost = document.getElementById('shippingCost');

    const rates = {
        inner: 5.00,
        metro: 10.00,
        regional: 15.00,
        interstate: 15.00
    };

    if (shippingZone && rates[shippingZone]) {
        shippingCost.textContent = `Shipping: ${rates[shippingZone].toFixed(2)}`;
        shippingCost.setAttribute('data-cost', rates[shippingZone]);
    } else {
        shippingCost.textContent = '';
        shippingCost.removeAttribute('data-cost');
    }
}

// Proceed to checkout
function proceedToCheckout() {
    if (cart.length === 0) {
        showNotification('Your cart is empty');
        return;
    }

    const modal = document.getElementById('checkoutModal');
    const orderSummary = document.getElementById('orderSummary');

    let subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
    let shipping = parseFloat(document.getElementById('shippingCost').getAttribute('data-cost') || 0);
    let total = subtotal + shipping;

    orderSummary.innerHTML = `
        <h4>Order Summary</h4>
        ${cart.map(item => `
            <div style="display: flex; justify-content: space-between; margin: 5px 0;">
                <span>${item.name} x${item.quantity}</span>
                <span>${(item.price * item.quantity).toFixed(2)}</span>
            </div>
        `).join('')}
        <div style="display: flex; justify-content: space-between; margin: 10px 0; padding-top: 10px; border-top: 1px solid #ccc;">
            <span>Subtotal:</span>
            <span>${subtotal.toFixed(2)}</span>
        </div>
        <div style="display: flex; justify-content: space-between; margin: 5px 0;">
            <span>Shipping:</span>
            <span>${shipping.toFixed(2)}</span>
        </div>
        <div style="display: flex; justify-content: space-between; margin: 10px 0; padding-top: 10px; border-top: 1px solid #ccc; font-weight: bold; font-size: 1.1rem;">
            <span>Total:</span>
            <span>${total.toFixed(2)}</span>
        </div>
    `;

    modal.style.display = 'block';
}

// Close checkout
function closeCheckout() {
    document.getElementById('checkoutModal').style.display = 'none';
}

// Handle checkout form submission
document.getElementById('checkoutForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const formData = {
        customerName: document.getElementById('customerName').value,
        customerEmail: document.getElementById('customerEmail').value,
        customerPhone: document.getElementById('customerPhone').value,
        shippingAddress: document.getElementById('shippingAddress').value,
        paymentMethod: document.getElementById('paymentMethod').value,
        items: cart,
        subtotal: cart.reduce((sum, item) => sum + (item.price * item.quantity), 0),
        shipping: parseFloat(document.getElementById('shippingCost').getAttribute('data-cost') || 0),
        total: cart.reduce((sum, item) => sum + (item.price * item.quantity), 0) + parseFloat(document.getElementById('shippingCost').getAttribute('data-cost') || 0),
        orderDate: new Date().toISOString(),
        orderId: 'LK' + Date.now()
    };

    processOrder(formData);
});

// Process order
function processOrder(orderData) {
    orders.push(orderData);
    sendOrderConfirmation(orderData);
    cart = [];
    updateCartDisplay();
    saveData();
    closeCheckout();
    showNotification(`Order ${orderData.orderId} placed successfully! Confirmation sent to ${orderData.customerEmail}`);
    document.getElementById('cartSidebar').classList.remove('open');
}

// Simulate sending order confirmation
function sendOrderConfirmation(orderData) {
    console.log('Order confirmation sent to:', orderData.customerEmail);
    console.log('Order notification sent to: lure.kings.fishing.aus@gmail.com');
    console.log('Order details:', orderData);
}

// Show notification
function showNotification(message) {
    const notification = document.getElementById('notification');
    notification.textContent = message;
    notification.classList.add('show');
    setTimeout(() => {
        notification.classList.remove('show');
    }, 3000);
}

// Admin Functions
function loadAdminData() {
    loadAdminProducts();
    loadAdminOrders();
    loadAdminReviews();
}

// Load admin products
function loadAdminProducts() {
    const adminProductList = document.getElementById('adminProductList');
    adminProductList.innerHTML = '';

    products.forEach(product => {
        const productDiv = document.createElement('div');
        productDiv.style.cssText = 'border: 1px solid #bfdbfe; padding: 1rem; margin: 1rem 0; border-radius: 6px;';
        productDiv.innerHTML = `
            <h4>${product.name}</h4>
            <p>Price: ${product.price}</p>
            <p>Category: ${product.category}</p>
            <p>Reviews: ${product.reviews.length}</p>
            <button class="btn btn-danger" onclick="deleteProduct(${product.id})">Delete Product</button>
        `;
        adminProductList.appendChild(productDiv);
    });
}

// Load admin orders
function loadAdminOrders() {
    const ordersList = document.getElementById('ordersList');
    ordersList.innerHTML = '';

    if (orders.length === 0) {
        ordersList.innerHTML = '<p>No orders yet.</p>';
        return;
    }

    orders.forEach(order => {
        const orderDiv = document.createElement('div');
        orderDiv.style.cssText = 'border: 1px solid #bfdbfe; padding: 1rem; margin: 1rem 0; border-radius: 6px;';
        orderDiv.innerHTML = `
            <h4>Order ${order.orderId}</h4>
            <p><strong>Customer:</strong> ${order.customerName} (${order.customerEmail})</p>
            <p><strong>Date:</strong> ${new Date(order.orderDate).toLocaleDateString()}</p>
            <p><strong>Total:</strong> ${order.total.toFixed(2)}</p>
            <p><strong>Payment:</strong> ${order.paymentMethod}</p>
            <p><strong>Items:</strong></p>
            <ul>
                ${order.items.map(item => `<li>${item.name} x${item.quantity} - ${(item.price * item.quantity).toFixed(2)}</li>`).join('')}
            </ul>
            <p><strong>Shipping Address:</strong> ${order.shippingAddress}</p>
        `;
        ordersList.appendChild(orderDiv);
    });
}

// Load admin reviews
function loadAdminReviews() {
    const adminReviewsList = document.getElementById('adminReviewsList');
    adminReviewsList.innerHTML = '';

    const allReviews = [...websiteReviews];
    products.forEach(product => {
        product.reviews.forEach(review => {
            allReviews.push({...review, productName: product.name});
        });
    });

    if (allReviews.length === 0) {
        adminReviewsList.innerHTML = '<p>No reviews yet.</p>';
        return;
    }

    allReviews.forEach((review, index) => {
        const reviewDiv = document.createElement('div');
        reviewDiv.style.cssText = 'border: 1px solid #bfdbfe; padding: 1rem; margin: 1rem 0; border-radius: 6px;';
        reviewDiv.innerHTML = `
            <h4>${review.name}</h4>
            <p><strong>Rating:</strong> ${generateStarDisplay(review.rating)}</p>
            <p><strong>Product:</strong> ${review.productName || 'Website Review'}</p>
            <p><strong>Review:</strong> ${review.text}</p>
            <p><strong>Date:</strong> ${new Date(review.date).toLocaleDateString()}</p>
            <button class="btn btn-danger" onclick="deleteReview(${index}, '${review.productName || 'website'}')">Delete Review</button>
        `;
        adminReviewsList.appendChild(reviewDiv);
    });
}

// Add product form handler
document.getElementById('productForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const files = document.getElementById('productImageFiles').files;
    const imagePromises = Array.from(files).map(file => {
        return new Promise((resolve) => {
            const reader = new FileReader();
            reader.onload = () => resolve(reader.result);
            reader.readAsDataURL(file);
        });
    });

    Promise.all(imagePromises).then(images => {
        const newProduct = {
            id: Date.now(),
            name: document.getElementById('productName').value,
            price: parseFloat(document.getElementById('productPrice').value),
            description: document.getElementById('productDescription').value,
            category: document.getElementById('productCategory').value,
            images: images.length > 0 ? images : [`data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 150'><rect fill='%23e6f3ff' width='200' height='150'/><text x='100' y='75' text-anchor='middle' font-family='Arial' font-size='14' fill='%23333'>${document.getElementById('productName').value}</text></svg>`],
            reviews: []
        };

        products.push(newProduct);
        loadProducts();
        loadAdminProducts();
        saveData();
        this.reset();
        showNotification('Product added successfully');
    });
});

// Delete product
function deleteProduct(productId) {
    if (confirm('Are you sure you want to delete this product?')) {
        products = products.filter(p => p.id !== productId);
        loadProducts();
        loadAdminProducts();
        saveData();
        showNotification('Product deleted successfully');
    }
}

// Delete review
function deleteReview(reviewIndex, productName) {
    if (confirm('Are you sure you want to delete this review?')) {
        if (productName === 'website') {
            websiteReviews.splice(reviewIndex, 1);
        } else {
            const product = products.find(p => p.name === productName);
            if (product) {
                product.reviews.splice(reviewIndex, 1);
            }
        }
        loadAdminReviews();
        loadReviews();
        calculateOverallRating();
        saveData();
        showNotification('Review deleted successfully');
    }
}

// Review form handler
document.getElementById('reviewForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const newReview = {
        name: document.getElementById('reviewerName').value,
        rating: parseInt(document.getElementById('reviewRating').value),
        text: document.getElementById('reviewText').value,
        date: new Date().toISOString()
    };

    websiteReviews.push(newReview);
    loadReviews();
    calculateOverallRating();
    saveData();
    this.reset();
    showNotification('Review submitted successfully');
});

// Load reviews
function loadReviews() {
    const reviewsList = document.getElementById('reviewsList');
    reviewsList.innerHTML = '';

    websiteReviews.forEach(review => {
        const reviewDiv = document.createElement('div');
        reviewDiv.className = 'review-item';
        reviewDiv.innerHTML = `
            <div class="review-header">
                <strong>${review.name}</strong>
                <div class="stars">${generateStarDisplay(review.rating)}</div>
            </div>
            <p>${review.text}</p>
            <small style="color: #4b5e8e;">${new Date(review.date).toLocaleDateString()}</small>
        `;
        reviewsList.appendChild(reviewDiv);
    });
}

// Calculate overall rating
function calculateOverallRating() {
    const overallRating = document.getElementById('overallRating');
    const overallRatingText = document.getElementById('overallRatingText');

    if (websiteReviews.length === 0) {
        overallRating.innerHTML = generateStarDisplay(0);
        overallRatingText.textContent = 'No reviews yet';
        return;
    }

    const avgRating = websiteReviews.reduce((sum, review) => sum + review.rating, 0) / websiteReviews.length;
    overallRating.innerHTML = generateStarDisplay(avgRating);
    overallRatingText.textContent = `${avgRating.toFixed(1)} out of 5 (${websiteReviews.length} reviews)`;
}

// Close modals when clicking outside
window.addEventListener('click', function(e) {
    const checkoutModal = document.getElementById('checkoutModal');
    const adminPasswordModal = document.getElementById('adminPasswordModal');
    if (e.target === checkoutModal) {
        closeCheckout();
    }
    if (e.target === adminPasswordModal) {
        closeAdminPasswordModal();
    }
});

// Initialize the application
init();
</script>
</body>
</html>
