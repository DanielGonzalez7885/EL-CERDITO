# EL-CERDITO
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>El Cerdito</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #fff0f5;
      margin: 0;
      color: #333;
    }
    header {
      background-color: #ff4d6d;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 2rem;
      background: #ffccd5;
      padding: 1rem;
    }
    nav a {
      color: #900c3f;
      text-decoration: none;
      font-weight: bold;
    }
    .container {
      padding: 2rem;
    }
    .product {
      border: 2px solid #ff4d6d;
      border-radius: 10px;
      padding: 1rem;
      margin-bottom: 1rem;
      background: #fff;
    }
    .product h3 {
      margin: 0.2rem 0;
    }
    .cart {
      background: #ffe5ec;
      padding: 1rem;
      border-radius: 10px;
      margin-top: 2rem;
    }
    button {
      background-color: #ff4d6d;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 5px;
      cursor: pointer;
    }
    footer {
      background: #ffccd5;
      text-align: center;
      padding: 1rem;
      margin-top: 2rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>El Cerdito 🐷</h1>
    <p>Productos cárnicos 100% naturales</p>
  </header>
  <nav>
    <a href="#productos">Productos</a>
    <a href="#carrito">Carrito</a>
    <a href="#contacto">Contacto</a>
  </nav>

  <div class="container">
    <section id="productos">
      <h2>Catálogo</h2>
      <div class="product">
        <h3>Grasa líquida</h3>
        <p>$10.000 y $20.000 según tamaño</p>
        <p>Este producto ofrece la más alta calidad y no utiliza nada de productos químicos. Es 100% natural.</p>
        <button onclick="agregarAlCarrito('Grasa líquida', 10000)">Agregar $10.000</button>
        <button onclick="agregarAlCarrito('Grasa líquida', 20000)">Agregar $20.000</button>
      </div>
      <div class="product">
        <h3>Chorizo artesanal</h3>
        <p>$1.500 por unidad</p>
        <p>El chorizo es totalmente artesanal y cuenta con ingredientes frescos de la localidad, ya que nosotros mismos cultivamos todo.</p>
        <button onclick="agregarAlCarrito('Chorizo artesanal', 1500)">Agregar</button>
      </div>
      <div class="product">
        <h3>Rellena</h3>
        <p>$1.200 por unidad</p>
        <p>Rellena tradicional preparada con receta casera, sabor auténtico y textura suave. Ideal para parrillas y comidas típicas.</p>
        <button onclick="agregarAlCarrito('Rellena', 1200)">Agregar</button>
      </div>
    </section>

    <section id="carrito" class="cart">
      <h2>Carrito de Compras</h2>
      <ul id="lista-carrito"></ul>
      <p><strong>Total: </strong>$<span id="total">0</span></p>
      <button onclick="enviarPorWhatsApp()">Pedir por WhatsApp</button>
    </section>

    <section id="contacto">
      <h2>Contacto</h2>
      <p>📱 WhatsApp: <a href="https://wa.me/573115342042" target="_blank">311 534 2042</a></p>
      <p>📧 Correo: <a href="mailto:danielgonzalez7885@gmail.com">danielgonzalez7885@gmail.com</a></p>
      <p>📍 Cite, Santander, Colombia</p>
      <p>📷 Instagram: <a href="https://instagram.com/tiendaelcerdito1" target="_blank">@tiendaelcerdito1</a></p>
    </section>
  </div>

  <footer>
    <p>&copy; 2025 El Cerdito. Todos los derechos reservados.</p>
  </footer>

  <script>
    let carrito = [];

    function agregarAlCarrito(producto, precio) {
      carrito.push({ producto, precio });
      actualizarCarrito();
    }

    function actualizarCarrito() {
      const lista = document.getElementById("lista-carrito");
      const totalEl = document.getElementById("total");
      lista.innerHTML = "";
      let total = 0;
      carrito.forEach(item => {
        const li = document.createElement("li");
        li.textContent = `${item.producto} - $${item.precio}`;
        lista.appendChild(li);
        total += item.precio;
      });
      totalEl.textContent = total;
    }

    function enviarPorWhatsApp() {
      let mensaje = "Hola, quiero hacer un pedido:\n";
      carrito.forEach(item => {
        mensaje += `- ${item.producto} ($${item.precio})\n`;
      });
      const total = carrito.reduce((sum, item) => sum + item.precio, 0);
      mensaje += `Total: $${total}`;
      const url = `https://wa.me/573115342042?text=${encodeURIComponent(mensaje)}`;
      window.open(url, '_blank');
    }
  </script>
</body>
</html>
