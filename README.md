# ECO-Shop-Website
Creating a interactive web site using HTML,CSS,JAVA SCRIPT.
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>EcoShop - Eco-friendly Marketplace</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap');
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background-color: #f4f9f4;
    color: #2a3a2a;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #4caf50;
    padding: 1rem 2rem;
    color: white;
    position: sticky;
    top: 0;
    z-index: 1001;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  }
  header .logo {
    font-weight: 700;
    font-size: 1.7rem;
    letter-spacing: 1.2px;
    cursor: pointer;
    user-select: none;
  }
  header nav {
    display: flex;
    gap: 1.5rem;
    font-weight: 500;
    font-size: 1rem;
  }
  header nav a {
    color: white;
    text-decoration: none;
    transition: color 0.3s ease;
    cursor: pointer;
    user-select: none;
  }
  header nav a:hover,
  header nav a.active {
    color: #c8facc;
  }
  .search-bar {
    flex: 1;
    margin: 0 2rem;
    position: relative;
    max-width: 380px;
  }
  .search-bar input[type="text"] {
    width: 100%;
    padding: 0.6rem 1rem;
    border-radius: 20px;
    border: none;
    font-size: 1rem;
    outline: none;
  }
  .search-bar button {
    position: absolute;
    right: 0.3rem;
    top: 50%;
    transform: translateY(-50%);
    background-color: #2e7d32;
    border: none;
    padding: 0.45rem 0.9rem;
    border-radius: 50%;
    cursor: pointer;
    color: white;
    font-size: 1rem;
    transition: background-color 0.3s ease;
  }
  .search-bar button:hover {
    background-color: #1b4d19;
  }
  /* Cart icon */
  .cart-btn {
    position: relative;
    cursor: pointer;
    font-size: 1.4rem;
    user-select: none;
  }
  .cart-count {
    position: absolute;
    top: -6px;
    right: -10px;
    background: #f44336;
    color: white;
    border-radius: 50%;
    padding: 0 6px;
    font-size: 0.75rem;
    font-weight: 700;
    min-width: 18px;
    text-align: center;
    line-height: 18px;
  }
  main {
    max-width: 1200px;
    margin: 2rem auto;
    padding: 0 1rem;
  }
  /* Home page sections */
  #home-section {
    display: flex;
    gap: 2rem;
  }
  .categories {
    flex: 0 0 200px;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 0 18px rgb(43 97 39 / 0.15);
    padding: 1rem 1.5rem;
    height: fit-content;
    user-select: none;
  }
  .categories h3 {
    margin-top: 0;
    font-weight: 700;
    border-bottom: 2px solid #4caf50;
    padding-bottom: 0.5rem;
    margin-bottom: 1.3rem;
    color: #357a38;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }
  .categories ul {
    list-style: none;
    padding-left: 0;
    margin: 0;
  }
  .categories ul li {
    margin-bottom: 0.9rem;
  }
  .categories ul li button {
    background: none;
    border: none;
    color: #4caf50;
    font-weight: 600;
    font-size: 1rem;
    cursor: pointer;
    text-align: left;
    width: 100%;
    padding: 0.3rem 0;
    transition: color 0.3s ease;
    border-radius: 4px;
    user-select: none;
  }
  .categories ul li button:hover,
  .categories ul li button.active {
    color: #2e7d32;
    font-weight: 700;
    background-color: #e6f4e1;
  }
  .products {
    flex: 1;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px,1fr));
    gap: 1.9rem;
    user-select: none;
  }
  .product-card {
    background-color: white;
    border-radius: 12px;
    box-shadow: 0 4px 18px rgb(43 97 39 / 0.08);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    cursor: pointer;
    outline-offset: 4px;
  }
  .product-card:hover,
  .product-card:focus {
    transform: scale(1.05);
    box-shadow: 0 10px 25px rgb(43 97 39 / 0.22);
  }
  .product-image {
    width: 100%;
    object-fit: cover;
    height: 180px;
    border-bottom: 4px solid #4caf50;
    transition: filter 0.3s ease;
  }
  .product-card:hover .product-image,
  .product-card:focus .product-image {
    filter: brightness(1.1);
  }
  .product-details {
    flex-grow: 1;
    padding: 0.9rem 1.2rem 0.7rem 1.2rem;
    display: flex;
    flex-direction: column;
  }
  .product-title {
    font-weight: 600;
    font-size: 1.12rem;
    margin: 0 0 0.5rem 0;
    flex-grow: 1;
    color: #2a3a2a;
    line-height: 1.2;
    user-select: text;
  }
  .product-price {
    font-weight: 700;
    font-size: 1.28rem;
    color: #388e3c;
    margin-bottom: 0.45rem;
  }
  .product-rating {
    display: flex;
    align-items: center;
    gap: 0.35rem;
    color: #fbc02d;
    font-weight: 700;
    margin-bottom: 0.75rem;
  }
  .star {
    display: inline-block;
    color: #fbc02d;
  }
  .add-cart-btn {
    background-color: #4caf50;
    border: none;
    color: white;
    font-weight: 600;
    font-size: 1rem;
    padding: 0.55rem;
    margin: 0 1rem 1.2rem 1rem;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.35s ease;
    user-select: none;
  }
  .add-cart-btn:hover,
  .add-cart-btn:focus {
    background-color: #2e7d32;
    outline: none;
  }
  /* Cart modal */
  #cart-modal {
    position: fixed;
    top: 60px;
    right: 20px;
    width: 360px;
    max-height: 85vh;
    overflow-y: auto;
    background: white;
    box-shadow: 0 6px 25px rgb(43 97 39 / 0.3);
    border-radius: 14px;
    z-index: 1002;
    padding: 1.2rem 1.4rem 1.5rem 1.4rem;
    display: none;
    flex-direction: column;
    font-size: 0.95rem;
  }
  #cart-modal h3 {
    margin-top: 0;
    border-bottom: 2px solid #4caf50;
    padding-bottom: 0.4rem;
    color: #357a38;
    letter-spacing: 0.05em;
    font-weight: 700;
    text-transform: uppercase;
  }
  .cart-close-btn {
    align-self: flex-end;
    background: none;
    border: none;
    font-size: 1.8rem;
    cursor: pointer;
    color: #2a3a2a;
    font-weight: 700;
    line-height: 1;
    user-select: none;
  }
  .cart-close-btn:hover,
  .cart-close-btn:focus {
    color: #4caf50;
    outline: none;
  }
  .cart-item {
    border-bottom: 1px solid #ddd;
    padding: 0.7rem 0;
    display: flex;
    gap: 1rem;
    align-items: center;
  }
  .cart-item img {
    width: 60px;
    height: 60px;
    object-fit: cover;
    border-radius: 10px;
    flex-shrink: 0;
  }
  .cart-item-details {
    flex: 1;
  }
  .cart-item-title {
    font-weight: 600;
    margin: 0 0 0.15rem 0;
    color: #2a3a2a;
    user-select: text;
  }
  .cart-item-price {
    color: #388e3c;
    font-weight: 700;
    font-size: 0.84rem;
  }
  .cart-item-qty {
    margin-top: 0.3rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .qty-btn {
    cursor: pointer;
    border: 1px solid #4caf50;
    background: #e8f5e9;
    color: #357a38;
    font-weight: 700;
    padding: 0 0.6rem;
    border-radius: 8px;
    user-select: none;
    transition: background-color 0.3s ease;
    font-size: 1.1rem;
    line-height: 1;
  }
  .qty-btn:hover,
  .qty-btn:focus {
    background-color: #c8facc;
    outline: none;
  }
  .remove-btn {
    background:#f44336 !important;
    color:white !important;
    border:none !important;
    margin-left: 12px !important;
    font-weight: 700 !important;
    font-size: 1.15rem !important;
    padding: 0 0.5rem !important;
  }
  .cart-empty {
    text-align: center;
    padding: 2rem 0;
    color: #666;
    font-weight: 600;
    font-size: 1.1rem;
    user-select: none;
  }
  /* Login & Signup Pages */
  section.auth-section {
    max-width: 420px;
    margin: 2rem auto;
    background: white;
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 4px 18px rgb(43 97 39 / 0.16);
    display: none;
    flex-direction: column;
  }
  section.auth-section.active {
    display: flex;
  }
  section.auth-section h2 {
    margin: 0 0 1.6rem 0;
    color: #357a38;
    text-align: center;
    font-weight: 700;
    letter-spacing: 0.05em;
    user-select: none;
  }
  form {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 1.1rem;
  }
  label {
    font-weight: 600;
    user-select: none;
  }
  input[type="text"],
  input[type="email"],
  input[type="password"] {
    padding: 0.8rem 1rem;
    border-radius: 10px;
    border: 1.8px solid #4caf50;
    font-size: 1rem;
    outline: none;
    transition: border-color 0.3s ease;
    font-family: 'Poppins', sans-serif;
  }
  input[type="text"]:focus,
  input[type="email"]:focus,
  input[type="password"]:focus {
    border-color: #357a38;
  }
  button.submit-btn {
    background-color: #4caf50;
    color: white;
    font-weight: 700;
    font-size: 1.15rem;
    padding: 0.7rem;
    border: none;
    border-radius: 14px;
    cursor: pointer;
    transition: background-color 0.35s ease;
    user-select: none;
  }
  button.submit-btn:hover,
  button.submit-btn:focus {
    background-color: #357a38;
    outline: none;
  }
  .auth-switch {
    margin-top: 1.3rem;
    font-size: 1rem;
    text-align: center;
    color: #357a38;
    user-select: none;
  }
  .auth-switch button {
    background: none;
    border: none;
    color: #4caf50;
    cursor: pointer;
    font-weight: 700;
    text-decoration: underline;
    padding: 0;
    user-select: none;
  }
  .auth-switch button:hover,
  .auth-switch button:focus {
    color: #2e7d32;
    outline: none;
  }
  /* Responsive */
  @media (max-width: 768px) {
    header {
      flex-wrap: wrap;
      gap: 0.8rem;
    }
    .search-bar {
      margin: 0 0 0.7rem 0;
      flex: 1 1 100%;
      max-width: 100%;
    }
    main {
      padding: 0 1rem;
    }
    #home-section {
      flex-direction: column;
      margin: 1rem 0;
    }
    .categories {
      width: 100%;
      display: flex;
      overflow-x: auto;
      padding: 0.6rem 1rem;
      border-radius: 8px;
      box-shadow: 0 0 15px rgb(43 97 39 / 0.18);
      gap: 1rem;
      margin-bottom: 1rem;
    }
    .categories ul {
      display: flex;
      gap: 1rem;
      margin: 0;
      padding: 0;
    }
    .categories ul li {
      margin-bottom: 0;
    }
    .products {
      grid-template-columns: repeat(auto-fit, minmax(180px,1fr));
      gap: 1.2rem;
    }
    #cart-modal {
      width: 90vw;
      right: 5vw;
      top: 70px;
      padding: 1rem 1rem 1.3rem 1rem;
    }
    section.auth-section {
      margin: 1.8rem 10px;
      width: auto;
    }
  }
</style>
</head>
<body>
<header>
  <div class="logo" tabindex="0" id="logo">EcoShop</div>
  <nav aria-label="Primary navigation">
    <a href="#" class="nav-link active" data-target="home" tabindex="0">Home</a>
    <a href="#" class="nav-link" data-target="login" tabindex="0">Login</a>
    <a href="#" class="nav-link" data-target="signup" tabindex="0">Signup</a>
    <span class="cart-btn" aria-label="View cart" tabindex="0" id="cartBtn" role="button" title="View Cart">🛒<span class="cart-count" id="cartCount" aria-live="polite" aria-atomic="true">0</span></span>
  </nav>
  <div class="search-bar">
    <input type="text" placeholder="Search eco products..." aria-label="Search products" id="searchInput" />
    <button aria-label="Search" id="searchBtn" tabindex="0">🔍</button>
  </div>
</header>
<main>
  <!-- Home Section -->
  <section id="home-section">
    <aside class="categories" aria-label="Product categories">
      <h3>Categories</h3>
      <ul id="categoryList">
        <li><button class="category-btn active" data-category="all" aria-pressed="true">All</button></li>
        <li><button class="category-btn" data-category="home">Home & Kitchen</button></li>
        <li><button class="category-btn" data-category="personal-care">Personal Care</button></li>
        <li><button class="category-btn" data-category="fashion">Fashion</button></li>
        <li><button class="category-btn" data-category="stationery">Stationery</button></li>
        <li><button class="category-btn" data-category="kids">Kids</button></li>
        <li><button class="category-btn" data-category="garden">Garden</button></li>
        <li><button class="category-btn" data-category="pets">Pets</button></li>
      </ul>
    </aside>
    <section class="products" id="productGrid" aria-live="polite" aria-label="Product listings">
      <!-- Product cards inserted by JS -->
    </section>
  </section>

  <!-- Login Section -->
  <section id="login-section" class="auth-section" aria-label="Login form" tabindex="0" aria-hidden="true">
    <h2>Login</h2>
    <form id="loginForm" novalidate>
      <label for="loginEmail">Email address</label>
      <input type="email" id="loginEmail" required autocomplete="username" placeholder="you@example.com" />
      <label for="loginPassword">Password</label>
      <input type="password" id="loginPassword" required autocomplete="current-password" placeholder="Password" />
      <button type="submit" class="submit-btn">Login</button>
    </form>
    <div class="auth-switch">
      New here? <button id="toSignupBtn" aria-label="Switch to signup form">Create an account</button>
    </div>
  </section>

  <!-- Signup Section -->
  <section id="signup-section" class="auth-section" aria-label="Signup form" tabindex="0" aria-hidden="true">
    <h2>Signup</h2>
    <form id="signupForm" novalidate>
      <label for="signupName">Full Name</label>
      <input type="text" id="signupName" required placeholder="Your full name" autocomplete="name" />
      <label for="signupEmail">Email address</label>
      <input type="email" id="signupEmail" required placeholder="you@example.com" autocomplete="email" />
      <label for="signupPassword">Password</label>
      <input type="password" id="signupPassword" required placeholder="Password" autocomplete="new-password" />
      <button type="submit" class="submit-btn">Signup</button>
    </form>
    <div class="auth-switch">
      Already have an account? <button id="toLoginBtn" aria-label="Switch to login form">Login here</button>
    </div>
  </section>
</main>

<!-- Cart Modal -->
<aside id="cart-modal" role="dialog" aria-modal="true" aria-labelledby="cartTitle">
  <button class="cart-close-btn" aria-label="Close cart" id="closeCartBtn">&times;</button>
  <h3 id="cartTitle">Your Cart</h3>
  <div id="cartItemsContainer" aria-live="polite" aria-atomic="true">
    <p class="cart-empty">Your cart is empty.</p>
  </div>
</aside>

<footer>
  &copy; 2024 EcoShop - Sustainable &amp; Eco-friendly Marketplace
</footer>

<script>
  /***********************
   * Data and Utilities  *
   ***********************/
  const products = [
    {id:1,name:"Bamboo Toothbrush (Pack of 4)",price:299,category:"personal-care",image:"https://images.unsplash.com/photo-1581574202237-54be6d06dc23?auto=format&fit=crop&w=500&q=60",rating:4.5},
    {id:2,name:"Organic Cotton Tote Bag",price:499,category:"fashion",image:"https://images.unsplash.com/photo-1556905055-8f358a7a47b4?auto=format&fit=crop&w=500&q=60",rating:4.7},
    {id:3,name:"Natural Beeswax Food Wraps (3 pcs)",price:399,category:"home",image:"https://images.unsplash.com/photo-1505739619272-81fea8cf016a?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:4,name:"Reusable Stainless Steel Straw Set",price:249,category:"home",image:"https://images.unsplash.com/photo-1590080877777-f0db57507b2a?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:5,name:"Eco-friendly Stationery Set",price:599,category:"stationery",image:"https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:6,name:"Kids' Organic Cotton T-shirt",price:699,category:"kids",image:"https://images.unsplash.com/photo-1590080877847-d328798603bb?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:7,name:"Recycled Paper Notebook",price:199,category:"stationery",image:"https://images.unsplash.com/photo-1515377905703-c4788e51af15?auto=format&fit=crop&w=600&q=60",rating:4.2},
    {id:8,name:"Natural Shampoo Bar",price:349,category:"personal-care",image:"https://images.unsplash.com/photo-1598514982757-f09a70002f2d?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:9,name:"Eco-friendly Jute Backpack",price:1299,category:"fashion",image:"https://images.unsplash.com/photo-1564463831911-ba47c822cfb1?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:10,name:"Organic Herbal Tea Sampler",price:499,category:"home",image:"https://images.unsplash.com/photo-1509042239860-f550ce710b93?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:11,name:"Reusable Cotton Produce Bags (Set of 5)",price:349,category:"home",image:"https://images.unsplash.com/photo-1494256997604-768d1f608cac?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:12,name:"Plantable Seed Paper Greeting Cards",price:299,category:"stationery",image:"https://images.unsplash.com/photo-1486308510493-cb39430f70d8?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:13,name:"Water-saving Shower Head",price:1099,category:"home",image:"https://images.unsplash.com/photo-1590081442644-d4bf821fe334?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:14,name:"Organic Cotton Bath Towels",price:999,category:"home",image:"https://images.unsplash.com/photo-1501261379830-fb85f89d9f72?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:15,name:"Compostable Phone Case",price:799,category:"fashion",image:"https://images.unsplash.com/photo-1549924231-f129b911e442?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:16,name:"Natural Soy Candle Set",price:399,category:"home",image:"https://images.unsplash.com/photo-1563237029-eb8daf423d18?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:17,name:"Hemp Rope Plant Hanger",price:199,category:"garden",image:"https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:18,name:"Organic Cotton Face Masks (Set of 3)",price:349,category:"personal-care",image:"https://images.unsplash.com/photo-1579621970795-87facc2f976d?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:19,name:"Biodegradable Dog Waste Bags",price:279,category:"pets",image:"https://images.unsplash.com/photo-1517849845537-4d257902454a?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:20,name:"Recycled Plastic Plant Pots",price:499,category:"garden",image:"https://images.unsplash.com/photo-1501004318641-b39e6451bec6?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:21,name:"Solar-powered Garden Lights",price:1199,category:"garden",image:"https://images.unsplash.com/photo-1575708573998-71054071d36a?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:22,name:"Organic Jute Floor Mat",price:899,category:"home",image:"https://images.unsplash.com/photo-1501004318644-b8b7e0d8ffb0?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:23,name:"Reusable Bamboo Cutlery Set",price:449,category:"personal-care",image:"https://images.unsplash.com/photo-1590946842433-833878d3d53f?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:24,name:"Organic Cotton Pajama Set",price:1599,category:"fashion",image:"https://images.unsplash.com/photo-1520951402471-3274c64a17c9?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:25,name:"Plant-Based Soap Bars (Set of 4)",price:399,category:"personal-care",image:"https://images.unsplash.com/photo-1589118949245-7d38baf380d6?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:26,name:"Natural Fiber Rug",price:2499,category:"home",image:"https://images.unsplash.com/photo-1519710164239-da123dc03ef4?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:27,name:"Recycled Glass Drinking Cups (6 pcs)",price:799,category:"home",image:"https://images.unsplash.com/photo-1508313483452-5bbf884177d6?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:28,name:"Organic Cotton Bed Sheets",price:3499,category:"home",image:"https://images.unsplash.com/photo-1505751172876-fa1923c5c528?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:29,name:"Eco Bamboo Shelf",price:2599,category:"home",image:"https://images.unsplash.com/photo-1505691938895-1758d7feb511?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:30,name:"Organic Cotton Socks (6 pairs)",price:699,category:"fashion",image:"https://images.unsplash.com/photo-1562072540-df5fa26072a5?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:31,name:"Compost Bin for Kitchen",price:1299,category:"home",image:"https://images.unsplash.com/photo-1506377247377-2a5b3b417ebb?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:32,name:"Natural Linen Tablecloth",price:1599,category:"home",image:"https://images.unsplash.com/photo-1509042239862-d9b9f998ae6c?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:33,name:"Sustainable Wooden Toys - Blocks Set",price:1799,category:"kids",image:"https://images.unsplash.com/photo-1513938709626-033611b8cc03?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:34,name:"Organic Cotton Baby Blanket",price:1299,category:"kids",image:"https://images.unsplash.com/photo-1512917774080-9991f1c4c750?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:35,name:"Natural Bamboo Cutting Board",price:899,category:"home",image:"https://images.unsplash.com/photo-1561043433-aaf687c4cf4b?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:36,name:"Compostable Bamboo Plates (Pack of 10)",price:499,category:"home",image:"https://images.unsplash.com/photo-1604335399105-3ddb0e638af9?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:37,name:"Recycled Fabric Yoga Mat",price:2199,category:"fashion",image:"https://images.unsplash.com/photo-1554284126-7551d723f7a9?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:38,name:"Natural Beeswax Lip Balm",price:249,category:"personal-care",image:"https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:39,name:"Organic Cotton Canvas Shoes",price:1999,category:"fashion",image:"https://images.unsplash.com/photo-1542068829-1115f7259450?auto=format&fit=crop&w=600&q=60",rating:4.8},
    {id:40,name:"Recyclable Paper Gift Wrap Set",price:349,category:"stationery",image:"https://images.unsplash.com/photo-1515377905703-c4788e51af15?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:41,name:"Plant-based Biodegradable Glitter",price:399,category:"personal-care",image:"https://images.unsplash.com/photo-1536305036-8ea06d64d4d1?auto=format&fit=crop&w=600&q=60",rating:4.3},
    {id:42,name:"Organic Herbal Bath Salts",price:549,category:"personal-care",image:"https://images.unsplash.com/photo-1509021436665-8f07dbf5bf1d?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:43,name:"Recycled Denim Backpack",price:2399,category:"fashion",image:"https://images.unsplash.com/photo-1553456558-aff63285bddc?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:44,name:"Eco-friendly Laptop Sleeve",price:1299,category:"fashion",image:"https://images.unsplash.com/photo-1489987707025-afc232f7ea0f?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:45,name:"Sustainable Cork Wallet",price:799,category:"fashion",image:"https://images.unsplash.com/photo-1516856942494-2023dbe05e75?auto=format&fit=crop&w=600&q=60",rating:4.6},
    {id:46,name:"Zero Waste Bamboo Makeup Brush Set",price:1599,category:"personal-care",image:"https://images.unsplash.com/photo-1508214751196-bcfd4ca60f91?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:47,name:"Recycled Paper Wall Art",price:899,category:"home",image:"https://images.unsplash.com/photo-1533777324565-a04df0e527b7?auto=format&fit=crop&w=600&q=60",rating:4.5},
    {id:48,name:"Organic Cotton Apron",price:799,category:"home",image:"https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&fit=crop&w=600&q=60",rating:4.4},
    {id:49,name:"Solar Phone Charger",price:2199,category:"fashion",image:"https://images.unsplash.com/photo-1549924231-f129b911e442?auto=format&fit=crop&w=600&q=60",rating:4.7},
    {id:50,name:"Organic Herbal Facial Mist",price:449,category:"personal-care",image:"https://images.unsplash.com/photo-1507679799987-c73779587ccf?auto=format&fit=crop&w=600&q=60",rating:4.5}
  ];

  /***********************
   * Navigation & Views  *
   ***********************/
  const navLinks = document.querySelectorAll('.nav-link');
  const homeSection = document.getElementById('home-section');
  const loginSection = document.getElementById('login-section');
  const signupSection = document.getElementById('signup-section');

  function showSection(sectionName) {
    navLinks.forEach(link => {
      if (link.dataset.target === sectionName) {
        link.classList.add('active');
      } else {
        link.classList.remove('active');
      }
    });
    if (sectionName === 'home') {
      homeSection.style.display = 'flex';
      homeSection.setAttribute('aria-hidden', 'false');
      loginSection.style.display = 'none';
      loginSection.setAttribute('aria-hidden', 'true');
      signupSection.style.display = 'none';
      signupSection.setAttribute('aria-hidden', 'true');
    } else if (sectionName === 'login') {
      homeSection.style.display = 'none';
      homeSection.setAttribute('aria-hidden', 'true');
      loginSection.style.display = 'flex';
      loginSection.setAttribute('aria-hidden', 'false');
      signupSection.style.display = 'none';
      signupSection.setAttribute('aria-hidden', 'true');
      loginSection.focus();
    } else if (sectionName === 'signup') {
      homeSection.style.display = 'none';
      homeSection.setAttribute('aria-hidden', 'true');
      loginSection.style.display = 'none';
      loginSection.setAttribute('aria-hidden', 'true');
      signupSection.style.display = 'flex';
      signupSection.setAttribute('aria-hidden', 'false');
      signupSection.focus();
    }
  }

  navLinks.forEach(link => {
    link.addEventListener('click', e => {
      e.preventDefault();
      const target = link.dataset.target;
      if(target === 'home') {
        clearSearchAndCategory();
      }
      showSection(target);
      closeCart();
    });
  });

  // Switch buttons inside auth forms
  document.getElementById('toSignupBtn').addEventListener('click', e => {
    e.preventDefault();
    showSection('signup');
  });
  document.getElementById('toLoginBtn').addEventListener('click', e => {
    e.preventDefault();
    showSection('login');
  });

  // Clicking on logo always goes home
  document.getElementById('logo').addEventListener('click', e => {
    e.preventDefault();
    clearSearchAndCategory();
    showSection('home');
  });

  /***********************
   * Product Grid & Filtering  *
   ***********************/
  const productGrid = document.getElementById('productGrid');
  const categoryButtons = document.querySelectorAll('.category-btn');
  const searchInput = document.getElementById('searchInput');
  const searchBtn = document.getElementById('searchBtn');

  function renderProducts(items) {
    productGrid.innerHTML = '';
    if (items.length === 0) {
      productGrid.innerHTML = '<p style="grid-column:1/-1; text-align:center; font-weight:600; color:#666;">No products found.</p>';
      return;
    }
    items.forEach(product => {
      const starCount = Math.floor(product.rating);
      const halfStar = product.rating % 1 >= 0.5;
      const starHtml = Array(5).fill().map((_, i) => {
        if(i < starCount) return '★';
        else if(i === starCount && halfStar) return '½';
        else return '☆';
      }).join('');

      const productCard = document.createElement('article');
      productCard.className = 'product-card';
      productCard.setAttribute('tabindex', '0');
      productCard.setAttribute('data-id', product.id);
      productCard.innerHTML = `
        <img src="${product.image}" alt="${product.name}" class="product-image" loading="lazy" />
        <div class="product-details">
          <h4 class="product-title">${product.name}</h4>
          <div class="product-price">₹${product.price}</div>
          <div class="product-rating" aria-label="Rating: ${product.rating} out of 5 stars">${starHtml}</div>
          <button class="add-cart-btn" aria-label="Add ${product.name} to cart">Add to Cart</button>
        </div>
      `;
      productGrid.appendChild(productCard);
    });
    // Add event listeners to add to cart buttons
    document.querySelectorAll('.add-cart-btn').forEach(btn => {
      btn.addEventListener('click', e => {
        const productId = parseInt(e.target.closest('.product-card').dataset.id, 10);
        addToCart(productId);
      });
    });
  }

  function filterByCategory(category) {
    if(category === 'all') return products;
    return products.filter(p => p.category === category);
  }

  function searchProducts(query) {
    query = query.trim().toLowerCase();
    if (!query) return products;
    return products.filter(p => p.name.toLowerCase().includes(query));
  }

  categoryButtons.forEach(btn => {
    btn.addEventListener('click', () => {
      categoryButtons.forEach(b => {
        b.classList.remove('active');
        b.setAttribute('aria-pressed', 'false');
      });
      btn.classList.add('active');
      btn.setAttribute('aria-pressed', 'true');
      applyFilters();
    });
  });

  function applyFilters() {
    const activeCategoryButton = document.querySelector('.category-btn.active');
    const category = activeCategoryButton ? activeCategoryButton.dataset.category : 'all';
    const query = searchInput.value.trim().toLowerCase();

    let results = filterByCategory(category);
    if(query) {
      results = results.filter(p => p.name.toLowerCase().includes(query));
    }
    renderProducts(results);
  }

  searchBtn.addEventListener('click', applyFilters);
  searchInput.addEventListener('keypress', e => {
    if(e.key === 'Enter') {
      applyFilters();
    }
  });

  function clearSearchAndCategory() {
    searchInput.value = '';
    categoryButtons.forEach(b => {
      b.classList.remove('active');
      b.setAttribute('aria-pressed', 'false');
    });
    categoryButtons[0].classList.add('active');
    categoryButtons[0].setAttribute('aria-pressed', 'true');
    renderProducts(products);
  }

  /***********************
   * Cart Functionality  *
   ***********************/
  const cartBtn = document.getElementById('cartBtn');
  const cartModal = document.getElementById('cart-modal');
  const closeCartBtn = document.getElementById('closeCartBtn');
  const cartCountEl = document.getElementById('cartCount');
  const cartItemsContainer = document.getElementById('cartItemsContainer');

  // Get cart from localStorage or empty
  let cart = JSON.parse(localStorage.getItem('ecoCart')) || [];

  function saveCart() {
    localStorage.setItem('ecoCart', JSON.stringify(cart));
  }

  function addToCart(productId) {
    const product = products.find(p => p.id === productId);
    if(!product) return;

    const cartItem = cart.find(i => i.id === productId);
    if(cartItem) {
      cartItem.quantity++;
    } else {
      cart.push({ ...product, quantity: 1 });
    }
    saveCart();
    updateCartCount();
    alert(`${product.name} has been added to your cart.`);
  }

  function updateCartCount() {
    const count = cart.reduce((acc, i) => acc + i.quantity, 0);
    cartCountEl.textContent = count;
  }

  function renderCartItems() {
    cartItemsContainer.innerHTML = '';
    if(cart.length === 0) {
      cartItemsContainer.innerHTML = '<p class="cart-empty">Your cart is empty.</p>';
      return;
    }
    cart.forEach(item => {
      const cartItem = document.createElement('div');
      cartItem.className = 'cart-item';
      cartItem.innerHTML = `
        <img src="${item.image}" alt="${item.name}" />
        <div class="cart-item-details">
          <p class="cart-item-title">${item.name}</p>
          <p class="cart-item-price">₹${item.price} × ${item.quantity} = ₹${(item.price * item.quantity).toFixed(2)}</p>
          <div class="cart-item-qty" aria-label="Quantity controls">
            <button class="qty-btn" aria-label="Decrease quantity" data-id="${item.id}">−</button>
            <span aria-live="polite" aria-atomic="true">${item.quantity}</span>
            <button class="qty-btn" aria-label="Increase quantity" data-id="${item.id}">+</button>
            <button class="qty-btn remove-btn" aria-label="Remove item" data-id="${item.id}" style="background:#f44336; color:white; margin-left:10px; font-weight:bold; border:none;">×</button>
          </div>
        </div>
      `;
      cartItemsContainer.appendChild(cartItem);
    });
    // Add event listeners for qty buttons
    cartItemsContainer.querySelectorAll('.qty-btn').forEach(btn => {
      btn.addEventListener('click', e => {
        const id = parseInt(e.target.dataset.id, 10);
        if(e.target.classList.contains('remove-btn')) {
          removeFromCart(id);
        } else if(e.target.textContent === '−') {
          decreaseQty(id);
        } else if(e.target.textContent === '+') {
          increaseQty(id);
        }
      });
    });
  }

  function openCart() {
    cartModal.style.display = 'flex';
    renderCartItems();
  }

  function closeCart() {
    cartModal.style.display = 'none';
  }

  function increaseQty(id) {
    const item = cart.find(i => i.id === id);
    if(item) {
      item.quantity++;
      saveCart();
      updateCartCount();
      renderCartItems();
    }
  }

  function decreaseQty(id) {
    const item = cart.find(i => i.id === id);
    if(item && item.quantity > 1) {
      item.quantity--;
      saveCart();
      updateCartCount();
      renderCartItems();
    }
  }

  function removeFromCart(id) {
    cart = cart.filter(i => i.id !== id);
    saveCart();
    updateCartCount();
    renderCartItems();
  }

  cartBtn.addEventListener('click', () => {
    if(cartModal.style.display === 'flex') {
      closeCart();
    } else {
      openCart();
      // Also switch to home page view in case user is on login/signup
      showSection('home');
    }
  });

  closeCartBtn.addEventListener('click', closeCart);

  // Close cart on outside click
  window.addEventListener('click', e => {
    if(e.target === cartModal) {
      closeCart();
    }
  });

  // Keyboard accessibility for cart button and escape key to close cart
  cartBtn.addEventListener('keydown', e => {
    if(e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      cartBtn.click();
    }
  });
  window.addEventListener('keydown', e => {
    if(e.key === 'Escape' && cartModal.style.display === 'flex') {
      closeCart();
      cartBtn.focus();
    }
  });

  /***********************
   * Login & Signup Forms *
   ***********************/
  const loginForm = document.getElementById('loginForm');
  const signupForm = document.getElementById('signupForm');

  loginForm.addEventListener('submit', e => {
    e.preventDefault();
    const email = loginForm.loginEmail.value.trim();
    const password = loginForm.loginPassword.value.trim();

    if(!email || !password) {
      alert('Please fill in all login fields.');
      return;
    }

    // Simple email format check
    if(!validateEmail(email)) {
      alert('Please enter a valid email address.');
      return;
    }

    // Since no backend, fake login success
    alert(`Welcome back, ${email}! You are now logged in.`);
    loginForm.reset();
    showSection('home');
  });

  signupForm.addEventListener('submit', e => {
    e.preventDefault();
    const name = signupForm.signupName.value.trim();
    const email = signupForm.signupEmail.value.trim();
    const password = signupForm.signupPassword.value.trim();

    if(!name || !email || !password) {
      alert('Please fill in all signup fields.');
      return;
    }
    if(!validateEmail(email)) {
      alert('Please enter a valid email address.');
      return;
    }
    if(password.length < 6) {
      alert('Password should be at least 6 characters.');
      return;
    }

    // Fake signup success
    alert(`Thanks for signing up, ${name}! You can now login.`);
    signupForm.reset();
    showSection('login');
  });

  function validateEmail(email) {
    const re = /\S+@\S+\.\S+/;
    return re.test(email);
  }

  /***********************
   * Initialization      *
   ***********************/
  updateCartCount();
  clearSearchAndCategory();
  showSection('home');
</script>
</body>
</html>
