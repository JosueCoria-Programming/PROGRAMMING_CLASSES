# 📏 Estándares y Buenas Prácticas en C++

Este documento resume los principales estándares de estilo y buenas prácticas al escribir código en C++. Seguir estas reglas te ayudará a crear programas más legibles, organizados y fáciles de mantener.

---

## 🧠 1. Nombres descriptivos

- Usa nombres claros para variables, funciones y constantes.
- Los nombres deben expresar su propósito.

```cpp
int sumaTotal;        // Bien
int s;                // Mal
float promedioEdad;   // Bien
```

---

## 🐫 2. Convenciones de nombres

- **Variables y funciones:** `camelCase`
- **Clases:** `PascalCase`
- **Constantes:** `MAYUSCULAS_CON_GUIONES`

```cpp
int cantidadJugadores;
float calcularPromedio(int a, int b);
const int MAX_INTENTOS = 5;
```

---

## 🎯 3. Comentarios claros

- Usa `//` para comentarios de una línea y `/* */` para varias.
- Explica "por qué" más que "qué".

```cpp
// Verificamos si el jugador adivinó el número
if (intento == secreto) {
    // Mensaje de éxito
    cout << "¡Correcto!";
}
```

---

## 🔧 4. Indentación y bloques de código

- Usa **4 espacios** por nivel de indentación.
- Siempre usa llaves `{}` en estructuras de control, incluso si hay solo una línea.

```cpp
if (vidas > 0) {
    cout << "¡Sigue jugando!";
}
```

---

## 🧪 5. Declaración y uso de variables

- Declara variables al inicio del bloque o justo antes de usarlas.
- Inicialízalas si es posible.

```cpp
int puntuacion = 0;
```

---

## 🔁 6. Uso de funciones

- Divide el código en funciones pequeñas y específicas.
- Cada función debe hacer **una sola tarea**.

```cpp
void mostrarMenu();
int calcularPuntaje(int correctas, int tiempo);
```

---

## 🚫 7. Evitar malas prácticas

- No uses variables globales innecesarias.
- No copies y pegues código repetido (mejor haz una función).
- No uses nombres confusos como `a`, `b`, `c`, excepto en loops cortos.

---

## 📦 8. Organización de archivos

- Archivos `.cpp` para código principal.
- Archivos `.h` para declaraciones (en cursos más avanzados).
- Usa comentarios al inicio de cada archivo con:
  - Nombre del autor
  - Descripción del archivo
  - Fecha de última modificación

---

## ✅ 9. Buenas prácticas adicionales

- Valida siempre la entrada del usuario.
- Escribe código que otros puedan entender fácilmente.
- Sube tus proyectos con estructura clara y un `README.md`.

---

¿Quieres que ahora lo guarde como archivo `.md`?