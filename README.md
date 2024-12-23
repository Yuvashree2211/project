# Project Responsive Web Design using Bootstrap
# Date:12-10-2024
# AIM:
To create a simplified clone of Dribbble (https://dribbble.com/) landing page.

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Insert the necessary CSS and JavaScript files as external in order to use Bootstrap.

## Step 5:
Create a HTML file and include the needed Bootstrap components.

## Step 6:
Publish the website in the LocalHost.

# PROGRAM :
```
index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fashion Store</title>
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Custom CSS -->
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-success">
        <div class="container">
            <a class="navbar-brand" href="#">FashionWorld</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <!-- Centered Search Bar -->
                <form class="d-flex mx-auto" role="search">
                    <input class="form-control me-2" type="search" placeholder="Search..." aria-label="Search">
                    <button class="btn btn-outline-light" type="submit">Search</button>
                </form>
                <!-- Right-aligned Buttons -->
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <button class="btn btn-outline-light me-2" onclick="alert('Signup page coming soon!')">Signup</button>
                    </li>
                    <li class="nav-item">
                        <button class="btn btn-outline-light" onclick="alert('Login page coming soon!')">Login</button>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="bg-light text-center py-5">
        <div class="container">
            <h1>Welcome to the Fashion World </h1>
            <p class="lead">Your ultimate style destination for fresh fashion trends and daily must-haves</p>
        </div>
    </header>

    <!-- Featured Products Section -->
    <section id="products" class="py-5">
        <div class="container">
            <h2 class="text-center mb-4">Featured Products</h2>
            <div class="row">
                <div class="col-md-4">
                    <div class="card">
                        <img src="saree.jpg" class="card-img-top" alt="saree">
                        <div class="card-body text-center">
                            <h5 class="card-title">SAREES</h5>
                            <p class="card-text">$1700</p>
                            <button class="btn btn-success add-to-cart" data-name="Fresh Apples" data-price="3.5">Add to Buy</button>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card">
                        <img src="bag.avif" class="card-img-top" alt="bag">
                        <div class="card-body text-center">
                            <h5 class="card-title">HAND BAG</h5>
                            <p class="card-text">$899 </p>
                            <button class="btn btn-success add-to-cart" data-name="Tomatoes" data-price="2">Add to Buy</button>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card">
                        <img src="cream.webp" class="card-img-top" alt="cream">
                        <div class="card-body text-center">
                            <h5 class="card-title">MOISTURISER CREAM</h5>
                            <p class="card-text">$99 per one</p>
                            <button class="btn btn-success add-to-cart" data-name="Magiee" data-price="1.2">Add to Buy</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Cart Section -->
    <section id="cart" class="py-5 bg-light">
        <div class="container">
            <h2 class="text-center mb-4">Shopping Cart</h2>
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Product</th>
                        <th>Price</th>
                        <th>Quantity</th>
                        <th>Total</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody id="cartItems">
                    <tr>
                        <td colspan="5" class="text-center">Your Cart is empty</td>
                    </tr>
                </tbody>
            </table>
            <h3 class="text-end">Total: $<span id="cartTotal">0.00</span></h3>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-success text-center text-white py-3">
        <p>&copy; 2024 FashionWorld. All Rights Reserved.</p>
    </footer>

    <!-- Bootstrap JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <!-- Custom JS -->
    <script src="script.js"></script>
</body>
</html>


style.css

/* Center hero text */
header {
    background: url('bcg.jpg') center/cover no-repeat;
    color: whitesmoke;
    text-shadow: 1px 1px 5px rgba(66, 14, 237, 0.922);
}

/* Adjust product card hover */
.card:hover {
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    transform: scale(1.05);
    transition: transform 0.2s, box-shadow 0.2s;
}

/* Footer styling */
footer {
    font-size: 0.9rem;
    letter-spacing: 0.5px;
}


script.js

let Buy = [];
const BuyItems = document.getElementById('cartItems');
const BuyTotal = document.getElementById('cartTotal');

// Add to cart functionality
document.querySelectorAll('.add-to-cart').forEach((button) => {
    button.addEventListener('click', function () {
        const productName = this.dataset.name;
        const productPrice = parseFloat(this.dataset.price);

        const existingProduct = Buy.find((item) => item.name === productName);

        if (existingProduct) {
            existingProduct.quantity += 1;
        } else {
            Buy.push({ name: productName, price: productPrice, quantity: 1 });
        }

        updateCart();
    });
});

// Update cart display
function updateBuy() {
    BuyItems.innerHTML = '';
    let total = 0;

    if (cart.length === 0) {
        BuyItems.innerHTML = <tr><td colspan="5" class="text-center">Your Buy is empty</td></tr>;
    } else {
        Buy.forEach((item) => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;

            BuyItems.innerHTML += `
                <tr>
                    <td>${item.name}</td>
                    <td>$${item.price.toFixed(2)}</td>
                    <td>${item.quantity}</td>
                    <td>$${itemTotal.toFixed(2)}</td>
                    <td><button class="btn btn-danger btn-sm" onclick="removeItem('${item.name}')">Remove</button></td>
                </tr>
            `;
        });
    }

    BuyTotal.textContent = total.toFixed(2);
}

// Remove item from cart
function removeItem(name) {
    Buy = Buy.filter((item) => item.name !== name);
    updateCart();
}

```
# OUTPUT:
![Screenshot (46)](https://github.com/user-attachments/assets/6b7d3c96-1a51-4fa4-8d76-e8ce46d91122)
![Screenshot (47)](https://github.com/user-attachments/assets/7f5998c1-b6fd-42bc-925e-94fa3b2379b1)


# RESULT:
The Project for responsive web design using Bootstrap is completed successfully.
