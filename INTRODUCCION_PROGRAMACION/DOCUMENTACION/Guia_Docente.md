# Guía para Docente
## Cuatrimestre 1 – Introducción a la Programación
### Curso de Programación en C++ Orientado a Videojuegos

Esta guía está diseñada para que **cualquier docente** pueda impartir el Cuatrimestre 1 con claridad, ritmo y consistencia.

Cada tema incluye:
- **Explicación para el alumno** (lenguaje sencillo, sin asumir experiencia previa)
- **Descripción para el docente** (explicación detallada para complementar la clase)
- **Conceptos clave** (con explicación + ejemplo)
- **Errores comunes** (con explicación + ejemplo)
- **6 ejemplos con código** contextualizados en videojuegos
- **2 ejercicios con solución**

> Nota: Los nombres en el código deben estar en **inglés** y seguir las convenciones del curso.

---

## TEMA 1 – ¿Qué es programar?

### Explicación para el alumno
Programar es darle instrucciones claras y ordenadas a una computadora para que realice una tarea. En videojuegos, programar significa definir reglas (qué está permitido), acciones (qué puede hacer el jugador) y consecuencias (qué pasa cuando lo hace).

### Descripción para el docente
Este tema construye el **modelo mental** del curso: programar no es “escribir código”, es **resolver problemas** con pasos bien definidos.

Sugerencia didáctica:
- Inicia con una analogía: una receta de cocina o reglas de un juego de mesa.
- Resalta que el código es solo la **representación** final de una solución ya pensada.
- Conecta con videojuegos: “si presiono jump, ¿qué debe ocurrir?” → eso es una regla programable.

Puntos a enfatizar:
- Un programa es una secuencia de instrucciones.
- La computadora ejecuta literalmente lo que se le indica.
- El programador debe pensar en casos: normal, error, borde.

### Conceptos clave (con explicación + ejemplo)
- **Programación:** traducir una solución a instrucciones ejecutables.
  - Ejemplo: definir cómo se gana: si `score >= 100` entonces victoria.
- **Algoritmo:** lista ordenada de pasos para lograr un objetivo.
  - Ejemplo: mostrar menú → leer opción → ejecutar acción.
- **Pensamiento paso a paso:** dividir un problema grande en acciones pequeñas.
  - Ejemplo: “jugar un turno” = elegir acción + aplicar daño + actualizar estado.

### Errores comunes (con explicación + ejemplo)
- **Creer que programar es memorizar código:** el alumno busca “la respuesta” en lugar de construirla.
  - Ejemplo: copia un `if` sin entender la condición.
- **Pensar que solo existe una solución correcta:** no entiende que hay muchas soluciones con distintos niveles de calidad.
  - Ejemplo: resuelve todo en un bloque gigante cuando podría separarlo en pasos.

### Ejemplos

**Ejemplo 1 – Secuencia de inicio de un juego (pseudocódigo)**
```cpp
Mostrar menu
Leer opcion
Ejecutar accion
```

**Ejemplo 2 – Algoritmo de turnos (pseudocódigo)**
```cpp
Jugador ataca
Enemigo responde
Actualizar estado
```

**Ejemplo 3 – Regla de victoria (pseudocódigo)**
```cpp
Si score >= 100
  Mostrar victoria
```

**Ejemplo 4 – Regla de derrota (pseudocódigo)**
```cpp
Si lives <= 0
  Mostrar Game Over
```

**Ejemplo 5 – Flujo simple de juego (pseudocódigo)**
```cpp
Iniciar juego
Jugar turno
Finalizar juego
```

**Ejemplo 6 – Algoritmo de pausa (pseudocódigo)**
```cpp
Si jugador pausa
  Detener juego
```

### Ejercicios (con solución)

**Ejercicio 1:** Escribir un algoritmo (pseudocódigo) para iniciar un juego con menú.

**Solución:**
```cpp
Mostrar menu
Leer opcion
Si opcion es jugar
  Iniciar juego
Si opcion es salir
  Terminar programa
```

**Ejercicio 2:** Escribir un algoritmo (pseudocódigo) para un sistema de vidas.

**Solución:**
```cpp
Inicializar lives
Mientras lives > 0
  Jugar turno
  Reducir vida si hay daño
```

---

## TEMA 2 – Diagramas de flujo y pseudocódigo

### Explicación para el alumno
Antes de escribir código, necesitamos ordenar ideas. Los **diagramas de flujo** muestran decisiones y repeticiones con dibujitos; el **pseudocódigo** lo escribe con frases. Ambos sirven para entender el programa antes de programarlo.

### Descripción para el docente
Este tema es el “puente” que evita que el alumno se lance al código sin estructura.

Sugerencia didáctica:
- Trabaja primero en pizarrón: un diagrama simple de menú.
- Luego conviértelo a pseudocódigo línea por línea.
- Finalmente menciona: “el código C++ será esta misma idea, pero con sintaxis”.

Puntos a enfatizar:
- Un diagrama debe tener inicio y fin.
- Toda decisión debe contemplar alternativas (sí/no o casos).
- Los ciclos deben tener condición de salida.

### Conceptos clave (con explicación + ejemplo)
- **Decisión:** punto donde el programa elige entre caminos.
  - Ejemplo: si el jugador elige “Jugar” o “Salir”.
- **Ciclo:** repetir una acción mientras se cumpla una condición.
  - Ejemplo: mientras `lives > 0` se siguen jugando turnos.
- **Pseudocódigo:** describir el algoritmo sin la sintaxis de un lenguaje.
  - Ejemplo: “Leer opción” en lugar de `cin >> option;`.

### Errores comunes (con explicación + ejemplo)
- **Saltar al código sin diagrama/pseudocódigo:** el alumno escribe y se pierde.
  - Ejemplo: mezcla menú, turnos y reglas en un solo bloque.
- **No definir condición de salida en ciclos:** crea bucles infinitos.
  - Ejemplo: “Mientras jugando” sin definir cuándo termina.

### Ejemplos

**Ejemplo 1 – Diagrama de menú (texto)**
```cpp
Inicio -> Mostrar menu -> Leer opcion -> (Jugar?)
```

**Ejemplo 2 – Decisión de juego (pseudocódigo)**
```cpp
Si opcion es jugar
  Iniciar juego
Si opcion es salir
  Fin
```

**Ejemplo 3 – Ciclo de juego (pseudocódigo)**
```cpp
Mientras lives > 0
  Ejecutar turno
```

**Ejemplo 4 – Pseudocódigo de puntaje**
```cpp
Inicializar score
Mientras juego activo
  Aumentar score
```

**Ejemplo 5 – Fin de juego (pseudocódigo)**
```cpp
Si lives <= 0
  Mostrar Game Over
```

**Ejemplo 6 – Reinicio (pseudocódigo)**
```cpp
Reiniciar variables
Volver al menu
```

### Ejercicios (con solución)

**Ejercicio 1:** Crear pseudocódigo para un sistema de puntaje que aumenta cada turno.

**Solución:**
```cpp
Inicializar score
Mientras juego activo
  Aumentar score
  Pasar al siguiente turno
```

**Ejercicio 2:** Crear un diagrama de flujo (en texto) para “reintentar” después de Game Over.

**Solución:**
```cpp
Game Over -> Preguntar reintentar?
Si si -> Reiniciar -> Jugar
Si no -> Fin
```

---

## TEMA 3 – Introducción a C++ y estructura básica

### Explicación para el alumno
C++ es un lenguaje para crear programas rápidos. Un programa en C++ tiene una forma básica: incluye librerías, tiene una función principal `main()` y dentro escribe instrucciones.

### Descripción para el docente
Aquí se introduce la realidad del desarrollo: hay que **compilar** el código para convertirlo en un programa ejecutable.

Sugerencia didáctica:
- Explica la diferencia entre **error de compilación** (no entiende tu código) y **error lógico** (entiende, pero hace algo incorrecto).
- Muestra 2–3 errores típicos y cómo leer el mensaje.
- Mantén ejemplos pequeños para evitar saturación.

Puntos a enfatizar:
- `main()` es el punto de inicio.
- `cout` imprime, `cin` lee.
- Los errores son pistas: hay que aprender a leerlos.

### Conceptos clave (con explicación + ejemplo)
- **Compilar:** transformar código en ejecutable.
  - Ejemplo: si falta `;`, no compila.
- **`main()`**: función donde inicia el programa.
  - Ejemplo: el juego arranca desde `main()`.
- **Entrada/Salida:** interacción por consola.
  - Ejemplo: elegir opción de menú.

### Errores comunes (con explicación + ejemplo)
- **Olvidar `;` o llaves:** provoca error de compilación.
  - Ejemplo: `cout << "Hi"` (sin `;`).
- **Leer entrada con tipo incorrecto:** la variable no recibe lo esperado.
  - Ejemplo: leer texto en un `int`.

### Ejemplos

**Ejemplo 1 – Programa mínimo**
```cpp
#include <iostream>
using namespace std;

int main() {
    return 0;
}
```

**Ejemplo 2 – Mensaje en consola**
```cpp
cout << "Start Game" << endl;
```

**Ejemplo 3 – Leer opción**
```cpp
int option;
cin >> option;
```

**Ejemplo 4 – Mostrar estado**
```cpp
int playerHealth = 100;
cout << playerHealth << endl;
```

**Ejemplo 5 – Mostrar score**
```cpp
int score = 0;
cout << "Score: " << score << endl;
```

**Ejemplo 6 – Estructura de menú básica**
```cpp
cout << "1) Play" << endl;
cout << "2) Exit" << endl;
```

### Ejercicios (con solución)

**Ejercicio 1:** Mostrar un mensaje de bienvenida y un menú con 2 opciones.

**Solución:**
```cpp
cout << "Welcome" << endl;
cout << "1) Play" << endl;
cout << "2) Exit" << endl;
```

**Ejercicio 2:** Leer una opción del usuario y mostrarla en consola.

**Solución:**
```cpp
int choice;
cin >> choice;
cout << "Choice: " << choice << endl;
```

---

## TEMA 4 – Variables y tipos de datos

### Explicación para el alumno
Las variables guardan información. En un videojuego, las variables son como el “estado” del juego: vidas, puntaje, energía, nivel.

### Descripción para el docente
Este tema se debe enseñar con ejemplos que el alumno pueda imaginar: barras de vida, números en pantalla, estados de “Game Over”.

Sugerencia didáctica:
- Relaciona tipo de dato con el tipo de información.
- Repite la idea: el tipo define qué valores se pueden guardar.

### Conceptos clave (con explicación + ejemplo)
- **`int`:** números enteros.
  - Ejemplo: `score`, `lives`.
- **`float`:** números con decimales.
  - Ejemplo: `speed`, `cooldown`.
- **`bool`:** verdadero/falso.
  - Ejemplo: `isGameOver`.

### Errores comunes (con explicación + ejemplo)
- **Usar el tipo incorrecto:** guarda información equivocada.
  - Ejemplo: usar `int` para velocidad con decimales.
- **Nombres poco descriptivos:** dificulta leer el código.
  - Ejemplo: `int x = 3;` en lugar de `int lives = 3;`.

### Ejemplos

**Ejemplo 1 – Vida del jugador**
```cpp
int playerHealth = 100;
```

**Ejemplo 2 – Puntaje**
```cpp
int score = 0;
```

**Ejemplo 3 – Velocidad**
```cpp
float playerSpeed = 5.0f;
```

**Ejemplo 4 – Estado del juego**
```cpp
bool isGameOver = false;
```

**Ejemplo 5 – Energía**
```cpp
int energy = 50;
```

**Ejemplo 6 – Nivel**
```cpp
int level = 1;
```

### Ejercicios (con solución)

**Ejercicio 1:** Crear variables para `lives`, `score` y `energy` con valores iniciales.

**Solución:**
```cpp
int lives = 3;
int score = 0;
int energy = 50;
```

**Ejercicio 2:** Crear una variable booleana `isPlaying` y asignarla en `true`.

**Solución:**
```cpp
bool isPlaying = true;
```

---

## TEMA 5 – Estructuras de control

### Explicación para el alumno
Las estructuras de control permiten que el programa tome decisiones y repita acciones. En videojuegos esto define reglas: ganar, perder, turnos, menús.

### Descripción para el docente
Este tema debe sentirse como “controlar el juego”.

Sugerencia didáctica:
- Presenta `if` como una regla (“si pasa esto, entonces…”).
- Presenta `while` como un loop de juego simplificado (“mientras siga vivo, juega”).

### Conceptos clave (con explicación + ejemplo)
- **Condicional (`if/else`):** ejecuta código dependiendo de una condición.
  - Ejemplo: si `lives <= 0` → Game Over.
- **Ciclo (`while`):** repite mientras una condición sea verdadera.
  - Ejemplo: mientras `lives > 0` → seguir jugando.

### Errores comunes (con explicación + ejemplo)
- **Condición mal planteada:** el juego termina cuando no debería.
  - Ejemplo: usar `<` en lugar de `<=`.
- **Bucle infinito:** el juego nunca termina.
  - Ejemplo: `while (lives > 0)` pero nunca reduces `lives`.

### Ejemplos

**Ejemplo 1 – Condición de victoria (estructura)**
```cpp
if (score >= 100) {
    cout << "You win" << endl;
}
```

**Ejemplo 2 – Game Over (estructura)**
```cpp
if (lives <= 0) {
    cout << "Game Over" << endl;
}
```

**Ejemplo 3 – Bucle de juego (estructura)**
```cpp
while (lives > 0) {
    cout << "Playing..." << endl;
    lives--;
}
```

**Ejemplo 4 – Turnos (estructura)**
```cpp
while (turns > 0) {
    turns--;
}
```

**Ejemplo 5 – Menú activo (estructura)**
```cpp
while (menuActive) {
    // mostrar opciones
}
```

**Ejemplo 6 – Reintentar (estructura)**
```cpp
while (retry) {
    // reiniciar y jugar
    retry = false;
}
```

### Ejercicios (con solución)

**Ejercicio 1:** Escribir una condición que muestre “Low Health” si `playerHealth < 20`.

**Solución:**
```cpp
if (playerHealth < 20) {
    cout << "Low Health" << endl;
}
```

**Ejercicio 2:** Crear un bucle que ejecute 5 turnos y muestre el número de turno.

**Solución:**
```cpp
int turn = 1;
while (turn <= 5) {
    cout << "Turn: " << turn << endl;
    turn++;
}
```

---

## TEMA 6 – Funciones

### Explicación para el alumno
Las funciones permiten dividir un programa en acciones pequeñas. En videojuegos, una función puede ser “atacar”, “curar”, “jugar un turno” o “mostrar menú”.

### Descripción para el docente
Las funciones son el cierre del cuatrimestre porque elevan al alumno de “escribo instrucciones” a “diseño un sistema”.

Sugerencia didáctica:
- Refuerza la idea: si algo se repite o se entiende como acción, es función.
- Conecta con videojuegos: un juego es un conjunto de acciones.
- Introduce parámetros como “configuración de la acción” (por ejemplo, curar cierta cantidad).

### Conceptos clave (con explicación + ejemplo)
- **Función `void`:** realiza una acción sin regresar valor.
  - Ejemplo: `showMenu()`.
- **Función con retorno:** devuelve un valor.
  - Ejemplo: `calculateDamage()`.
- **Parámetros:** datos que una función necesita para trabajar.
  - Ejemplo: `heal(int amount)`.

### Errores comunes (con explicación + ejemplo)
- **Hacer todo en `main()`:** código largo e ilegible.
  - Ejemplo: menú, turnos y reglas sin separar.
- **Nombres de funciones poco claros:** no se entiende qué hace.
  - Ejemplo: `doStuff()` en lugar de `playTurn()`.

### Ejemplos

**Ejemplo 1 – Función simple**
```cpp
void startGame() {
    cout << "Starting..." << endl;
}
```

**Ejemplo 2 – Mostrar menú**
```cpp
void showMenu() {
    cout << "1) Play" << endl;
    cout << "2) Exit" << endl;
}
```

**Ejemplo 3 – Función de ataque**
```cpp
void attackEnemy() {
    cout << "Attack!" << endl;
}
```

**Ejemplo 4 – Función con retorno**
```cpp
int calculateDamage() {
    return 10;
}
```

**Ejemplo 5 – Función con parámetro**
```cpp
void heal(int amount) {
    cout << "Healing " << amount << endl;
}
```

**Ejemplo 6 – Acción de turno**
```cpp
void playTurn() {
    attackEnemy();
}
```

### Ejercicios (con solución)

**Ejercicio 1:** Crear una función `void showStatus(int lives, int score)` que imprima vidas y score.

**Solución:**
```cpp
void showStatus(int lives, int score) {
    cout << "Lives: " << lives << " | Score: " << score << endl;
}
```

**Ejercicio 2:** Crear una función `int addScore(int currentScore, int points)` que regrese el nuevo score.

**Solución:**
```cpp
int addScore(int currentScore, int points) {
    return currentScore + points;
}
```

---

Esta guía es un documento vivo y debe usarse como apoyo permanente durante el Cuatrimestre 1.

