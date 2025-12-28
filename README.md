🎨 Canvas Color T‑Shirt Picker
Pequeño módulo para seleccionar un color desde una base de datos MySQL y aplicarlo a una camiseta usando <canvas>, manteniendo un estilo de dashboard azul neón.

🧩 Características
Selector de colores alimentado desde la tabla colores_bex (MySQL / PDO).

Imagen de camiseta base en PNG con fondo transparente.

Aplicación de color con HTML5 Canvas (globalCompositeOperation + overlay).

Estilos neón integrados con dashboard (fondos oscuros, cian brillante).

Diseño responsive con media queries para pantallas móviles.

🗄️ Base de datos
Nombre BD: colores (ejemplo)

sql
CREATE TABLE `colores_bex` (
  `id_color`  int(11)      NOT NULL AUTO_INCREMENT,
  `colores`   varchar(50)  NOT NULL,
  `rgb_color` varchar(50)  NOT NULL, -- guarda hex ej: "#00ffff"
  PRIMARY KEY (`id_color`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
Ejemplos de registros:

sql
INSERT INTO colores_bex (colores, rgb_color) VALUES
('Neon Cyan', '#00ffff'),
('Electric Blue', '#007bff'),
('Hot Pink', '#ff00aa'),
('Black', '#000000');
🛠️ Stack y tecnologías
Backend: PHP 8.x con PDO (MySQL).
​

Base de datos: MySQL / MariaDB.

Frontend: HTML5, CSS3 (neon UI), JavaScript ES6.
​

Canvas: API 2D (drawImage, globalCompositeOperation, fillRect).
​

Iconos: Font Awesome (para integrar con el dashboard si se desea).
​

🚀 Modo de uso
Clonar el repo

bash
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo
Configurar la conexión a la BD

En db.php:

php
$DB_HOST = 'localhost';
$DB_NAME = 'colores';
$DB_USER = 'tu_usuario';
$DB_PASS = 'tu_password';
$DB_CHAR = 'utf8mb4';
Crear la tabla y datos

Ejecuta el script SQL de la sección Base de datos en tu servidor MySQL.

Agregar la imagen de la camiseta

Coloca un PNG con fondo transparente, por ejemplo:

text
/proyectos/dashjc/assets/images/tshirt_base.png
Asegúrate de que la ruta en el JS coincida:

js
img.src = '/proyectos/dashjc/assets/images/tshirt_base.png';
Integrar en tu dashboard

Incluye el módulo (por ejemplo canvas_color.php) dentro del layout de tu dashboard:

php
<?php include __DIR__ . '/proyectos/dashjc/canvas_color/canvas_color.php'; ?>
📂 Estructura del módulo
text
canvas_color/
├── canvas_color.php   # Módulo principal (PHP + HTML + CSS + JS)
├── db.php             # Conexión PDO a MySQL
└── assets/
    └── images/
        └── tshirt_base.png  # Camiseta base con fondo transparente
🧪 Detalles técnicos de Canvas
La camiseta se dibuja sobre el canvas con drawImage.

El color se aplica solo sobre los píxeles de la prenda usando:

js
ctx.globalCompositeOperation = 'source-atop';
ctx.fillStyle = `rgba(r, g, b, 0.6)`;
ctx.fillRect(0, 0, canvas.width, canvas.height);
ctx.globalCompositeOperation = 'source-over';
Los colores se leen como hex (#rrggbb) desde MySQL y se convierten a r,g,b en JS.
​
