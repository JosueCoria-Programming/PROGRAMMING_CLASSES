# Buenas Prácticas de Programación en C++

Este documento define las **buenas prácticas obligatorias** para el curso de Programación en C++ orientado a videojuegos.  
Su objetivo es formar desde el inicio **criterio profesional**, claridad mental y disciplina al escribir código.

---

## 1. El código siempre se escribe en inglés

### Regla fundamental
Todo el **código fuente** debe escribirse en **inglés**:
- Variables
- Funciones
- Clases
- Constantes
- Archivos

### ¿Por qué en inglés?
- Es el idioma estándar de la programación
- Librerías, motores y documentación profesional usan inglés
- Facilita el trabajo en equipo y la lectura de código de otros

### ¿Qué sí puede estar en español?
- Comentarios (cuando sea necesario)
- Documentación Markdown del curso

### ¿Qué NO debe estar en español?
- Nombres de variables
- Nombres de funciones
- Nombres de clases

Ejemplo incorrecto:
```cpp
int vidasJugador;
```

Ejemplo correcto:
```cpp
int playerLives;
```

---

## 2. Usar nombres descriptivos

### Principio clave
Un buen nombre **explica qué representa la variable sin comentarios adicionales**.

### Malos ejemplos
```cpp
int x;
int a;
int temp;
```

### Buenos ejemplos
```cpp
int playerHealth;
int enemyCount;
float playerSpeed;
```

### Regla práctica
Si necesitas un comentario para explicar una variable, el nombre no es bueno.

---

## 3. Convenciones de escritura (Naming Conventions)

Usar convenciones de escritura **no es opcional**. Permite que el código sea consistente y legible.

---

### 3.1 camelCase

**Uso:**
- Variables
- Funciones

**Formato:**
- Primera palabra en minúscula
- Cada palabra nueva inicia con mayúscula

Ejemplos:
```cpp
int playerScore;
float enemySpeed;

void calculateDamage();
void movePlayer();
```

---

### 3.2 PascalCase

**Uso:**
- Clases
- Estructuras (`struct`)

**Formato:**
- Todas las palabras inician con mayúscula

Ejemplos:
```cpp
class Player;
struct Enemy;
```

---

### 3.3 SNAKE_CASE

**Uso:**
- Constantes

**Formato:**
- Todas las letras en mayúscula
- Palabras separadas por guion bajo `_`

Ejemplos:
```cpp
const int MAX_LIVES = 3;
const float GRAVITY_FORCE = 9.8f;
```

---

## 4. Uso correcto de comentarios

### ¿Para qué sirven los comentarios?
Los comentarios explican **por qué** se hace algo, no **qué** hace el código.

### Comentario innecesario
```cpp
playerLives--; // Decrementa playerLives
```

### Comentario útil
```cpp
playerLives--; // Reduce una vida cuando el jugador recibe daño
```

### Regla
Si el código es claro por sí mismo, **no necesita comentario**.

---

## 5. Organización básica del código

### Principios importantes
- El código debe leerse de arriba hacia abajo con lógica
- Cada bloque debe tener una sola responsabilidad
- Evitar repetir código

### Ejemplo conceptual
Si una acción se repite muchas veces (atacar, curar, avanzar), probablemente debe ser una **función**.

---

## 6. Errores comunes de principiantes

Evita conscientemente estos errores:

- Usar nombres genéricos (`x`, `num`, `var`)
- Copiar código sin entenderlo
- No probar el programa
- Ignorar mensajes de error
- Hacer todo en una sola función

Programar **no es escribir rápido**, es pensar con claridad.

---

## 7. Mentalidad de programador

### Programar es resolver problemas
- El código es una herramienta
- El objetivo es resolver un problema de forma clara

### El error es parte del proceso
- Todos los programas fallan al inicio
- Depurar es una habilidad, no un castigo

### El código se escribe para humanos
- Tú mismo leerás tu código en el futuro
- Otros programadores lo leerán

Si tu código es fácil de entender, vas por buen camino.

---

## 8. Regla final del curso

> Un programa que funciona pero es ilegible **no es un buen programa**.

La claridad, la organización y las buenas prácticas son tan importantes como la lógica.

Este documento es una referencia permanente durante todo el curso.

