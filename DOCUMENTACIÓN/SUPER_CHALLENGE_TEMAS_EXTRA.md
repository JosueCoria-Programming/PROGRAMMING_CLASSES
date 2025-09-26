# 📘 Temas extra utilizados en el Super Challenge

En el desarrollo del **Super Challenge – Mini-RPG en C++**, se aplicaron principalmente los **14 temas vistos en clase**.  
Sin embargo, para enriquecer la experiencia y hacer el proyecto más realista, se incluyeron algunos **temas adicionales** que no fueron vistos formalmente en clase.

---

## 🔹 1. Estructuras (`struct`)
Se usaron para representar al **jugador**, al **enemigo** y al **mapa**.  
Esto permitió agrupar atributos relacionados bajo un mismo nombre en lugar de usar múltiples variables sueltas.

Ejemplo:
```cpp
struct Jugador {
    string nombre;
    int hp;
    int atk;
    int def_;
};
```

**Por qué se incluyó:**  
- Facilita la organización del código.  
- Hace que el manejo de datos del jugador y enemigo sea más claro.  

---

## 🔹 2. Manejo de constantes (`const`)
Se usaron valores fijos para definir **tamaños de inventario, mapa y vida máxima**.  
Esto evita el uso de “números mágicos” en el código.

Ejemplo:
```cpp
const int MAP_N = 5;
const int INV_SIZE = 5;
const int HP_MAX = 50;
```

**Por qué se incluyó:**  
- Mejora la legibilidad.  
- Permite modificar parámetros del juego fácilmente.  

---

## 🔹 3. Funciones utilitarias adicionales
Se implementaron funciones de apoyo que no fueron vistas directamente, como:  
- `limpiarPantalla()` → simula limpiar la consola.  
- `pausar()` → espera a que el usuario presione ENTER.  
- `imprimirLinea()` → imprime una línea de separación.  

Ejemplo:
```cpp
void pausar() {
    cout << "Presiona ENTER para continuar...";
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
    cin.get();
}
```

**Por qué se incluyó:**  
- Mejora la interacción con el usuario.  
- Ayuda a estructurar mejor el flujo de ejecución.  

---

## 🔹 4. Uso de `numeric_limits`
Para manejar correctamente el buffer de entrada en la función `pausar()`, se utilizó:

```cpp
#include <limits>
cin.ignore(numeric_limits<streamsize>::max(), '\n');
```

**Por qué se incluyó:**  
- Evita problemas al leer entradas en consola.  
- No se vio en clase, pero es un buen ejemplo de librerías estándar de C++.  

---

## 🔹 5. Modularidad más avanzada
En el Super Challenge se dividió el proyecto en módulos por persona (jugador, inventario, mapa, combate, flujo del juego).  
Aunque en clase vimos funciones básicas, aquí se extendió a un **diseño modular completo**.

**Por qué se incluyó:**  
- Refuerza la importancia de dividir responsabilidades.  
- Prepara al alumno para proyectos más grandes.  

---

# ✅ Conclusión
Los temas adicionales fueron incluidos para dar realismo y estructura al Super Challenge, pero **no son obligatorios para la comprensión básica del curso**.  
Su finalidad es mostrar a los alumnos cómo se pueden usar **herramientas extra de C++** para enriquecer un proyecto real.

