# Módulo 2: CSS - Diseño y Estilos

## 1. Introducción a CSS

### ¿Qué es CSS?

**CSS (Cascading Style Sheets)** es un lenguaje de hojas de estilo que se utiliza para describir la presentación visual de documentos HTML. Mientras HTML define la estructura y el contenido de una página web, CSS se encarga de cómo se ve ese contenido: colores, fuentes, espaciado, layout y efectos visuales.

### Sintaxis de CSS

La sintaxis de CSS sigue una estructura simple compuesta por tres elementos principales:

```css
selector {
    propiedad: valor;
    propiedad: valor;
}
```

**Componentes:**
- **Selector**: Indica qué elemento(s) HTML se van a estilizar
- **Propiedad**: Especifica qué aspecto visual se quiere modificar
- **Valor**: Define cómo se aplicará esa propiedad

**Ejemplo:**
```css
h1 {
    color: blue;
    font-size: 24px;
    text-align: center;
}
```

### Métodos para incluir CSS

#### 1. CSS Inline (En línea)
Se aplica directamente en el elemento HTML usando el atributo `style`.

```html
<h1 style="color: red; font-size: 20px;">Título con estilo inline</h1>
```

**Ventajas:** Aplicación inmediata y específica
**Desventajas:** Difícil de mantener, no reutilizable

#### 2. CSS Interno
Se incluye dentro del documento HTML en la sección `<head>` usando la etiqueta `<style>`.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h1 {
            color: green;
            text-align: center;
        }
        p {
            font-family: Arial, sans-serif;
        }
    </style>
</head>
<body>
    <h1>Mi título</h1>
    <p>Mi párrafo</p>
</body>
</html>
```

**Ventajas:** Estilos centralizados para una página
**Desventajas:** No reutilizable en múltiples páginas

#### 3. CSS Externo (Recomendado)
Se crea un archivo separado con extensión `.css` y se vincula al HTML.

**archivo: estilos.css**
```css
h1 {
    color: purple;
    font-size: 28px;
}

p {
    line-height: 1.5;
    margin: 10px 0;
}
```

**archivo: index.html**
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="estilos.css">
</head>
<body>
    <h1>Mi título</h1>
    <p>Mi párrafo</p>
</body>
</html>
```

**Ventajas:** Reutilizable, mantenible, separación de responsabilidades
**Desventajas:** Requiere un archivo adicional

---

## 2. Selectores y Modelo de Caja

### Selectores Básicos

#### Selector de Etiqueta
Selecciona todos los elementos de un tipo específico.

```css
/* Selecciona todos los párrafos */
p {
    color: gray;
    font-size: 16px;
}

/* Selecciona todos los títulos h2 */
h2 {
    color: navy;
    font-weight: bold;
}
```

#### Selector de Clase
Selecciona elementos que tienen un atributo `class` específico. Se identifica con un punto (`.`).

```css
/* CSS */
.destacado {
    background-color: yellow;
    padding: 10px;
}

.texto-grande {
    font-size: 20px;
    font-weight: bold;
}
```

```html
<!-- HTML -->
<p class="destacado">Este párrafo está destacado</p>
<div class="texto-grande">Texto grande</div>
<p class="destacado texto-grande">Múltiples clases</p>
```

#### Selector de ID
Selecciona un elemento único que tiene un atributo `id` específico. Se identifica con una almohadilla (`#`).

```css
/* CSS */
#encabezado-principal {
    background-color: #333;
    color: white;
    padding: 20px;
}

#pie-pagina {
    text-align: center;
    border-top: 1px solid #ccc;
}
```

```html
<!-- HTML -->
<header id="encabezado-principal">
    <h1>Mi sitio web</h1>
</header>
<footer id="pie-pagina">
    <p>&copy; 2024 Mi empresa</p>
</footer>
```

### Modelo de Caja (Box Model)

El modelo de caja es un concepto fundamental en CSS que describe cómo se calculan las dimensiones de los elementos. Cada elemento HTML es una "caja" rectangular compuesta por cuatro áreas:

```
┌─────────────────────────────────┐
│           MARGIN                │
│  ┌────────────────────────────┐ │
│  │         BORDER             │ │
│  │  ┌───────────────────────┐ │ │
│  │  │       PADDING         │ │ │
│  │  │  ┌──────────────────┐ │ │ │
│  │  │  │     CONTENT      │ │ │ │
│  │  │  │                  │ │ │ │
│  │  │  └──────────────────┘ │ │ │
│  │  └───────────────────────┘ │ │
│  └────────────────────────────┘ │
└─────────────────────────────────┘
```

#### Propiedades del Modelo de Caja

```css
.caja-ejemplo {
    /* Contenido */
    width: 200px;
    height: 100px;
    
    /* Relleno interno */
    padding: 20px;
    padding-top: 10px;
    padding-right: 15px;
    padding-bottom: 10px;
    padding-left: 15px;
    /* Forma abreviada: padding: arriba derecha abajo izquierda; */
    padding: 10px 15px 10px 15px;
    
    /* Borde */
    border: 2px solid #333;
    border-width: 2px;
    border-style: solid;
    border-color: #333;
    
    /* Margen externo */
    margin: 20px;
    margin-top: 10px;
    margin-right: auto; /* Centrar horizontalmente */
    margin-bottom: 10px;
    margin-left: auto;
    /* Forma abreviada */
    margin: 10px auto;
}
```

#### Ejemplo Práctico del Modelo de Caja

```css
.tarjeta {
    width: 300px;
    height: 200px;
    background-color: #f0f0f0;
    padding: 20px;
    border: 3px solid #ddd;
    margin: 25px auto;
    border-radius: 10px;
}
```

```html
<div class="tarjeta">
    <h3>Mi Tarjeta</h3>
    <p>Contenido de la tarjeta con padding interno.</p>
</div>
```

### Propiedades de Texto y Fuentes

#### Color del Texto
```css
.texto-rojo { color: red; }
.texto-hex { color: #3366cc; }
.texto-rgb { color: rgb(255, 128, 0); }
.texto-rgba { color: rgba(255, 128, 0, 0.7); }
```

#### Familias de Fuentes
```css
.fuente-serif {
    font-family: "Times New Roman", Times, serif;
}

.fuente-sans-serif {
    font-family: Arial, Helvetica, sans-serif;
}

.fuente-monospace {
    font-family: "Courier New", Courier, monospace;
}

.fuente-personalizada {
    font-family: "Roboto", Arial, sans-serif;
}
```

#### Propiedades de Texto
```css
.estilo-texto {
    font-size: 18px;           /* Tamaño de fuente */
    font-weight: bold;         /* Grosor: normal, bold, 100-900 */
    font-style: italic;        /* Estilo: normal, italic, oblique */
    text-align: center;        /* Alineación: left, center, right, justify */
    text-decoration: underline; /* Decoración: none, underline, line-through */
    line-height: 1.5;          /* Altura de línea */
    letter-spacing: 2px;       /* Espaciado entre letras */
    text-transform: uppercase; /* Transformación: uppercase, lowercase, capitalize */
}
```

#### Ejemplo Completo de Texto
```css
.articulo {
    font-family: Georgia, serif;
    font-size: 16px;
    line-height: 1.6;
    color: #333;
    text-align: justify;
    margin: 0 auto;
    max-width: 600px;
    padding: 20px;
}

.articulo h2 {
    color: #2c3e50;
    font-size: 24px;
    margin-bottom: 15px;
    text-transform: capitalize;
}

.articulo .destacado {
    font-weight: bold;
    color: #e74c3c;
    background-color: #fdf2f2;
    padding: 5px;
}
```

---

## 3. Diseño Moderno con CSS

### Flexbox - Diseño Flexible

**Flexbox** es un sistema de layout unidimensional que permite distribuir elementos de manera eficiente en un contenedor, incluso cuando su tamaño es desconocido o dinámico.

#### Conceptos Básicos de Flexbox

```css
.contenedor-flex {
    display: flex; /* Activa Flexbox */
}
```

#### Propiedades del Contenedor (Flex Container)

```css
.contenedor-flex {
    display: flex;
    
    /* Dirección principal */
    flex-direction: row;        /* row, row-reverse, column, column-reverse */
    
    /* Justificación (eje principal) */
    justify-content: center;    /* flex-start, flex-end, center, space-between, space-around, space-evenly */
    
    /* Alineación (eje transversal) */
    align-items: center;        /* flex-start, flex-end, center, stretch, baseline */
    
    /* Salto de línea */
    flex-wrap: wrap;           /* nowrap, wrap, wrap-reverse */
    
    /* Espaciado entre elementos */
    gap: 20px;
}
```

#### Ejemplo Práctico de Flexbox

```css
/* Navegación horizontal */
.navegacion {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #333;
    padding: 10px 20px;
}

.navegacion .logo {
    color: white;
    font-size: 24px;
    font-weight: bold;
}

.navegacion .menu {
    display: flex;
    gap: 30px;
    list-style: none;
    margin: 0;
    padding: 0;
}

.navegacion .menu a {
    color: white;
    text-decoration: none;
    padding: 10px 15px;
    border-radius: 5px;
    transition: background-color 0.3s;
}

.navegacion .menu a:hover {
    background-color: #555;
}

/* Tarjetas en grid flexible */
.galeria {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    padding: 20px;
}

.tarjeta {
    flex: 1 1 300px; /* grow, shrink, basis */
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    padding: 20px;
    min-height: 200px;
}
```

### CSS Grid - Sistema de Cuadrícula

**CSS Grid** es un sistema de layout bidimensional que permite crear diseños complejos con filas y columnas.

#### Conceptos Básicos de Grid

```css
.contenedor-grid {
    display: grid;
    
    /* Definir columnas */
    grid-template-columns: 1fr 2fr 1fr;  /* 3 columnas con proporciones */
    grid-template-columns: 200px 1fr 150px; /* Columnas fijas y flexible */
    grid-template-columns: repeat(3, 1fr); /* 3 columnas iguales */
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); /* Responsivo */
    
    /* Definir filas */
    grid-template-rows: 100px auto 50px;
    
    /* Espaciado */
    gap: 20px;
    grid-gap: 20px; /* Versión anterior */
    grid-row-gap: 10px;
    grid-column-gap: 15px;
}
```

#### Ejemplo de Layout con Grid

```css
/* Layout de página completa */
.layout-principal {
    display: grid;
    grid-template-columns: 250px 1fr;
    grid-template-rows: 80px 1fr 60px;
    grid-template-areas: 
        "sidebar header"
        "sidebar main"
        "sidebar footer";
    min-height: 100vh;
    gap: 10px;
}

.header {
    grid-area: header;
    background-color: #3498db;
    display: flex;
    align-items: center;
    padding: 0 20px;
    color: white;
}

.sidebar {
    grid-area: sidebar;
    background-color: #2c3e50;
    padding: 20px;
    color: white;
}

.main {
    grid-area: main;
    padding: 20px;
    background-color: #ecf0f1;
}

.footer {
    grid-area: footer;
    background-color: #34495e;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
}

/* Grid de productos */
.productos {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    padding: 20px;
}

.producto {
    background-color: white;
    border-radius: 12px;
    box-shadow: 0 8px 16px rgba(0,0,0,0.1);
    overflow: hidden;
    transition: transform 0.3s ease;
}

.producto:hover {
    transform: translateY(-5px);
}
```

### Responsive Design - Diseño Adaptativo

#### Media Queries

Las **media queries** permiten aplicar estilos diferentes según las características del dispositivo.

```css
/* Móvil primero (Mobile First) */
.contenedor {
    padding: 10px;
    font-size: 14px;
}

/* Tablet */
@media (min-width: 768px) {
    .contenedor {
        padding: 20px;
        font-size: 16px;
        max-width: 750px;
        margin: 0 auto;
    }
}

/* Escritorio */
@media (min-width: 1024px) {
    .contenedor {
        padding: 30px;
        font-size: 18px;
        max-width: 1200px;
    }
}

/* Pantalla grande */
@media (min-width: 1200px) {
    .contenedor {
        max-width: 1400px;
    }
}
```

#### Unidades Relativas

```css
.responsive-text {
    /* Unidades relativas al viewport */
    font-size: 4vw;        /* 4% del ancho de viewport */
    line-height: 6vh;      /* 6% de la altura de viewport */
    
    /* Unidades relativas al elemento padre */
    font-size: 1.2rem;     /* 1.2 veces el tamaño de fuente del elemento raíz */
    padding: 2em;          /* 2 veces el tamaño de fuente del elemento actual */
    
    /* Unidades responsivas avanzadas */
    font-size: clamp(16px, 2.5vw, 24px); /* Mínimo 16px, máximo 24px, preferible 2.5vw */
}
```

#### Ejemplo de Grid Responsivo

```css
.galeria-responsiva {
    display: grid;
    gap: 15px;
    padding: 15px;
    
    /* Móvil: 1 columna */
    grid-template-columns: 1fr;
}

@media (min-width: 480px) {
    .galeria-responsiva {
        /* Móvil grande: 2 columnas */
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
    }
}

@media (min-width: 768px) {
    .galeria-responsiva {
        /* Tablet: 3 columnas */
        grid-template-columns: repeat(3, 1fr);
        padding: 30px;
        gap: 25px;
    }
}

@media (min-width: 1024px) {
    .galeria-responsiva {
        /* Escritorio: 4 columnas */
        grid-template-columns: repeat(4, 1fr);
        max-width: 1200px;
        margin: 0 auto;
    }
}
```

### Transiciones y Animaciones

#### Transiciones CSS

Las **transiciones** permiten cambios suaves entre estados de CSS.

```css
.boton {
    background-color: #3498db;
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 16px;
    
    /* Transición básica */
    transition: background-color 0.3s ease;
    
    /* Múltiples propiedades */
    transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
    
    /* Forma abreviada para todas las propiedades */
    transition: all 0.3s ease;
}

.boton:hover {
    background-color: #2980b9;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

.boton:active {
    transform: translateY(0);
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
```

#### Animaciones con @keyframes

Las **animaciones** permiten crear secuencias de cambios más complejas.

```css
/* Definir la animación */
@keyframes fadeInUp {
    0% {
        opacity: 0;
        transform: translateY(30px);
    }
    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

@keyframes pulse {
    0%, 100% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.05);
    }
}

@keyframes rotate {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

/* Aplicar las animaciones */
.fade-in {
    animation: fadeInUp 0.6s ease-out;
}

.pulso {
    animation: pulse 2s infinite;
}

.spinner {
    animation: rotate 1s linear infinite;
}

/* Animación compleja */
.card-animada {
    opacity: 0;
    transform: translateY(50px);
    animation: fadeInUp 0.8s ease-out 0.2s forwards;
    /* nombre duración timing-function delay fill-mode */
}
```

#### Ejemplo de Componente Animado

```css
.tarjeta-interactiva {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    transform: translateY(0);
    transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
    cursor: pointer;
    overflow: hidden;
    position: relative;
}

.tarjeta-interactiva::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.6s;
}

.tarjeta-interactiva:hover {
    transform: translateY(-10px) scale(1.02);
    box-shadow: 0 20px 40px rgba(0,0,0,0.4);
}

.tarjeta-interactiva:hover::before {
    left: 100%;
}

.tarjeta-interactiva h3 {
    margin: 0 0 15px 0;
    font-size: 24px;
    transform: translateX(0);
    transition: transform 0.3s ease;
}

.tarjeta-interactiva:hover h3 {
    transform: translateX(10px);
}
```

Código completo

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo - Tarjeta Interactiva</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            max-width: 1200px;
            width: 100%;
        }

        .tarjeta-interactiva {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            transform: translateY(0);
            transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
            cursor: pointer;
            overflow: hidden;
            position: relative;
            min-height: 200px;
        }

        .tarjeta-interactiva::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.6s;
        }

        .tarjeta-interactiva:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        .tarjeta-interactiva:hover::before {
            left: 100%;
        }

        .tarjeta-interactiva h3 {
            margin: 0 0 15px 0;
            font-size: 24px;
            transform: translateX(0);
            transition: transform 0.3s ease;
        }

        .tarjeta-interactiva:hover h3 {
            transform: translateX(10px);
        }

        .tarjeta-interactiva p {
            font-size: 16px;
            line-height: 1.5;
            opacity: 0.9;
            margin-bottom: 20px;
        }

        .tarjeta-interactiva .precio {
            font-size: 28px;
            font-weight: bold;
            color: #ffd700;
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        /* Variantes de colores */
        .tarjeta-verde {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
        }

        .tarjeta-naranja {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        .tarjeta-azul {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .titulo-principal {
            text-align: center;
            color: white;
            font-size: 2.5rem;
            margin-bottom: 40px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background-color: rgba(255,255,255,0.2);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: bold;
            text-transform: uppercase;
            backdrop-filter: blur(10px);
        }

        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .titulo-principal {
                font-size: 2rem;
            }
            
            .tarjeta-interactiva {
                padding: 25px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="titulo-principal" style="grid-column: 1 / -1;">Tarjetas Interactivas CSS</h1>
        
        <div class="tarjeta-interactiva">
            <div class="badge">Premium</div>
            <h3>Diseño Web Profesional</h3>
            <p>Creamos sitios web modernos y responsivos que impresionan a tus clientes y mejoran tu presencia online.</p>
            <div class="precio">$299</div>
        </div>

        <div class="tarjeta-interactiva tarjeta-verde">
            <div class="badge">Popular</div>
            <h3>Desarrollo de Apps</h3>
            <p>Aplicaciones móviles nativas y web apps que conectan con tu audiencia en cualquier dispositivo.</p>
            <div class="precio">$499</div>
        </div>

        <div class="tarjeta-interactiva tarjeta-naranja">
            <div class="badge">Nuevo</div>
            <h3>Marketing Digital</h3>
            <p>Estrategias de marketing digital personalizadas para hacer crecer tu negocio en el mundo online.</p>
            <div class="precio">$199</div>
        </div>

        <div class="tarjeta-interactiva tarjeta-azul">
            <div class="badge">Oferta</div>
            <h3>Consultoría Tech</h3>
            <p>Asesoramiento tecnológico especializado para optimizar tus procesos y mejorar la eficiencia.</p>
            <div class="precio">$149</div>
        </div>

        <div class="tarjeta-interactiva">
            <div class="badge">Pro</div>
            <h3>E-commerce Completo</h3>
            <p>Tienda online completa con sistema de pagos, gestión de inventario y panel de administración.</p>
            <div class="precio">$799</div>
        </div>

        <div class="tarjeta-interactiva tarjeta-verde">
            <div class="badge">Básico</div>
            <h3>Mantenimiento Web</h3>
            <p>Servicio de mantenimiento y actualización continua para mantener tu sitio web siempre actualizado.</p>
            <div class="precio">$99/mes</div>
        </div>
    </div>
</body>
</html>
```

---

## Práctica: Sitio Web Responsive

### Objetivo
Crear un sitio web responsive que incluya una página de inicio con navegación, sección hero, galería de productos y footer, utilizando Flexbox y Grid.

### Estructura HTML Base

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Sitio Responsive</title>
    <link rel="stylesheet" href="estilos.css">
</head>
<body>
    <!-- Navegación -->
    <nav class="navegacion">
        <div class="logo">MiSitio</div>
        <ul class="menu">
            <li><a href="#inicio">Inicio</a></li>
            <li><a href="#productos">Productos</a></li>
            <li><a href="#contacto">Contacto</a></li>
        </ul>
    </nav>
    
    <!-- Sección Hero -->
    <section class="hero">
        <div class="hero-content">
            <h1>Bienvenido a Nuestro Sitio</h1>
            <p>Descubre productos increíbles con diseño moderno</p>
            <button class="cta-button">Ver Productos</button>
        </div>
    </section>
    
    <!-- Galería de Productos -->
    <section class="productos" id="productos">
        <h2>Nuestros Productos</h2>
        <div class="productos-grid">
            <div class="producto">
                <img src="producto1.jpg" alt="Producto 1">
                <h3>Producto Premium</h3>
                <p>Descripción del producto con características principales.</p>
                <span class="precio">$299</span>
            </div>
            <!-- Repetir para más productos -->
        </div>
    </section>
    
    <!-- Footer -->
    <footer class="footer">
        <p>&copy; 2024 MiSitio. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
```

### CSS Completo

```css
/* Reset y estilos base */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    color: #333;
}

/* Variables CSS para consistencia */
:root {
    --color-primario: #3498db;
    --color-secundario: #2c3e50;
    --color-acento: #e74c3c;
    --color-fondo: #ecf0f1;
    --espaciado: 20px;
    --radio-borde: 8px;
    --sombra: 0 4px 6px rgba(0,0,0,0.1);
}

/* Navegación */
.navegacion {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: var(--color-secundario);
    padding: 1rem 2rem;
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 1000;
    box-shadow: var(--sombra);
}

.logo {
    color: white;
    font-size: 1.8rem;
    font-weight: bold;
}

.menu {
    display: flex;
    list-style: none;
    gap: 2rem;
}

.menu a {
    color: white;
    text-decoration: none;
    padding: 0.5rem 1rem;
    border-radius: var(--radio-borde);
    transition: background-color 0.3s ease;
}

.menu a:hover {
    background-color: rgba(255,255,255,0.1);
}

/* Sección Hero */
.hero {
    background: linear-gradient(135deg, var(--color-primario), var(--color-secundario));
    color: white;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 2rem;
}

.hero-content h1 {
    font-size: 3.5rem;
    margin-bottom: 1rem;
    animation: fadeInUp 1s ease-out;
}

.hero-content p {
    font-size: 1.3rem;
    margin-bottom: 2rem;
    animation: fadeInUp 1s ease-out 0.3s both;
}

.cta-button {
    background-color: var(--color-acento);
    color: white;
    padding: 1rem 2rem;
    border: none;
    border-radius: var(--radio-borde);
    font-size: 1.1rem;
    cursor: pointer;
    transition: all 0.3s ease;
    animation: fadeInUp 1s ease-out 0.6s both;
}

.cta-button:hover {
    background-color: #c0392b;
    transform: translateY(-2px);
    box-shadow: 0 6px 12px rgba(0,0,0,0.2);
}

/* Sección de Productos */
.productos {
    padding: 4rem 2rem;
    background-color: var(--color-fondo);
}

.productos h2 {
    text-align: center;
    font-size: 2.5rem;
    margin-bottom: 3rem;
    color: var(--color-secundario);
}

.productos-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.producto {
    background: white;
    border-radius: var(--radio-borde);
    box-shadow: var(--sombra);
    overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.producto:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.producto img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.producto h3 {
    padding: 1rem;
    color: var(--color-secundario);
    font-size: 1.3rem;
}

.producto p {
    padding: 0 1rem;
    color: #666;
    margin-bottom: 1rem;
}

.precio {
    display: block;
    padding: 1rem;
    font-size: 1.5rem;
    font-weight: bold;
    color: var(--color-acento);
    text-align: right;
}

/* Footer */
.footer {
    background-color: var(--color-secundario);
    color: white;
    text-align: center;
    padding: 2rem;
}

/* Animaciones */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Media Queries - Responsive Design */
@media (max-width: 768px) {
    .navegacion {
        flex-direction: column;
        padding: 1rem;
    }
    
    .menu {
        margin-top: 1rem;
        gap: 1rem;
    }
    
    .hero-content h1 {
        font-size: 2.5rem;
    }
    
    .hero-content p {
        font-size: 1.1rem;
    }
    
    .productos {
        padding: 2rem 1rem;
    }
    
    .productos-grid {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 480px) {
    .hero-content h1 {
        font-size: 2rem;
    }
    
    .productos h2 {
        font-size: 2rem;
    }
    
    .cta-button {
        padding: 0.8rem 1.5rem;
        font-size: 1rem;
    }
}
```

### Ejercicios Propuestos

1. **Modificar el diseño**: Cambiar la disposición de la navegación para que sea vertical en pantallas móviles usando un menú hamburguesa.

2. **Agregar más secciones**: Incluir una sección "Acerca de" con un layout de dos columnas (texto e imagen) usando Flexbox.

3. **Implementar un carousel**: Crear un carousel de imágenes en la sección hero usando CSS Grid y animaciones.
