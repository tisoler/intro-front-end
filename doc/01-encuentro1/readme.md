# Módulo 1: Fundamentos de la Web y HTML

## 1. Introducción a la Web

### ¿Cómo funciona internet?

Internet es una red global de computadoras interconectadas que se comunican utilizando protocolos estandarizados. Para entender su funcionamiento, debemos conocer algunos conceptos fundamentales:

#### Modelo Cliente-Servidor

La web funciona bajo un modelo **cliente-servidor**, donde:

- **Cliente**: Es el navegador web (Chrome, Firefox, Safari, etc.) que utilizamos para acceder a sitios web. El cliente solicita información y recursos.
- **Servidor**: Es una computadora especializada que almacena y sirve páginas web, archivos e información. Responde a las solicitudes de los clientes.

El proceso básico es:
1. El usuario escribe una URL en el navegador
2. El navegador (cliente) envía una solicitud al servidor
3. El servidor procesa la solicitud y envía la respuesta
4. El navegador recibe y muestra el contenido

#### Protocolos HTTP/HTTPS

##### HTTP (HyperText Transfer Protocol)

HTTP es el protocolo de comunicación fundamental de la World Wide Web. Define las reglas y el formato para el intercambio de información entre clientes (navegadores) y servidores web.

**Características principales de HTTP:**

- **Sin estado (Stateless)**: Cada solicitud HTTP es independiente. El servidor no recuerda solicitudes anteriores del mismo cliente.
- **Basado en texto**: Los mensajes HTTP están en formato de texto legible, lo que facilita la depuración.
- **Puerto por defecto**: Utiliza el puerto 80 por defecto.
- **Métodos HTTP**: Define diferentes tipos de solicitudes:
  - **GET**: Solicita datos del servidor (obtener una página web)
  - **POST**: Envía datos al servidor (enviar un formulario)
  - **PUT**: Actualiza o crea un recurso
  - **DELETE**: Elimina un recurso
  - **HEAD**: Solicita solo los encabezados de respuesta

**Estructura de una solicitud HTTP:**
```
GET /index.html HTTP/1.1
Host: www.ejemplo.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml
Connection: keep-alive
```

**Estructura de una respuesta HTTP:**
```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234
Date: Tue, 03 Jun 2025 10:00:00 GMT

<!DOCTYPE html>
<html>
<head>...
```

**Códigos de estado HTTP más comunes:**
- **200 OK**: Solicitud exitosa
- **404 Not Found**: Recurso no encontrado
- **500 Internal Server Error**: Error del servidor
- **301 Moved Permanently**: Redirección permanente
- **403 Forbidden**: Acceso denegado

##### HTTPS (HTTP Secure)

HTTPS es la versión segura de HTTP que utiliza cifrado criptográfico para proteger la comunicación entre el cliente y el servidor.

**¿Cómo funciona HTTPS?**

HTTPS utiliza **SSL/TLS (Secure Sockets Layer/Transport Layer Security)** para crear un canal de comunicación cifrado:

1. **Handshake SSL/TLS**: El cliente y servidor establecen una conexión segura
2. **Intercambio de certificados**: El servidor presenta su certificado digital para verificar su identidad
3. **Cifrado de datos**: Toda la información se cifra antes de ser transmitida
4. **Descifrado**: Los datos se descifran en el destino usando claves criptográficas

**Ventajas de HTTPS:**

- **Confidencialidad**: Los datos están cifrados y no pueden ser leídos por terceros
- **Integridad**: Los datos no pueden ser modificados durante la transmisión sin ser detectado
- **Autenticación**: Verifica que el servidor es quien dice ser mediante certificados digitales
- **SEO**: Google favorece sitios con HTTPS en los resultados de búsqueda
- **Confianza del usuario**: Los navegadores muestran indicadores de seguridad (candado verde)

**Diferencias técnicas clave:**

| Aspecto | HTTP | HTTPS |
|---------|------|-------|
| Puerto por defecto | 80 | 443 |
| Seguridad | No cifrado | Cifrado SSL/TLS |
| Velocidad | Más rápido | Ligeramente más lento (por el cifrado) |
| Certificado | No requiere | Requiere certificado SSL |
| URL | http://ejemplo.com | https://ejemplo.com |

**Certificados SSL/TLS:**

Los certificados son archivos digitales que contienen:
- Información sobre el propietario del sitio web
- La clave pública para el cifrado
- Firma digital de una Autoridad Certificadora (CA) confiable
- Fecha de vencimiento

**Tipos de certificados:**
- **DV (Domain Validated)**: Validación básica del dominio
- **OV (Organization Validated)**: Validación de la organización
- **EV (Extended Validation)**: Validación extendida con verificación rigurosa

**¿Cuándo usar HTTP vs HTTPS?**

- **Usar HTTPS siempre que sea posible**, especialmente para:
  - Sitios con formularios (login, registro, contacto)
  - Comercio electrónico
  - Sitios con información sensible
  - Aplicaciones web modernas

- **HTTP solo en entornos de desarrollo local** o sitios estáticos sin información sensible (aunque esto cada vez es menos recomendable)

**Implementación práctica:**

Para implementar HTTPS necesitas:
1. Obtener un certificado SSL (Let's Encrypt ofrece certificados gratuitos)
2. Configurar el servidor web para usar HTTPS
3. Redirigir todo el tráfico HTTP a HTTPS
4. Actualizar enlaces internos para usar HTTPS

**Herramientas para verificar HTTPS:**
- Verificar el candado en el navegador
- SSL Labs Server Test (ssllabs.com/ssltest/)
- Herramientas de desarrollador del navegador (pestaña Security)

### Estructura básica de un sitio web

Un sitio web típico está compuesto por:

- **Páginas HTML**: Definen la estructura y contenido
- **Archivos CSS**: Controlan la presentación visual (colores, fuentes, diseño)
- **Archivos JavaScript**: Añaden interactividad y funcionalidad dinámica
- **Recursos multimedia**: Imágenes, videos, audio
- **Otros archivos**: Fuentes, íconos, documentos

  
### Estructura básica de un sitio web

Un sitio web típico está compuesto por:

- **Páginas HTML**: Definen la estructura y contenido
- **Archivos CSS**: Controlan la presentación visual (colores, fuentes, diseño)
- **Archivos JavaScript**: Añaden interactividad y funcionalidad dinámica
- **Recursos multimedia**: Imágenes, videos, audio
- **Otros archivos**: Fuentes, íconos, documentos

### Herramientas de desarrollo

#### Navegador web
Es la herramienta principal para visualizar y probar nuestras páginas web. Los navegadores modernos incluyen potentes herramientas de desarrollo.

#### Editores de código
Software especializado para escribir código de manera eficiente:
- **Visual Studio Code**: Editor gratuito y muy popular
- **Sublime Text**: Editor liviano y rápido
- **Atom**: Editor de código abierto
- **WebStorm**: IDE profesional para desarrollo web

#### DevTools (Herramientas de desarrollador)
Conjunto de herramientas integradas en los navegadores que permiten:
- Inspeccionar y modificar HTML/CSS en tiempo real
- Depurar JavaScript
- Analizar el rendimiento de la página
- Simular diferentes dispositivos
- Monitorear el tráfico de red

Para acceder: F12 o clic derecho → "Inspeccionar elemento"

## 2. HTML: Estructura y Semántica

HTML (HyperText Markup Language) es el lenguaje de marcado estándar para crear páginas web. Define la estructura y el significado del contenido mediante etiquetas.

### Sintaxis básica de HTML

#### Etiquetas
Las etiquetas son los elementos fundamentales de HTML. Se escriben entre corchetes angulares `< >`:

```html
<etiqueta>contenido</etiqueta>
```

- **Etiqueta de apertura**: `<etiqueta>`
- **Contenido**: Texto o elementos anidados
- **Etiqueta de cierre**: `</etiqueta>`

Algunas etiquetas son **auto-cerradas** (no tienen contenido):
```html
<img src="imagen.jpg" alt="Descripción">
<br>
<hr>
```

#### Atributos
Los atributos proporcionan información adicional sobre los elementos:

```html
<etiqueta atributo="valor">contenido</etiqueta>
```

Ejemplos:
```html
<a href="https://ejemplo.com" target="_blank">Enlace</a>
<img src="foto.jpg" alt="Descripción de la foto" width="300">
```

### Estructura de un documento HTML

Todo documento HTML debe seguir esta estructura básica:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título de la página</title>
</head>
<body>
    <!-- Contenido visible de la página -->
</body>
</html>
```

#### Elementos principales:

- **`<!DOCTYPE html>`**: Declara que el documento usa HTML5
- **`<html>`**: Elemento raíz que contiene todo el documento
- **`<head>`**: Contiene metadatos (información sobre la página que no se muestra)
- **`<body>`**: Contiene el contenido visible de la página

### Elementos básicos

#### Títulos (h1-h6)
Los títulos definen la jerarquía del contenido:

```html
<h1>Título principal</h1>
<h2>Subtítulo</h2>
<h3>Título de sección</h3>
<h4>Subtítulo de sección</h4>
<h5>Título menor</h5>
<h6>Título más pequeño</h6>
```

#### Párrafos
```html
<p>Este es un párrafo de texto. Puede contener múltiples oraciones y se renderiza como un bloque de texto.</p>
```

#### Enlaces
```html
<!-- Enlace externo -->
<a href="https://www.ejemplo.com">Visitar ejemplo.com</a>

<!-- Enlace interno -->
<a href="pagina.html">Ir a otra página</a>

<!-- Enlace a sección de la misma página -->
<a href="#seccion1">Ir a sección 1</a>
```

#### Imágenes
```html
<img src="ruta/imagen.jpg" alt="Descripción de la imagen" width="400" height="300">
```

- **`src`**: Ubicación de la imagen
- **`alt`**: Texto alternativo (importante para accesibilidad)
- **`width/height`**: Dimensiones opcionales

### Listas

#### Lista desordenada (ul)
```html
<ul>
    <li>Elemento 1</li>
    <li>Elemento 2</li>
    <li>Elemento 3</li>
</ul>
```

#### Lista ordenada (ol)
```html
<ol>
    <li>Primer elemento</li>
    <li>Segundo elemento</li>
    <li>Tercer elemento</li>
</ol>
```

### Tablas

```html
<table>
    <thead>
        <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Ciudad</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Juan</td>
            <td>25</td>
            <td>Madrid</td>
        </tr>
        <tr>
            <td>María</td>
            <td>30</td>
            <td>Barcelona</td>
        </tr>
    </tbody>
</table>
```

- **`<table>`**: Contenedor de la tabla
- **`<thead>`**: Encabezado de la tabla
- **`<tbody>`**: Cuerpo de la tabla
- **`<tr>`**: Fila de la tabla
- **`<th>`**: Celda de encabezado
- **`<td>`**: Celda de datos

### Formularios

Los formularios permiten recopilar información del usuario:

```html
<form action="/procesar" method="POST">
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre" required>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <label for="mensaje">Mensaje:</label>
    <textarea id="mensaje" name="mensaje" rows="4"></textarea>
    
    <label for="pais">País:</label>
    <select id="pais" name="pais">
        <option value="es">España</option>
        <option value="mx">México</option>
        <option value="ar">Argentina</option>
    </select>
    
    <button type="submit">Enviar</button>
</form>
```

#### Elementos de formulario:
- **`<form>`**: Contenedor del formulario
- **`<input>`**: Campo de entrada (texto, email, password, etc.)
- **`<textarea>`**: Área de texto multilínea
- **`<select>`** y **`<option>`**: Lista desplegable
- **`<button>`**: Botón de acción
- **`<label>`**: Etiqueta descriptiva para campos

### HTML semántico

HTML5 introdujo elementos semánticos que describen el significado del contenido:

```html
<header>
    <h1>Mi Sitio Web</h1>
    <nav>
        <ul>
            <li><a href="#inicio">Inicio</a></li>
            <li><a href="#sobre">Sobre mí</a></li>
            <li><a href="#contacto">Contacto</a></li>
        </ul>
    </nav>
</header>

<main>
    <section id="inicio">
        <h2>Bienvenido</h2>
        <p>Contenido principal de la página.</p>
    </section>
    
    <article>
        <h2>Artículo destacado</h2>
        <p>Contenido del artículo...</p>
    </article>
    
    <aside>
        <h3>Información adicional</h3>
        <p>Contenido secundario o complementario.</p>
    </aside>
</main>

<footer>
    <p>&copy; 2024 Mi Sitio Web. Todos los derechos reservados.</p>
</footer>
```

#### Elementos semánticos principales:
- **`<header>`**: Encabezado de la página o sección
- **`<nav>`**: Navegación principal
- **`<main>`**: Contenido principal de la página
- **`<section>`**: Sección temática del contenido
- **`<article>`**: Contenido independiente y reutilizable
- **`<aside>`**: Contenido relacionado pero secundario
- **`<footer>`**: Pie de página

## 3. Práctica: Página web básica con estructura semántica

### Objetivo
Crear una página web personal que incluya estructura semántica HTML y un formulario de contacto funcional.

### Requisitos
1. Estructura HTML5 semántica completa
2. Información personal (nombre, bio, habilidades)
3. Formulario de contacto con validación básica
4. Navegación interna
5. Al menos una imagen y una lista

### Código de ejemplo

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Página personal de [Tu Nombre] - Desarrollador Web">
    <title>[Tu Nombre] - Desarrollador Web</title>
</head>
<body>
    <header>
        <h1>Bienvenido a mi sitio web</h1>
        <nav>
            <ul>
                <li><a href="#sobre-mi">Sobre mí</a></li>
                <li><a href="#habilidades">Habilidades</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="sobre-mi">
            <h2>Sobre mí</h2>
            <img src="mi-foto.jpg" alt="Foto de [Tu Nombre]" width="200">
            <p>Hola, soy [Tu Nombre], un apasionado del desarrollo web en formación. 
               Me encanta crear experiencias digitales que sean útiles y atractivas para los usuarios.</p>
            <p>Actualmente estoy aprendiendo las tecnologías fundamentales del desarrollo web 
               y busco constantemente nuevos desafíos para mejorar mis habilidades.</p>
        </section>

        <section id="habilidades">
            <h2>Mis Habilidades</h2>
            <h3>Tecnologías que estoy aprendiendo:</h3>
            <ul>
                <li>HTML5 - Estructura semántica</li>
                <li>CSS3 - Diseño y estilos</li>
                <li>JavaScript - Interactividad</li>
                <li>Git - Control de versiones</li>
            </ul>
        </section>

        <section id="contacto">
            <h2>Contacto</h2>
            <p>¿Tienes alguna pregunta o quieres colaborar? ¡Escríbeme!</p>
            
            <form action="#" method="POST">
                <p>
                    <label for="nombre">Nombre completo:</label><br>
                    <input type="text" id="nombre" name="nombre" required>
                </p>
                
                <p>
                    <label for="email">Email:</label><br>
                    <input type="email" id="email" name="email" required>
                </p>
                
                <p>
                    <label for="asunto">Asunto:</label><br>
                    <select id="asunto" name="asunto" required>
                        <option value="">Selecciona un asunto</option>
                        <option value="colaboracion">Colaboración</option>
                        <option value="consulta">Consulta técnica</option>
                        <option value="trabajo">Oportunidad laboral</option>
                        <option value="otro">Otro</option>
                    </select>
                </p>
                
                <p>
                    <label for="mensaje">Mensaje:</label><br>
                    <textarea id="mensaje" name="mensaje" rows="5" cols="50" 
                              placeholder="Escribe tu mensaje aquí..." required></textarea>
                </p>
                
                <p>
                    <button type="submit">Enviar mensaje</button>
                    <button type="reset">Limpiar formulario</button>
                </p>
            </form>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 [Tu Nombre]. Creado como parte del aprendizaje de desarrollo web.</p>
        <p>Sígueme en: 
            <a href="https://github.com/tu-usuario" target="_blank">GitHub</a> | 
            <a href="https://linkedin.com/in/tu-perfil" target="_blank">LinkedIn</a>
        </p>
    </footer>
</body>
</html>
```

### Elementos a personalizar:
- Reemplazar `[Tu Nombre]` con tu nombre real
- Actualizar la información personal en la sección "Sobre mí"
- Añadir tu propia foto (o usar una imagen placeholder)
- Modificar las habilidades según tu progreso
- Actualizar los enlaces sociales con tus perfiles reales

### Próximos pasos:
Una vez completada esta práctica, estarás listo para el siguiente módulo donde aprenderemos CSS para dar estilo y mejorar la presentación visual de esta página web.

---

## Recursos adicionales

- [MDN Web Docs - HTML](https://developer.mozilla.org/es/docs/Web/HTML)
- [W3Schools HTML Tutorial](https://www.w3schools.com/html/)
- [HTML5 Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)
- [Can I Use](https://caniuse.com/) - Compatibilidad de navegadores
