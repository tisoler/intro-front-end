# Clase 2: Construyendo una Página HTML Paso a Paso

## Objetivo de la Clase
Aprender a usar elementos HTML básicos construyendo progresivamente una página web simple sin estilos ni funcionalidad.

## Elementos que Usaremos Hoy
- `<nav>` - Navegación
- `<h1>`, `<h2>` - Encabezados
- `<div>` - Contenedores
- `<input>` - Campos de entrada
- `<table>` - Tablas
- `<button>` - Botones

## Desarrollo de la Clase

### Paso 1: Estructura Básica
Comenzamos con la estructura HTML que ya conocemos:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Primera Página Web</title>
</head>
<body>
    
</body>
</html>
```

### Paso 2: Añadiendo el Encabezado Principal
Agregamos nuestro primer elemento dentro del body:

```html
<body>
    <h1>Bienvenidos a Mi Sitio Web</h1>
</body>
```

**Explicación:** El `<h1>` es el encabezado más importante de la página. Solo debe haber uno por página.

### Paso 3: Creando la Navegación
Ahora añadimos un menú de navegación:

```html
<body>
    <nav>
        <h2>Menú Principal</h2>
        <a href="#inicio">Inicio</a>
        <a href="#productos">Productos</a>
        <a href="#contacto">Contacto</a>
    </nav>
    
    <h1>Bienvenidos a Mi Sitio Web</h1>
</body>
```

**Explicación:** El elemento `<nav>` agrupa enlaces de navegación. Aunque no funcionen todavía, preparamos la estructura.

### Paso 4: Organizando el Contenido con Div
Usamos `<div>` para organizar nuestro contenido en secciones:

```html
<body>
    <nav>
        <h2>Menú Principal</h2>
        <a href="#inicio">Inicio</a>
        <a href="#productos">Productos</a>
        <a href="#contacto">Contacto</a>
    </nav>
    
    <div>
        <h1>Bienvenidos a Mi Sitio Web</h1>
        <p>Esta es la página principal de nuestro sitio.</p>
    </div>
</body>
```

**Explicación:** Los `<div>` son contenedores genéricos que nos ayudan a agrupar y organizar elementos relacionados.

### Paso 5: Añadiendo Más Secciones
Creamos más secciones con encabezados secundarios:

```html
<body>
    <nav>
        <h2>Menú Principal</h2>
        <a href="#inicio">Inicio</a>
        <a href="#productos">Productos</a>
        <a href="#contacto">Contacto</a>
    </nav>
    
    <div>
        <h1>Bienvenidos a Mi Sitio Web</h1>
        <p>Esta es la página principal de nuestro sitio.</p>
    </div>
    
    <div>
        <h2>Sobre Nosotros</h2>
        <p>Somos una empresa dedicada a crear páginas web increíbles.</p>
    </div>
</body>
```

**Explicación:** Los `<h2>` son encabezados secundarios, útiles para subtítulos y secciones importantes.

### Paso 6: Creando un Formulario con Inputs
Agregamos campos de entrada para recopilar información:

```html
<div>
    <h2>Contacto</h2>
    <p>Déjanos tus datos:</p>
    
    <input type="text" placeholder="Tu nombre">
    <input type="email" placeholder="Tu email">
    <input type="tel" placeholder="Tu teléfono">
</div>
```

**Explicación:** Los `<input>` permiten al usuario ingresar información. Diferentes tipos (text, email, tel) dan diferentes comportamientos.

### Paso 7: Añadiendo Botones
Incluimos botones para acciones:

```html
<div>
    <h2>Contacto</h2>
    <p>Déjanos tus datos:</p>
    
    <input type="text" placeholder="Tu nombre">
    <input type="email" placeholder="Tu email">
    <input type="tel" placeholder="Tu teléfono">
    
    <button>Enviar Información</button>
    <button>Limpiar Formulario</button>
</div>
```

**Explicación:** Los `<button>` crean botones clickeables. Aunque no tengan funcionalidad aún, definen la estructura.

### Paso 8: Creando una Tabla
Finalmente, añadimos una tabla para mostrar información estructurada:

```html
<div>
    <h2>Nuestros Servicios</h2>
    
    <table>
        <tr>
            <th>Servicio</th>
            <th>Precio</th>
            <th>Duración</th>
        </tr>
        <tr>
            <td>Página Web Básica</td>
            <td>$500</td>
            <td>1 semana</td>
        </tr>
        <tr>
            <td>Tienda Online</td>
            <td>$1200</td>
            <td>3 semanas</td>
        </tr>
        <tr>
            <td>Aplicación Web</td>
            <td>$2000</td>
            <td>6 semanas</td>
        </tr>
    </table>
</div>
```

**Explicación:** Las tablas usan `<table>` como contenedor, `<tr>` para filas, `<th>` para encabezados y `<td>` para celdas de datos.

## Código Completo Final

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Primera Página Web</title>
</head>
<body>
    <nav>
        <h2>Menú Principal</h2>
        <a href="#inicio">Inicio</a>
        <a href="#productos">Productos</a>
        <a href="#contacto">Contacto</a>
    </nav>
    
    <div>
        <h1>Bienvenidos a Mi Sitio Web</h1>
        <p>Esta es la página principal de nuestro sitio.</p>
    </div>
    
    <div>
        <h2>Sobre Nosotros</h2>
        <p>Somos una empresa dedicada a crear páginas web increíbles.</p>
    </div>
    
    <div>
        <h2>Contacto</h2>
        <p>Déjanos tus datos:</p>
        
        <input type="text" placeholder="Tu nombre">
        <input type="email" placeholder="Tu email">
        <input type="tel" placeholder="Tu teléfono">
        
        <button>Enviar Información</button>
        <button>Limpiar Formulario</button>
    </div>
    
    <div>
        <h2>Nuestros Servicios</h2>
        
        <table>
            <tr>
                <th>Servicio</th>
                <th>Precio</th>
                <th>Duración</th>
            </tr>
            <tr>
                <td>Página Web Básica</td>
                <td>$500</td>
                <td>1 semana</td>
            </tr>
            <tr>
                <td>Tienda Online</td>
                <td>$1200</td>
                <td>3 semanas</td>
            </tr>
            <tr>
                <td>Aplicación Web</td>
                <td>$2000</td>
                <td>6 semanas</td>
            </tr>
        </table>
    </div>
</body>
</html>
```

## Puntos Clave para Recordar

### Jerarquía de Encabezados
- `<h1>`: Un solo encabezado principal por página
- `<h2>`: Encabezados de sección
- Usar en orden jerárquico (h1, h2, h3, etc.)

### Organización con Div
- Los `<div>` nos ayudan a agrupar contenido relacionado
- Son contenedores genéricos sin significado semántico específico
- Útiles para estructurar y organizar el layout

### Formularios Básicos
- `<input>` con diferentes tipos para diferentes datos
- `<button>` para acciones del usuario
- Los placeholders ayudan a entender qué información poner

### Tablas
- Útiles para datos tabulares
- Estructura: table > tr > th/td
- `<th>` para encabezados, `<td>` para datos

## Actividad Práctica
Pide a los estudiantes que:
1. Modifiquen el contenido de la página con su propia información
2. Añadan una fila más a la tabla
3. Agreguen un input adicional al formulario
4. Creen una nueva sección con div, h2 y contenido

## Próxima Clase
En la siguiente clase aprenderemos sobre CSS para dar estilo y mejorar la apariencia de nuestra página HTML.
