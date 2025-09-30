# JavaScript Nivel Inicial - Primer Encuentro

## 1. Introducción a JavaScript

### 1.1 Un poco de historia

JavaScript fue creado en **1995** por **Brendan Eich** en la empresa Netscape Communications. Algunos datos importantes:

- **Tiempo de desarrollo**: Fue creado en solo **10 días**
- **Nombre original**: Mocha, luego LiveScript, y finalmente JavaScript
- **¿Por qué "Java"Script?**: Por marketing, para aprovechar la popularidad de Java (aunque son lenguajes completamente diferentes)
- **Evolución**: De ser un simple lenguaje para páginas web a convertirse en uno de los lenguajes más populares del mundo

**Línea de tiempo clave:**
- 1995: Creación de JavaScript
- 1997: Primera estandarización (ECMAScript 1)
- 2009: ECMAScript 5 (gran actualización)
- 2015: ECMAScript 6/ES2015 (revolución moderna)
- Actualidad: Actualizaciones anuales

### 1.2 Usos de JavaScript

JavaScript ha evolucionado mucho desde sus inicios. Hoy se usa en:

#### Frontend (Cliente)
- **Páginas web interactivas**: Validación de formularios, efectos visuales
- **Aplicaciones web complejas**: Gmail, Facebook, Netflix
- **Frameworks populares**: React, Vue.js, Angular

#### Backend (Servidor)
- **Node.js**: Permite ejecutar JavaScript en el servidor
- **APIs y servicios web**: Crear servicios que respondan a aplicaciones
- **Bases de datos**: MongoDB usa JavaScript para consultas

#### Aplicaciones Móviles
- **React Native**: Apps nativas para iOS y Android
- **Ionic**: Apps híbridas multiplataforma

#### Otras aplicaciones
- **Aplicaciones de escritorio**: Electron (Visual Studio Code, Discord)
- **Juegos**: Desarrollo de videojuegos en navegador
- **Internet of Things (IoT)**: Programación de dispositivos inteligentes

### 1.3 ECMAScript

**ECMAScript (ES)** es el estándar oficial que define JavaScript. Es importante entenderlo:

#### ¿Qué es ECMAScript?
- **Estándar internacional**: Define las reglas y características del lenguaje
- **Organización**: Mantenido por ECMA International
- **Relación con JavaScript**: JavaScript es una implementación de ECMAScript

#### Versiones importantes
- **ES5 (2009)**: Añadió métodos de arrays, JSON, modo estricto
- **ES6/ES2015 (2015)**: Gran revolución - let/const, arrow functions, clases
- **ES2016-ES2023**: Actualizaciones anuales con nuevas características
- **ES2024**: Versión más reciente

#### Ejemplo de evolución:
```javascript
// Estilo antiguo (ES5)
var nombre = "Juan";
function saludar() {
    return "Hola " + nombre;
}

// Estilo moderno (ES6+)
const nombre = "Juan";
const saludar = () => `Hola ${nombre}`;
```

---

## 2. Fundamentos de JavaScript

### 2.1 Sintaxis Básica

#### Variables: let y const

Las variables son contenedores que almacenan datos. En JavaScript moderno usamos `let` y `const`:

##### `let` - Variables que pueden cambiar
```javascript
let nombre = "Ana";
let edad = 25;
let activo = true;

// Podemos cambiar su valor
nombre = "Carlos";
edad = 30;

console.log(nombre); // "Carlos"
```

##### `const` - Variables constantes (no cambian)
```javascript
const PI = 3.14159;
const nombreEmpresa = "TechCorp";
const diasSemana = 7;

// ❌ Error: no podemos cambiar una constante
// PI = 3.14; // Esto generaría un error
```

##### ¿Cuándo usar cada una?
- **`const`**: Cuando el valor no va a cambiar (recomendado por defecto)
- **`let`**: Cuando el valor puede cambiar durante la ejecución

#### Tipos de Datos

JavaScript maneja diferentes tipos de datos:

##### Tipos Primitivos

**1. String (texto)**
```javascript
let saludo = "Hola mundo";
let mensaje = 'JavaScript es genial';
let plantilla = `Mi nombre es ${nombre}`; // Template literals

// Métodos útiles
console.log(saludo.length); // 10
console.log(saludo.toUpperCase()); // "HOLA MUNDO"
```

**2. Number (números)**
```javascript
let entero = 42;
let decimal = 3.14;
let negativo = -100;

// Operaciones
console.log(entero + decimal); // 45.14
console.log(entero * 2); // 84
```

**3. Boolean (verdadero/falso)**
```javascript
let esMayor = true;
let esMenor = false;
let activo = true;

console.log(esMayor && activo); // true
console.log(esMayor || esMenor); // true
```

**4. Undefined y Null**
```javascript
let sinValor; // undefined
let vacio = null; // null (intencionalmente vacío)

console.log(sinValor); // undefined
console.log(vacio); // null
```

##### Tipos de Referencia

**Arrays (arreglos)**
```javascript
const frutas = ["manzana", "banana", "naranja"];
const numeros = [1, 2, 3, 4, 5];
const mixto = ["texto", 42, true];

console.log(frutas[0]); // "manzana"
console.log(frutas.length); // 3
```

**Objects (objetos)**
```javascript
const persona = {
    nombre: "María",
    edad: 28,
    activo: true
};

console.log(persona.nombre); // "María"
console.log(persona["edad"]); // 28
```

#### Operadores

##### Operadores Aritméticos
```javascript
let a = 10;
let b = 3;

console.log(a + b); // 13 (suma)
console.log(a - b); // 7 (resta)
console.log(a * b); // 30 (multiplicación)
console.log(a / b); // 3.333... (división)
console.log(a % b); // 1 (módulo/resto)
console.log(a ** b); // 1000 (potencia)
```

##### Operadores de Comparación
```javascript
let x = 5;
let y = "5";

console.log(x == y);  // true (igualdad simple)
console.log(x === y); // false (igualdad estricta)
console.log(x != y);  // false (desigualdad simple)
console.log(x !== y); // true (desigualdad estricta)
console.log(x > 3);   // true
console.log(x >= 5);  // true
console.log(x < 10);  // true
console.log(x <= 5);  // true
```

##### Operadores Lógicos
```javascript
let verdadero = true;
let falso = false;

console.log(verdadero && falso); // false (AND)
console.log(verdadero || falso); // true (OR)
console.log(!verdadero); // false (NOT)
```

### 2.2 Estructuras de Control

#### if/else - Condicionales

##### Estructura básica
```javascript
let edad = 18;

if (edad >= 18) {
    console.log("Eres mayor de edad");
} else {
    console.log("Eres menor de edad");
}
```

##### if/else if/else
```javascript
let nota = 85;

if (nota >= 90) {
    console.log("Excelente");
} else if (nota >= 80) {
    console.log("Muy bien");
} else if (nota >= 70) {
    console.log("Bien");
} else if (nota >= 60) {
    console.log("Suficiente");
} else {
    console.log("Insuficiente");
}
```

##### Condicionales con operadores lógicos
```javascript
let edad = 25;
let tieneCarnet = true;

if (edad >= 18 && tieneCarnet) {
    console.log("Puede conducir");
} else {
    console.log("No puede conducir");
}
```

#### for - Bucles de repetición

##### for tradicional
```javascript
// Contar del 1 al 5
for (let i = 1; i <= 5; i++) {
    console.log("Número: " + i);
}

// Recorrer un array
const colores = ["rojo", "verde", "azul"];
for (let i = 0; i < colores.length; i++) {
    console.log("Color: " + colores[i]);
}
```

##### for...of (para arrays)
```javascript
const frutas = ["manzana", "banana", "naranja"];

for (const fruta of frutas) {
    console.log("Fruta: " + fruta);
}
```

##### for...in (para objetos)
```javascript
const persona = {
    nombre: "Juan",
    edad: 30,
    ciudad: "Madrid"
};

for (const propiedad in persona) {
    console.log(propiedad + ": " + persona[propiedad]);
}
```

#### while - Bucle condicional

##### while básico
```javascript
let contador = 1;

while (contador <= 5) {
    console.log("Contador: " + contador);
    contador++; // Incrementar para evitar bucle infinito
}
```

##### do...while
```javascript
let numero;

do {
    numero = Math.floor(Math.random() * 10) + 1;
    console.log("Número generado: " + numero);
} while (numero !== 7);

console.log("¡Salió el 7!");
```

### 2.3 Funciones

Las funciones son bloques de código reutilizable que realizan una tarea específica.

#### Declaración de Funciones

##### Función tradicional
```javascript
function saludar() {
    console.log("¡Hola mundo!");
}

// Llamar la función
saludar(); // ¡Hola mundo!
```

##### Función con parámetros
```javascript
function saludarPersona(nombre) {
    console.log("¡Hola " + nombre + "!");
}

saludarPersona("Ana"); // ¡Hola Ana!
saludarPersona("Carlos"); // ¡Hola Carlos!
```

##### Función con múltiples parámetros
```javascript
function sumar(a, b) {
    console.log("La suma es: " + (a + b));
}

sumar(5, 3); // La suma es: 8
sumar(10, 20); // La suma es: 30
```

##### Parámetros con valores por defecto
```javascript
function presentarse(nombre, edad = "no especificada") {
    console.log(`Hola, soy ${nombre} y tengo ${edad} años`);
}

presentarse("María", 25); // Hola, soy María y tengo 25 años
presentarse("Juan"); // Hola, soy Juan y tengo no especificada años
```

#### Retorno de Valores

##### Función que retorna un valor
```javascript
function multiplicar(a, b) {
    return a * b;
}

let resultado = multiplicar(4, 5);
console.log(resultado); // 20

// Usar directamente el retorno
console.log("El doble de 8 es: " + multiplicar(8, 2)); // El doble de 8 es: 16
```

##### Función con múltiples retornos
```javascript
function evaluarNota(nota) {
    if (nota >= 90) {
        return "Excelente";
    } else if (nota >= 70) {
        return "Bueno";
    } else if (nota >= 50) {
        return "Regular";
    } else {
        return "Insuficiente";
    }
}

console.log(evaluarNota(85)); // Bueno
console.log(evaluarNota(95)); // Excelente
```

#### Expresiones de Función

##### Function Expression
```javascript
const calcularArea = function(base, altura) {
    return base * altura;
};

console.log(calcularArea(5, 3)); // 15
```

##### Arrow Functions (ES6+)
```javascript
// Sintaxis básica
const cuadrado = (numero) => {
    return numero * numero;
};

// Sintaxis simplificada (una línea)
const cubo = numero => numero * numero * numero;

// Sin parámetros
const saludar = () => console.log("¡Hola!");

// Múltiples parámetros
const dividir = (a, b) => a / b;

console.log(cuadrado(4)); // 16
console.log(cubo(3)); // 27
console.log(dividir(10, 2)); // 5
```

#### Ejemplos Prácticos Integradores

##### Calculadora básica
```javascript
function calculadora(operacion, a, b) {
    if (operacion === "suma") {
        return a + b;
    } else if (operacion === "resta") {
        return a - b;
    } else if (operacion === "multiplicacion") {
        return a * b;
    } else if (operacion === "division") {
        if (b !== 0) {
            return a / b;
        } else {
            return "Error: División por cero";
        }
    } else {
        return "Operación no válida";
    }
}

console.log(calculadora("suma", 10, 5)); // 15
console.log(calculadora("division", 10, 0)); // Error: División por cero
```

##### Validador de edad
```javascript
function puedeVotar(edad) {
    if (edad >= 18) {
        return true;
    } else {
        return false;
    }
}

function mostrarMensajeVoto(nombre, edad) {
    if (puedeVotar(edad)) {
        console.log(`${nombre} puede votar`);
    } else {
        console.log(`${nombre} no puede votar todavía`);
    }
}

mostrarMensajeVoto("Ana", 20); // Ana puede votar
mostrarMensajeVoto("Pedro", 16); // Pedro no puede votar todavía
```

---

## Ejercicios Prácticos

### Ejercicio 1: Variables y tipos de datos
Crear variables para almacenar información de un estudiante y mostrarla en consola.

### Ejercicio 2: Condicionales
Crear una función que determine si un año es bisiesto.

### Ejercicio 3: Bucles
Crear una función que muestre la tabla de multiplicar de un número.

### Ejercicio 4: Funciones
Crear una función que calcule el área de diferentes figuras geométricas.

---

## Recursos Adicionales

- **MDN Web Docs**: Documentación oficial de JavaScript
- **JavaScript.info**: Tutorial completo y actualizado
- **Console del navegador**: Para practicar código en tiempo real
- **Node.js**: Para ejecutar JavaScript fuera del navegador
