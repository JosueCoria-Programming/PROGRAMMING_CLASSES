# Guía para el Alumno
## Cuatrimestre 1 – Introducción a la Programación
### Curso de Programación en C++ Orientado a Videojuegos

Esta guía está pensada para acompañarte durante todo el **Cuatrimestre 1**. No asume experiencia previa en programación.

Aquí aprenderás **cómo pensar como programador**, no solo a escribir código.

Regla importante:
- Los **ejercicios no incluyen código solución**. El objetivo es que practiques y pienses.
- Todos los ejercicios y proyectos se trabajan en **GitHub**, cada uno con su propio `README.md`.

---

## TEMA 1 – ¿Qué es programar?

### Explicación
Programar significa **dar instrucciones a una computadora** para que haga algo. La computadora no “adivina”, no “interpreta intenciones” y no entiende “más o menos”: solo sigue instrucciones exactas.

En videojuegos, programar es lo que convierte una idea en un sistema real. Por ejemplo:
- Si presionas **saltar**, el personaje sube.
- Si te golpea un enemigo, pierdes **vida**.
- Si juntas monedas, sube el **puntaje**.

Todo eso son reglas. Y esas reglas son programación.

Una forma útil de pensar en programación es esta:
- Tú tienes un **objetivo** (por ejemplo, “hacer un menú”).
- Lo divides en **pasos** (“mostrar opciones”, “leer la opción”, “hacer algo con esa opción”).
- Esos pasos se vuelven un **algoritmo**.

Programar no es memorizar código. Memorizar puede ayudarte con la sintaxis, pero lo importante es **aprender a pensar**:
- ¿Qué información necesita el programa?
- ¿Qué decisiones debe tomar?
- ¿Qué cosas se repiten?
- ¿Cuándo termina el juego?

En el cuatrimestre 1, vas a aprender justo eso: pensamiento lógico + bases de C++.

### Conceptos clave
- **Programación:** convertir una idea en instrucciones que una computadora puede ejecutar.
- **Algoritmo:** una lista de pasos ordenados para resolver un problema.
- **Pensamiento lógico:** dividir un problema grande en partes pequeñas.

### Ejemplos

**Ejemplo 1 – Secuencia básica de un juego (pseudocódigo)**
```text
Mostrar menu
Leer opcion
Ejecutar accion
```

**Ejemplo 2 – Turno de juego (pseudocódigo)**
```text
Jugador ataca
Enemigo responde
Actualizar estado
```

**Ejemplo 3 – Regla de victoria**
```text
Si score >= 100
  Ganar
```

**Ejemplo 4 – Regla de derrota**
```text
Si lives <= 0
  Game Over
```

**Ejemplo 5 – Flujo simple**
```text
Iniciar juego
Jugar turno
Finalizar juego
```

**Ejemplo 6 – Pausa**
```text
Si jugador pausa
  Detener juego
```

### Ejercicios

1. Escribe un algoritmo (en texto o pseudocódigo) para iniciar un videojuego con menú.
2. Escribe un algoritmo para un sistema de vidas.

---

## TEMA 2 – Diagramas de flujo y pseudocódigo

### Explicación
Antes de escribir código, es muy importante **ordenar las ideas**. Cuando intentas programar directamente sin planear, es común confundirse, cometer errores o no saber por dónde continuar.

Para evitar eso, existen dos herramientas clave:

- **Diagramas de flujo:** usan símbolos y flechas para mostrar el camino que sigue el programa.
- **Pseudocódigo:** describe la lógica usando texto, sin la sintaxis estricta de C++.

Estas herramientas te ayudan a responder preguntas como:
- ¿Qué pasa primero?
- ¿Qué decisiones se toman?
- ¿Qué cosas se repiten?
- ¿Cuándo termina el programa?

En videojuegos, casi todo se puede representar así:
- Menús
- Turnos
- Condiciones de victoria y derrota
- Reintentos

Si puedes explicarlo con un diagrama o pseudocódigo, **entonces estás listo para programarlo**.

### Conceptos clave
- **Decisión:** punto donde el programa elige un camino.
- **Ciclo:** repetir acciones mientras se cumpla una condición.
- **Pseudocódigo:** forma de escribir la lógica sin usar C++.

### Ejemplos

**Ejemplo 1 – Menú (texto)**
```text
Inicio -> Menu -> Opcion
```

**Ejemplo 2 – Decisión**
```text
Si jugar
  Iniciar
```

**Ejemplo 3 – Ciclo**
```text
Mientras lives > 0
  Jugar turno
```

**Ejemplo 4 – Puntaje**
```text
Inicializar score
Incrementar score
```

**Ejemplo 5 – Fin de juego**
```text
Si lives <= 0
  Game Over
```

**Ejemplo 6 – Reinicio**
```text
Reiniciar variables
```

### Ejercicios

1. Crea un pseudocódigo para un sistema de puntaje.
2. Dibuja o escribe un diagrama de flujo para reintentar después de Game Over.

---

## TEMA 3 – Introducción a C++ y estructura básica

### Explicación
C++ es un lenguaje de programación que se usa para crear programas rápidos y eficientes, incluidos muchos videojuegos.

Un programa en C++ tiene una **estructura básica** que siempre se repite:
- Se incluyen librerías
- Existe una función principal llamada `main()`
- Dentro de `main()` se escriben las instrucciones

Cuando escribes código en C++, no se ejecuta directamente. Primero debe **compilarse**, es decir, convertirse en un programa que la computadora pueda ejecutar.

Es normal cometer errores al inicio. Los mensajes de error no son enemigos: son pistas que te dicen qué está mal.

### Conceptos clave
- **main():** punto donde inicia el programa.
- **Compilar:** convertir código en ejecutable.
- **Entrada y salida:** leer y mostrar información.

### Ejemplos

**Ejemplo 1 – Programa mínimo**
```cpp
#include <iostream>
using namespace std;

int main() {
    return 0;
}
```

**Ejemplo 2 – Mostrar texto**
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
cout << playerHealth << endl;
```

**Ejemplo 5 – Mostrar score**
```cpp
cout << "Score: " << score << endl;
```

**Ejemplo 6 – Menú básico**
```cpp
cout << "1) Play" << endl;
cout << "2) Exit" << endl;
```

### Ejercicios

1. Escribe un programa que muestre un mensaje de bienvenida.
2. Escribe un programa que muestre un menú con dos opciones y lea la opción del usuario.

---

## TEMA 4 – Variables y tipos de datos

### Explicación
Las variables sirven para **guardar información**. En un videojuego, las variables representan el estado del juego: vidas, puntaje, energía, nivel, etc.

Cada variable tiene un **tipo de dato**, que define qué tipo de información puede guardar.

Elegir el tipo correcto es importante para que el programa funcione bien y sea claro.

### Conceptos clave
- **int:** números enteros (vidas, puntaje).
- **float:** números con decimales (velocidad).
- **bool:** verdadero o falso (estado del juego).

### Ejemplos

**Ejemplo 1 – Vidas**
```cpp
int lives = 3;
```

**Ejemplo 2 – Puntaje**
```cpp
int score = 0;
```

**Ejemplo 3 – Velocidad**
```cpp
float speed = 5.0f;
```

**Ejemplo 4 – Estado**
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

### Ejercicios

1. Crea variables para `lives`, `score` y `energy`.
2. Crea una variable booleana llamada `isPlaying`.

---

## TEMA 5 – Estructuras de control

### Explicación
Las estructuras de control permiten que el programa **tome decisiones** y **repita acciones**.

En videojuegos, esto define las reglas del juego:
- Ganar o perder
- Turnos
- Menús

Sin estructuras de control, el programa solo ejecutaría instrucciones en línea recta.

### Conceptos clave
- **if / else:** ejecutar código dependiendo de una condición.
- **while:** repetir mientras una condición sea verdadera.

### Ejemplos

**Ejemplo 1 – Victoria**
```cpp
if (score >= 100) {
    cout << "You win" << endl;
}
```

**Ejemplo 2 – Game Over**
```cpp
if (lives <= 0) {
    cout << "Game Over" << endl;
}
```

**Ejemplo 3 – Bucle de juego**
```cpp
while (lives > 0) {
    lives--;
}
```

**Ejemplo 4 – Turnos**
```cpp
while (turns > 0) {
    turns--;
}
```

**Ejemplo 5 – Menú activo**
```cpp
while (menuActive) {
}
```

**Ejemplo 6 – Reintentar**
```cpp
while (retry) {
    retry = false;
}
```

### Ejercicios

1. Escribe una condición que muestre "Low Health" si la vida es menor a 20.
2. Escribe un bucle que ejecute 5 turnos.

---

## TEMA 6 – Funciones

### Explicación
Las funciones permiten **dividir un programa grande en acciones pequeñas**. Esto hace que el código sea más fácil de entender, probar y modificar.

En videojuegos, casi todo se puede ver como una función:
- Mostrar menú
- Jugar un turno
- Atacar
- Curar

Si algo se repite o se puede describir como una acción, probablemente debe ser una función.

### Conceptos clave
- **Funciones:** acciones del programa.
- **Parámetros:** datos que recibe la función.
- **Retorno:** valor que la función regresa.

### Ejemplos

**Ejemplo 1 – Función simple**
```cpp
void startGame() {}
```

**Ejemplo 2 – Mostrar menú**
```cpp
void showMenu() {}
```

**Ejemplo 3 – Atacar**
```cpp
void attackEnemy() {}
```

**Ejemplo 4 – Retorno**
```cpp
int calculateDamage() { return 10; }
```

**Ejemplo 5 – Parámetro**
```cpp
void heal(int amount) {}
```

**Ejemplo 6 – Turno**
```cpp
void playTurn() {}
```

### Ejercicios

1. Crea una función que muestre las vidas y el score.
2. Crea una función que regrese el nuevo puntaje después de sumar puntos.

---

Esta guía es tu referencia principal durante el Cuatrimestre 1. Estudia los ejemplos, intenta los ejercicios y no temas equivocarte.

