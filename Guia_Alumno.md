# 🧑‍🎓 GUÍA DEL ALUMNO + DESAFÍOS — INTRODUCCIÓN A LA PROGRAMACIÓN (C++)

**Profesor:** Josue Coria  
**Institución:**   
**Duración:** 4 meses

---

## Índice de temas
1. [¿Qué es programar?](#1-qué-es-programar)
2. [Variables, tipos y operaciones](#2-variables-tipos-y-operaciones)
3. [Entrada y salida](#3-entrada-y-salida)
4. [Condicionales](#4-condicionales)
5. [Switch + menús](#5-switch--menús)
6. [Ciclos (while)](#6-ciclos-while)
7. [Ciclos (for) + patrones comunes](#7-ciclos-for--patrones-comunes)
8. [Funciones (bases)](#8-funciones-bases)
9. [Arreglos (arrays) 1D](#9-arreglos-arrays-1d)
10. [Vectores (std::vector)](#10-vectores-stdvector)
11. [Strings (más a fondo)](#11-strings-más-a-fondo)
12. [Estructuras (struct)](#12-estructuras-struct)
13. [Archivos (persistencia básica)](#13-archivos-persistencia-básica)
14. [Depuración y calidad](#14-depuración-y-calidad)

---

# 1) ¿Qué es programar?

## Explicación
Programar es escribir instrucciones claras para que la computadora haga algo específico. Un programa es como una receta: se ejecuta en orden y produce un resultado visible. En C++, casi siempre iniciamos con una estructura básica que la computadora entiende para arrancar.

En videojuegos, programar significa controlar lo que pasa: mostrar mensajes, contar una historia, presentar un menú, o avisar que el jugador ganó/perdió. Hoy nos enfocamos en el flujo mínimo: **abrir archivo → escribir código → compilar → ejecutar**, y en entender la idea de “salida” (lo que se imprime en la consola).

---

## Ejemplos

### Ejemplo 1 — El programa más pequeño útil
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, Game!\n";
    return 0;
}
```

### Ejemplo 2 — Pantalla de título
```cpp
#include <iostream>

int main() {
    std::cout << "=====================\n";
    std::cout << "   DUNGEON CONSOLE    \n";
    std::cout << "=====================\n";
    return 0;
}
```

### Ejemplo 3 — “Press Start”
```cpp
#include <iostream>

int main() {
    std::cout << "[Press Start]\n";
    std::cout << "Loading...\n";
    std::cout << "Ready!\n";
    return 0;
}
```

### Ejemplo 4 — Diálogo simple
```cpp
#include <iostream>

int main() {
    std::cout << "NPC: Welcome, traveler.\n";
    std::cout << "NPC: The dungeon is dangerous.\n";
    std::cout << "NPC: Take this sword.\n";
    return 0;
}
```

### Ejemplo 5 — Menú “mock”
```cpp
#include <iostream>

int main() {
    std::cout << "1) New Game\n";
    std::cout << "2) Load Game\n";
    std::cout << "3) Options\n";
    std::cout << "4) Exit\n";
    return 0;
}
```

### Ejemplo 6 — Comentarios
```cpp
#include <iostream>

int main() {
    // This is the title screen of the game.
    std::cout << "=== SPACE RUNNER ===\n";

    // Next lessons will add input and game logic.
    std::cout << "Tip: Collect coins to score points.\n";
    return 0;
}
```
---

## Desafíos

### En clase
1) **HUD estático:** imprime una línea tipo:  
   `HP: [#####-----]  Coins: 000  Level: 1`

2) **Pantalla de “Game Over”:** imprime un recuadro ASCII con el texto `GAME OVER`.

3) **Menú principal:** imprime un menú con 4 opciones (New/Load/Options/Exit) y un título.

### En casa
1) **Intro de juego:** imprime una introducción narrativa de mínimo 8 líneas (historia + objetivo).

2) **Controles:** imprime una sección “Controls” con al menos 6 líneas (Move, Jump, Attack, etc.).

3) **Diálogo con elección simulada:** imprime un diálogo de 10 líneas y al final muestra 2 opciones:
    - `1) Help the village`
    - `2) Ignore and leave`
      *(sin leer la opción, solo mostrarla)*

4) **Pantalla de créditos:** imprime créditos con al menos 10 líneas (roles y nombres inventados).

5) **Mini tutorial:** imprime un “tutorial” en consola con pasos numerados del 1 al 8.

---

# 2) Variables, tipos y operaciones

## Explicación
Una **variable** es un espacio en memoria con un nombre donde guardas un valor para usarlo después (por ejemplo: `playerHP`, `coins`, `score`). Un **tipo de dato** describe qué clase de valor es: `int` (enteros), `double` (decimales), `bool` (verdadero/falso), `char` (un carácter) y `std::string` (texto).

En videojuegos, casi todo son variables: vida, daño, monedas, velocidad, experiencia. En este tema aprenderás a **declarar variables**, **asignar valores** y hacer **operaciones** (sumar, restar, multiplicar, dividir, módulo) para actualizar estados del juego.

---

## Ejemplos

### Ejemplo 1 — HP máximo (constante) y HP actual
```cpp
#include <iostream>

int main() {
    const int MAX_HP = 100;   // constante visible
    int playerHP = 75;

    std::cout << "MAX_HP: " << MAX_HP << "
";
    std::cout << "playerHP: " << playerHP << "
";
    return 0;
}
```

### Ejemplo 2 — Recibir daño
```cpp
#include <iostream>

int main() {
    int playerHP = 90;
    int damage = 35;

    int hpAfterHit = playerHP - damage;

    std::cout << "HP after hit: " << hpAfterHit << "
";
    return 0;
}
```

### Ejemplo 3 — Comprar pociones
```cpp
#include <iostream>

int main() {
    int coins = 120;
    int potionPrice = 25;
    int potionQty = 3;

    int totalCost = potionPrice * potionQty;
    int coinsLeft = coins - totalCost;

    std::cout << "Total cost: " << totalCost << "
";
    std::cout << "Coins left: " << coinsLeft << "
";
    return 0;
}
```

### Ejemplo 4 — ¿Cuántas compras alcanzan?
```cpp
#include <iostream>

int main() {
    int coins = 103;
    int arrowPrice = 8;

    int maxArrows = coins / arrowPrice;   // división entera
    int remainder = coins % arrowPrice;   // lo que sobra

    std::cout << "Max arrows: " << maxArrows << "
";
    std::cout << "Remaining coins: " << remainder << "
";
    return 0;
}
```

### Ejemplo 5 — Velocidad y distancia
```cpp
#include <iostream>

int main() {
    double moveSpeed = 3.5;   // units per second
    double timeSeconds = 4.0;

    double distance = moveSpeed * timeSeconds;

    std::cout << "Distance: " << distance << "
";
    return 0;
}
```

### Ejemplo 6 — Score y boosts
```cpp
#include <iostream>

int main() {
    int score = 0;

    score += 10;  // collect coin pack
    score += 25;  // defeat enemy
    score++;      // bonus point

    std::cout << "Score: " << score << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Damage calc:** declara `baseDamage` y `weaponBonus`, calcula `finalDamage` y muéstralo.
2) **Coins left:** declara `coins`, `price`, `qty`, calcula `coinsLeft` y muéstralo.
3) **XP total:** declara `currentXP` y `questXP`, calcula `newXP` y muéstralo.

### En casa
1) **DPS (daño por segundo):** declara `totalDamage` y `seconds` (usa `double`) y calcula `dps`.
2) **Crafting:** declara `herbs` y `herbsPerPotion`. Calcula cuántas pociones puedes hacer (`/`) y cuántas hierbas sobran (`%`).
3) **Currency system:** declara `gold`, `silver`, `copper`. Convierte todo a `totalCopper` (ej: 1 gold=100 copper, 1 silver=10 copper) y muestra el total.
4) **XP progress (%):** declara `currentXP` y `xpToLevel`. Calcula `progressPercent = (currentXP * 100.0) / xpToLevel` y muéstralo.
5) **Cooldown:** declara `cooldownSeconds` y `timePassed`. Calcula `remaining` y muéstralo.

---

# 3) Entrada y salida

## Explicación
Un programa se vuelve interactivo cuando puede **recibir datos** y usarlos para producir una salida. En C++ eso se hace con `std::cin` (entrada) y `std::cout` (salida). La idea es simple: **pides un dato**, lo guardas en una variable y después lo usas para mostrar un resultado.

En videojuegos, esto se parece a capturar decisiones del jugador (nombre, dificultad, cantidad de objetos a comprar) y luego mostrar un resumen en pantalla. En este tema practicarás **leer valores** (`int`, `double`, `std::string`) y **mostrar mensajes** claros.

---

## Ejemplos

### Ejemplo 1 — Nombre del jugador
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;

    std::cout << "Enter player name: ";
    std::cin >> playerName;

    std::cout << "Welcome, " << playerName << "!
";
    return 0;
}
```

### Ejemplo 2 — Elegir dificultad
```cpp
#include <iostream>

int main() {
    int difficulty;

    std::cout << "Choose difficulty (1-3): ";
    std::cin >> difficulty;

    std::cout << "Difficulty selected: " << difficulty << "
";
    return 0;
}
```

### Ejemplo 3 — Comprar ítems
```cpp
#include <iostream>

int main() {
    int coins;
    int itemPrice;
    int qty;

    std::cout << "Coins: ";
    std::cin >> coins;

    std::cout << "Item price: ";
    std::cin >> itemPrice;

    std::cout << "Quantity: ";
    std::cin >> qty;

    int totalCost = itemPrice * qty;
    int coinsLeft = coins - totalCost;

    std::cout << "Total cost: " << totalCost << "
";
    std::cout << "Coins left: " << coinsLeft << "
";
    return 0;
}
```

### Ejemplo 4 — Reporte de combate
```cpp
#include <iostream>

int main() {
    int playerHP;
    int enemyDamage;

    std::cout << "Player HP: ";
    std::cin >> playerHP;

    std::cout << "Enemy damage: ";
    std::cin >> enemyDamage;

    int hpAfterHit = playerHP - enemyDamage;

    std::cout << "HP after hit: " << hpAfterHit << "
";
    return 0;
}
```

### Ejemplo 5 — Tiempo y distancia
```cpp
#include <iostream>

int main() {
    double speed;
    double seconds;

    std::cout << "Speed (units/sec): ";
    std::cin >> speed;

    std::cout << "Time (sec): ";
    std::cin >> seconds;

    double distance = speed * seconds;

    std::cout << "Distance traveled: " << distance << "
";
    return 0;
}
```

### Ejemplo 6 — Pantalla de resumen
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;
    int level;
    int coins;

    std::cout << "Name: ";
    std::cin >> playerName;

    std::cout << "Level: ";
    std::cin >> level;

    std::cout << "Coins: ";
    std::cin >> coins;

    std::cout << "=== PLAYER SUMMARY ===
";
    std::cout << "Name: " << playerName << "
";
    std::cout << "Level: " << level << "
";
    std::cout << "Coins: " << coins << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **HUD input:** lee `playerName` y `playerHP`, imprime una línea tipo: `Player <name> | HP: <hp>`.
2) **Coins reward:** lee `coins` y `reward`, imprime `newCoins`.
3) **Shop total:** lee `itemPrice` y `qty`, imprime `totalCost`.

### En casa
1) **Character creator:** lee `playerName`, `className` (usa una sola palabra), `level` y `coins`. Imprime una “ficha” con mínimo 5 líneas.
2) **Quest payout:** lee `coins`, `questReward`, `bonusReward`. Calcula y muestra `newCoins` y un mensaje resumen.
3) **Damage + heal report:** lee `playerHP`, `damage`, `heal`. Calcula `hpAfterHit` y `hpAfterHeal` (solo suma/resta) e imprime reporte en 3–5 líneas.
4) **Travel calculator:** lee `speed` y `seconds` (double), calcula `distance` y muestra el resultado con una frase clara.
5) **Potion recipe:** lee `herbs` y `herbsPerPotion`. Calcula `potions` (/) y `leftoverHerbs` (%) y muestra ambos.


---

# 4) Condicionales

## Explicación
Un **condicional** permite que el programa tome decisiones: “si pasa esto, haz aquello; si no, haz otra cosa”. En C++ usamos `if`, `else if` y `else` para controlar el flujo. La idea clave es evaluar una **condición** que resulta verdadera o falsa (por ejemplo: `playerHP <= 0`, `coins >= price`, `level == 10`).

En videojuegos, los condicionales están en todas partes: morir si la vida llega a 0, permitir comprar si alcanzan las monedas, desbloquear una puerta si tienes la llave, o cambiar el mensaje según la dificultad.

---

## Ejemplos

### Ejemplo 1 — ¿El jugador sigue vivo?
```cpp
#include <iostream>

int main() {
    int playerHP;
    std::cout << "Player HP: ";
    std::cin >> playerHP;

    if (playerHP > 0) {
        std::cout << "Status: ALIVE
";
    } else {
        std::cout << "Status: DEAD
";
    }

    return 0;
}
```

### Ejemplo 2 — Compra en tienda
```cpp
#include <iostream>

int main() {
    int coins;
    int price;

    std::cout << "Coins: ";
    std::cin >> coins;

    std::cout << "Item price: ";
    std::cin >> price;

    if (coins >= price) {
        std::cout << "Purchase: OK
";
        std::cout << "Coins left: " << (coins - price) << "
";
    } else {
        std::cout << "Purchase: NOT ENOUGH COINS
";
    }

    return 0;
}
```

### Ejemplo 3 — Clampeo simple de HP
```cpp
#include <iostream>

int main() {
    const int MAX_HP = 100;
    int playerHP;

    std::cout << "Player HP: ";
    std::cin >> playerHP;

    if (playerHP > MAX_HP) {
        playerHP = MAX_HP;
    }

    std::cout << "Final HP: " << playerHP << "
";
    return 0;
}
```

### Ejemplo 4 — Elegir mensaje por dificultad
```cpp
#include <iostream>

int main() {
    int difficulty;
    std::cout << "Difficulty (1-3): ";
    std::cin >> difficulty;

    if (difficulty == 1) {
        std::cout << "Mode: EASY
";
    } else if (difficulty == 2) {
        std::cout << "Mode: NORMAL
";
    } else if (difficulty == 3) {
        std::cout << "Mode: HARD
";
    } else {
        std::cout << "Mode: UNKNOWN
";
    }

    return 0;
}
```

### Ejemplo 5 — ¿Tiene llave?
```cpp
#include <iostream>

int main() {
    int hasKeyInput; // 1 = yes, 0 = no
    std::cout << "Has key? (1=yes, 0=no): ";
    std::cin >> hasKeyInput;

    bool hasKey = (hasKeyInput == 1);

    if (hasKey) {
        std::cout << "Door: UNLOCKED
";
    } else {
        std::cout << "Door: LOCKED
";
    }

    return 0;
}
```

### Ejemplo 6 — Crítico simple
```cpp
#include <iostream>

int main() {
    int baseDamage;
    int isCriticalInput; // 1 = critical, 0 = normal

    std::cout << "Base damage: ";
    std::cin >> baseDamage;

    std::cout << "Critical? (1=yes, 0=no): ";
    std::cin >> isCriticalInput;

    int finalDamage = baseDamage;

    if (isCriticalInput == 1) {
        finalDamage = baseDamage * 2;
    }

    std::cout << "Final damage: " << finalDamage << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Game Over check:** lee `playerHP` y muestra `GAME OVER` si `playerHP <= 0`, si no muestra `KEEP PLAYING`.
2) **Can buy?:** lee `coins` y `price` y muestra `BUY` o `NO BUY`.
3) **Level gate:** lee `level` y muestra `UNLOCKED` si `level >= 10`, si no `LOCKED`.

### En casa
1) **Potion heal cap:** lee `playerHP`, `heal`, `MAX_HP` (const=100). Suma y si se pasa, ajusta a 100. Imprime HP final.
2) **Damage resistance:** lee `damage` y `hasShield` (1/0). Si hay escudo, reduce daño a la mitad (división entera). Imprime daño final.
3) **Score rank:** lee `score` y muestra:
    - `S` si score >= 1000
    - `A` si score >= 700
    - `B` si score >= 400
    - `C` en otro caso
4) **Door system:** lee `hasKey` (1/0) y `hasPermission` (1/0). Solo abre si ambas son 1. Imprime `OPEN` o `CLOSED`.
5) **Loot bonus:** lee `coins` y `isBonus` (1/0). Si es bonus, agrega +50 coins. Imprime coins finales.


---

# 5) Switch + menús

## Explicación
`switch` sirve para elegir entre **varias opciones** usando un solo valor (normalmente `int` o `char`). Es ideal cuando tienes un menú: según lo que el usuario elija, ejecutas una acción. Cada opción vive en un `case` y casi siempre se usa `break` para no “caer” en el siguiente caso.

En videojuegos (y prototipos en consola), `switch` aparece en menús de inicio, opciones, inventario y tiendas. En este tema haremos **menús de una sola interacción**: mostrar menú → leer opción → ejecutar → terminar.

---

## Ejemplos

### Ejemplo 1 — Menú básico
```cpp
#include <iostream>

int main() {
    int option;

    std::cout << "=== MAIN MENU ===
";
    std::cout << "1) New Game
";
    std::cout << "2) Load Game
";
    std::cout << "3) Exit
";
    std::cout << "Choose option: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "Starting new game...
"; break;
        case 2: std::cout << "Loading game...
"; break;
        case 3: std::cout << "Goodbye!
"; break;
        default: std::cout << "Invalid option.
"; break;
    }

    return 0;
}
```

### Ejemplo 2 — Dificultad
```cpp
#include <iostream>

int main() {
    int difficulty;
    std::cout << "Difficulty (1=Easy, 2=Normal, 3=Hard): ";
    std::cin >> difficulty;

    switch (difficulty) {
        case 1: std::cout << "Mode: EASY
"; break;
        case 2: std::cout << "Mode: NORMAL
"; break;
        case 3: std::cout << "Mode: HARD
"; break;
        default: std::cout << "Mode: UNKNOWN
"; break;
    }

    return 0;
}
```

### Ejemplo 3 — Selección de arma
```cpp
#include <iostream>

int main() {
    char weapon;
    std::cout << "Choose weapon (s=sword, b=bow, m=magic): ";
    std::cin >> weapon;

    switch (weapon) {
        case 's': std::cout << "Weapon: SWORD
"; break;
        case 'b': std::cout << "Weapon: BOW
"; break;
        case 'm': std::cout << "Weapon: MAGIC
"; break;
        default: std::cout << "Weapon: UNKNOWN
"; break;
    }

    return 0;
}
```

### Ejemplo 4 — Tienda con `switch` + `if`
```cpp
#include <iostream>

int main() {
    int coins;
    int option;

    const int POTION_PRICE = 20;
    const int ARROW_PRICE = 5;
    const int KEY_PRICE = 50;

    std::cout << "Coins: ";
    std::cin >> coins;

    std::cout << "=== SHOP (1 purchase) ===
";
    std::cout << "1) Potion (20)
";
    std::cout << "2) Arrows (5)
";
    std::cout << "3) Key (50)
";
    std::cout << "Choose item: ";
    std::cin >> option;

    switch (option) {
        case 1:
            if (coins >= POTION_PRICE) std::cout << "Bought Potion.
";
            else std::cout << "Not enough coins.
";
            break;
        case 2:
            if (coins >= ARROW_PRICE) std::cout << "Bought Arrows.
";
            else std::cout << "Not enough coins.
";
            break;
        case 3:
            if (coins >= KEY_PRICE) std::cout << "Bought Key.
";
            else std::cout << "Not enough coins.
";
            break;
        default:
            std::cout << "Invalid option.
";
            break;
    }

    return 0;
}
```

### Ejemplo 5 — Estado del juego
```cpp
#include <iostream>

int main() {
    int gameState; // 0=Title, 1=Playing, 2=Paused, 3=GameOver
    std::cout << "Game state (0-3): ";
    std::cin >> gameState;

    switch (gameState) {
        case 0: std::cout << "STATE: TITLE
"; break;
        case 1: std::cout << "STATE: PLAYING
"; break;
        case 2: std::cout << "STATE: PAUSED
"; break;
        case 3: std::cout << "STATE: GAME OVER
"; break;
        default: std::cout << "STATE: UNKNOWN
"; break;
    }

    return 0;
}
```

### Ejemplo 6 — Submenú simple
```cpp
#include <iostream>

int main() {
    int menu;

    std::cout << "1) Inventory
";
    std::cout << "2) Stats
";
    std::cout << "3) Exit
";
    std::cout << "Choose: ";
    std::cin >> menu;

    switch (menu) {
        case 1:
            std::cout << "[Inventory]
- Potion
- Key
";
            break;
        case 2:
            std::cout << "[Stats]
HP: 80
Coins: 120
";
            break;
        case 3:
            std::cout << "Exit.
";
            break;
        default:
            std::cout << "Invalid.
";
            break;
    }

    return 0;
}
```
---

## Desafíos

### En clase
1) **Menu ping:** menú con 3 opciones; con `switch` imprime un mensaje distinto.
2) **Difficulty switch:** lee `difficulty` (1-3) e imprime el nombre del modo.
3) **Weapon select:** lee un `char` (`s/b/m`) e imprime el arma.

### En casa
1) **Shop (1 compra):** lee `coins` y opción (1-4). Precio fijo por opción. `switch` + `if` para verificar compra.
2) **Options menu:** menú con 4 opciones (Audio/Video/Controls/Back). `switch` imprime pantalla distinta (texto).
3) **Attack type:** lee `attackType` (1=melee, 2=ranged, 3=magic) y `baseDamage`. `switch` aplica multiplicador x1/x2/x3.
4) **Game state report:** lee `gameState` (0-3) e imprime el nombre. Si inválido: `UNKNOWN`.
5) **Dialogue choice:** muestra 3 respuestas, lee opción y con `switch` imprime reacción distinta del NPC.


---

# 6) Ciclos (while)

## Explicación
Un **ciclo** permite repetir un bloque de código mientras una condición sea verdadera. `while` se usa cuando no sabes exactamente cuántas veces vas a repetir. La clave es que la condición debe cambiar para evitar un ciclo infinito.

En videojuegos, `while` aparece en menús que se repiten, en conteos, y en lógica tipo “seguir hasta que…”. En este tema haremos repeticiones simples con contadores y acumuladores.

---

## Ejemplos

### Ejemplo 1 — Contar hasta N
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "Count to: ";
    std::cin >> n;

    int i = 1;
    while (i <= n) {
        std::cout << i << "
";
        i++;
    }
    return 0;
}
```

### Ejemplo 2 — Acumular coins
```cpp
#include <iostream>

int main() {
    int coins = 0;
    int pickUps;

    std::cout << "How many coin pickups? ";
    std::cin >> pickUps;

    int i = 0;
    while (i < pickUps) {
        coins += 1;
        i++;
    }

    std::cout << "Coins: " << coins << "
";
    return 0;
}
```

### Ejemplo 3 — Menú repetible hasta Exit
```cpp
#include <iostream>

int main() {
    int option = 0;
    int coins = 0;

    while (option != 3) {
        std::cout << "=== MENU ===
";
        std::cout << "1) Add coins (+10)
";
        std::cout << "2) Show coins
";
        std::cout << "3) Exit
";
        std::cout << "Choose: ";
        std::cin >> option;

        if (option == 1) coins += 10;
        else if (option == 2) std::cout << "Coins: " << coins << "
";
        else if (option == 3) std::cout << "Bye!
";
        else std::cout << "Invalid.
";
    }

    return 0;
}
```

### Ejemplo 4 — Cooldown
```cpp
#include <iostream>

int main() {
    int cooldown;
    std::cout << "Cooldown seconds: ";
    std::cin >> cooldown;

    while (cooldown > 0) {
        std::cout << "Cooldown: " << cooldown << "
";
        cooldown--;
    }

    std::cout << "Skill ready!
";
    return 0;
}
```

### Ejemplo 5 — Total damage
```cpp
#include <iostream>

int main() {
    int hits;
    int damagePerHit;

    std::cout << "Hits: ";
    std::cin >> hits;

    std::cout << "Damage per hit: ";
    std::cin >> damagePerHit;

    int totalDamage = 0;
    int i = 0;

    while (i < hits) {
        totalDamage += damagePerHit;
        i++;
    }

    std::cout << "Total damage: " << totalDamage << "
";
    return 0;
}
```

### Ejemplo 6 — HP drain hasta 0
```cpp
#include <iostream>

int main() {
    int hp;
    int drain;

    std::cout << "HP: ";
    std::cin >> hp;
    std::cout << "Drain per turn: ";
    std::cin >> drain;

    while (hp > 0) {
        hp -= drain;
        std::cout << "HP: " << hp << "
";
    }

    std::cout << "GAME OVER
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Countdown:** imprime cuenta regresiva hasta 0.
2) **Coin loop:** suma +1 coin por pickup usando `while`.
3) **Menu repeat:** menú que repita hasta Exit.

### En casa
1) **Damage simulator:** calcula `totalDamage` con `while`.
2) **Potion crafting:** crea pociones restando hierbas mientras alcance.
3) **Shop until exit:** tienda repetible con 3 ítems (sin arrays).
4) **XP grind:** repite quests hasta llegar a `xpToLevel`.
5) **Life drain:** drena HP por turno hasta `GAME OVER`.


---

# 7) Ciclos (for) + patrones comunes

## Explicación
`for` es un ciclo ideal cuando sabes cuántas repeticiones necesitas. Junta inicio, condición y avance en una sola línea, perfecto para conteos y recorridos.

En videojuegos, `for` se usa para oleadas, combos y estadísticas. En este tema practicamos sumas, promedios, máximos/mínimos y tablas.

---

## Ejemplos

### Ejemplo 1 — Imprimir 1..N
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "N: ";
    std::cin >> n;

    for (int i = 1; i <= n; i++) {
        std::cout << i << "
";
    }
    return 0;
}
```

### Ejemplo 2 — Suma de XP por quests
```cpp
#include <iostream>

int main() {
    int quests;
    int xpPerQuest;

    std::cout << "Quests: ";
    std::cin >> quests;
    std::cout << "XP per quest: ";
    std::cin >> xpPerQuest;

    int totalXP = 0;
    for (int i = 0; i < quests; i++) {
        totalXP += xpPerQuest;
    }

    std::cout << "Total XP: " << totalXP << "
";
    return 0;
}
```

### Ejemplo 3 — Promedio de daño
```cpp
#include <iostream>

int main() {
    int hits;
    std::cout << "Hits: ";
    std::cin >> hits;

    int sum = 0;
    for (int i = 1; i <= hits; i++) {
        int damage;
        std::cout << "Damage " << i << ": ";
        std::cin >> damage;
        sum += damage;
    }

    double avg = static_cast<double>(sum) / hits;
    std::cout << "Average: " << avg << "
";
    return 0;
}
```

### Ejemplo 4 — Máximo de N scores
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "How many scores? ";
    std::cin >> n;

    int maxScore = -999999;
    for (int i = 1; i <= n; i++) {
        int score;
        std::cout << "Score " << i << ": ";
        std::cin >> score;
        if (score > maxScore) maxScore = score;
    }

    std::cout << "Max score: " << maxScore << "
";
    return 0;
}
```

### Ejemplo 5 — Tabla de combo 1..5
```cpp
#include <iostream>

int main() {
    int baseDamage;
    std::cout << "Base damage: ";
    std::cin >> baseDamage;

    for (int combo = 1; combo <= 5; combo++) {
        std::cout << "Combo " << combo << ": " << (baseDamage * combo) << "
";
    }
    return 0;
}
```

### Ejemplo 6 — Contar crits (1/0) en N ataques
```cpp
#include <iostream>

int main() {
    int attacks;
    std::cout << "Attacks: ";
    std::cin >> attacks;

    int critCount = 0;
    for (int i = 1; i <= attacks; i++) {
        int isCrit;
        std::cout << "Crit? (1/0): ";
        std::cin >> isCrit;
        if (isCrit == 1) critCount++;
    }

    std::cout << "Crits: " << critCount << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Combo table:** imprime combo 1..5.
2) **Sum coins:** suma coins con `for`.
3) **Count crits:** cuenta crits con `for`.

### En casa
1) **Average damage:** promedio de N daños.
2) **Best run:** máximo de N puntajes.
3) **XP ladder:** imprime XP después de cada quest.
4) **Wave spawner:** imprime texto por wave.
5) **Min/Max:** encuentra min y max de N valores.


---

# 8) Funciones

## Explicación
Una **función** es un bloque con nombre que puedes reutilizar. Sirve para separar responsabilidades: calcular daño, clamping, compras, etc. Las funciones reciben **parámetros** y pueden regresar un valor con `return` (o ser `void` si solo imprimen).

En videojuegos, funciones son la base para sistemas reutilizables. En este tema aprenderás a declarar funciones, usar parámetros y retorno, y llamarlas desde `main`.

---

## Ejemplos

### Ejemplo 1 — Sumar coins
```cpp
#include <iostream>

int addCoins(int coins, int reward) {
    return coins + reward;
}

int main() {
    std::cout << addCoins(10, 25) << "
";
    return 0;
}
```

### Ejemplo 2 — Calcular daño final
```cpp
#include <iostream>

int calculateDamage(int baseDamage, int bonus) {
    return baseDamage + bonus;
}

int main() {
    std::cout << calculateDamage(30, 12) << "
";
    return 0;
}
```

### Ejemplo 3 — Clamp int
```cpp
#include <iostream>

int clampInt(int value, int minV, int maxV) {
    if (value < minV) return minV;
    if (value > maxV) return maxV;
    return value;
}

int main() {
    std::cout << clampInt(140, 0, 100) << "
";
    return 0;
}
```

### Ejemplo 4 — canBuy
```cpp
#include <iostream>

bool canBuy(int coins, int price) {
    return coins >= price;
}

int main() {
    std::cout << (canBuy(50, 20) ? "BUY
" : "NO BUY
");
    return 0;
}
```

### Ejemplo 5 — Multiplicador por tipo de ataque
```cpp
#include <iostream>

int applyAttackType(int baseDamage, int attackType) {
    switch (attackType) {
        case 1: return baseDamage;
        case 2: return baseDamage * 2;
        case 3: return baseDamage * 3;
        default: return baseDamage;
    }
}

int main() {
    std::cout << applyAttackType(10, 3) << "
";
    return 0;
}
```

### Ejemplo 6 — HUD
```cpp
#include <iostream>
#include <string>

void printHud(const std::string& playerName, int hp, int coins) {
    std::cout << "Player: " << playerName << " | HP: " << hp << " | Coins: " << coins << "
";
}

int main() {
    printHud("Aline", 80, 120);
    return 0;
}
```
---

## Desafíos

### En clase
1) **calculateDamage:** crea y úsala.
2) **clampInt:** crea y prueba.
3) **canBuy:** crea y muestra.

### En casa
1) **applyHeal:** suma heal y clampa a 100.
2) **xpAfterQuests:** XP final tras quests.
3) **attackReport:** daño x2 si crit.
4) **menuAction:** función con switch que imprime acción.
5) **cooldownTicks:** imprime ticks hasta 0 con ciclo.


---

# 9) Arreglos

## Explicación
Un **array** es una colección de valores del mismo tipo en posiciones consecutivas. Se accede con índices desde 0. Los arrays tienen tamaño fijo, útiles para listas con un límite definido (por ejemplo: 5 highscores).

En videojuegos, arrays sirven para tablas y listas fijas. En este tema declaras arrays, los llenas y los recorres con ciclos para hacer cálculos.

---

## Ejemplos

### Ejemplo 1 — 5 scores inicializados
```cpp
#include <iostream>

int main() {
    int scores[5] = { 100, 250, 75, 400, 60 };
    std::cout << scores[0] << "
";
    std::cout << scores[3] << "
";
    return 0;
}
```

### Ejemplo 2 — Llenar 3 daños
```cpp
#include <iostream>

int main() {
    int damages[3];

    for (int i = 0; i < 3; i++) {
        std::cout << "Damage " << i << ": ";
        std::cin >> damages[i];
    }
    return 0;
}
```

### Ejemplo 3 — Suma total
```cpp
#include <iostream>

int main() {
    int coinsPerRoom[4] = { 5, 10, 3, 7 };
    int total = 0;

    for (int i = 0; i < 4; i++) total += coinsPerRoom[i];
    std::cout << total << "
";
    return 0;
}
```

### Ejemplo 4 — High score
```cpp
#include <iostream>

int main() {
    int scores[5];

    for (int i = 0; i < 5; i++) {
        std::cout << "Score " << i << ": ";
        std::cin >> scores[i];
    }

    int maxScore = scores[0];
    for (int i = 1; i < 5; i++) {
        if (scores[i] > maxScore) maxScore = scores[i];
    }

    std::cout << "High score: " << maxScore << "
";
    return 0;
}
```

### Ejemplo 5 — Buscar id
```cpp
#include <iostream>

int main() {
    int itemIds[4] = { 10, 22, 35, 41 };
    int target;

    std::cout << "Search item id: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < 4; i++) {
        if (itemIds[i] == target) found = true;
    }

    std::cout << (found ? "FOUND
" : "NOT FOUND
");
    return 0;
}
```

### Ejemplo 6 — Contar misses
```cpp
#include <iostream>

int main() {
    int hits[6] = { 10, 0, 5, 0, 12, 3 };
    int missCount = 0;

    for (int i = 0; i < 6; i++) {
        if (hits[i] == 0) missCount++;
    }

    std::cout << "Misses: " << missCount << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **3 scores avg:** lee 3 scores y promedio.
2) **Max of 5:** lee 5 daños y máximo.
3) **Find item:** busca un id en array fijo.

### En casa
1) **Room coins:** lee 10 valores y suma.
2) **Damage stats:** min, max, promedio de 8 daños.
3) **Inventory fixed:** array de 5 strings, imprime numerado.
4) **Count rares:** cuenta valores >= 50 en 12 loot values.
5) **Swap positions:** intercambia 0<->4 y 1<->3 en 5 valores.


---

# 10) Vectores

## Explicación 
`std::vector` es una lista dinámica: crece y se reduce cuando lo necesitas. Puedes agregar con `push_back`, quitar con `pop_back` y obtener el tamaño con `size()`.

En videojuegos, vectores sirven para inventarios que crecen, listas de enemigos, quests, etc. En este tema crearás vectores, agregarás datos y los recorrerás.

---

## Ejemplos

### Ejemplo 1 — Agregar items
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory;
    inventory.push_back("Potion");
    inventory.push_back("Key");

    std::cout << inventory.size() << "
";
    return 0;
}
```

### Ejemplo 2 — Imprimir inventario
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Key", "Gem" };

    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << i << ") " << inventory[i] << "
";
    }
    return 0;
}
```

### Ejemplo 3 — Leer N scores
```cpp
#include <iostream>
#include <vector>

int main() {
    int n;
    std::cout << "How many scores? ";
    std::cin >> n;

    std::vector<int> scores;
    for (int i = 0; i < n; i++) {
        int s;
        std::cout << "Score: ";
        std::cin >> s;
        scores.push_back(s);
    }

    std::cout << "Saved: " << scores.size() << "
";
    return 0;
}
```

### Ejemplo 4 — Suma total
```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> coins = { 5, 10, 3, 7 };
    int total = 0;

    for (int i = 0; i < (int)coins.size(); i++) total += coins[i];
    std::cout << total << "
";
    return 0;
}
```

### Ejemplo 5 — Buscar item
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Key", "Gem" };
    std::string target;

    std::cout << "Search: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inventory.size(); i++) {
        if (inventory[i] == target) found = true;
    }

    std::cout << (found ? "FOUND
" : "NOT FOUND
");
    return 0;
}
```

### Ejemplo 6 — pop_back
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Key", "Gem" };
    inventory.pop_back();

    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << inventory[i] << "
";
    }
    return 0;
}
```
---

## Desafíos

### En clase
1) **Add 3 items:** agrega 3 items e imprime size.
2) **Print list:** imprime vector numerado.
3) **Sum vector:** suma un vector de 5 ints.

### En casa
1) **Dynamic inventory:** lee N items, guarda e imprime.
2) **High score:** lee N scores y encuentra máximo.
3) **Search:** busca un target y reporta si existe.
4) **Remove last:** agrega 5 items, elimina 2, imprime.
5) **Sentinel coins:** lee coins hasta -1, guarda en vector, imprime total.


---

# 11) Strings

## Explicación
`std::string` representa texto. Además de leer palabras, puedes medir longitud, buscar texto, cortar partes y leer líneas completas con `getline`. Esto sirve para comandos, diálogos y parsing simple.

En videojuegos de consola, strings te permiten crear comandos (“attack”, “heal”), construir mensajes y manejar entradas del usuario. En este tema practicamos operaciones comunes con strings.

---

## Ejemplos

### Ejemplo 1 — Longitud
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;
    std::cout << "Name: ";
    std::cin >> playerName;

    std::cout << playerName.length() << "
";
    return 0;
}
```

### Ejemplo 2 — Concatenación
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name = "Player";
    std::string hud = "Name: " + name + " | HP: 100";
    std::cout << hud << "
";
    return 0;
}
```

### Ejemplo 3 — substr
```cpp
#include <iostream>
#include <string>

int main() {
    std::string item = "Potion_Healing";
    std::string prefix = item.substr(0, 6);
    std::cout << prefix << "
";
    return 0;
}
```

### Ejemplo 4 — find
```cpp
#include <iostream>
#include <string>

int main() {
    std::string command;
    std::cout << "Command: ";
    std::cin >> command;

    if (command.find("atk") != std::string::npos) std::cout << "Attack-ish
";
    else std::cout << "Other
";

    return 0;
}
```

### Ejemplo 5 — getline
```cpp
#include <iostream>
#include <string>

int main() {
    std::string line;
    std::cout << "Dialog: ";
    std::getline(std::cin >> std::ws, line);

    std::cout << line << "
";
    return 0;
}
```

### Ejemplo 6 — Comando exacto
```cpp
#include <iostream>
#include <string>

int main() {
    std::string command;
    std::cout << "Type command (attack/heal): ";
    std::cin >> command;

    if (command == "attack") std::cout << "ATTACK!
";
    else if (command == "heal") std::cout << "HEAL!
";
    else std::cout << "UNKNOWN
";

    return 0;
}
```
---

## Desafíos

### En clase
1) **Name length:** lee nombre y muestra longitud.
2) **Concat HUD:** arma un HUD string con coins.
3) **Command compare:** attack/heal/unknown.

### En casa
1) **Nickname:** lee nombre completo con getline, imprime primeros 3 chars.
2) **Item parsing:** separa antes/después de '_' usando find+substr.
3) **Dialog builder:** lee 3 líneas con getline e imprime con "NPC:".
4) **Search keyword:** frase + palabra, indica si aparece.
5) **Command menu:** comandos string que impriman acciones con if/else.


---

# 12) Estructuras

## Explicación
Un `struct` agrupa datos relacionados en un solo tipo. En vez de variables sueltas, puedes representar un jugador o un item como una sola “cosa” con campos.

En videojuegos, structs representan entidades: jugador, enemigo, item, quest. En este tema crearás structs, los usarás y harás listas con `std::vector` de structs.

---

## Ejemplos

### Ejemplo 1 — Player
```cpp
#include <iostream>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    Player p{ "Aline", 80, 120 };
    std::cout << p.name << " HP=" << p.hp << " Coins=" << p.coins << "
";
    return 0;
}
```

### Ejemplo 2 — Leer Player
```cpp
#include <iostream>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    Player p;
    std::cout << "Name: ";
    std::cin >> p.name;
    std::cout << "HP: ";
    std::cin >> p.hp;
    std::cout << "Coins: ";
    std::cin >> p.coins;

    std::cout << p.name << "
";
    return 0;
}
```

### Ejemplo 3 — Item
```cpp
#include <iostream>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    Item potion{ "Potion", 20 };
    std::cout << potion.name << " " << potion.price << "
";
    return 0;
}
```

### Ejemplo 4 — Vector<Item>
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inventory = { {"Potion",20}, {"Key",50} };

    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << inventory[i].name << " (" << inventory[i].price << ")
";
    }
    return 0;
}
```

### Ejemplo 5 — Buscar por nombre
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inventory = { {"Potion",20}, {"Key",50}, {"Gem",200} };
    std::string target;
    std::cout << "Search: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inventory.size(); i++) {
        if (inventory[i].name == target) {
            found = true;
            std::cout << "Price: " << inventory[i].price << "
";
        }
    }
    if (!found) std::cout << "Not found
";
    return 0;
}
```

### Ejemplo 6 — Actualizar stats
```cpp
#include <iostream>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    Player p{ "Player", 60, 10 };
    p.coins += 25;
    p.hp += 10;

    std::cout << p.coins << " " << p.hp << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Player struct:** crea y muestra.
2) **Item struct:** crea y muestra.
3) **Update:** actualiza hp/coins.

### En casa
1) **Inventory list:** lee 5 Items a vector e imprime.
2) **Search item:** buscar por nombre y mostrar price.
3) **Total cost:** suma precios de items comprados.
4) **Enemy struct:** Enemy{name,hp,damage} y preview.
5) **Loot filter:** imprime items con price >= 50.


---

# 13) Archivos

## Explicación
Persistencia significa guardar datos en un archivo para usarlos después. En C++ se usa `<fstream>`: `std::ofstream` para escribir y `std::ifstream` para leer. Un formato simple y consistente evita errores.

En videojuegos, esto es un “save file”. En este tema guardarás y cargarás valores básicos y listas simples en archivos de texto.

---

## Ejemplos

### Ejemplo 1 — Escribir save.txt
```cpp
#include <fstream>

int main() {
    std::ofstream out("save.txt");
    out << "name=Player
";
    out << "hp=80
";
    out << "coins=120
";
    return 0;
}
```

### Ejemplo 2 — Leer líneas
```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::ifstream in("save.txt");
    std::string line;

    while (std::getline(in, line)) {
        std::cout << line << "
";
    }
    return 0;
}
```

### Ejemplo 3 — Guardar 3 valores
```cpp
#include <fstream>
#include <string>

int main() {
    std::string name = "Aline";
    int hp = 70;
    int coins = 55;

    std::ofstream out("player_save.txt");
    out << name << "
" << hp << "
" << coins << "
";
    return 0;
}
```

### Ejemplo 4 — Cargar 3 valores
```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::ifstream in("player_save.txt");
    std::string name;
    int hp;
    int coins;

    std::getline(in, name);
    in >> hp;
    in >> coins;

    std::cout << name << " " << hp << " " << coins << "
";
    return 0;
}
```

### Ejemplo 5 — Guardar inventario
```cpp
#include <fstream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Key", "Gem" };

    std::ofstream out("inventory.txt");
    out << inventory.size() << "
";
    for (int i = 0; i < (int)inventory.size(); i++) {
        out << inventory[i] << "
";
    }
    return 0;
}
```

### Ejemplo 6 — Cargar inventario
```cpp
#include <fstream>
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::ifstream in("inventory.txt");
    int n;
    in >> n;

    std::vector<std::string> inventory;
    inventory.reserve(n);

    for (int i = 0; i < n; i++) {
        std::string item;
        in >> item;
        inventory.push_back(item);
    }

    std::cout << inventory.size() << "
";
    return 0;
}
```
---

## Desafíos

### En clase
1) **Write save:** guarda name/hp/coins (1 por línea).
2) **Read save:** carga y muestra.
3) **Write inventory:** guarda 3 items en archivo.

### En casa
1) **Save/Load player:** menú para guardar o cargar jugador.
2) **Inventory save/load:** lee N items, guarda, carga y muestra.
3) **Highscores file:** guarda 5 scores, carga y muestra máximo.
4) **Quest log:** guarda 5 quests y luego carga y lista.
5) **Append log:** elegir sobrescribir o agregar una línea al log.


---

# 14) Depuración y calidad

## Explicación
Depurar es entender por qué el programa no hace lo esperado. La técnica más accesible es imprimir estados con `[DEBUG]` y seguir el rastro. Calidad también incluye mejorar nombres y estructura sin cambiar funcionalidad (refactor).

En videojuegos, bugs típicos: vida negativa, monedas incorrectas, duplicación de items. Aquí practicarás prints de depuración, casos de prueba simples y refactor básico.

---

## Ejemplos

### Ejemplo 1 — Debug prints
```cpp
#include <iostream>

int main() {
    int hp = 50;
    int damage = 20;

    std::cout << "[DEBUG] hp=" << hp << " damage=" << damage << "
";
    int hpAfter = hp - damage;
    std::cout << "[DEBUG] hpAfter=" << hpAfter << "
";

    std::cout << hpAfter << "
";
    return 0;
}
```

### Ejemplo 2 — Detectar not enough coins
```cpp
#include <iostream>

int main() {
    int coins = 30;
    int price = 50;

    int coinsLeft = coins - price;
    std::cout << "[DEBUG] coinsLeft=" << coinsLeft << "
";

    if (coinsLeft < 0) std::cout << "Not enough coins.
";
    else std::cout << "Purchase OK.
";

    return 0;
}
```

### Ejemplo 3 — Refactor a función
```cpp
#include <iostream>

int applyDamage(int hp, int damage) {
    return hp - damage;
}

int main() {
    std::cout << applyDamage(80, 35) << "
";
    return 0;
}
```

### Ejemplo 4 — Menú limpio con switch
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "1) Show
2) Add
3) Exit
Choose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "Showing...
"; break;
        case 2: std::cout << "Adding...
"; break;
        case 3: std::cout << "Bye
"; break;
        default: std::cout << "Invalid
"; break;
    }
    return 0;
}
```

### Ejemplo 5 — Helper clamp
```cpp
#include <iostream>

int clampInt(int value, int minV, int maxV) {
    if (value < minV) return minV;
    if (value > maxV) return maxV;
    return value;
}

int main() {
    std::cout << clampInt(140, 0, 100) << "
";
    return 0;
}
```

### Ejemplo 6 — Prueba manual
```cpp
#include <iostream>

int main() {
    int expected = 15;
    int result = 10 + 5;

    std::cout << "Expected: " << expected << "
";
    std::cout << "Result:   " << result << "
";
    std::cout << (result == expected ? "TEST PASS
" : "TEST FAIL
");
    return 0;
}
```
---

## Desafíos

### En clase
1) **Debug coins:** prints antes/después de compra.
2) **Find bug:** agrega prints para detectar error.
3) **Refactor:** convierte bloque repetido en función.

### En casa
1) **Bug hunt:** documenta cómo encontraste un bug con prints.
2) **Refactor menu:** if/else → switch + funciones.
3) **Edge cases:** prueba clamp HP con extremos.
4) **Mini tests:** 5 pruebas expected/result de funciones.
5) **Readability pass:** renombra variables y mejora formato.


---