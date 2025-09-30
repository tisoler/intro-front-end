# JavaScript Interactivo - Conceptos Adicionales

## 6. Formularios y Validación

### ¿Qué son los formularios en JavaScript?
Los formularios son la principal forma de capturar datos del usuario. JavaScript nos permite interceptar, validar y procesar estos datos antes de enviarlos.

### Capturando datos de formularios
```javascript
const formulario = document.getElementById('miFormulario');

formulario.addEventListener('submit', function(evento) {
    evento.preventDefault(); // Evitar envío automático
    
    const datos = {
        nombre: document.getElementById('nombre').value,
        email: document.getElementById('email').value,
        mensaje: document.getElementById('mensaje').value
    };
    
    console.log('Datos capturados:', datos);
});
```

### Validación básica
```javascript
function validarEmail(email) {
    const patron = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return patron.test(email);
}

function validarFormulario() {
    const nombre = document.getElementById('nombre').value;
    const email = document.getElementById('email').value;
    
    if (nombre.length < 2) {
        alert('El nombre debe tener al menos 2 caracteres');
        return false;
    }
    
    if (!validarEmail(email)) {
        alert('Email inválido');
        return false;
    }
    
    return true;
}
```

### Ejemplo práctico: Formulario con validación
```html
<form id="contacto">
    <input type="text" id="nombre" placeholder="Nombre" required>
    <input type="email" id="email" placeholder="Email" required>
    <button type="submit">Enviar</button>
</form>
<div id="mensajes"></div>
```

```javascript
document.getElementById('contacto').addEventListener('submit', function(e) {
    e.preventDefault();
    
    const nombre = document.getElementById('nombre').value.trim();
    const email = document.getElementById('email').value.trim();
    const mensajes = document.getElementById('mensajes');
    
    // Limpiar mensajes anteriores
    mensajes.innerHTML = '';
    
    // Validar
    if (nombre.length < 2) {
        mensajes.innerHTML = '<p style="color: red;">Nombre muy corto</p>';
        return;
    }
    
    if (!email.includes('@')) {
        mensajes.innerHTML = '<p style="color: red;">Email inválido</p>';
        return;
    }
    
    // Éxito
    mensajes.innerHTML = '<p style="color: green;">¡Formulario enviado!</p>';
    this.reset();
});
```

---

## 7. Local Storage y Session Storage

### ¿Qué es el almacenamiento web?
El navegador puede guardar datos localmente. LocalStorage persiste al cerrar el navegador, SessionStorage solo durante la sesión actual.

### LocalStorage - Datos permanentes
```javascript
// Guardar datos
localStorage.setItem('usuario', 'Juan');
localStorage.setItem('config', JSON.stringify({ tema: 'oscuro', idioma: 'es' }));

// Recuperar datos
const usuario = localStorage.getItem('usuario');
const config = JSON.parse(localStorage.getItem('config') || '{}');

// Eliminar datos
localStorage.removeItem('usuario');
localStorage.clear(); // Eliminar todo
```

### SessionStorage - Datos temporales
```javascript
// Solo existe durante la sesión actual
sessionStorage.setItem('carrito', JSON.stringify(['producto1', 'producto2']));
const carrito = JSON.parse(sessionStorage.getItem('carrito') || '[]');
```

### Ejemplo práctico: Preferencias de usuario
```html
<div>
    <label>
        <input type="checkbox" id="temaOscuro"> Tema oscuro
    </label>
    <button id="guardar">Guardar Preferencias</button>
</div>
```

```javascript
// Cargar preferencias al iniciar
function cargarPreferencias() {
    const temaOscuro = localStorage.getItem('temaOscuro') === 'true';
    document.getElementById('temaOscuro').checked = temaOscuro;
    document.body.classList.toggle('tema-oscuro', temaOscuro);
}

// Guardar preferencias
document.getElementById('guardar').addEventListener('click', function() {
    const temaOscuro = document.getElementById('temaOscuro').checked;
    
    localStorage.setItem('temaOscuro', temaOscuro);
    document.body.classList.toggle('tema-oscuro', temaOscuro);
    
    alert('Preferencias guardadas');
});

// Cargar al iniciar la página
cargarPreferencias();
```

### Ejemplo: Lista persistente
```javascript
class ListaPersistente {
    constructor() {
        this.items = JSON.parse(localStorage.getItem('miLista') || '[]');
        this.mostrar();
    }
    
    agregar(item) {
        this.items.push(item);
        this.guardar();
        this.mostrar();
    }
    
    eliminar(index) {
        this.items.splice(index, 1);
        this.guardar();
        this.mostrar();
    }
    
    guardar() {
        localStorage.setItem('miLista', JSON.stringify(this.items));
    }
    
    mostrar() {
        const lista = document.getElementById('lista');
        lista.innerHTML = '';
        
        this.items.forEach((item, index) => {
            const li = document.createElement('li');
            li.innerHTML = `${item} <button onclick="lista.eliminar(${index})">X</button>`;
            lista.appendChild(li);
        });
    }
}

const lista = new ListaPersistente();
```

---

## 8. Timers e Intervalos

### setTimeout - Ejecutar una vez después de un tiempo
```javascript
// Ejecutar después de 3 segundos
setTimeout(function() {
    alert('¡3 segundos han pasado!');
}, 3000);

// Con arrow function
setTimeout(() => {
    console.log('Hola después de 2 segundos');
}, 2000);

// Cancelar un timeout
const temporizador = setTimeout(() => alert('Cancelado'), 5000);
clearTimeout(temporizador);
```

### setInterval - Ejecutar repetidamente
```javascript
// Ejecutar cada segundo
const intervalo = setInterval(function() {
    console.log('Cada segundo');
}, 1000);

// Detener después de 10 segundos
setTimeout(function() {
    clearInterval(intervalo);
    console.log('Intervalo detenido');
}, 10000);
```

### Ejemplo práctico: Reloj digital
```html
<div id="reloj">00:00:00</div>
```

```javascript
function actualizarReloj() {
    const ahora = new Date();
    const tiempo = ahora.toLocaleTimeString();
    document.getElementById('reloj').textContent = tiempo;
}

// Actualizar inmediatamente y luego cada segundo
actualizarReloj();
setInterval(actualizarReloj, 1000);
```

### Ejemplo: Cronómetro simple
```html
<div id="cronometro">00:00</div>
<button id="iniciar">Iniciar</button>
<button id="pausar">Pausar</button>
<button id="reiniciar">Reiniciar</button>
```

```javascript
let segundos = 0;
let intervalo = null;
let corriendo = false;

function actualizarCronometro() {
    const mins = Math.floor(segundos / 60);
    const segs = segundos % 60;
    document.getElementById('cronometro').textContent = 
        `${mins.toString().padStart(2, '0')}:${segs.toString().padStart(2, '0')}`;
}

document.getElementById('iniciar').addEventListener('click', function() {
    if (!corriendo) {
        corriendo = true;
        intervalo = setInterval(function() {
            segundos++;
            actualizarCronometro();
        }, 1000);
    }
});

document.getElementById('pausar').addEventListener('click', function() {
    corriendo = false;
    clearInterval(intervalo);
});

document.getElementById('reiniciar').addEventListener('click', function() {
    corriendo = false;
    clearInterval(intervalo);
    segundos = 0;
    actualizarCronometro();
});
```

### Ejemplo: Contador regresivo
```javascript
function crearCountdown(minutos) {
    let tiempoRestante = minutos * 60;
    
    const intervalo = setInterval(function() {
        const mins = Math.floor(tiempoRestante / 60);
        const segs = tiempoRestante % 60;
        
        console.log(`${mins}:${segs.toString().padStart(2, '0')}`);
        
        tiempoRestante--;
        
        if (tiempoRestante < 0) {
            clearInterval(intervalo);
            alert('¡Tiempo agotado!');
        }
    }, 1000);
}

// Countdown de 5 minutos
crearCountdown(5);
```

---

## 9. Manejo Avanzado de Errores

### Try-Catch básico
```javascript
try {
    // Código que puede fallar
    const data = JSON.parse(jsonString);
    console.log(data);
} catch (error) {
    console.error('Error al procesar JSON:', error.message);
    // Código alternativo
    const data = {};
}
```

### Manejo de errores con fetch
```javascript
async function cargarDatos() {
    try {
        const response = await fetch('https://api.ejemplo.com/datos');
        
        if (!response.ok) {
            throw new Error(`Error ${response.status}: ${response.statusText}`);
        }
        
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error de red:', error);
        
        // Mostrar mensaje amigable al usuario
        document.getElementById('mensaje').textContent = 
            'No se pudieron cargar los datos. Intenta más tarde.';
        
        return null;
    }
}
```

### Sistema simple de notificaciones
```html
<div id="notificaciones"></div>
```

```javascript
function mostrarNotificacion(mensaje, tipo = 'info') {
    const notificaciones = document.getElementById('notificaciones');
    const div = document.createElement('div');
    
    div.className = `notificacion ${tipo}`;
    div.textContent = mensaje;
    div.style.cssText = `
        padding: 10px; margin: 5px 0; border-radius: 4px;
        background: ${tipo === 'error' ? '#ffebee' : '#e8f5e8'};
        color: ${tipo === 'error' ? '#c62828' : '#2e7d32'};
    `;
    
    notificaciones.appendChild(div);
    
    // Auto-eliminar después de 3 segundos
    setTimeout(() => {
        if (div.parentNode) {
            div.remove();
        }
    }, 3000);
}

// Uso
try {
    // Operación riesgosa
    const resultado = operacionRiesgosa();
    mostrarNotificacion('Operación exitosa', 'exito');
} catch (error) {
    mostrarNotificacion('Error en la operación', 'error');
}
```

### Validación con manejo de errores
```javascript
function validarDatos(datos) {
    const errores = [];
    
    if (!datos.nombre || datos.nombre.trim().length < 2) {
        errores.push('Nombre inválido');
    }
    
    if (!datos.email || !datos.email.includes('@')) {
        errores.push('Email inválido');
    }
    
    if (!datos.edad || datos.edad < 18) {
        errores.push('Debe ser mayor de 18 años');
    }
    
    if (errores.length > 0) {
        throw new Error('Datos inválidos: ' + errores.join(', '));
    }
    
    return true;
}

// Uso
try {
    validarDatos({ nombre: 'Juan', email: 'juan@email.com', edad: 25 });
    console.log('Datos válidos');
} catch (error) {
    console.error(error.message);
}
```

---

## 10. Delegación de Eventos

### ¿Qué es la delegación de eventos?
La delegación permite manejar eventos de elementos que se crean dinámicamente, aprovechando que los eventos "burbujean" hacia arriba en el DOM.

### Problema con elementos dinámicos
```javascript
// ❌ Esto NO funciona para botones creados después
document.querySelectorAll('.boton-eliminar').forEach(boton => {
    boton.addEventListener('click', eliminar);
});

// ✅ Esto SÍ funciona para elementos dinámicos
document.body.addEventListener('click', function(evento) {
    if (evento.target.classList.contains('boton-eliminar')) {
        eliminar(evento);
    }
});
```

### Ejemplo práctico: Lista dinámica
```html
<button id="agregar">Agregar Item</button>
<ul id="lista"></ul>
```

```javascript
let contador = 0;
const lista = document.getElementById('lista');

// Agregar nuevos items
document.getElementById('agregar').addEventListener('click', function() {
    contador++;
    const li = document.createElement('li');
    li.innerHTML = `
        Item ${contador} 
        <button class="eliminar">Eliminar</button>
        <button class="editar">Editar</button>
    `;
    lista.appendChild(li);
});

// Delegación: manejar clicks en botones dinámicos
lista.addEventListener('click', function(evento) {
    const elemento = evento.target;
    const li = elemento.closest('li');
    
    if (elemento.classList.contains('eliminar')) {
        li.remove();
        console.log('Item eliminado');
    }
    
    if (elemento.classList.contains('editar')) {
        const nuevoTexto = prompt('Nuevo texto:', li.firstChild.textContent.trim());
        if (nuevoTexto) {
            li.firstChild.textContent = nuevoTexto + ' ';
        }
    }
});
```

### Delegación con diferentes tipos de eventos
```javascript
// Manejar múltiples tipos de eventos
document.addEventListener('click', manejarClick);
document.addEventListener('change', manejarCambio);
document.addEventListener('keydown', manejarTecla);

function manejarClick(evento) {
    const elemento = evento.target;
    
    if (elemento.classList.contains('boton-guardar')) {
        guardarDatos();
    } else if (elemento.classList.contains('boton-cancelar')) {
        cancelarOperacion();
    }
}

function manejarCambio(evento) {
    const elemento = evento.target;
    
    if (elemento.type === 'checkbox') {
        console.log(`Checkbox ${elemento.checked ? 'marcado' : 'desmarcado'}`);
    }
}

function manejarTecla(evento) {
    if (evento.key === 'Escape') {
        cerrarModal();
    } else if (evento.key === 'Enter' && evento.target.tagName === 'INPUT') {
        procesarInput(evento.target);
    }
}
```

### Ejemplo completo: Todo list con delegación
```html
<input type="text" id="nuevaTarea" placeholder="Nueva tarea">
<button id="agregar">Agregar</button>
<ul id="tareas"></ul>
```

```javascript
const tareas = [];
const listaTareas = document.getElementById('tareas');

// Agregar nueva tarea
document.getElementById('agregar').addEventListener('click', agregarTarea);
document.getElementById('nuevaTarea').addEventListener('keydown', function(e) {
    if (e.key === 'Enter') agregarTarea();
});

function agregarTarea() {
    const input = document.getElementById('nuevaTarea');
    const texto = input.value.trim();
    
    if (texto) {
        const tarea = {
            id: Date.now(),
            texto: texto,
            completada: false
        };
        
        tareas.push(tarea);
        input.value = '';
        mostrarTareas();
    }
}

// Delegación para manejar todas las acciones de las tareas
listaTareas.addEventListener('click', function(evento) {
    const elemento = evento.target;
    const li = elemento.closest('li');
    const id = parseInt(li.dataset.id);
    
    if (elemento.classList.contains('completar')) {
        toggleCompletada(id);
    } else if (elemento.classList.contains('eliminar')) {
        eliminarTarea(id);
    }
});

function mostrarTareas() {
    listaTareas.innerHTML = '';
    
    tareas.forEach(tarea => {
        const li = document.createElement('li');
        li.dataset.id = tarea.id;
        li.innerHTML = `
            <span style="text-decoration: ${tarea.completada ? 'line-through' : 'none'}">
                ${tarea.texto}
            </span>
            <button class="completar">${tarea.completada ? 'Desmarcar' : 'Completar'}</button>
            <button class="eliminar">Eliminar</button>
        `;
        listaTareas.appendChild(li);
    });
}

function toggleCompletada(id) {
    const tarea = tareas.find(t => t.id === id);
    if (tarea) {
        tarea.completada = !tarea.completada;
        mostrarTareas();
    }
}

function eliminarTarea(id) {
    const index = tareas.findIndex(t => t.id === id);
    if (index !== -1) {
        tareas.splice(index, 1);
        mostrarTareas();
    }
}
```

---

## Conceptos Clave de esta Sección

### ✅ **Formularios**
- `preventDefault()` para controlar el envío
- Captura de datos con `.value`
- Validación con expresiones regulares
- Feedback inmediato al usuario

### ✅ **Storage**
- `localStorage` para datos permanentes
- `sessionStorage` para datos temporales
- `JSON.stringify()` y `JSON.parse()` para objetos
- Verificar existencia con `|| '{}'`

### ✅ **Timers**
- `setTimeout()` para ejecución única
- `setInterval()` para repetición
- Siempre usar `clearTimeout()` y `clearInterval()`
- Padstart para formato de tiempo

### ✅ **Errores**
- `try-catch` para capturar errores
- Verificar `response.ok` en fetch
- Mensajes amigables al usuario
- Logging para debugging

### ✅ **Delegación**
- Event bubbling para elementos dinámicos
- `event.target` vs `event.currentTarget`
- `closest()` para encontrar elementos padre
- Un solo listener para múltiples elementos
