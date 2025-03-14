<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>La Moda del Mañana</title>
    <style>
        /* Global */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #101010;
            color: #fff;
        }

        /* Header */
        header {
            text-align: center;
            background: linear-gradient(45deg, #ff5500, #ff8800); /* Degradado de naranja */
            color: white;
            padding: 30px 0;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }
        h1 {
            font-size: 36px;
            letter-spacing: 2px;
            margin: 0;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.6); /* Sombra sutil al texto */
        }

        /* Categories */
        .categories {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
            padding: 0 20px;
        }
        .category {
            background-color: #333;
            padding: 15px 25px;
            text-align: center;
            font-size: 18px;
            cursor: pointer;
            border-radius: 50px;
            transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }
        .category:hover {
            background-color: #555;
            transform: scale(1.05);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.5);
        }

        /* Product Grid */
        .products {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            margin: 0 20px;
            padding-bottom: 50px;
        }
        .product {
            background-color: #1f1f1f;
            border-radius: 10px;
            overflow: hidden;
            width: 240px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid #444;
        }
        .product:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.7);
        }
        .product img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            border-bottom: 2px solid #444;
        }
        .product-details {
            padding: 15px;
            text-align: center;
        }
        .product h3 {
            font-size: 20px;
            margin: 10px 0;
        }
        .product p {
            font-size: 16px;
            margin: 10px 0;
        }
        .price {
            font-weight: bold;
            color: #ff5500;
            font-size: 18px;
        }

        /* Media Queries */
        @media (max-width: 768px) {
            h1 {
                font-size: 28px;
            }
            .categories {
                flex-direction: column;
                gap: 15px;
            }
            .category {
                font-size: 16px;
                padding: 12px 20px;
            }
            .products {
                gap: 20px;
                margin: 0 15px;
            }
            .product {
                width: 200px;
            }
        }

        @media (max-width: 480px) {
            h1 {
                font-size: 24px;
            }
            .categories {
                gap: 10px;
            }
            .category {
                font-size: 14px;
                padding: 10px 15px;
            }
            .products {
                gap: 15px;
                margin: 0 10px;
            }
            .product {
                width: 180px;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>La Moda del Mañana</h1>
</header>

<div class="categories">
    <div class="category" onclick="showProducts('ropa')">ROPA</div>
    <div class="category" onclick="showProducts('zapatos')">ZAPATOS</div>
    <div class="category" onclick="showProducts('otros')">OTROS PRODUCTOS</div>
</div>

<div id="products" class="products"></div>

<script>
    const products = {
        ropa: [
            { name: "Camiseta Estilo Retro", price: "$25", img: "https://via.placeholder.com/240x250?text=Camiseta+Retro" },
            { name: "Pantalón Slim Fit", price: "$35", img: "https://via.placeholder.com/240x250?text=Pantalón+Slim+Fit" },
            { name: "Chaqueta de Cuero", price: "$60", img: "https://via.placeholder.com/240x250?text=Chaqueta+de+Cuero" },
            { name: "Vestido de Noche", price: "$50", img: "https://via.placeholder.com/240x250?text=Vestido+de+Noche" },
            { name: "Suéter de Lana", price: "$40", img: "https://via.placeholder.com/240x250?text=Suéter+de+Lana" },
            { name: "Pantalón Corto", price: "$20", img: "https://via.placeholder.com/240x250?text=Pantalón+Corto" },
            { name: "Blusa de Seda", price: "$30", img: "https://via.placeholder.com/240x250?text=Blusa+de+Seda" },
            { name: "Chaqueta de Invierno", price: "$80", img: "https://via.placeholder.com/240x250?text=Chaqueta+de+Invierno" },
            { name: "Falda Elegante", price: "$45", img: "https://via.placeholder.com/240x250?text=Falda+Elegante" },
            { name: "Camisa de Algodón", price: "$28", img: "https://via.placeholder.com/240x250?text=Camisa+de+Algodón" }
        ],
        zapatos: [
            { name: "Zapatos de Cuero", price: "$70", img: "https://via.placeholder.com/240x250?text=Zapatos+de+Cuero" },
            { name: "Zapatillas Deportivas", price: "$50", img: "https://via.placeholder.com/240x250?text=Zapatillas+Deportivas" },
            { name: "Botines de Moda", price: "$90", img: "https://via.placeholder.com/240x250?text=Botines+de+Moda" },
            { name: "Sandalias de Verano", price: "$40", img: "https://via.placeholder.com/240x250?text=Sandalias+de+Verano" },
            { name: "Zapatos de Charol", price: "$60", img: "https://via.placeholder.com/240x250?text=Zapatos+de+Charol" },
            { name: "Botas Altas", price: "$100", img: "https://via.placeholder.com/240x250?text=Botas+Altas" },
            { name: "Mocasines Elegantes", price: "$65", img: "https://via.placeholder.com/240x250?text=Mocasines+Elegantes" },
            { name: "Zapatillas de Cuero", price: "$55", img: "https://via.placeholder.com/240x250?text=Zapatillas+de+Cuero" },
            { name: "Botines Cortos", price: "$80", img: "https://via.placeholder.com/240x250?text=Botines+Cortos" },
            { name: "Sandalias de Playa", price: "$30", img: "https://via.placeholder.com/240x250?text=Sandalias+de+Playa" }
        ],
        otros: [
            { name: "Gafas de Sol", price: "$15", img: "https://via.placeholder.com/240x250?text=Gafas+de+Sol" },
            { name: "Reloj Digital", price: "$45", img: "https://via.placeholder.com/240x250?text=Reloj+Digital" },
            { name: "Cartera de Cuero", price: "$50", img: "https://via.placeholder.com/240x250?text=Cartera+de+Cuero" },
            { name: "Sombrero de Verano", price: "$20", img: "https://via.placeholder.com/240x250?text=Sombrero+de+Verano" },
            { name: "Bufanda de Lana", price: "$25", img: "https://via.placeholder.com/240x250?text=Bufanda+de+Lana" },
            { name: "Gorra Deportiva", price: "$18", img: "https://via.placeholder.com/240x250?text=Gorra+Deportiva" },
            { name: "Cinturón de Cuero", price: "$30", img: "https://via.placeholder.com/240x250?text=Cinturón+de+Cuero" },
            { name: "Mochila Urbana", price: "$40", img: "https://via.placeholder.com/240x250?text=Mochila+Urbana" },
            { name: "Auriculares Inalámbricos", price: "$70", img: "https://via.placeholder.com/240x250?text=Auriculares+Inalámbricos" },
            { name: "Paraguas Elegante", price: "$22", img: "https://via.placeholder.com/240x250?text=Paraguas+Elegante" }
        ]
    };

    function showProducts(category) {
        const productContainer = document.getElementById('products');
        productContainer.innerHTML = '';
        products[category].forEach(product => {
            const productDiv = document.createElement('div');
            productDiv.classList.add('product');
            productDiv.innerHTML = `
                <img src="${product.img}" alt="${product.name}">
                <div class="product-details">
                    <h3>${product.name}</h3>
                    <p class="price">${product.price}</p>
                </div>
            `;
            productContainer.appendChild(productDiv);
        });
    }
</script>

</body>
</html>
