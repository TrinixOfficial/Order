<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Trinix.Store] Order Via WhatsApp</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background-image: url('https://cdn.pixabay.com/photo/2017/08/06/13/09/aisle-2594993_1280.jpg');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
      color: #000;
      padding: 20px;
    }

    .container {
      max-width: 1200px;
      margin: auto;
      background-color: rgba(255, 255, 255, 0.1);
      color: #333;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
      text-align: center;
      animation: fadeIn 1.5s ease-in-out;
    }

    h1 {
      font-size: 36px;
      background-image: linear-gradient(to right, #6a0dad, #ff5722);
      color: white;
      margin-bottom: 20px;
      font-weight: 600;
      border-radius: 50px;
      text-align: center;
    }

    input[type="text"], input[type="number"], input[type="tel"], select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border-radius: 8px;
      border: 2px solid #ddd;
      font-size: 16px;
      color: #333;
      background-color: #f9f9f9;
    }

    input[type="text"]:focus, input[type="number"]:focus, input[type="tel"]:focus, select:focus {
      border-color: #6a0dad;
    }

    .promo-section {
      margin: 20px 0;
      background-color: #f2f2f2;
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      border: 2px solid #6a0dad;
    }

    .promo-section input {
      margin: 10px 0;
      width: 80%;
      border: 2px solid #6a0dad;
    }

    .promo-section button {
      background-color: #ff5722;
      color: white;
      padding: 12px 25px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      background-image: linear-gradient(to right, #6a0dad, #ff5722);
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .promo-section button:hover {
      background-color: #ff784e;
    }

    .animated-btn {
      background-image: linear-gradient(to right, #6a0dad, #ff5722);
      color: white;
      padding: 15px;
      border: none;
      border-radius: 50px;
      width: 100%;
      font-size: 18px;
      cursor: pointer;
      transition: background-position 0.3s ease;
      text-align: center;
      margin-top: 20px;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
    }

    .animated-btn:hover {
      background-position: right center;
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
    }

    @media (max-width: 768px) {
      .container {
        padding: 20px;
        width: 100%;
      }

      h1 {
        font-size: 28px;
      }
    }

    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(-30px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    input[readonly] {
      background-color: #e0e0e0;
      color: #666;
      pointer-events: none;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Order Via WhatsApp</h1>

    <!-- Product Selection -->
    <label for="productName">Enter Product Name:</label>
    <input list="productList" id="productName" placeholder="Start typing product name" oninput="fetchProductDetails()">
    
    <!-- Datalist for product suggestions -->
    <datalist id="productList">
      <option value="Cera.Ve Original Moisturizaing">
      <option value="Printed Polyster Track Suit">
      <option value="Pc Men's Cotton Plain Polo Shirt">
      <option value="T9 Professional Trimmer">
      <option value="Hand Gripper and Wrist Builder">
      <option value="Finger Gripper">
      <option value="Fordable Hair Dryer">
      <option value="Golden Colored Watch {Customizable}">
      <option value="Rich Dad Poor Dad Book">
      <option value="Dark Physicology Book">
      <option value="Physicology of Money Book">
      <option value="Think and Grow Rich Book">
      <option value="Ultra Watch">
      <option value="5 In One LipStick">
      <option value="Pixi High Pigments Blush">
      <option value="Simply and Classic HeadPhones">
      <option value="Black Colored Track Suit">
      <option value="Red Colored Track Suit {Customizable}">
      <option value="Black & White Track Suit">
      <option value="Plan White T Shirt {Customizable}">
      <option value="Rich Dad Poor Dad In Urdu">
    </datalist>

    <label for="quantity">Enter Quantity:</label>
    <input type="number" id="quantity" value="1" oninput="calculateTotal()">

    <label for="subtotal">Sub-total Price (Per Unit):</label>
    <input type="number" id="subtotal" readonly>

    <label for="deliveryCharges">Delivery Charges:</label>
    <input type="number" id="deliveryCharges" value="160" readonly>

    <label for="totalprice">Total Price:</label>
    <input type="number" id="totalprice" readonly>

    <!-- Promo Code Section -->
    <div class="promo-section">
      <h3>Promo Code</h3>
      <input type="text" id="promoCode" placeholder="Enter Promo Code">
      <button onclick="applyPromo()">Apply</button>
    </div>

    <!-- Order Form -->
    <form id="orderForm">
      <label for="name">Full Name:</label>
      <input type="text" id="name" required>

      <label for="phone1">Phone No 1:</label>
      <input type="tel" id="phone1" required>

      <label for="phone2">Phone No 2 (optional):</label>
      <input type="tel" id="phone2">

      <label for="address">Address:</label>
      <input type="text" id="address" required>

      <label for="postalCode">Postal Code:</label>
      <input type="number" id="postalCode" required>

      <label for="payment">Select Payment Method:</label>
      <select id="payment" required>
        <option value="JazzCash">JazzCash</option>
        <option value="EasyPaisa">EasyPaisa</option>
        <option value="Cash On Delivery">Cash On Delivery</option>
      </select>

      <button type="submit" class="animated-btn" onclick="placeOrder(event)">Place Your Order</button>
    </form>
  </div>

  <script>
    const productData = {
      "Cera.Ve Original Moisturizaing": 1099,
      "Printed Polyster Track Suit": 999,
      "Pc Men's Cotton Plain Polo Shirt": 1200,
      "T9 Professional Trimmer": 1200,
      "Hand Gripper and Wrist Builder": 400,
      "Finger Gripper": 499,
      "Fordable Hair Dryer": 1999,
      "Golden Colored Watch {Customizable}": 1500,
      "Rich Dad Poor Dad Book": 399,
      "Dark Physicology Book": 499,
      "Physicology of Money Book": 499,
      "Think and Grow Rich Book": 499,
      "Ultra Watch": 2249,
      "5 In One LipStick": 499,
      "Pixi High Pigments Blush": 899,
      "Simply and Classic HeadPhones": 999,
      "Black Colored Track Suit": 1999,
      "Red Colored Track Suit {Customizable}": 2249,
      "Black & White Track Suit": 1999,
      "Plan White T Shirt {Customizable}": 450,
      "Rich Dad Poor Dad In Urdu": 499,
    };

    let promoApplied = false;

    function fetchProductDetails() {
      const productName = document.getElementById('productName').value;
      const productPrice = productData[productName];

      if (productPrice) {
        document.getElementById('subtotal').value = productPrice;
        calculateTotal();
      } else {
        document.getElementById('subtotal').value = '';
        document.getElementById('totalprice').value = '';
      }
    }

    function calculateTotal() {
      const quantity = document.getElementById('quantity').value;
      const subtotal = document.getElementById('subtotal').value;
      const deliveryCharges = document.getElementById('deliveryCharges').value;

      if (subtotal && quantity) {
        let total = (subtotal * quantity) + parseInt(deliveryCharges);
        if (promoApplied) {
          total *= 0.9; // Applying 10% discount
        }
        document.getElementById('totalprice').value = total;
      }
    }

    function applyPromo() {
      const promoCode = document.getElementById('promoCode').value;
      if (promoCode === 'trinixisbest') {
        promoApplied = true;
        alert('Promo code applied. You get 10% discount!');
        calculateTotal();
      } else {
        alert('Invalid promo code.');
      }
    }

    function placeOrder(event) {
      event.preventDefault();
      
      const productName = document.getElementById('productName').value;
      const quantity = document.getElementById('quantity').value;
      const totalPrice = document.getElementById('totalprice').value;
      const name = document.getElementById('name').value;
      const phone1 = document.getElementById('phone1').value;
      const phone2 = document.getElementById('phone2').value || 'N/A';
      const address = document.getElementById('address').value;
      const postalCode = document.getElementById('postalCode').value;
      const paymentMethod = document.getElementById('payment').value;

      if (!productName || !quantity || !totalPrice || !name || !phone1 || !address || !postalCode) {
        alert('Please fill out all the required fields.');
        return;
      }

      const message = `*Order Details:*\n\nProduct: ${productName}\nQuantity: ${quantity}\nTotal Price: PKR ${totalPrice}\n\n*Customer Details:*\nName: ${name}\nPhone 1: ${phone1}\nPhone 2: ${phone2}\nAddress: ${address}\nPostal Code: ${postalCode}\nPayment Method: ${paymentMethod}`;
      
      const whatsappLink = `https://wa.me/923001234567?text=${encodeURIComponent(message)}`;
      window.open(whatsappLink, '_blank');
    }
  </script>

</body>
</html>
