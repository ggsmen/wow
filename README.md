<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda Electrónica</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        /* Estilo del encabezado */
        header {
            background-color: #000;
            color: white;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            margin: 0;
            font-size: 2.5em;
            font-weight: bold;
        }

        header nav {
            margin-top: 10px;
        }

        header nav a {
            color: white;
            margin: 0 20px;
            text-decoration: none;
            font-size: 1.2em;
            transition: color 0.3s ease;
        }

        header nav a:hover {
            color: #1abc9c;
        }

        header .login-btn,
        header .cart-btn {
            padding: 10px 20px;
            background-color: #808080;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 1.1em;
            border-radius: 5px;
        }

        header .cart-btn {
            position: relative;
        }

        header .cart-btn .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background-color: red;
            color: white;
            border-radius: 50%;
            padding: 5px;
            font-size: 1em;
        }

        /* Estilos para la galería de productos */
        .product-gallery {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin: 30px 0;
            padding: 0 10px;
        }

        .product-card {
            background-color: white;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            overflow: hidden;
            transition: transform 0.3s ease;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .product-card img {
            width: 100%;
            height: auto;
            transition: transform 0.3s ease;
            cursor: pointer;
        }

        .product-card:hover {
            transform: scale(1.05);
        }

        .product-card h3 {
            text-align: center;
            padding: 10px 0;
            margin: 0;
            background-color: #000;
            color: white;
        }

        .product-card p {
            padding: 10px;
            text-align: center;
            color: #555;
            flex-grow: 1;
        }

        .product-card .price {
            font-size: 1.2em;
            color: #27AE60; /* Color verde */
            margin-top: 10px;
            text-align: center;
        }

        .product-card .add-to-cart {
            background-color: #808080;
            color: white;
            padding: 10px;
            text-align: center;
            cursor: pointer;
            border: none;
            width: 100%;
            font-size: 1.1em;
            border-radius: 5px;
            transition: background-color 0.3s ease;
        }

        .product-card .add-to-cart:hover {
            background-color: #696969;
        }

        /* Formulario de inicio de sesión */
        .login-form,
        .payment-form {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
        }

        .login-form form,
        .payment-form form {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
            width: 350px;
        }

        .login-form input,
        .payment-form input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .login-form button,
        .payment-form button {
            width: 100%;
            padding: 10px;
            background-color: #808080;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        .login-form button:hover,
        .payment-form button:hover {
            background-color: #696969;
        }

        .payment-form .cancel-btn {
            background-color: #e74c3c;
        }

        .payment-form .cancel-btn:hover {
            background-color: #c0392b;
        }

        /* Estilos para el carrito */
        .cart-section {
            background-color: #fff;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            position: fixed;
            top: 0;
            right: 0;
            width: 300px;
            height: 100%;
            overflow-y: auto;
            z-index: 100;
            display: none;
        }

        .cart-section h2 {
            text-align: center;
            font-size: 1.8em;
            margin-bottom: 20px;
            color: #000;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
        }

        .cart-item span {
            font-size: 1.2em;
        }

        .cart-total {
            text-align: center;
            font-size: 1.5em;
            margin-top: 20px;
            font-weight: bold;
            color: #000;
        }

        .cart-btns {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }

        .cart-btns button {
            padding: 10px;
            background-color: #808080;
            color: white;
            border: none;
            cursor: pointer;
            width: 48%;
            border-radius: 5px;
            font-size: 1.1em;
        }

        .cart-btns button:hover {
            background-color: #696969;
        }

        /* Estilos para la sección de contacto */
        .contact-section {
            padding: 20px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin: 30px 0;
            text-align: center;
            border-radius: 15px;
        }

        .contact-section h2 {
            font-size: 1.8em;
            margin-bottom: 20px;
            color: #000;
        }

        .contact-section img {
            width: 200px;
            height: auto;
            border-radius: 8px;
            margin-bottom: 20px;
        }

        .contact-section .highlight {
            font-size: 1.5em;
            color: #27AE60;
            font-weight: bold;
            margin-top: 20px;
        }

        .contact-section .black-section {
            background-color: #f4f4f4;
            color: #000;
            padding: 20px;
            border-radius: 8px;
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
        }

        .contact-section .black-section p {
            margin: 10px 0;
            font-size: 1.2em;
        }

        .hero {
            position: relative;
            width: 100%;
            height: 100vh; /* Hace que el slider ocupe toda la altura de la ventana */
            overflow: hidden; /* Oculta cualquier parte de la imagen que sobresalga */
        }

        .slider {
            display: flex;
            width: 100%;
            height: 100%;
            transition: transform 1s ease;
        }

        .slider img {
            width: 100%;
            height: 100%;
            object-fit: cover; /* Asegura que la imagen cubra todo el área */
        }

        /* Estilos para la sección de derechos reservados */
        .footer {
            background-color: #000;
            color: white;
            text-align: center;
            padding: 10px 0;
            position: relative;
            bottom: 0;
            width: 100%;
        }

        .footer p {
            margin: 0;
            font-size: 1em;
        }
    </style>
</head>

<body>

    <!-- Encabezado con botón de inicio de sesión y carrito -->
    <header>
        <h1>ElectroTienda</h1>
        <nav>
            <a href="#">Inicio</a>
            <a href="#product-gallery">Productos</a>
            <a href="#contact-section">Contacto</a>
        </nav>
        <button class="login-btn" onclick="openLoginForm()">Iniciar sesión</button>
        <button class="cart-btn" onclick="toggleCart()">Ver Carrito
            <span class="cart-count" id="cartCount">0</span>
        </button>
    </header>

    <!-- Slider de imágenes -->
    <section class="hero">
        <div class="slider">
            <img src="https://images.hdqwalls.com/download/republic-of-gamers-8-bit-3n-1280x768.jpg" alt="Imagen 1">
            <img src="https://rog.asus.com/media/1461084809567.jpg" alt="Imagen 2">
            <img src="https://th.bing.com/th/id/R.8f6192c8a2bb0924f49fd2febfd64a0b?rik=iXHuUQj%2fIgOd3w&riu=http%3a%2f%2fcdn.mos.cms.futurecdn.net%2fzbVuzTHxdkezAQB2FjgeML.jpg&ehk=9ipqx22ZBhtlWJKNHra5sQMjJgo6ww%2b%2foMceioiSgQM%3d&risl=&pid=ImgRaw&r=0" alt="Imagen 3">
        </div>
    </section>

    <!-- Galería de productos -->
    <div class="product-gallery" id="product-gallery">
        <div class="product-card" onclick="changeMainImage('https://i5.walmartimages.com.mx/gr/images/product-images/img_large/00019513315449L.jpg?odnHeight=612&odnWidth=612&odnBg=FFFFFF')">
            <img src="https://m.media-amazon.com/images/I/71efVEnhq9L._AC_SX522_.jpg" alt="Producto 1">
            <h3>ASUS Laptop TUF Gaming A15</h3>
            <p>Marca	ASUS<br>
                Nombre del modelo	FA507NUR-LP012W<br>
                Tamaño de la pantalla	15,6 Pulgadas<br>
                Color	Gris<br>
                Tamaño del disco duro	512 GB<br>
                Modelo de CPU	Ryzen 7<br>
                Tamaño de la memoria RAM instalada	16 GB</p>
            <div class="price">$27,999</div>
            <button class="add-to-cart" onclick="addToCart('ASUS Laptop TUF Gaming A15', 27999)">Añadir al carrito</button>
        </div>
        <div class="product-card" onclick="changeMainImage('https://via.placeholder.com/1200x400/4682b4')">
            <img src="https://m.media-amazon.com/images/I/71u9rNXbS-L._AC_SX522_.jpg" alt="Producto 2" width="522" height="398">
            <h3>ASUS Laptop TUF Gaming A15 v2 </h3>
            <p>Marca	ASUS
                Nombre del modelo	FA506NC-HN003W<br>
                Tamaño de la pantalla	15,6 Pulgadas<br>
                Color	Negro<br>
                Tamaño del disco duro	512 GB<br>
                Modelo de CPU	Ryzen 5<br>
                Tamaño de la memoria RAM instalada	16 GB<br>
                </p>
            <div class="price">$75,999</div>
            <button class="add-to-cart" onclick="addToCart('ASUS Laptop TUF Gaming A15 v2', 75999)">Añadir al carrito</button>
        </div>
        <div class="product-card" onclick="changeMainImage('https://via.placeholder.com/1200x400/32cd32')">
            <img src="https://m.media-amazon.com/images/I/718UPbUG7HL._AC_SX522_.jpg" alt="Producto 3">
            <h3>ASUS Laptop TUF Gaming A14</h3>
            <p>Marca	ASUS
                Nombre del modelo	FA401WV-RG026W<br>
                Tamaño de la pantalla	14 Pulgadas<br>
                Color	Gris<br>
                Tamaño del disco duro	1 TB<br>
                Modelo de CPU	Ryzen 9<br>
                Tamaño de la memoria RAM instalada	16 GB</p>
            <div class="price">$35,999</div>
            <button class="add-to-cart" onclick="addToCart('ASUS Laptop TUF Gaming A14', 35999)">Añadir al carrito</button>
        </div>
        <div class="product-card" onclick="changeMainImage('https://via.placeholder.com/1200x400/8a2be2')">
            <img src="https://m.media-amazon.com/images/I/710d+LzoQJL._AC_SX522_.jpg" alt="Producto 4">
            <h3>ASUS Laptop ROG Strix G14</h3>
            <p> Marca	ASUS
                Nombre del modelo	G614JV-N3192W<br>
                Tamaño de la pantalla	16 Pulgadas<br>
                Modelo de CPU	Intel Core i7<br>
                Tamaño de la memoria RAM instalada	16 GB</p>
            <div class="price">$32,999</div>
            <button class="add-to-cart" onclick="addToCart('ASUS Laptop ROG Strix G14', 32999)">Añadir al carrito</button>
        </div>
    </div>

    <!-- Sección de contacto -->
    <section class="contact-section" id="contact-section">
    
        <img src="https://usecim.net/wp-content/uploads/2020/07/conaleplogo.png" alt="Logo de Contacto">
        <div class="black-section">
            <p class="highlight">¡Estamosquí para ayudarate!</p>
            <p>Materia: Diseño y elaboracion de paginas Web</p>
            <p>Profesor: Luis Felipe</p>
            <p>Si tienes alguna pregunta o necesitas más información, no dudes en ponerte en contacto con nosotros.</p>
            <p>Correo electrónico: <a href="mailto:contacto@electrotienda.com">abelingilipollas@gimail.com</a></p>
            <p>Teléfono: +52 123 456 7890</p>
            <p>Dirección: Av. Principal 123, entre el gako y el jales.</p>
        </div>
    </section>

    <!-- Formulario de inicio de sesión -->
    <div class="login-form" id="loginForm">
        <form>
            <h2>Iniciar sesión</h2>
            <input type="text" placeholder="Correo electrónico" required>
            <input type="password" placeholder="Contraseña" required>
            <button type="submit">Entrar</button>
        </form>
    </div>

    <!-- Carrito de compras -->
    <div class="cart-section" id="cartSection">
        <h2>Carrito</h2>
        <div id="cartItems"></div>
        <div class="cart-total" id="cartTotal">Total: $0</div>
        <div class="cart-btns">
            <button onclick="checkout()">Comprar</button>
            <button onclick="clearCart()">Vaciar carrito</button>
            <button onclick="toggleCart()">Salir</button>
        </div>
    </div>

    <!-- Formulario de pago -->
    <div class="payment-form" id="paymentForm">
        <form>
            <h2>Información de la tarjeta</h2>
            <input type="text" placeholder="Número de tarjeta" id="cardNumber" required>
            <input type="text" placeholder="Nombre en la tarjeta" id="cardName" required>
            <button type="button" onclick="processPayment()">Pagar</button>
            <button type="button" class="cancel-btn" onclick="cancelPayment()">Cancelar</button>
        </form>
    </div>

    <!-- Derechos reservados -->
    <footer class="footer">
        <p>&copy; 2023 ElectroTienda. Todos los derechos reservados.</p>
    </footer>

    <script>
        // Variables del carrito
        let cart = [];

        // Función para agregar productos al carrito
        function addToCart(product, price) {
            cart.push({ product, price });
            updateCart();
        }

        // Función para actualizar el carrito
        function updateCart() {
            const cartItemsContainer = document.getElementById('cartItems');
            cartItemsContainer.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                const itemElement = document.createElement('div');
                itemElement.classList.add('cart-item');
                itemElement.innerHTML = `
                    <span>${item.product}</span>
                    <span>$${item.price.toFixed(2)}</span>
                `;
                cartItemsContainer.appendChild(itemElement);
                total += item.price;
            });

            document.getElementById('cartTotal').innerText = `Total: $${total.toFixed(2)}`;
            document.getElementById('cartCount').innerText = cart.length;
        }

        // Función para cambiar la imagen principal del producto
        function changeMainImage(imageUrl) {
            document.getElementById('mainImage').style.backgroundImage = `url(${imageUrl})`;
        }

        // Función para mostrar/ocultar el carrito
        function toggleCart() {
            const cartSection = document.getElementById('cartSection');
            cartSection.style.display = cartSection.style.display === 'none' || !cartSection.style.display ? 'block' : 'none';
        }

        // Función para proceder a la compra
        function checkout() {
            document.getElementById('cartSection').style.display = 'none';
            document.getElementById('paymentForm').style.display = 'flex';
        }

        // Función para procesar el pago
        function processPayment() {
            const cardNumber = document.getElementById('cardNumber').value;
            const cardName = document.getElementById('cardName').value;
            if (cardNumber && cardName) {
                alert('Pago procesado con éxito');
                clearCart();
                document.getElementById('paymentForm').style.display = 'none';
            } else {
                alert('Por favor, completa toda la información de la tarjeta');
            }
        }

        // Función para cancelar el pago
        function cancelPayment() {
            document.getElementById('paymentForm').style.display = 'none';
        }

        // Función para vaciar el carrito
        function clearCart() {
            cart = [];
            updateCart();
        }

        // Función para mostrar el formulario de inicio de sesión
        function openLoginForm() {
            document.getElementById('loginForm').style.display = 'flex';
        }

        // Función para cerrar el formulario de inicio de sesión
        document.getElementById('loginForm').addEventListener('click', function (e) {
            if (e.target === this) {
                this.style.display = 'none';
            }
        });

        // Función para cerrar el formulario de pago
        document.getElementById('paymentForm').addEventListener('click', function (e) {
            if (e.target === this) {
                this.style.display = 'none';
            }
        });
    </script>
    <script>
        // Configuración de un slider simple
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slider img');

        function showSlide(index) {
            slides.forEach((slide, i) => {
                slide.style.display = i === index ? 'block' : 'none';
            });
        }

        function nextSlide() {
            currentSlide = (currentSlide + 1) % slides.length;
            showSlide(currentSlide);
        }

        setInterval(nextSlide, 3000); // Cambia la imagen cada 3 segundos
        showSlide(currentSlide); // Muestra la primera imagen
    </script>
</body>

</html>
