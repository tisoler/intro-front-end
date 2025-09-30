# JavaScript Interactivo - Agregando Funcionalidad a las Páginas Web

## Objetivos del Encuentro
- Aprender a manejar eventos del usuario
- Manipular el DOM dinámicamente
- Realizar peticiones HTTP con fetch
- Trabajar con el objeto window
- Modificar estilos en tiempo real

---

## 1. Eventos en JavaScript

### ¿Qué son los eventos?
Los eventos son acciones que ocurren en la página web, como clics, teclas presionadas, movimiento del mouse, etc. JavaScript nos permite "escuchar" estos eventos y ejecutar código cuando suceden.

### Tipos de eventos más comunes
- `click` - Cuando se hace clic en un elemento
- `submit` - Cuando se envía un formulario
- `keydown/keyup` - Cuando se presiona/suelta una tecla
- `mouseover/mouseout` - Cuando el mouse entra/sale de un elemento
- `load` - Cuando la página termina de cargar

### Agregando Event Listeners

```javascript
// Método addEventListener (recomendado)
const boton = document.getElementById('miBoton');
boton.addEventListener('click', function() {
    alert('¡Botón clickeado!');
});

// Versión con arrow function
boton.addEventListener('click', () => {
    console.log('Botón clickeado');
});

// Evento con parámetro
boton.addEventListener('click', function(evento) {
    console.log('Tipo de evento:', evento.type);
    console.log('Elemento clickeado:', evento.target);
});
```

### Ejemplo práctico: Contador
```html
<button id="incrementar">+</button>
<span id="contador">0</span>
<button id="decrementar">-</button>
```

```javascript
let contador = 0;
const spanContador = document.getElementById('contador');
const botonIncrementar = document.getElementById('incrementar');
const botonDecrementar = document.getElementById('decrementar');

botonIncrementar.addEventListener('click', () => {
    contador++;
    spanContador.textContent = contador;
});

botonDecrementar.addEventListener('click', () => {
    contador--;
    spanContador.textContent = contador;
});
```

---

## 2. Manipulación del DOM

### Seleccionar elementos
```javascript
// Por ID
const elemento = document.getElementById('miId');

// Por clase (primer elemento)
const elemento = document.querySelector('.miClase');

// Por clase (todos los elementos)
const elementos = document.querySelectorAll('.miClase');

// Por etiqueta
const parrafos = document.querySelectorAll('p');
```

### Crear elementos dinámicamente
```javascript
// Crear un nuevo elemento
const nuevoDiv = document.createElement('div');
nuevoDiv.textContent = 'Soy un div nuevo';
nuevoDiv.className = 'contenedor';

// Agregarlo al DOM
document.body.appendChild(nuevoDiv);

// O agregarlo a un contenedor específico
const contenedor = document.getElementById('contenedor');
contenedor.appendChild(nuevoDiv);
```

### Modificar contenido y atributos
```javascript
const elemento = document.getElementById('miElemento');

// Cambiar texto
elemento.textContent = 'Nuevo texto';

// Cambiar HTML interno
elemento.innerHTML = '<strong>Texto en negrita</strong>';

// Cambiar atributos
elemento.setAttribute('data-valor', '123');
elemento.id = 'nuevoId';
elemento.className = 'nuevaClase';
```

### Ejemplo práctico: Lista de tareas
```html
<input type="text" id="nuevaTarea" placeholder="Nueva tarea">
<button id="agregar">Agregar</button>
<ul id="listaTareas"></ul>
```

```javascript
const input = document.getElementById('nuevaTarea');
const botonAgregar = document.getElementById('agregar');
const lista = document.getElementById('listaTareas');

function agregarTarea() {
    const textoTarea = input.value.trim();
    
    if (textoTarea === '') {
        alert('Por favor ingresa una tarea');
        return;
    }
    
    // Crear elementos
    const li = document.createElement('li');
    const botonEliminar = document.createElement('button');
    
    li.textContent = textoTarea;
    botonEliminar.textContent = 'Eliminar';
    
    // Agregar evento de eliminar
    botonEliminar.addEventListener('click', () => {
        lista.removeChild(li);
    });
    
    // Agregar elementos al DOM
    li.appendChild(botonEliminar);
    lista.appendChild(li);
    
    // Limpiar input
    input.value = '';
}

botonAgregar.addEventListener('click', agregarTarea);

// También agregar con Enter
input.addEventListener('keydown', (evento) => {
    if (evento.key === 'Enter') {
        agregarTarea();
    }
});
```

---

## 3. Trabajando con estilos dinámicos

### Modificar estilos CSS desde JavaScript
```javascript
const elemento = document.getElementById('miElemento');

// Cambiar estilos individuales
elemento.style.color = 'red';
elemento.style.fontSize = '20px';
elemento.style.backgroundColor = '#f0f0f0';

// Cambiar múltiples estilos
elemento.style.cssText = 'color: blue; font-size: 16px; margin: 10px;';
```

### Trabajar con clases CSS
```javascript
const elemento = document.getElementById('miElemento');

// Agregar clase
elemento.classList.add('nuevaClase');

// Quitar clase
elemento.classList.remove('claseVieja');

// Alternar clase (toggle)
elemento.classList.toggle('activo');

// Verificar si tiene una clase
if (elemento.classList.contains('activo')) {
    console.log('El elemento está activo');
}
```

### Ejemplo práctico: Tema oscuro/claro
```html
<button id="cambiarTema">🌙 Cambiar tema</button>
<div class="contenido">
    <h1>Mi página web</h1>
    <p>Contenido de ejemplo</p>
</div>
```

```css
/* Estilos en CSS */
.tema-oscuro {
    background-color: #333;
    color: white;
}

.tema-oscuro .contenido {
    background-color: #555;
    padding: 20px;
    border-radius: 8px;
}
```

```javascript
const botonTema = document.getElementById('cambiarTema');
let temaOscuro = false;

botonTema.addEventListener('click', () => {
    document.body.classList.toggle('tema-oscuro');
    temaOscuro = !temaOscuro;
    
    botonTema.textContent = temaOscuro ? '☀️ Cambiar tema' : '🌙 Cambiar tema';
});
```

---

## 4. El objeto Window

### ¿Qué es el objeto window?
El objeto `window` representa la ventana del navegador y proporciona métodos para interactuar con ella.

### Redirección de páginas
```javascript
// Redirigir a otra página
window.location.href = 'https://www.google.com';

// O simplemente
location.href = 'nueva-pagina.html';

// Recargar la página actual
window.location.reload();

// Ir atrás en el historial
window.history.back();

// Ir adelante en el historial
window.history.forward();
```

### Trabajar con parámetros de URL
```javascript
// URL ejemplo: https://misite.com/pagina.html?nombre=Juan&edad=25

// Obtener todos los parámetros
const parametros = new URLSearchParams(window.location.search);

// Obtener un parámetro específico
const nombre = parametros.get('nombre'); // "Juan"
const edad = parametros.get('edad'); // "25"

// Verificar si existe un parámetro
if (parametros.has('nombre')) {
    console.log('El parámetro nombre existe');
}

// Obtener todos los parámetros como objeto
const todosParametros = Object.fromEntries(parametros);
console.log(todosParametros); // {nombre: "Juan", edad: "25"}
```

### Ejemplo práctico: Saludo personalizado
```javascript
// Obtener nombre de la URL
const params = new URLSearchParams(window.location.search);
const nombre = params.get('nombre');

if (nombre) {
    document.getElementById('saludo').textContent = `¡Hola, ${nombre}!`;
} else {
    // Pedir nombre y redirigir
    const nombreUsuario = prompt('¿Cuál es tu nombre?');
    if (nombreUsuario) {
        window.location.href = `${window.location.pathname}?nombre=${nombreUsuario}`;
    }
}
```

### Ventanas emergentes y diálogos
```javascript
// Alerta simple
window.alert('¡Hola mundo!');

// Confirmación (devuelve true/false)
const confirmar = window.confirm('¿Estás seguro?');
if (confirmar) {
    console.log('Usuario confirmó');
}

// Prompt para input del usuario
const respuesta = window.prompt('¿Cuál es tu color favorito?');
console.log('Color favorito:', respuesta);
```

---

## 5. Fetch - Peticiones HTTP

### ¿Qué es fetch?
Fetch es una función moderna de JavaScript que permite realizar peticiones HTTP a servidores para obtener o enviar datos.

### Sintaxis básica
```javascript
fetch('https://api.ejemplo.com/datos')
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error('Error:', error);
    });
```

### Con async/await (más moderno)
```javascript
async function obtenerDatos() {
    try {
        const response = await fetch('https://api.ejemplo.com/datos');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Error:', error);
    }
}
```

### Ejemplo práctico: Cargar frases aleatorias
```html
<button id="cargarFrase">Cargar frase inspiradora</button>
<div id="frase"></div>
```

```javascript
const botonCargar = document.getElementById('cargarFrase');
const divFrase = document.getElementById('frase');

async function cargarFrase() {
    try {
        // Mostrar loading
        divFrase.innerHTML = '<p>Cargando...</p>';
        
        const response = await fetch('https://api.quotable.io/random');
        const data = await response.json();
        
        divFrase.innerHTML = `
            <blockquote>
                <p>"${data.content}"</p>
                <cite>- ${data.author}</cite>
            </blockquote>
        `;
    } catch (error) {
        divFrase.innerHTML = '<p>Error al cargar la frase</p>';
        console.error('Error:', error);
    }
}

botonCargar.addEventListener('click', cargarFrase);
```

### Ejemplo con datos locales (JSON)
```javascript
// archivo: datos.json
{
    "productos": [
        {"id": 1, "nombre": "Laptop", "precio": 1000},
        {"id": 2, "nombre": "Mouse", "precio": 25},
        {"id": 3, "nombre": "Teclado", "precio": 75}
    ]
}

// JavaScript
async function cargarProductos() {
    try {
        const response = await fetch('./datos.json');
        const datos = await response.json();
        
        const contenedor = document.getElementById('productos');
        contenedor.innerHTML = '';
        
        datos.productos.forEach(producto => {
            const div = document.createElement('div');
            div.innerHTML = `
                <h3>${producto.nombre}</h3>
                <p>Precio: $${producto.precio}</p>
            `;
            contenedor.appendChild(div);
        });
    } catch (error) {
        console.error('Error:', error);
    }
}
```

---

## 6. Proyecto Integrador: Mini Dashboard

Vamos a crear un pequeño dashboard que combine todos los conceptos:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Mi Dashboard</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .dashboard { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
        .card { border: 1px solid #ddd; padding: 20px; border-radius: 8px; }
        .button { background: #007bff; color: white; border: none; padding: 10px 15px; border-radius: 4px; cursor: pointer; }
        .button:hover { background: #0056b3; }
        .tema-oscuro { background: #333; color: white; }
        .tema-oscuro .card { background: #555; border-color: #666; }
    </style>
</head>
<body>
    <h1>Mi Dashboard Personal</h1>
    <button id="cambiarTema" class="button">🌙 Tema Oscuro</button>
    
    <div class="dashboard">
        <div class="card">
            <h2>Contador</h2>
            <p>Valor: <span id="contador">0</span></p>
            <button id="incrementar" class="button">+1</button>
            <button id="decrementar" class="button">-1</button>
        </div>
        
        <div class="card">
            <h2>Información del Usuario</h2>
            <p id="infoUsuario">Cargando...</p>
            <button id="cambiarUsuario" class="button">Cambiar Usuario</button>
        </div>
        
        <div class="card">
            <h2>Frase del Día</h2>
            <div id="frase">Haz clic para cargar una frase</div>
            <button id="cargarFrase" class="button">Nueva Frase</button>
        </div>
        
        <div class="card">
            <h2>Notas Rápidas</h2>
            <input type="text" id="nuevaNota" placeholder="Escribe una nota...">
            <button id="agregarNota" class="button">Agregar</button>
            <ul id="listaNotas"></ul>
        </div>
    </div>
</body>
</html>
```

```javascript
// Inicialización cuando carga la página
document.addEventListener('DOMContentLoaded', function() {
    inicializarDashboard();
});

function inicializarDashboard() {
    // Variables globales
    let contador = 0;
    let temaOscuro = false;
    
    // Elementos del DOM
    const elementos = {
        contador: document.getElementById('contador'),
        incrementar: document.getElementById('incrementar'),
        decrementar: document.getElementById('decrementar'),
        cambiarTema: document.getElementById('cambiarTema'),
        infoUsuario: document.getElementById('infoUsuario'),
        cambiarUsuario: document.getElementById('cambiarUsuario'),
        frase: document.getElementById('frase'),
        cargarFrase: document.getElementById('cargarFrase'),
        nuevaNota: document.getElementById('nuevaNota'),
        agregarNota: document.getElementById('agregarNota'),
        listaNotas: document.getElementById('listaNotas')
    };
    
    // Funcionalidad del contador
    elementos.incrementar.addEventListener('click', () => {
        contador++;
        elementos.contador.textContent = contador;
    });
    
    elementos.decrementar.addEventListener('click', () => {
        contador--;
        elementos.contador.textContent = contador;
    });
    
    // Cambio de tema
    elementos.cambiarTema.addEventListener('click', () => {
        document.body.classList.toggle('tema-oscuro');
        temaOscuro = !temaOscuro;
        elementos.cambiarTema.textContent = temaOscuro ? '☀️ Tema Claro' : '🌙 Tema Oscuro';
    });
    
    // Información del usuario (desde URL params)
    function mostrarInfoUsuario() {
        const params = new URLSearchParams(window.location.search);
        const nombre = params.get('usuario') || 'Usuario Anónimo';
        elementos.infoUsuario.textContent = `¡Bienvenido, ${nombre}!`;
    }
    
    elementos.cambiarUsuario.addEventListener('click', () => {
        const nuevoUsuario = prompt('¿Cuál es tu nombre?');
        if (nuevoUsuario) {
            const nuevaUrl = `${window.location.pathname}?usuario=${encodeURIComponent(nuevoUsuario)}`;
            window.location.href = nuevaUrl;
        }
    });
    
    // Cargar frases
    async function cargarFraseAleatoria() {
        try {
            elementos.frase.innerHTML = '<p>Cargando frase...</p>';
            const response = await fetch('https://api.quotable.io/random');
            const data = await response.json();
            elementos.frase.innerHTML = `<blockquote><p>"${data.content}"</p><cite>- ${data.author}</cite></blockquote>`;
        } catch (error) {
            elementos.frase.innerHTML = '<p>Error al cargar frase</p>';
        }
    }
    
    elementos.cargarFrase.addEventListener('click', cargarFraseAleatoria);
    
    // Sistema de notas
    function agregarNota() {
        const textoNota = elementos.nuevaNota.value.trim();
        if (textoNota === '') return;
        
        const li = document.createElement('li');
        const botonEliminar = document.createElement('button');
        
        li.textContent = textoNota;
        botonEliminar.textContent = '❌';
        botonEliminar.style.marginLeft = '10px';
        botonEliminar.style.cursor = 'pointer';
        botonEliminar.addEventListener('click', () => {
            elementos.listaNotas.removeChild(li);
        });
        
        li.appendChild(botonEliminar);
        elementos.listaNotas.appendChild(li);
        elementos.nuevaNota.value = '';
    }
    
    elementos.agregarNota.addEventListener('click', agregarNota);
    elementos.nuevaNota.addEventListener('keydown', (e) => {
        if (e.key === 'Enter') agregarNota();
    });
    
    // Inicializar
    mostrarInfoUsuario();
}
```

---

## Ejercicios Propuestos

### Ejercicio 1: Calculadora Simple
Crea una calculadora con botones para números y operaciones básicas (+, -, *, /).

### Ejercicio 2: Galería de Imágenes
Crea una galería que cargue imágenes desde una API y permita navegarlas con botones anterior/siguiente.

### Ejercicio 3: Formulario Dinámico
Crea un formulario que agregue campos dinámicamente y valide los datos antes de enviarlos.

### Ejercicio 4: Clima Local
Usa la API de clima para mostrar el clima actual según los parámetros de la URL.

---

## Recursos Adicionales

- [MDN Web Docs - Events](https://developer.mozilla.org/en-US/docs/Web/Events)
- [MDN Web Docs - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [APIs públicas gratuitas](https://public-apis.io/)
- [Can I Use](https://caniuse.com/) - Compatibilidad de navegadores

---

## Resumen de Conceptos Clave

1. **Eventos**: Permiten responder a acciones del usuario
2. **DOM Manipulation**: Crear, modificar y eliminar elementos dinámicamente
3. **Estilos dinámicos**: Cambiar la apariencia en tiempo real
4. **Window object**: Navegar, obtener parámetros y controlar la ventana
5. **Fetch**: Realizar peticiones HTTP para obtener datos externos

¡Con estos conocimientos ya puedes crear páginas web verdaderamente interactivas!
