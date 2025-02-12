/* Global Styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ff7e5f, #feb47b, #86a8e7, #91eae4);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
    margin: 0;
    padding: 0;
}

@keyframes gradientBG {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

/* Header */
header {
    background-color: #333;
    color: white;
    padding: 15px;
    text-align: center;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

header h1 {
    font-size: 2rem;
}

nav a {
    color: white;
    padding: 0 15px;
    text-decoration: none;
    font-size: 1rem;
}

nav a:hover {
    text-decoration: underline;
}

/* Container */
.container {
    width: 80%;
    margin: 20px auto;
    text-align: center;
}

h2 {
    font-size: 2rem;
    color: #333;
    margin-bottom: 15px;
}

p {
    color: #555;
    font-size: 1.2rem;
    margin-bottom: 20px;
}

/* Product Section */
.product {
    display: inline-block;
    width: 30%;
    margin: 15px;
    padding: 15px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
}

.product img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
}

.product h3 {
    margin: 10px 0;
    font-size: 1.4rem;
    color: #333;
}

.product p {
    color: #888;
    font-size: 1.1rem;
}

/* Footer */
footer {
    background-color: #333;
    color: white;
    padding: 15px;
    text-align: center;
    position: fixed;
    bottom: 0;
    width: 100%;
    box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.2);
}

footer p {
    font-size: 1rem;
    margin: 0;
}


