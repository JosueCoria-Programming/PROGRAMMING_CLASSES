# 🧠 GUÍA DE BUENAS PRÁCTICAS — INTRODUCCIÓN A LA PROGRAMACIÓN (C++)

**Profesor:** Josue Coria  
**Institución:** UNITEC

> Objetivo: que tu programa no solo funcione, sino que sea **entendible, mantenible y defendible**.  
> Un código legible se depura más rápido y se mejora sin romperlo.

---

## 1) Programar en inglés

### Por qué existe esta regla
El inglés es el idioma “default” del código en la industria: librerías, errores, documentación, motores, APIs.

### Trasfondo
En equipos mixtos y repos públicos, el inglés reduce fricción y hace tu código portable.

✅ **Esperado (código en inglés)**
```cpp
int playerHP = 100;
int damage = 20;
int hpAfterHit = playerHP - damage;
```

❌ **Evitar (código en español)**
```cpp
int vidaJugador = 100;
int dano = 20;
int vidaDespues = vidaJugador - dano;
```

> **Excepción práctica:** comentarios, README e issues pueden ir en español según la empresa/cliente (ver regla 2).

---

## 2) Documentación y GitHub: idioma según la empresa

### Por qué
El repo es comunicación. Algunas empresas prefieren español para operación local; otras, inglés.

### Trasfondo
El “mejor idioma” es el que maximiza el entendimiento del equipo real.

✅ **Esperado**
- Código (identificadores): **inglés siempre**
- README / documentación: **español o inglés** según contexto
- Commits: consistentes (pueden ser ES si el equipo lo usa)

---

## 3) Convenciones de nombres: snake_case, PascalCase, camelCase

### Por qué
La consistencia evita confusión y hace el proyecto más “escanneable”.

### Trasfondo
En proyectos reales, las convenciones ayudan a identificar **qué** es algo solo por su forma.

✅ **Estándar del curso**
- **PascalCase**: tipos (structs, clases, enums)
- **camelCase**: variables y funciones
- **SNAKE_CASE**: constantes globales (y macros si se usan)

✅ **Ejemplo**
```cpp
struct PlayerStats { 
    int hp; 
    int coins; 
};

int calculateDamage(int baseDamage, int strength) { 
    return baseDamage + strength; 
}

const int MAX_HP = 100;   // constante visible
int playerHp = 80;        // variable
PlayerStats stats{playerHp, 50};
```

❌ **Evitar**
```cpp
int Player_hp;
int Calculate_damage();
const int maxHp = 100;
```

---

## 4) Nombres claros (variables, funciones, structs)

### Por qué existe esta regla
El 70% del tiempo es **leer**. Si el nombre explica, tu cerebro no se desgasta.

### Trasfondo
En sistemas de juego, nombres claros reducen bugs por malentendidos.

✅ **Esperado**
```cpp
int playerHP = 100;
int damage = 25;
int hpAfterHit = playerHP - damage;
```

❌ **Evitar**
```cpp
int x = 100;
int d = 25;
int y = x - d;
```

---

## 5) Una función = un propósito

### Por qué
Si una función hace 5 cosas, cuando falla no sabes cuál.

### Trasfondo
Modularidad = reusar lógica (inventario, combate, UI).

✅ **Esperado**
```cpp
int applyDamage(int hp, int damage) {
    return hp - damage;
}
```

❌ **Evitar (mezcla entrada + lógica + salida)**
```cpp
#include <iostream>

void doEverything() {
    int hp; std::cin >> hp;
    int dmg; std::cin >> dmg;
    std::cout << hp - dmg << "\n";
}
```

---

## 6) Evita “números mágicos”

### Por qué
`37` no significa nada. Una constante sí.

### Trasfondo
En juegos, balancear = cambiar números. Hazlo fácil.

✅ **Esperado**
```cpp
const int MAX_HP = 100;
const int MAX_POTIONS = 5;
```

❌ **Evitar**
```cpp
int hp = 100; // ¿por qué 100? ¿si cambia?
```

---

## 7) Control de flujo limpio

### Por qué
Muchos `if` anidados vuelven el código ilegible.

### Trasfondo
Los juegos tienen reglas. Mantén la lógica directa.

✅ **Esperado**
```cpp
bool canBuy(int coins, int price) {
    if (price <= 0) return false;
    return coins >= price;
}
```

❌ **Evitar**
```cpp
bool canBuy(int coins, int price) {
    if (price > 0) {
        if (coins >= price) return true;
        else return false;
    } else {
        return false;
    }
}
```

---

## 8) Estructura mínima del proyecto

### Por qué
Orden = menos tiempo perdido.

### Trasfondo
Preparación suave para motores.

✅ **Esperado**
- `main.cpp`
- `game/` (lógica: combate, inventario, tienda)
- `utils/` (helpers)
- `assets/` (si hay archivos)

---

## 9) Includes y `std::`

### Por qué
`using namespace std;` puede causar colisiones.

### Trasfondo
Proyectos grandes = nombres repetidos.

✅ **Esperado**
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name = "Player";
    std::cout << name << "\n";
}
```

⚠️ **Aceptable solo en tareas muy pequeñas (pero no ideal)**
```cpp
using namespace std;
```

---

## 10) Comentarios que expliquen intención (no lo obvio)

### Por qué
Los comentarios deben explicar “por qué”, no narrar la línea.

### Trasfondo
En juegos importa la intención (reglas y balance).

✅ **Esperado**
```cpp
#include <algorithm> // std::min

// Regla: el jugador no puede curarse por encima del HP máximo.
hp = std::min(hp + heal, MAX_HP);
```

❌ **Evitar**
```cpp
// sumamos heal a hp
hp = hp + heal;
```

---

## 11) Formato consistente (legibilidad)

### Por qué
Si se ve desordenado, se entiende desordenado.

✅ **Esperado**
- Indentación consistente
- Llaves claras
- Espacios alrededor de operadores

---

## 12) Evita duplicación

### Por qué
Copiar/pegar lógica crea bugs repetidos.

### Trasfondo
Si arreglas un bug en un lugar y olvidas los demás, el bug “regresa”.

✅ **Esperado**
```cpp
int clamp(int value, int minV, int maxV) {
    if (value < minV) return minV;
    if (value > maxV) return maxV;
    return value;
}
```

---

## 13) Usa `struct` para agrupar datos del juego

### Por qué
Variables sueltas = pierdes relación.

### Trasfondo
Esto es una puerta suave hacia diseño de sistemas (sin OO pesada aún).

✅ **Esperado**
```cpp
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};
```

---

## 14) `std::vector` para listas dinámicas (inventario, enemigos, etc.)

### Por qué
Los arreglos fijos se quedan cortos.

### Trasfondo
Inventarios, loot, quests: todo crece y se reduce.

✅ **Esperado**
```cpp
#include <vector>
#include <string>

std::vector<std::string> inventory;
inventory.push_back("Potion");
inventory.push_back("Key");
```

---

## 15) Persistencia: guarda/carga con formato claro

### Por qué
Guardar mal genera bugs “fantasma”.

### Trasfondo
Un archivo simple necesita orden: una línea por valor o clave=valor.

✅ **Esperado (clave=valor)**
```ini
name=Player1
hp=85
coins=120
```

---

## 16) GitHub

### Por qué
La evaluación considera proceso.

### Trasfondo
Git/GitHub ayudan a evidenciar progreso real y a recuperar versiones.

✅ **Esperado**
- Commits pequeños y con mensaje útil (ES o EN según equipo)
- README breve (ES o EN según empresa)
- Repo ordenado

❌ **Evitar**
- 1 commit: `final final ahora si`
- Sin README
- Subir basura (builds, `.exe`, etc.)
