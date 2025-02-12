<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VRTVON</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ff7e5f, #feb47b, #86a8e7, #91eae4);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
        }
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        nav a {
            color: white;
            padding: 10px;
            text-decoration: none;
        }
        .container {
            width: 80%;
            margin: 20px auto;
        }
        .product {
            display: inline-block;
            width: 30%;
            margin: 10px;
            padding: 15px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .product img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
        }
        .product h3 {
            margin: 10px 0;
        }
        footer {
            text-align: center;
            padding: 10px 0;
            background-color: #333;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <header>
        <h1>My Dropshipping Store</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/products">Products</a>
            <a href="/contact">Contact Us</a>
        </nav>
    </header>

    <div class="container" id="content">
        <h2>Welcome to Our Store</h2>
        <p>Find the best products for dropshipping!</p>
        <div class="product">
            <img src="" alt="NVIDIA RTX 5070">
            <h3>Product 1</h3>
            <p>Price: $549</p>
        </div>
        <div class="product">
            <img src="https://sl.bing.net/eqsKeoTGCRw" alt="NVIDIA RTX 5090">
            <h3>Product 2</h3>
            <p>Price: $1599</p>
        </div>
        <div class="product">
            <img src="https://via.placeholder.com/150" alt="NVIDIA RTX 4090">
            <h3>Product 3</h3>
            <p>Price: $1399</p>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 My Dropshipping Store</p>
    </footer>
</body>
</html>

