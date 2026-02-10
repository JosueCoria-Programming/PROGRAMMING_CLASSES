# Guía del profesor + desafíos resueltos (C++ — Consola)
**Materia:** INTRODUCCIÓN A LA PROGRAMACIÓN  
**Profesor:** Josue Coria  
**Institución:** UNITEC

> Esta guía está pensada para darte: (1) explicación extendida, (2) ejemplos distintos a los del alumno y (3) soluciones de desafíos por tema.

---

# 1) ¿Qué es programar?

## Explicación (máx 5 párrafos)
Programar es **escribir instrucciones** para que una computadora haga algo. La computadora no “adivina”: ejecuta exactamente lo que le dices, en el orden que lo dices. Cuando algo sale mal, casi siempre es porque **faltó una instrucción**, está en el orden equivocado, o la instrucción no significa lo que creíamos.

Para estudiantes “cero absoluto”, la prioridad no es memorizar sintaxis, sino dominar el ciclo: **editar → compilar → ejecutar → observar**. Ese ciclo entrena el cerebro a trabajar como ingeniero: propones una hipótesis (“esto imprimirá X”), la pruebas, y corriges según evidencia (la salida real).

En C++, la estructura mínima es `#include <iostream>` para poder imprimir, y `int main()` como punto de entrada del programa. Si esto se siente como un ritual arcano… lo es un poco. Pero la magia se vuelve mecánica rápido: “main” es donde empieza la historia.

En contexto de videojuegos de consola, hoy estamos construyendo la primera “pantalla”: título, HUD, menú y mensajes. Aunque todavía no hay interacción, ya estamos diseñando **comunicación con el jugador**: claridad, formato, consistencia, y estética de texto (ASCII).

Regla didáctica del tema: **solo salida por consola**. Nada de `cin` todavía. Si alguien intenta “hacerlo interactivo”, se le celebra la intención y se redirige: primero dominar “mostrar”, luego dominar “leer”.

---

## 6 ejemplos resueltos (distintos a la guía del alumno)

### Ejemplo 1 — “Boot sequence” (estilo arcade)
```cpp
#include <iostream>

int main() {
    std::cout << "[BOOT] Loading assets... OK\n";
    std::cout << "[BOOT] Initializing game systems... OK\n";
    std::cout << "[BOOT] Ready.\n";
    return 0;
}
```

### Ejemplo 2 — Título con separadores
```cpp
#include <iostream>

int main() {
    std::cout << "==============================\n";
    std::cout << "        CONSOLE QUEST         \n";
    std::cout << "==============================\n";
    return 0;
}
```

### Ejemplo 3 — “Patch notes” en consola
```cpp
#include <iostream>

int main() {
    std::cout << "Patch 0.1\n";
    std::cout << "- Added title screen\n";
    std::cout << "- Added main menu (text)\n";
    std::cout << "- Fixed: typo in HUD\n";
    return 0;
}
```

### Ejemplo 4 — Mini mapa ASCII (estático)
```cpp
#include <iostream>

int main() {
    std::cout << "Map:\n";
    std::cout << "###########\n";
    std::cout << "#P....#...#\n";
    std::cout << "#.####...E#\n";
    std::cout << "###########\n";
    return 0;
}
```

### Ejemplo 5 — Mensaje de misión (brief)
```cpp
#include <iostream>

int main() {
    std::cout << "Mission: Escape the dungeon\n";
    std::cout << "Objective: Find the key and reach the exit\n";
    std::cout << "Tip: Avoid traps.\n";
    return 0;
}
```

### Ejemplo 6 — Créditos compactos (formato tabla)
```cpp
#include <iostream>

int main() {
    std::cout << "CREDITS\n";
    std::cout << "----------------\n";
    std::cout << "Code     : You\n";
    std::cout << "Design   : You\n";
    std::cout << "Testing  : You\n";
    std::cout << "Producer : Coffee\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) HUD estático
**Objetivo:** que practiquen formato y consistencia visual.
```cpp
#include <iostream>

int main() {
    std::cout << "HP: [#####-----]  Coins: 000  Level: 1\n";
    return 0;
}
```

#### 2) Pantalla “GAME OVER” con recuadro ASCII
**Tip docente:** deja que inventen su propio recuadro; evalúa claridad, no “arte”.
```cpp
#include <iostream>

int main() {
    std::cout << "+------------------+\n";
    std::cout << "|     GAME OVER    |\n";
    std::cout << "+------------------+\n";
    return 0;
}
```

#### 3) Menú principal (4 opciones)
**Nota:** no es interactivo todavía, solo mostrar.
```cpp
#include <iostream>

int main() {
    std::cout << "=== MAIN MENU ===\n";
    std::cout << "1) New Game\n";
    std::cout << "2) Load Game\n";
    std::cout << "3) Options\n";
    std::cout << "4) Exit\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Intro de juego (mínimo 8 líneas)
```cpp
#include <iostream>

int main() {
    std::cout << "Night falls over the city.\n";
    std::cout << "A single neon sign flickers: 'EXIT'.\n";
    std::cout << "You wake up with no memory and one goal.\n";
    std::cout << "Find the key.\n";
    std::cout << "Avoid the guards.\n";
    std::cout << "Trust no one.\n";
    std::cout << "Reach the gate before dawn.\n";
    std::cout << "Good luck, runner.\n";
    return 0;
}
```

#### 2) Controls (mínimo 6 líneas)
```cpp
#include <iostream>

int main() {
    std::cout << "CONTROLS\n";
    std::cout << "- Move Left  : A\n";
    std::cout << "- Move Right : D\n";
    std::cout << "- Jump       : Space\n";
    std::cout << "- Attack     : J\n";
    std::cout << "- Block      : K\n";
    std::cout << "- Pause      : P\n";
    return 0;
}
```

#### 3) Diálogo con elección simulada (10 líneas + 2 opciones)
```cpp
#include <iostream>

int main() {
    std::cout << "NPC: Traveler... you look lost.\n";
    std::cout << "You: Where am I?\n";
    std::cout << "NPC: In the ruins of Old Byte.\n";
    std::cout << "You: I need to leave.\n";
    std::cout << "NPC: Then you need a key.\n";
    std::cout << "You: Where do I find it?\n";
    std::cout << "NPC: Deep below, past the traps.\n";
    std::cout << "You: Sounds fun.\n";
    std::cout << "NPC: It isn't.\n";
    std::cout << "NPC: Decide now.\n";
    std::cout << "1) Help the village\n";
    std::cout << "2) Ignore and leave\n";
    return 0;
}
```

#### 4) Pantalla de créditos (mínimo 10 líneas)
```cpp
#include <iostream>

int main() {
    std::cout << "CREDITS\n";
    std::cout << "Director........: Alex Pixel\n";
    std::cout << "Lead Programmer.: Byte Knight\n";
    std::cout << "Gameplay Design.: Luna Loop\n";
    std::cout << "Art............: Neon Brush\n";
    std::cout << "Music..........: Chiptune Cat\n";
    std::cout << "QA.............: Bug Hunter\n";
    std::cout << "Producer.......: Coffee Wizard\n";
    std::cout << "Special Thanks.: The Player\n";
    std::cout << "Made with love.\n";
    return 0;
}
```

#### 5) Mini tutorial (pasos 1 al 8)
```cpp
#include <iostream>

int main() {
    std::cout << "TUTORIAL\n";
    std::cout << "1) Read the mission.\n";
    std::cout << "2) Open the main menu.\n";
    std::cout << "3) Start a new game.\n";
    std::cout << "4) Learn the controls.\n";
    std::cout << "5) Explore the first room.\n";
    std::cout << "6) Avoid traps.\n";
    std::cout << "7) Find the key.\n";
    std::cout << "8) Reach the exit.\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Pide que todos muestren su salida en consola **sin compilar por ellos** (ellos deben ejecutar).
- Revisa 3 cosas: **(1)** que el programa corra, **(2)** que la salida sea clara/ordenada, **(3)** que no haya texto “mezclado” o difícil de leer.
- Mini-puente hacia el súper desafío: “Tu súper desafío va a ser un sistema de videojuego en consola. Hoy ya tienes: título, menú y UI textual. Próximo paso: **leer entradas** para que deje de ser estático.”

---

# (Siguiente) Tema 2
> En el siguiente turno agregamos el Tema 2 a este mismo archivo.

---

# 2) Variables, tipos y operaciones

## Explicación (máx 5 párrafos)
Una **variable** es una “caja” con nombre donde guardas un valor. En C++ cada caja tiene un **tipo** (por ejemplo `int` para enteros, `double` para decimales). El tipo importa porque define qué operaciones tienen sentido y cuánta precisión necesitas.

En programación de videojuegos, casi todo termina siendo números: vida, daño, velocidad, oro, tiempo, experiencia. Si eliges mal el tipo, aparecen bugs raros: truncas decimales, desbordas enteros, o calculas porcentajes incorrectos.

Este tema se centra en: declarar variables, asignar valores, usar operadores (`+ - * / %`) y mostrar resultados. **Sin input todavía**: primero controlamos el mundo con valores fijos, luego lo hacemos interactivo.

Tip de docencia: insiste en que el alumno pueda “leer” su programa como una receta. Si no entiende qué significa cada variable, el código no existe: solo es ruido.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Daño final con bono
```cpp
#include <iostream>

int main() {
    int base_damage = 35;
    int weapon_bonus = 12;
    int final_damage = base_damage + weapon_bonus;

    std::cout << "Final damage: " << final_damage << "\n";
    return 0;
}
```

### Ejemplo 2 — Monedas después de comprar (1 ítem)
```cpp
#include <iostream>

int main() {
    int coins = 100;
    int price = 35;
    int coins_left = coins - price;

    std::cout << "Coins left: " << coins_left << "\n";
    return 0;
}
```

### Ejemplo 3 — Tiempo total de misión (segundos → minutos)
```cpp
#include <iostream>

int main() {
    int seconds = 245;
    int minutes = seconds / 60;
    int leftover_seconds = seconds % 60;

    std::cout << "Time: " << minutes << "m " << leftover_seconds << "s\n";
    return 0;
}
```

### Ejemplo 4 — Porcentaje de progreso (double)
```cpp
#include <iostream>

int main() {
    int current_xp = 350;
    int xp_to_level = 500;

    double progress_percent = (current_xp * 100.0) / xp_to_level;
    std::cout << "Progress: " << progress_percent << "%\n";
    return 0;
}
```

### Ejemplo 5 — Conversión de monedas a “copper”
```cpp
#include <iostream>

int main() {
    const int COPPER_PER_SILVER = 10;
    const int COPPER_PER_GOLD = 100;

    int gold = 3;
    int silver = 7;
    int copper = 4;

    int total_copper = gold * COPPER_PER_GOLD + silver * COPPER_PER_SILVER + copper;
    std::cout << "Total copper: " << total_copper << "\n";
    return 0;
}
```

### Ejemplo 6 — DPS simple
```cpp
#include <iostream>

int main() {
    int total_damage = 250;
    double seconds = 12.5;

    double dps = total_damage / seconds;
    std::cout << "DPS: " << dps << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Damage calc
```cpp
#include <iostream>

int main() {
    int baseDamage = 20;
    int weaponBonus = 5;
    int finalDamage = baseDamage + weaponBonus;

    std::cout << "finalDamage: " << finalDamage << "\n";
    return 0;
}
```

#### 2) Coins left
```cpp
#include <iostream>

int main() {
    int coins = 120;
    int price = 15;
    int qty = 3;

    int coinsLeft = coins - (price * qty);
    std::cout << "coinsLeft: " << coinsLeft << "\n";
    return 0;
}
```

#### 3) XP total
```cpp
#include <iostream>

int main() {
    int currentXP = 80;
    int questXP = 45;
    int newXP = currentXP + questXP;

    std::cout << "newXP: " << newXP << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) DPS (daño por segundo)
```cpp
#include <iostream>

int main() {
    int totalDamage = 300;
    double seconds = 12.0;

    double dps = totalDamage / seconds;
    std::cout << "dps: " << dps << "\n";
    return 0;
}
```

#### 2) Crafting (/, %)
```cpp
#include <iostream>

int main() {
    int herbs = 53;
    int herbsPerPotion = 10;

    int potions = herbs / herbsPerPotion;
    int leftoverHerbs = herbs % herbsPerPotion;

    std::cout << "potions: " << potions << "\n";
    std::cout << "leftoverHerbs: " << leftoverHerbs << "\n";
    return 0;
}
```

#### 3) Currency system (todo a copper)
```cpp
#include <iostream>

int main() {
    int gold = 2;
    int silver = 5;
    int copper = 7;

    int totalCopper = gold * 100 + silver * 10 + copper;
    std::cout << "totalCopper: " << totalCopper << "\n";
    return 0;
}
```

#### 4) XP progress (%)
```cpp
#include <iostream>

int main() {
    int currentXP = 120;
    int xpToLevel = 500;

    double progressPercent = (currentXP * 100.0) / xpToLevel;
    std::cout << "progressPercent: " << progressPercent << "%\n";
    return 0;
}
```

#### 5) Cooldown (remaining)
```cpp
#include <iostream>

int main() {
    int cooldownSeconds = 30;
    int timePassed = 12;

    int remaining = cooldownSeconds - timePassed;
    std::cout << "remaining: " << remaining << "s\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Pide que expliquen en voz alta qué representa cada variable y por qué el tipo es correcto.
- Revisa que usen `100.0` (double) cuando se requieran porcentajes.
- Puente: “Tu súper desafío necesitará **stats** (HP/coins/xp) y cálculos. Hoy ya tienes la base.”

---

# 3) Entrada y salida

## Explicación (máx 5 párrafos)
La **salida** (`std::cout`) es cómo tu programa “habla” con el jugador. La **entrada** (`std::cin`) es cómo el jugador le da decisiones a tu sistema. En juegos de consola, `cin/cout` es tu UI.

Este tema introduce lectura de números y texto simple (una palabra). Para texto con espacios se usa `std::getline`, pero aquí lo usaremos solo cuando el ejercicio lo pida explícitamente (para no mezclar demasiado al inicio).

Didácticamente, tu meta es que el estudiante aprenda el patrón: **prompt claro → leer → calcular → imprimir resultado**. Si el prompt es confuso, el programa “funciona” pero el juego es injugable.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Elegir nombre y mostrar bienvenida
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;
    std::cout << "Enter name: ";
    std::cin >> playerName;

    std::cout << "Welcome, " << playerName << "!\n";
    return 0;
}
```

### Ejemplo 2 — Leer HP y mostrar barra textual simple
```cpp
#include <iostream>

int main() {
    int hp;
    std::cout << "HP (0-100): ";
    std::cin >> hp;

    std::cout << "HP: " << hp << "/100\n";
    return 0;
}
```

### Ejemplo 3 — Leer daño y aplicar a HP (sin condicionales)
```cpp
#include <iostream>

int main() {
    int hp;
    int damage;

    std::cout << "HP: ";
    std::cin >> hp;
    std::cout << "Damage: ";
    std::cin >> damage;

    int hpAfter = hp - damage;
    std::cout << "HP after hit: " << hpAfter << "\n";
    return 0;
}
```

### Ejemplo 4 — Leer tiempo y calcular distancia
```cpp
#include <iostream>

int main() {
    double speed;
    double seconds;

    std::cout << "Speed: ";
    std::cin >> speed;
    std::cout << "Seconds: ";
    std::cin >> seconds;

    double distance = speed * seconds;
    std::cout << "Distance: " << distance << "\n";
    return 0;
}
```

### Ejemplo 5 — Leer costo y monedas, calcular cambio (sin validar)
```cpp
#include <iostream>

int main() {
    int coins;
    int cost;

    std::cout << "Coins: ";
    std::cin >> coins;
    std::cout << "Cost: ";
    std::cin >> cost;

    int change = coins - cost;
    std::cout << "Change: " << change << "\n";
    return 0;
}
```

### Ejemplo 6 — Leer una línea (getline) para “dialog”
```cpp
#include <iostream>
#include <string>

int main() {
    std::string dialog;
    std::cout << "NPC says: ";
    std::getline(std::cin >> std::ws, dialog);

    std::cout << "NPC: " << dialog << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) HUD input
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;
    int playerHP;

    std::cout << "playerName: ";
    std::cin >> playerName;
    std::cout << "playerHP: ";
    std::cin >> playerHP;

    std::cout << "Player " << playerName << " | HP: " << playerHP << "\n";
    return 0;
}
```

#### 2) Coins reward
```cpp
#include <iostream>

int main() {
    int coins, reward;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "reward: ";
    std::cin >> reward;

    int newCoins = coins + reward;
    std::cout << "newCoins: " << newCoins << "\n";
    return 0;
}
```

#### 3) Shop total
```cpp
#include <iostream>

int main() {
    int itemPrice, qty;
    std::cout << "itemPrice: ";
    std::cin >> itemPrice;
    std::cout << "qty: ";
    std::cin >> qty;

    int totalCost = itemPrice * qty;
    std::cout << "totalCost: " << totalCost << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Character creator (mínimo 5 líneas)
```cpp
#include <iostream>
#include <string>

int main() {
    std::string playerName;
    std::string className;
    int level;
    int coins;

    std::cout << "playerName: ";
    std::cin >> playerName;
    std::cout << "className (1 word): ";
    std::cin >> className;
    std::cout << "level: ";
    std::cin >> level;
    std::cout << "coins: ";
    std::cin >> coins;

    std::cout << "=== CHARACTER SHEET ===\n";
    std::cout << "Name : " << playerName << "\n";
    std::cout << "Class: " << className << "\n";
    std::cout << "Level: " << level << "\n";
    std::cout << "Coins: " << coins << "\n";
    return 0;
}
```

#### 2) Quest payout
```cpp
#include <iostream>

int main() {
    int coins, questReward, bonusReward;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "questReward: ";
    std::cin >> questReward;
    std::cout << "bonusReward: ";
    std::cin >> bonusReward;

    int newCoins = coins + questReward + bonusReward;
    std::cout << "newCoins: " << newCoins << "\n";
    std::cout << "Quest complete! +" << questReward << " + bonus " << bonusReward << "\n";
    return 0;
}
```

#### 3) Damage + heal report
```cpp
#include <iostream>

int main() {
    int playerHP, damage, heal;
    std::cout << "playerHP: ";
    std::cin >> playerHP;
    std::cout << "damage: ";
    std::cin >> damage;
    std::cout << "heal: ";
    std::cin >> heal;

    int hpAfterHit = playerHP - damage;
    int hpAfterHeal = hpAfterHit + heal;

    std::cout << "HP start: " << playerHP << "\n";
    std::cout << "After hit: " << hpAfterHit << "\n";
    std::cout << "After heal: " << hpAfterHeal << "\n";
    return 0;
}
```

#### 4) Travel calculator (double)
```cpp
#include <iostream>

int main() {
    double speed, seconds;
    std::cout << "speed: ";
    std::cin >> speed;
    std::cout << "seconds: ";
    std::cin >> seconds;

    double distance = speed * seconds;
    std::cout << "You traveled " << distance << " units.\n";
    return 0;
}
```

#### 5) Potion recipe (/, %)
```cpp
#include <iostream>

int main() {
    int herbs, herbsPerPotion;
    std::cout << "herbs: ";
    std::cin >> herbs;
    std::cout << "herbsPerPotion: ";
    std::cin >> herbsPerPotion;

    int potions = herbs / herbsPerPotion;
    int leftoverHerbs = herbs % herbsPerPotion;

    std::cout << "potions: " << potions << "\n";
    std::cout << "leftoverHerbs: " << leftoverHerbs << "\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Observa si los prompts son claros y consistentes (esto es UX).
- Pide que expliquen el flujo: input → proceso → output.
- Puente: “Tu súper desafío va a necesitar decisiones del jugador. Hoy ya aprendiste a leer datos.”

---

# 4) Condicionales (if / else)

## Explicación (máx 5 párrafos)
Un condicional permite que el programa tome decisiones. `if` pregunta “¿se cumple esto?”; si sí, ejecuta un bloque. Con `else` tienes el plan B. Con `else if` encadenas varias decisiones.

En videojuegos, condicionales son reglas: “si HP <= 0 entonces GAME OVER”, “si coins >= price entonces compra”, “si level >= requirement entonces equipar”. Para principiantes, la disciplina es escribir condiciones simples y comprobar resultados con prints.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — ¿Tiene vida?
```cpp
#include <iostream>

int main() {
    int hp;
    std::cout << "HP: ";
    std::cin >> hp;

    if (hp > 0) std::cout << "Alive\n";
    else std::cout << "Game Over\n";

    return 0;
}
```

### Ejemplo 2 — Compra con validación
```cpp
#include <iostream>

int main() {
    int coins, price;
    std::cout << "Coins: ";
    std::cin >> coins;
    std::cout << "Price: ";
    std::cin >> price;

    if (coins >= price) std::cout << "Purchase OK\n";
    else std::cout << "Not enough coins\n";

    return 0;
}
```

### Ejemplo 3 — Rango de dificultad
```cpp
#include <iostream>

int main() {
    int difficulty;
    std::cout << "Difficulty (1-3): ";
    std::cin >> difficulty;

    if (difficulty == 1) std::cout << "Easy\n";
    else if (difficulty == 2) std::cout << "Normal\n";
    else if (difficulty == 3) std::cout << "Hard\n";
    else std::cout << "Invalid\n";

    return 0;
}
```

### Ejemplo 4 — Bonus por combo
```cpp
#include <iostream>

int main() {
    int combo;
    std::cout << "Combo: ";
    std::cin >> combo;

    int bonus = 0;
    if (combo >= 10) bonus = 30;
    else if (combo >= 5) bonus = 10;

    std::cout << "Bonus: " << bonus << "\n";
    return 0;
}
```

### Ejemplo 5 — Clamp simple (sin función)
```cpp
#include <iostream>

int main() {
    int hp;
    std::cout << "HP: ";
    std::cin >> hp;

    if (hp < 0) hp = 0;
    if (hp > 100) hp = 100;

    std::cout << "HP clamped: " << hp << "\n";
    return 0;
}
```

### Ejemplo 6 — Estado por monedas
```cpp
#include <iostream>

int main() {
    int coins;
    std::cout << "Coins: ";
    std::cin >> coins;

    if (coins == 0) std::cout << "Broke\n";
    else std::cout << "You have money\n";

    return 0;
}
```

---

## Desafíos resueltos (alumnos)
> Nota: usa los mismos desafíos del alumno del Tema 4 y muéstralos aquí resueltos (con soluciones equivalentes).

### En clase (≤5 min c/u)

#### 1) Is alive
```cpp
#include <iostream>

int main() {
    int playerHP;
    std::cout << "playerHP: ";
    std::cin >> playerHP;

    if (playerHP > 0) std::cout << "ALIVE\n";
    else std::cout << "GAME OVER\n";

    return 0;
}
```

#### 2) Can buy
```cpp
#include <iostream>

int main() {
    int coins, price;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "price: ";
    std::cin >> price;

    if (coins >= price) std::cout << "BUY\n";
    else std::cout << "NO BUY\n";

    return 0;
}
```

#### 3) Damage result (no negativos)
```cpp
#include <iostream>

int main() {
    int hp, damage;
    std::cout << "hp: ";
    std::cin >> hp;
    std::cout << "damage: ";
    std::cin >> damage;

    int hpAfter = hp - damage;
    if (hpAfter < 0) hpAfter = 0;

    std::cout << "hpAfter: " << hpAfter << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Shop with qty (validación)
```cpp
#include <iostream>

int main() {
    int coins, price, qty;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "price: ";
    std::cin >> price;
    std::cout << "qty: ";
    std::cin >> qty;

    int total = price * qty;
    if (coins >= total) std::cout << "PURCHASE OK\n";
    else std::cout << "NOT ENOUGH COINS\n";

    return 0;
}
```

#### 2) Level gate
```cpp
#include <iostream>

int main() {
    int playerLevel, requiredLevel;
    std::cout << "playerLevel: ";
    std::cin >> playerLevel;
    std::cout << "requiredLevel: ";
    std::cin >> requiredLevel;

    if (playerLevel >= requiredLevel) std::cout << "ACCESS GRANTED\n";
    else std::cout << "ACCESS DENIED\n";

    return 0;
}
```

#### 3) HP clamp 0..100
```cpp
#include <iostream>

int main() {
    int hp;
    std::cout << "hp: ";
    std::cin >> hp;

    if (hp < 0) hp = 0;
    if (hp > 100) hp = 100;

    std::cout << "hp: " << hp << "\n";
    return 0;
}
```

#### 4) Critical hit (1/0)
```cpp
#include <iostream>

int main() {
    int baseDamage, isCrit;
    std::cout << "baseDamage: ";
    std::cin >> baseDamage;
    std::cout << "isCrit (1/0): ";
    std::cin >> isCrit;

    int finalDamage = baseDamage;
    if (isCrit == 1) finalDamage = baseDamage * 2;

    std::cout << "finalDamage: " << finalDamage << "\n";
    return 0;
}
```

#### 5) Quest reward with bonus rule
```cpp
#include <iostream>

int main() {
    int coins, reward;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "reward: ";
    std::cin >> reward;

    int totalReward = reward;
    if (reward >= 50) totalReward += 10;

    int newCoins = coins + totalReward;
    std::cout << "newCoins: " << newCoins << "\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Haz que expliquen *por qué* la condición es correcta (no solo “porque sí”).
- Pide 2 casos de prueba por alumno: uno que entra al `if`, otro que cae al `else`.
- Puente: “Tu súper desafío necesitará reglas. Hoy aprendiste a escribir reglas ejecutables.”

---

# 5) Switch + menús

## Explicación (máx 5 párrafos)
`switch` es la herramienta de “menú” por excelencia cuando tus opciones son discretas (1,2,3… o letras). Es más limpio que muchos `else if` cuando hay muchas rutas.

En clase, exige dos hábitos: **(1)** siempre `break` por `case` (para evitar caídas accidentales) y **(2)** siempre `default` para opciones inválidas.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Menú de debug (1 paso)
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "1) Show stats\n2) Show map\n3) Quit\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "Stats...\n"; break;
        case 2: std::cout << "Map...\n"; break;
        case 3: std::cout << "Quit.\n"; break;
        default: std::cout << "Invalid.\n"; break;
    }
    return 0;
}
```

### Ejemplo 2 — Elegir “poción” por letra
```cpp
#include <iostream>

int main() {
    char p;
    std::cout << "Potion (h=heal, m=mana): ";
    std::cin >> p;

    switch (p) {
        case 'h': std::cout << "Heal potion\n"; break;
        case 'm': std::cout << "Mana potion\n"; break;
        default: std::cout << "Unknown\n"; break;
    }
    return 0;
}
```

### Ejemplo 3 — Tipo de enemigo (1-3)
```cpp
#include <iostream>

int main() {
    int type;
    std::cout << "Enemy type (1-3): ";
    std::cin >> type;

    switch (type) {
        case 1: std::cout << "Slime\n"; break;
        case 2: std::cout << "Goblin\n"; break;
        case 3: std::cout << "Knight\n"; break;
        default: std::cout << "???\n"; break;
    }
    return 0;
}
```

### Ejemplo 4 — Acción de inventario
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "1) Use potion\n2) Drop item\n3) Back\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "Used potion\n"; break;
        case 2: std::cout << "Dropped item\n"; break;
        case 3: std::cout << "Back\n"; break;
        default: std::cout << "Invalid\n"; break;
    }
    return 0;
}
```

### Ejemplo 5 — Ranking (A/B/C)
```cpp
#include <iostream>

int main() {
    char rank;
    std::cout << "Rank (A/B/C): ";
    std::cin >> rank;

    switch (rank) {
        case 'A': std::cout << "Excellent\n"; break;
        case 'B': std::cout << "Good\n"; break;
        case 'C': std::cout << "Ok\n"; break;
        default: std::cout << "Unknown\n"; break;
    }
    return 0;
}
```

### Ejemplo 6 — Shop (1 compra) por id
```cpp
#include <iostream>

int main() {
    int coins, option;
    std::cout << "Coins: ";
    std::cin >> coins;

    std::cout << "1) Potion(20)\n2) Key(50)\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1:
            if (coins >= 20) std::cout << "Bought potion\n";
            else std::cout << "Not enough\n";
            break;
        case 2:
            if (coins >= 50) std::cout << "Bought key\n";
            else std::cout << "Not enough\n";
            break;
        default:
            std::cout << "Invalid\n";
            break;
    }
    return 0;
}
```

---

## Desafíos resueltos (alumnos)
> Soluciones equivalentes a los desafíos del alumno del Tema 5.

### En clase (≤5 min c/u)

#### 1) Menu ping
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "1) Play\n2) Options\n3) Exit\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "PLAY\n"; break;
        case 2: std::cout << "OPTIONS\n"; break;
        case 3: std::cout << "EXIT\n"; break;
        default: std::cout << "INVALID\n"; break;
    }
    return 0;
}
```

#### 2) Difficulty switch
```cpp
#include <iostream>

int main() {
    int difficulty;
    std::cout << "difficulty (1-3): ";
    std::cin >> difficulty;

    switch (difficulty) {
        case 1: std::cout << "EASY\n"; break;
        case 2: std::cout << "NORMAL\n"; break;
        case 3: std::cout << "HARD\n"; break;
        default: std::cout << "UNKNOWN\n"; break;
    }
    return 0;
}
```

#### 3) Weapon select
```cpp
#include <iostream>

int main() {
    char weapon;
    std::cout << "weapon (s/b/m): ";
    std::cin >> weapon;

    switch (weapon) {
        case 's': std::cout << "SWORD\n"; break;
        case 'b': std::cout << "BOW\n"; break;
        case 'm': std::cout << "MAGIC\n"; break;
        default: std::cout << "UNKNOWN\n"; break;
    }
    return 0;
}
```

### En casa (más extensos)

#### 1) Shop (1 compra)
```cpp
#include <iostream>

int main() {
    int coins, option;
    std::cout << "coins: ";
    std::cin >> coins;

    std::cout << "1) Potion(20)\n2) Arrows(5)\n3) Key(50)\n4) Exit\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1:
            if (coins >= 20) std::cout << "Bought potion. Left: " << (coins - 20) << "\n";
            else std::cout << "Not enough coins\n";
            break;
        case 2:
            if (coins >= 5) std::cout << "Bought arrows. Left: " << (coins - 5) << "\n";
            else std::cout << "Not enough coins\n";
            break;
        case 3:
            if (coins >= 50) std::cout << "Bought key. Left: " << (coins - 50) << "\n";
            else std::cout << "Not enough coins\n";
            break;
        case 4:
            std::cout << "Exit\n";
            break;
        default:
            std::cout << "Invalid\n";
            break;
    }
    return 0;
}
```

#### 2) Options menu (texto)
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "1) Audio\n2) Video\n3) Controls\n4) Back\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "[AUDIO]\n"; break;
        case 2: std::cout << "[VIDEO]\n"; break;
        case 3: std::cout << "[CONTROLS]\n"; break;
        case 4: std::cout << "[BACK]\n"; break;
        default: std::cout << "Invalid\n"; break;
    }
    return 0;
}
```

#### 3) Attack type (x1/x2/x3)
```cpp
#include <iostream>

int main() {
    int attackType, baseDamage;
    std::cout << "attackType (1-3): ";
    std::cin >> attackType;
    std::cout << "baseDamage: ";
    std::cin >> baseDamage;

    int finalDamage = baseDamage;

    switch (attackType) {
        case 1: finalDamage = baseDamage * 1; break;
        case 2: finalDamage = baseDamage * 2; break;
        case 3: finalDamage = baseDamage * 3; break;
        default: finalDamage = baseDamage; break;
    }

    std::cout << "finalDamage: " << finalDamage << "\n";
    return 0;
}
```

#### 4) Game state report
```cpp
#include <iostream>

int main() {
    int gameState;
    std::cout << "gameState (0-3): ";
    std::cin >> gameState;

    switch (gameState) {
        case 0: std::cout << "TITLE\n"; break;
        case 1: std::cout << "PLAYING\n"; break;
        case 2: std::cout << "PAUSED\n"; break;
        case 3: std::cout << "GAME OVER\n"; break;
        default: std::cout << "UNKNOWN\n"; break;
    }
    return 0;
}
```

#### 5) Dialogue choice (1 paso)
```cpp
#include <iostream>

int main() {
    int option;
    std::cout << "NPC: Choose:\n1) Yes\n2) No\n3) Maybe\nChoose: ";
    std::cin >> option;

    switch (option) {
        case 1: std::cout << "NPC: Great.\n"; break;
        case 2: std::cout << "NPC: Sad.\n"; break;
        case 3: std::cout << "NPC: Hmmm.\n"; break;
        default: std::cout << "NPC: ...\n"; break;
    }
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Revisa: `default` presente y `break` en cada `case`.
- Pide que diseñen su menú del súper desafío (solo pantallas de texto por ahora).
- Puente: “Tu súper desafío empezará con un menú. Hoy ya sabes enrutar opciones.”

---

# 6) Ciclos (while)

## Explicación (máx 5 párrafos)
`while` repite mientras una condición sea verdadera. Es perfecto para menús que se repiten, conteos y simulaciones por turnos. El riesgo clásico: **ciclos infinitos** (la condición nunca cambia).

Didácticamente, pide dos cosas: (1) que identifiquen qué variable controla el ciclo y (2) que la actualicen en cada vuelta (contador, decremento, o cambio de opción).

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Loop de turnos fijo (contador)
```cpp
#include <iostream>

int main() {
    int turns = 3;
    int current = 1;

    while (current <= turns) {
        std::cout << "Turn " << current << "\n";
        current++;
    }
    return 0;
}
```

### Ejemplo 2 — Menú repetible (stats)
```cpp
#include <iostream>

int main() {
    int hp = 100;
    int option = 0;

    while (option != 3) {
        std::cout << "1) Take damage\n2) Show HP\n3) Exit\nChoose: ";
        std::cin >> option;

        if (option == 1) hp -= 10;
        else if (option == 2) std::cout << "HP: " << hp << "\n";
        else if (option == 3) std::cout << "Bye\n";
        else std::cout << "Invalid\n";
    }
    return 0;
}
```

### Ejemplo 3 — Acumulador (oro por turno)
```cpp
#include <iostream>

int main() {
    int turns = 5;
    int gold = 0;

    int i = 0;
    while (i < turns) {
        gold += 2;
        i++;
    }

    std::cout << "Gold: " << gold << "\n";
    return 0;
}
```

### Ejemplo 4 — Cooldown (decremento)
```cpp
#include <iostream>

int main() {
    int cd = 5;
    while (cd > 0) {
        std::cout << "CD: " << cd << "\n";
        cd--;
    }
    std::cout << "Ready\n";
    return 0;
}
```

### Ejemplo 5 — Repetir hasta alcanzar XP
```cpp
#include <iostream>

int main() {
    int xp = 0;
    int xp_to_level = 50;

    while (xp < xp_to_level) {
        xp += 10;
        std::cout << "XP: " << xp << "\n";
    }
    std::cout << "Level up!\n";
    return 0;
}
```

### Ejemplo 6 — “Respawn tokens”
```cpp
#include <iostream>

int main() {
    int tokens = 3;

    while (tokens > 0) {
        tokens--;
        std::cout << "Respawn. Tokens left: " << tokens << "\n";
    }
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Countdown
```cpp
#include <iostream>

int main() {
    int seconds;
    std::cout << "seconds: ";
    std::cin >> seconds;

    while (seconds >= 0) {
        std::cout << seconds << "\n";
        seconds--;
    }
    return 0;
}
```

#### 2) Coin loop
```cpp
#include <iostream>

int main() {
    int pickUps;
    std::cout << "pickUps: ";
    std::cin >> pickUps;

    int coins = 0;
    int i = 0;
    while (i < pickUps) {
        coins += 1;
        i++;
    }

    std::cout << "coins: " << coins << "\n";
    return 0;
}
```

#### 3) Menu repeat
```cpp
#include <iostream>

int main() {
    int coins = 0;
    int option = 0;

    while (option != 3) {
        std::cout << "1) +10 coins\n2) Show\n3) Exit\nChoose: ";
        std::cin >> option;

        if (option == 1) coins += 10;
        else if (option == 2) std::cout << "Coins: " << coins << "\n";
        else if (option == 3) std::cout << "Bye\n";
        else std::cout << "Invalid\n";
    }
    return 0;
}
```

### En casa (más extensos)

#### 1) Damage simulator
```cpp
#include <iostream>

int main() {
    int hits, damagePerHit;
    std::cout << "hits: ";
    std::cin >> hits;
    std::cout << "damagePerHit: ";
    std::cin >> damagePerHit;

    int totalDamage = 0;
    int i = 0;
    while (i < hits) {
        totalDamage += damagePerHit;
        i++;
    }

    std::cout << "totalDamage: " << totalDamage << "\n";
    return 0;
}
```

#### 2) Potion crafting loop
```cpp
#include <iostream>

int main() {
    int herbs, herbsPerPotion;
    std::cout << "herbs: ";
    std::cin >> herbs;
    std::cout << "herbsPerPotion: ";
    std::cin >> herbsPerPotion;

    int potions = 0;
    while (herbs >= herbsPerPotion) {
        herbs -= herbsPerPotion;
        potions++;
    }

    std::cout << "potions: " << potions << "\n";
    std::cout << "leftoverHerbs: " << herbs << "\n";
    return 0;
}
```

#### 3) Shop until exit (sin arrays)
```cpp
#include <iostream>

int main() {
    int coins;
    std::cout << "coins: ";
    std::cin >> coins;

    int option = 0;
    while (option != 4) {
        std::cout << "1) Potion(20)\n2) Arrows(5)\n3) Key(50)\n4) Exit\nChoose: ";
        std::cin >> option;

        if (option == 1 && coins >= 20) coins -= 20;
        else if (option == 2 && coins >= 5) coins -= 5;
        else if (option == 3 && coins >= 50) coins -= 50;
        else if (option == 4) std::cout << "Exit\n";
        else std::cout << "Not enough or invalid\n";

        std::cout << "Coins now: " << coins << "\n";
    }
    return 0;
}
```

#### 4) XP grind
```cpp
#include <iostream>

int main() {
    int xpToLevel, xpPerQuest;
    std::cout << "xpToLevel: ";
    std::cin >> xpToLevel;
    std::cout << "xpPerQuest: ";
    std::cin >> xpPerQuest;

    int xp = 0;
    int quests = 0;

    while (xp < xpToLevel) {
        xp += xpPerQuest;
        quests++;
    }

    std::cout << "quests: " << quests << "\n";
    std::cout << "xp: " << xp << "\n";
    return 0;
}
```

#### 5) Life drain
```cpp
#include <iostream>

int main() {
    int playerHP, drainPerTurn;
    std::cout << "playerHP: ";
    std::cin >> playerHP;
    std::cout << "drainPerTurn: ";
    std::cin >> drainPerTurn;

    while (playerHP > 0) {
        playerHP -= drainPerTurn;
        std::cout << "HP: " << playerHP << "\n";
    }

    std::cout << "GAME OVER\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Verifica que el loop tenga salida clara (condición que cambia).
- Haz que diseñen un “menú repetible” para su súper desafío (sin features extra).
- Puente: “Tu súper desafío vivirá en un loop. Hoy ya construiste el loop.”

---


# 7) Ciclos (for) + patrones comunes

## Explicación (máx 5 párrafos)
`for` es el ciclo ideal cuando conoces cuántas repeticiones necesitas. En videojuegos se usa para oleadas, combos, estadísticas y “hacer N veces”.

Enseña el patrón mental: **inicio → condición → avance**. Para principiantes, el error común es equivocarse con límites (`<` vs `<=`). Pide casos de prueba pequeños (N=1, N=2) para validar.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Spawn de 5 enemigos (texto)
```cpp
#include <iostream>

int main() {
    for (int i = 1; i <= 5; i++) {
        std::cout << "Spawn enemy #" << i << "\n";
    }
    return 0;
}
```

### Ejemplo 2 — Tabla de upgrades (1..3)
```cpp
#include <iostream>

int main() {
    int base = 10;
    for (int lvl = 1; lvl <= 3; lvl++) {
        std::cout << "Upgrade " << lvl << ": " << (base * lvl) << "\n";
    }
    return 0;
}
```

### Ejemplo 3 — Suma de loot de N cofres
```cpp
#include <iostream>

int main() {
    int chests;
    std::cout << "chests: ";
    std::cin >> chests;

    int total = 0;
    for (int i = 0; i < chests; i++) {
        int loot;
        std::cout << "loot: ";
        std::cin >> loot;
        total += loot;
    }
    std::cout << "total: " << total << "\n";
    return 0;
}
```

### Ejemplo 4 — Contar perfect blocks (1/0)
```cpp
#include <iostream>

int main() {
    int attempts;
    std::cout << "attempts: ";
    std::cin >> attempts;

    int perfect = 0;
    for (int i = 0; i < attempts; i++) {
        int ok;
        std::cout << "perfect? (1/0): ";
        std::cin >> ok;
        if (ok == 1) perfect++;
    }
    std::cout << "perfect: " << perfect << "\n";
    return 0;
}
```

### Ejemplo 5 — Promedio de 4 daños
```cpp
#include <iostream>

int main() {
    int sum = 0;
    for (int i = 1; i <= 4; i++) {
        int d;
        std::cout << "damage " << i << ": ";
        std::cin >> d;
        sum += d;
    }
    double avg = sum / 4.0;
    std::cout << "avg: " << avg << "\n";
    return 0;
}
```

### Ejemplo 6 — Mejor puntaje (N)
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "scores: ";
    std::cin >> n;

    int best = -999999;
    for (int i = 0; i < n; i++) {
        int s;
        std::cout << "score: ";
        std::cin >> s;
        if (s > best) best = s;
    }
    std::cout << "best: " << best << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Combo table (1..5)
```cpp
#include <iostream>

int main() {
    int baseDamage;
    std::cout << "baseDamage: ";
    std::cin >> baseDamage;

    for (int combo = 1; combo <= 5; combo++) {
        std::cout << "Combo " << combo << ": " << (baseDamage * combo) << "\n";
    }
    return 0;
}
```

#### 2) Sum coins
```cpp
#include <iostream>

int main() {
    int rooms;
    std::cout << "rooms: ";
    std::cin >> rooms;

    int coins = 0;
    for (int i = 0; i < rooms; i++) {
        coins += 10;
    }
    std::cout << "coins: " << coins << "\n";
    return 0;
}
```

#### 3) Count crits (1/0)
```cpp
#include <iostream>

int main() {
    int attacks;
    std::cout << "attacks: ";
    std::cin >> attacks;

    int critCount = 0;
    for (int i = 0; i < attacks; i++) {
        int isCrit;
        std::cout << "isCrit (1/0): ";
        std::cin >> isCrit;
        if (isCrit == 1) critCount++;
    }
    std::cout << "critCount: " << critCount << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Average damage
```cpp
#include <iostream>

int main() {
    int hits;
    std::cout << "hits: ";
    std::cin >> hits;

    int sum = 0;
    for (int i = 1; i <= hits; i++) {
        int damage;
        std::cout << "damage " << i << ": ";
        std::cin >> damage;
        sum += damage;
    }

    double avg = sum / (double)hits;
    std::cout << "avg: " << avg << "\n";
    return 0;
}
```

#### 2) Best run (max)
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "runs: ";
    std::cin >> n;

    int best = -999999;
    for (int i = 0; i < n; i++) {
        int score;
        std::cout << "score: ";
        std::cin >> score;
        if (score > best) best = score;
    }

    std::cout << "best: " << best << "\n";
    return 0;
}
```

#### 3) XP ladder (imprime XP tras cada quest)
```cpp
#include <iostream>

int main() {
    int quests, xpPerQuest;
    std::cout << "quests: ";
    std::cin >> quests;
    std::cout << "xpPerQuest: ";
    std::cin >> xpPerQuest;

    int xp = 0;
    for (int i = 1; i <= quests; i++) {
        xp += xpPerQuest;
        std::cout << "After quest " << i << ": XP=" << xp << "\n";
    }
    return 0;
}
```

#### 4) Wave spawner
```cpp
#include <iostream>

int main() {
    int waves;
    std::cout << "waves: ";
    std::cin >> waves;

    for (int w = 1; w <= waves; w++) {
        std::cout << "Wave " << w << " incoming!\n";
    }
    return 0;
}
```

#### 5) Min/Max de N valores
```cpp
#include <iostream>

int main() {
    int n;
    std::cout << "n: ";
    std::cin >> n;

    int minV = 999999;
    int maxV = -999999;

    for (int i = 0; i < n; i++) {
        int v;
        std::cout << "value: ";
        std::cin >> v;
        if (v < minV) minV = v;
        if (v > maxV) maxV = v;
    }

    std::cout << "min: " << minV << "\n";
    std::cout << "max: " << maxV << "\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Revisa límites: ¿empieza en 0 o 1?, ¿usa `<` o `<=`?
- Mini-puente: “Tu súper desafío tendrá loops para stats, inventario o quests.”
- Pide 2 pruebas: N=1 y N=5.

---

# 8) Funciones (bases)

## Explicación (máx 5 párrafos)
Una función encapsula una tarea con nombre (ej. `calculate_damage`). Reduce duplicación y mejora legibilidad. Para principiantes, lo importante es el triángulo: **parámetros → lógica → return**.

En videojuegos, funciones son “reglas reutilizables”: daño, curación, compras, clamp. Este tema se enfoca en funciones pequeñas, sin structs todavía.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — add_xp
```cpp
#include <iostream>

int add_xp(int current_xp, int reward_xp) {
    return current_xp + reward_xp;
}

int main() {
    std::cout << add_xp(10, 25) << "\n";
    return 0;
}
```

### Ejemplo 2 — is_dead
```cpp
#include <iostream>

bool is_dead(int hp) {
    return hp <= 0;
}

int main() {
    std::cout << (is_dead(0) ? "DEAD\n" : "ALIVE\n");
    return 0;
}
```

### Ejemplo 3 — apply_discount
```cpp
#include <iostream>

int apply_discount(int price, int percent) {
    return price - (price * percent / 100);
}

int main() {
    std::cout << apply_discount(100, 20) << "\n";
    return 0;
}
```

### Ejemplo 4 — clamp (int)
```cpp
#include <iostream>

int clamp_int(int v, int min_v, int max_v) {
    if (v < min_v) return min_v;
    if (v > max_v) return max_v;
    return v;
}

int main() {
    std::cout << clamp_int(140, 0, 100) << "\n";
    return 0;
}
```

### Ejemplo 5 — can_level_up
```cpp
#include <iostream>

bool can_level_up(int xp, int xp_to_level) {
    return xp >= xp_to_level;
}

int main() {
    std::cout << (can_level_up(120, 100) ? "LEVEL UP\n" : "KEEP GRINDING\n");
    return 0;
}
```

### Ejemplo 6 — print_title (void)
```cpp
#include <iostream>

void print_title() {
    std::cout << "=== CONSOLE QUEST ===\n";
}

int main() {
    print_title();
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) calculateDamage
```cpp
#include <iostream>

int calculateDamage(int baseDamage, int bonus) {
    return baseDamage + bonus;
}

int main() {
    std::cout << calculateDamage(30, 12) << "\n";
    return 0;
}
```

#### 2) clampInt
```cpp
#include <iostream>

int clampInt(int value, int minV, int maxV) {
    if (value < minV) return minV;
    if (value > maxV) return maxV;
    return value;
}

int main() {
    std::cout << clampInt(140, 0, 100) << "\n";
    return 0;
}
```

#### 3) canBuy
```cpp
#include <iostream>

bool canBuy(int coins, int price) {
    return coins >= price;
}

int main() {
    std::cout << (canBuy(50, 20) ? "BUY\n" : "NO BUY\n");
    return 0;
}
```

### En casa (más extensos)

#### 1) applyHeal (clamp a 100)
```cpp
#include <iostream>

int clampInt(int value, int minV, int maxV) {
    if (value < minV) return minV;
    if (value > maxV) return maxV;
    return value;
}

int applyHeal(int hp, int heal) {
    return clampInt(hp + heal, 0, 100);
}

int main() {
    std::cout << applyHeal(90, 25) << "\n";
    return 0;
}
```

#### 2) xpAfterQuests
```cpp
#include <iostream>

int xpAfterQuests(int currentXP, int quests, int xpPerQuest) {
    return currentXP + quests * xpPerQuest;
}

int main() {
    std::cout << xpAfterQuests(10, 3, 20) << "\n";
    return 0;
}
```

#### 3) attackReport (crit x2)
```cpp
#include <iostream>

int finalDamage(int baseDamage, int isCrit) {
    if (isCrit == 1) return baseDamage * 2;
    return baseDamage;
}

int main() {
    std::cout << finalDamage(15, 1) << "\n";
    return 0;
}
```

#### 4) menuAction (switch)
```cpp
#include <iostream>

void menuAction(int option) {
    switch (option) {
        case 1: std::cout << "PLAY\n"; break;
        case 2: std::cout << "OPTIONS\n"; break;
        case 3: std::cout << "EXIT\n"; break;
        default: std::cout << "INVALID\n"; break;
    }
}

int main() {
    int option;
    std::cin >> option;
    menuAction(option);
    return 0;
}
```

#### 5) cooldownTicks (imprime hasta 0)
```cpp
#include <iostream>

void cooldownTicks(int seconds) {
    while (seconds >= 0) {
        std::cout << seconds << "\n";
        seconds--;
    }
}

int main() {
    cooldownTicks(5);
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Pide que renombren funciones para que “se lean” (verbo + objeto).
- Exige 2 pruebas por función (caso normal y borde).
- Puente: “Tu súper desafío crecerá; funciones evitarán duplicación.”

---

# 9) Arreglos (arrays) 1D

## Explicación (máx 5 párrafos)
Un array es una lista fija de elementos del mismo tipo, indexados desde 0. Sirve para datos con tamaño conocido (por ejemplo 5 highscores).

Didácticamente: martilla “índice válido”. El bug #1 es salirse del rango. Aquí se usan ciclos para llenar, imprimir y calcular min/max/promedio.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — 3 vidas
```cpp
#include <iostream>

int main() {
    int lives[3] = { 3, 2, 1 };
    std::cout << lives[0] << "\n";
    return 0;
}
```

### Ejemplo 2 — Llenar 5 scores y sumarlos
```cpp
#include <iostream>

int main() {
    int scores[5];
    int sum = 0;

    for (int i = 0; i < 5; i++) {
        std::cout << "score: ";
        std::cin >> scores[i];
        sum += scores[i];
    }

    std::cout << "sum: " << sum << "\n";
    return 0;
}
```

### Ejemplo 3 — Contar items “raros” (>= 50)
```cpp
#include <iostream>

int main() {
    int loot[6] = { 10, 55, 2, 80, 50, 1 };
    int rare = 0;

    for (int i = 0; i < 6; i++) {
        if (loot[i] >= 50) rare++;
    }

    std::cout << "rare: " << rare << "\n";
    return 0;
}
```

### Ejemplo 4 — Min/Max de 4 daños
```cpp
#include <iostream>

int main() {
    int d[4] = { 12, 7, 30, 18 };
    int minV = d[0];
    int maxV = d[0];

    for (int i = 1; i < 4; i++) {
        if (d[i] < minV) minV = d[i];
        if (d[i] > maxV) maxV = d[i];
    }

    std::cout << "min=" << minV << " max=" << maxV << "\n";
    return 0;
}
```

### Ejemplo 5 — Buscar score exacto
```cpp
#include <iostream>

int main() {
    int scores[5] = { 10, 20, 30, 40, 50 };
    int target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < 5; i++) {
        if (scores[i] == target) found = true;
    }

    std::cout << (found ? "FOUND\n" : "NOT FOUND\n");
    return 0;
}
```

### Ejemplo 6 — Intercambiar extremos
```cpp
#include <iostream>

int main() {
    int v[5] = { 1, 2, 3, 4, 5 };
    int tmp = v[0];
    v[0] = v[4];
    v[4] = tmp;

    for (int i = 0; i < 5; i++) std::cout << v[i] << " ";
    std::cout << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) 3 scores avg
```cpp
#include <iostream>

int main() {
    int scores[3];
    int sum = 0;

    for (int i = 0; i < 3; i++) {
        std::cout << "score: ";
        std::cin >> scores[i];
        sum += scores[i];
    }

    double avg = sum / 3.0;
    std::cout << "avg: " << avg << "\n";
    return 0;
}
```

#### 2) Max of 5
```cpp
#include <iostream>

int main() {
    int d[5];
    for (int i = 0; i < 5; i++) {
        std::cout << "damage: ";
        std::cin >> d[i];
    }

    int maxV = d[0];
    for (int i = 1; i < 5; i++) {
        if (d[i] > maxV) maxV = d[i];
    }

    std::cout << "max: " << maxV << "\n";
    return 0;
}
```

#### 3) Find item (id)
```cpp
#include <iostream>

int main() {
    int ids[4] = { 10, 22, 35, 41 };
    int target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < 4; i++) {
        if (ids[i] == target) found = true;
    }

    std::cout << (found ? "FOUND\n" : "NOT FOUND\n");
    return 0;
}
```

### En casa (más extensos)

#### 1) Room coins (10 valores)
```cpp
#include <iostream>

int main() {
    int coins[10];
    int total = 0;

    for (int i = 0; i < 10; i++) {
        std::cout << "coins in room: ";
        std::cin >> coins[i];
        total += coins[i];
    }

    std::cout << "total: " << total << "\n";
    return 0;
}
```

#### 2) Damage stats (min/max/avg de 8)
```cpp
#include <iostream>

int main() {
    int d[8];
    int sum = 0;

    for (int i = 0; i < 8; i++) {
        std::cout << "damage: ";
        std::cin >> d[i];
        sum += d[i];
    }

    int minV = d[0];
    int maxV = d[0];

    for (int i = 1; i < 8; i++) {
        if (d[i] < minV) minV = d[i];
        if (d[i] > maxV) maxV = d[i];
    }

    double avg = sum / 8.0;

    std::cout << "min: " << minV << "\n";
    std::cout << "max: " << maxV << "\n";
    std::cout << "avg: " << avg << "\n";
    return 0;
}
```

#### 3) Inventory fixed (5 strings)
```cpp
#include <iostream>
#include <string>

int main() {
    std::string inventory[5] = { "Potion", "Key", "Gem", "Map", "Bread" };

    for (int i = 0; i < 5; i++) {
        std::cout << (i + 1) << ") " << inventory[i] << "\n";
    }
    return 0;
}
```

#### 4) Count rares (>=50) en 12 loot
```cpp
#include <iostream>

int main() {
    int loot[12];
    for (int i = 0; i < 12; i++) {
        std::cout << "loot value: ";
        std::cin >> loot[i];
    }

    int rare = 0;
    for (int i = 0; i < 12; i++) {
        if (loot[i] >= 50) rare++;
    }

    std::cout << "rare: " << rare << "\n";
    return 0;
}
```

#### 5) Swap positions (0<->4, 1<->3) en 5
```cpp
#include <iostream>

int main() {
    int v[5];
    for (int i = 0; i < 5; i++) {
        std::cout << "v[" << i << "]: ";
        std::cin >> v[i];
    }

    int tmp = v[0]; v[0] = v[4]; v[4] = tmp;
    tmp = v[1]; v[1] = v[3]; v[3] = tmp;

    for (int i = 0; i < 5; i++) std::cout << v[i] << " ";
    std::cout << "\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Revisa índices: siempre 0..size-1.
- Puente: “Tu súper desafío puede necesitar highscores o inventario fijo.”
- Haz que justifiquen el tamaño del array.

---

# 10) Vectores (std::vector)

## Explicación (máx 5 párrafos)
Un `std::vector` es una lista que puede crecer. Es ideal cuando no sabes cuántos elementos habrá (inventario variable, quests, scores).

Didácticamente: enseña `push_back`, `size()` y recorrido. Evita mezclar métodos avanzados (erase/iterators) hasta que dominen lo básico.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Agregar 2 quests
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> quests;
    quests.push_back("Find key");
    quests.push_back("Reach exit");

    std::cout << "quests: " << quests.size() << "\n";
    return 0;
}
```

### Ejemplo 2 — Listar inventario
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Gem" };

    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << (i + 1) << ") " << inventory[i] << "\n";
    }
    return 0;
}
```

### Ejemplo 3 — Leer N coins (vector<int>)
```cpp
#include <iostream>
#include <vector>

int main() {
    int n;
    std::cout << "n: ";
    std::cin >> n;

    std::vector<int> coins;
    for (int i = 0; i < n; i++) {
        int c;
        std::cout << "coin: ";
        std::cin >> c;
        coins.push_back(c);
    }

    std::cout << "saved: " << coins.size() << "\n";
    return 0;
}
```

### Ejemplo 4 — Total coins
```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> coins = { 5, 10, 3 };
    int total = 0;

    for (int i = 0; i < (int)coins.size(); i++) total += coins[i];
    std::cout << "total: " << total << "\n";
    return 0;
}
```

### Ejemplo 5 — Buscar por nombre
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv = { "Potion", "Key", "Gem" };
    std::string target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inv.size(); i++) {
        if (inv[i] == target) found = true;
    }

    std::cout << (found ? "FOUND\n" : "NOT FOUND\n");
    return 0;
}
```

### Ejemplo 6 — pop_back (remover último)
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv = { "Potion", "Key", "Gem" };
    inv.pop_back();

    for (int i = 0; i < (int)inv.size(); i++) std::cout << inv[i] << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Add 3 items
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory;
    inventory.push_back("Potion");
    inventory.push_back("Key");
    inventory.push_back("Gem");

    std::cout << "size: " << inventory.size() << "\n";
    return 0;
}
```

#### 2) Print list
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inventory = { "Potion", "Key", "Gem" };
    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << i << ") " << inventory[i] << "\n";
    }
    return 0;
}
```

#### 3) Sum vector
```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> values = { 1, 2, 3, 4, 5 };
    int total = 0;
    for (int i = 0; i < (int)values.size(); i++) total += values[i];
    std::cout << "total: " << total << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Dynamic inventory (leer N)
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    int n;
    std::cout << "n: ";
    std::cin >> n;

    std::vector<std::string> inventory;
    for (int i = 0; i < n; i++) {
        std::string item;
        std::cout << "item: ";
        std::cin >> item;
        inventory.push_back(item);
    }

    for (int i = 0; i < (int)inventory.size(); i++) {
        std::cout << (i + 1) << ") " << inventory[i] << "\n";
    }
    return 0;
}
```

#### 2) High score (max)
```cpp
#include <iostream>
#include <vector>

int main() {
    int n;
    std::cout << "n: ";
    std::cin >> n;

    std::vector<int> scores;
    for (int i = 0; i < n; i++) {
        int s;
        std::cout << "score: ";
        std::cin >> s;
        scores.push_back(s);
    }

    int best = scores[0];
    for (int i = 1; i < (int)scores.size(); i++) {
        if (scores[i] > best) best = scores[i];
    }

    std::cout << "best: " << best << "\n";
    return 0;
}
```

#### 3) Search
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv = { "Potion", "Key", "Gem" };
    std::string target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inv.size(); i++) {
        if (inv[i] == target) found = true;
    }

    std::cout << (found ? "FOUND\n" : "NOT FOUND\n");
    return 0;
}
```

#### 4) Remove last (agrega 5, elimina 2)
```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv;
    inv.push_back("A");
    inv.push_back("B");
    inv.push_back("C");
    inv.push_back("D");
    inv.push_back("E");

    inv.pop_back();
    inv.pop_back();

    for (int i = 0; i < (int)inv.size(); i++) std::cout << inv[i] << "\n";
    return 0;
}
```

#### 5) Sentinel coins (hasta -1)
```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> coins;
    int value;

    while (true) {
        std::cout << "coin (-1 to stop): ";
        std::cin >> value;
        if (value == -1) break;
        coins.push_back(value);
    }

    int total = 0;
    for (int i = 0; i < (int)coins.size(); i++) total += coins[i];

    std::cout << "total: " << total << "\n";
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Pide que expliquen diferencia array vs vector (tamaño fijo vs dinámico).
- Puente: “Tu súper desafío puede tener inventario variable con vector.”
- Revisa: siempre usar `(int)vec.size()` en comparaciones.

---

# 11) Strings (más a fondo)

## Explicación (máx 5 párrafos)
Strings permiten manejar texto: comandos (“attack”), diálogos, nombres y parsing simple. El salto grande es `getline` (líneas completas) y operaciones como `length`, `find`, `substr`.

Evita enseñar regex o parsing complejo. Aquí la meta es que puedan construir y detectar comandos con herramientas básicas.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Contar letras
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cout << "name: ";
    std::cin >> name;

    std::cout << "length: " << name.length() << "\n";
    return 0;
}
```

### Ejemplo 2 — Construir mensaje HUD
```cpp
#include <iostream>
#include <string>

int main() {
    std::string player = "Player";
    int hp = 80;

    std::string hud = "Player: " + player + " | HP: " + std::to_string(hp);
    std::cout << hud << "\n";
    return 0;
}
```

### Ejemplo 3 — Detectar palabra clave
```cpp
#include <iostream>
#include <string>

int main() {
    std::string line;
    std::cout << "line: ";
    std::getline(std::cin >> std::ws, line);

    if (line.find("key") != std::string::npos) std::cout << "KEYWORD FOUND\n";
    else std::cout << "NO KEYWORD\n";

    return 0;
}
```

### Ejemplo 4 — Extraer prefijo antes de '_'
```cpp
#include <iostream>
#include <string>

int main() {
    std::string item = "Potion_Healing";
    size_t pos = item.find('_');

    std::string left = item.substr(0, pos);
    std::cout << left << "\n";
    return 0;
}
```

### Ejemplo 5 — Comandos exactos
```cpp
#include <iostream>
#include <string>

int main() {
    std::string cmd;
    std::cout << "cmd: ";
    std::cin >> cmd;

    if (cmd == "attack") std::cout << "ATTACK\n";
    else if (cmd == "heal") std::cout << "HEAL\n";
    else std::cout << "UNKNOWN\n";

    return 0;
}
```

### Ejemplo 6 — Leer “frase” de diálogo
```cpp
#include <iostream>
#include <string>

int main() {
    std::string dialog;
    std::cout << "dialog: ";
    std::getline(std::cin >> std::ws, dialog);

    std::cout << "NPC: " << dialog << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Name length
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cout << "name: ";
    std::cin >> name;

    std::cout << name.length() << "\n";
    return 0;
}
```

#### 2) Concat HUD
```cpp
#include <iostream>
#include <string>

int main() {
    std::string name;
    int coins;

    std::cout << "name: ";
    std::cin >> name;
    std::cout << "coins: ";
    std::cin >> coins;

    std::string hud = "Player " + name + " | Coins: " + std::to_string(coins);
    std::cout << hud << "\n";
    return 0;
}
```

#### 3) Command compare
```cpp
#include <iostream>
#include <string>

int main() {
    std::string cmd;
    std::cout << "cmd: ";
    std::cin >> cmd;

    if (cmd == "attack") std::cout << "ATTACK\n";
    else if (cmd == "heal") std::cout << "HEAL\n";
    else std::cout << "UNKNOWN\n";

    return 0;
}
```

### En casa (más extensos)

#### 1) Nickname (getline, primeros 3 chars)
```cpp
#include <iostream>
#include <string>

int main() {
    std::string fullName;
    std::cout << "fullName: ";
    std::getline(std::cin >> std::ws, fullName);

    std::string nick = fullName.substr(0, 3);
    std::cout << "nickname: " << nick << "\n";
    return 0;
}
```

#### 2) Item parsing (antes/después de '_')
```cpp
#include <iostream>
#include <string>

int main() {
    std::string item;
    std::cout << "item (Name_Type): ";
    std::cin >> item;

    size_t pos = item.find('_');
    std::string name = item.substr(0, pos);
    std::string type = item.substr(pos + 1);

    std::cout << "name: " << name << "\n";
    std::cout << "type: " << type << "\n";
    return 0;
}
```

#### 3) Dialog builder (3 líneas)
```cpp
#include <iostream>
#include <string>

int main() {
    std::string a, b, c;
    std::cout << "line1: ";
    std::getline(std::cin >> std::ws, a);
    std::cout << "line2: ";
    std::getline(std::cin, b);
    std::cout << "line3: ";
    std::getline(std::cin, c);

    std::cout << "NPC: " << a << "\n";
    std::cout << "NPC: " << b << "\n";
    std::cout << "NPC: " << c << "\n";
    return 0;
}
```

#### 4) Search keyword
```cpp
#include <iostream>
#include <string>

int main() {
    std::string phrase;
    std::string word;

    std::cout << "phrase: ";
    std::getline(std::cin >> std::ws, phrase);
    std::cout << "word: ";
    std::cin >> word;

    bool found = (phrase.find(word) != std::string::npos);
    std::cout << (found ? "FOUND\n" : "NOT FOUND\n");
    return 0;
}
```

#### 5) Command menu (if/else)
```cpp
#include <iostream>
#include <string>

int main() {
    std::string cmd;
    std::cout << "cmd (attack/heal/stats): ";
    std::cin >> cmd;

    if (cmd == "attack") std::cout << "You swing your weapon.\n";
    else if (cmd == "heal") std::cout << "You drink a potion.\n";
    else if (cmd == "stats") std::cout << "HP=80 COINS=10\n";
    else std::cout << "Unknown command.\n";

    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Revisa: usan `getline` correctamente cuando hay espacios.
- Puente: “El súper desafío puede usar comandos: attack/heal/shop/save.”
- Pide que diseñen 3 comandos y su output.

---

# 12) Estructuras (struct)

## Explicación (máx 5 párrafos)
Un `struct` agrupa datos relacionados (ej. un jugador con nombre, HP, coins). Esto reduce variables sueltas y hace que el código se parezca más a cómo piensas el juego: entidades con atributos.

Aquí la meta es: declarar `struct`, crear instancias, leer campos y usar `vector<Struct>` para listas simples.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Enemy
```cpp
#include <iostream>
#include <string>

struct Enemy {
    std::string name;
    int hp;
    int damage;
};

int main() {
    Enemy e{ "Slime", 20, 5 };
    std::cout << e.name << " " << e.hp << " " << e.damage << "\n";
    return 0;
}
```

### Ejemplo 2 — Leer Enemy
```cpp
#include <iostream>
#include <string>

struct Enemy {
    std::string name;
    int hp;
    int damage;
};

int main() {
    Enemy e;
    std::cout << "name: ";
    std::cin >> e.name;
    std::cout << "hp: ";
    std::cin >> e.hp;
    std::cout << "damage: ";
    std::cin >> e.damage;

    std::cout << e.name << "\n";
    return 0;
}
```

### Ejemplo 3 — Item con rarity
```cpp
#include <iostream>
#include <string>

struct Item {
    std::string name;
    int price;
    int rarity; // 1-5
};

int main() {
    Item it{ "Gem", 200, 4 };
    std::cout << it.name << " " << it.rarity << "\n";
    return 0;
}
```

### Ejemplo 4 — Vector de players
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    std::vector<Player> party = { {"A",100,10}, {"B",80,30} };
    for (int i = 0; i < (int)party.size(); i++) {
        std::cout << party[i].name << " HP=" << party[i].hp << "\n";
    }
    return 0;
}
```

### Ejemplo 5 — Sumar coins de party
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    std::vector<Player> party = { {"A",100,10}, {"B",80,30} };
    int total = 0;
    for (int i = 0; i < (int)party.size(); i++) total += party[i].coins;
    std::cout << "totalCoins: " << total << "\n";
    return 0;
}
```

### Ejemplo 6 — Buscar item por nombre
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inv = { {"Potion",20}, {"Key",50} };
    std::string target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inv.size(); i++) {
        if (inv[i].name == target) {
            found = true;
            std::cout << inv[i].price << "\n";
        }
    }
    if (!found) std::cout << "Not found\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Player struct
```cpp
#include <iostream>
#include <string>

struct Player {
    std::string name;
    int hp;
    int coins;
};

int main() {
    Player p{ "Player", 80, 10 };
    std::cout << p.name << " " << p.hp << " " << p.coins << "\n";
    return 0;
}
```

#### 2) Item struct
```cpp
#include <iostream>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    Item it{ "Potion", 20 };
    std::cout << it.name << " " << it.price << "\n";
    return 0;
}
```

#### 3) Update hp/coins
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
    p.hp += 10;
    p.coins += 25;

    std::cout << p.hp << " " << p.coins << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Inventory list (leer 5 Items a vector)
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inv;

    for (int i = 0; i < 5; i++) {
        Item it;
        std::cout << "name: ";
        std::cin >> it.name;
        std::cout << "price: ";
        std::cin >> it.price;
        inv.push_back(it);
    }

    for (int i = 0; i < (int)inv.size(); i++) {
        std::cout << inv[i].name << " (" << inv[i].price << ")\n";
    }
    return 0;
}
```

#### 2) Search item
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inv = { {"Potion",20}, {"Key",50}, {"Gem",200} };
    std::string target;
    std::cout << "target: ";
    std::cin >> target;

    bool found = false;
    for (int i = 0; i < (int)inv.size(); i++) {
        if (inv[i].name == target) {
            found = true;
            std::cout << "price: " << inv[i].price << "\n";
        }
    }
    if (!found) std::cout << "Not found\n";
    return 0;
}
```

#### 3) Total cost (suma precios)
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> cart = { {"Potion",20}, {"Key",50} };
    int total = 0;

    for (int i = 0; i < (int)cart.size(); i++) total += cart[i].price;
    std::cout << "total: " << total << "\n";
    return 0;
}
```

#### 4) Enemy struct preview
```cpp
#include <iostream>
#include <string>

struct Enemy {
    std::string name;
    int hp;
    int damage;
};

int main() {
    Enemy e;
    std::cout << "name: ";
    std::cin >> e.name;
    std::cout << "hp: ";
    std::cin >> e.hp;
    std::cout << "damage: ";
    std::cin >> e.damage;

    std::cout << "Enemy: " << e.name << " HP=" << e.hp << " DMG=" << e.damage << "\n";
    return 0;
}
```

#### 5) Loot filter (price >= 50)
```cpp
#include <iostream>
#include <vector>
#include <string>

struct Item {
    std::string name;
    int price;
};

int main() {
    std::vector<Item> inv = { {"Potion",20}, {"Key",50}, {"Gem",200} };

    for (int i = 0; i < (int)inv.size(); i++) {
        if (inv[i].price >= 50) std::cout << inv[i].name << "\n";
    }
    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Pide que identifiquen “entidades” del súper desafío y las modelen como structs.
- Puente: “Un súper desafío se vuelve más limpio cuando tus datos están agrupados.”
- Revisa que usen nombres de campos en inglés.

---

# 13) Archivos (persistencia básica)

## Explicación (máx 5 párrafos)
Guardar y cargar archivos es persistencia: “save game”. En C++: `ofstream` para escribir y `ifstream` para leer. Empieza con formatos simples (1 valor por línea) para evitar parsing complejo.

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Guardar score
```cpp
#include <fstream>

int main() {
    int score = 123;
    std::ofstream out("score.txt");
    out << score << "\n";
    return 0;
}
```

### Ejemplo 2 — Cargar score
```cpp
#include <fstream>
#include <iostream>

int main() {
    int score = 0;
    std::ifstream in("score.txt");
    in >> score;

    std::cout << "score=" << score << "\n";
    return 0;
}
```

### Ejemplo 3 — Guardar HP/coins
```cpp
#include <fstream>

int main() {
    int hp = 80;
    int coins = 25;

    std::ofstream out("save.txt");
    out << hp << "\n" << coins << "\n";
    return 0;
}
```

### Ejemplo 4 — Cargar HP/coins
```cpp
#include <fstream>
#include <iostream>

int main() {
    int hp = 0;
    int coins = 0;

    std::ifstream in("save.txt");
    in >> hp >> coins;

    std::cout << hp << " " << coins << "\n";
    return 0;
}
```

### Ejemplo 5 — Guardar lista (N + items)
```cpp
#include <fstream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv = { "Potion", "Key" };

    std::ofstream out("inv.txt");
    out << inv.size() << "\n";
    for (int i = 0; i < (int)inv.size(); i++) out << inv[i] << "\n";

    return 0;
}
```

### Ejemplo 6 — Cargar lista (N + items)
```cpp
#include <fstream>
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::ifstream in("inv.txt");
    int n;
    in >> n;

    std::vector<std::string> inv;
    for (int i = 0; i < n; i++) {
        std::string item;
        in >> item;
        inv.push_back(item);
    }

    std::cout << inv.size() << "\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Write save (name/hp/coins 1 por línea)
```cpp
#include <fstream>
#include <string>

int main() {
    std::string name = "Player";
    int hp = 80;
    int coins = 120;

    std::ofstream out("save.txt");
    out << name << "\n" << hp << "\n" << coins << "\n";
    return 0;
}
```

#### 2) Read save
```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::ifstream in("save.txt");
    std::string name;
    int hp, coins;

    std::getline(in, name);
    in >> hp >> coins;

    std::cout << name << " " << hp << " " << coins << "\n";
    return 0;
}
```

#### 3) Write inventory (3 items)
```cpp
#include <fstream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> inv = { "Potion", "Key", "Gem" };
    std::ofstream out("inventory.txt");

    out << inv.size() << "\n";
    for (int i = 0; i < (int)inv.size(); i++) out << inv[i] << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Save/Load player (menú)
```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::string name = "Player";
    int hp = 100;
    int coins = 0;

    int option;
    std::cout << "1) Save\n2) Load\nChoose: ";
    std::cin >> option;

    if (option == 1) {
        std::ofstream out("save.txt");
        out << name << "\n" << hp << "\n" << coins << "\n";
        std::cout << "Saved\n";
    } else if (option == 2) {
        std::ifstream in("save.txt");
        std::getline(in, name);
        in >> hp >> coins;
        std::cout << "Loaded: " << name << " " << hp << " " << coins << "\n";
    } else {
        std::cout << "Invalid\n";
    }

    return 0;
}
```

#### 2) Inventory save/load (leer N, guardar, cargar, mostrar)
```cpp
#include <fstream>
#include <iostream>
#include <vector>
#include <string>

int main() {
    int n;
    std::cout << "n: ";
    std::cin >> n;

    std::vector<std::string> inv;
    for (int i = 0; i < n; i++) {
        std::string item;
        std::cout << "item: ";
        std::cin >> item;
        inv.push_back(item);
    }

    {   // save
        std::ofstream out("inv.txt");
        out << inv.size() << "\n";
        for (int i = 0; i < (int)inv.size(); i++) out << inv[i] << "\n";
    }

    // load
    std::ifstream in("inv.txt");
    int m;
    in >> m;

    std::vector<std::string> loaded;
    for (int i = 0; i < m; i++) {
        std::string item;
        in >> item;
        loaded.push_back(item);
    }

    for (int i = 0; i < (int)loaded.size(); i++) std::cout << loaded[i] << "\n";
    return 0;
}
```

#### 3) Highscores file (5 scores, cargar y máximo)
```cpp
#include <fstream>
#include <iostream>

int main() {
    int scores[5];

    for (int i = 0; i < 5; i++) {
        std::cout << "score: ";
        std::cin >> scores[i];
    }

    {   // save
        std::ofstream out("highscores.txt");
        for (int i = 0; i < 5; i++) out << scores[i] << "\n";
    }

    // load and max
    std::ifstream in("highscores.txt");
    int best = -999999;
    for (int i = 0; i < 5; i++) {
        int s;
        in >> s;
        if (s > best) best = s;
    }

    std::cout << "best: " << best << "\n";
    return 0;
}
```

#### 4) Quest log (guardar 5 quests, cargar y listar)
```cpp
#include <fstream>
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> quests;
    for (int i = 0; i < 5; i++) {
        std::string q;
        std::cout << "quest: ";
        std::cin >> q;
        quests.push_back(q);
    }

    {   // save
        std::ofstream out("quests.txt");
        out << quests.size() << "\n";
        for (int i = 0; i < (int)quests.size(); i++) out << quests[i] << "\n";
    }

    // load
    std::ifstream in("quests.txt");
    int n;
    in >> n;

    for (int i = 0; i < n; i++) {
        std::string q;
        in >> q;
        std::cout << (i + 1) << ") " << q << "\n";
    }
    return 0;
}
```

#### 5) Append log (sobrescribir o agregar)
```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    int option;
    std::cout << "1) Overwrite\n2) Append\nChoose: ";
    std::cin >> option;

    std::string line;
    std::cout << "line: ";
    std::cin >> line;

    if (option == 1) {
        std::ofstream out("log.txt");
        out << line << "\n";
    } else if (option == 2) {
        std::ofstream out("log.txt", std::ios::app);
        out << line << "\n";
    } else {
        std::cout << "Invalid\n";
    }

    return 0;
}
```

---

## Revisión (para arrancar el Súper Desafío)
- Revisa formato: 1 valor por línea o (N + lista).
- Puente: “Tu súper desafío del parcial probablemente pedirá save/load.”
- Pide que abran el archivo y verifiquen el contenido.

---

# 14) Depuración y calidad

## Explicación (máx 5 párrafos)
Depurar es rastrear por qué un valor no es el esperado. Para principiantes: prints de `[DEBUG]` + casos de prueba pequeños. Calidad también significa mejorar nombres y estructura sin cambiar qué hace el programa (refactor).

---

## 6 ejemplos resueltos (distintos a alumno)

### Ejemplo 1 — Debug de compra
```cpp
#include <iostream>

int main() {
    int coins = 30;
    int price = 50;

    std::cout << "[DEBUG] coins=" << coins << " price=" << price << "\n";
    int left = coins - price;
    std::cout << "[DEBUG] left=" << left << "\n";

    std::cout << (left >= 0 ? "OK\n" : "NOT ENOUGH\n");
    return 0;
}
```

### Ejemplo 2 — Expected vs Result
```cpp
#include <iostream>

int main() {
    int expected = 15;
    int result = 10 + 5;
    std::cout << "Expected: " << expected << "\n";
    std::cout << "Result:   " << result << "\n";
    return 0;
}
```

### Ejemplo 3 — Refactor: repetir a función
```cpp
#include <iostream>

int addCoins(int coins, int reward) { return coins + reward; }

int main() {
    std::cout << addCoins(10, 5) << "\n";
    std::cout << addCoins(15, 5) << "\n";
    return 0;
}
```

### Ejemplo 4 — Nombres claros
```cpp
#include <iostream>

int main() {
    int player_hp = 80;
    int incoming_damage = 35;

    int hp_after_hit = player_hp - incoming_damage;
    std::cout << hp_after_hit << "\n";
    return 0;
}
```

### Ejemplo 5 — Caso borde HP
```cpp
#include <iostream>

int main() {
    int hp = 5;
    int damage = 10;

    int after = hp - damage;
    if (after < 0) after = 0;

    std::cout << after << "\n";
    return 0;
}
```

### Ejemplo 6 — Debug en loop
```cpp
#include <iostream>

int main() {
    int hp = 30;

    while (hp > 0) {
        std::cout << "[DEBUG] hp=" << hp << "\n";
        hp -= 7;
    }
    std::cout << "GAME OVER\n";
    return 0;
}
```

---

## Desafíos resueltos (alumnos)

### En clase (≤5 min c/u)

#### 1) Debug coins
```cpp
#include <iostream>

int main() {
    int coins, price;
    std::cout << "coins: ";
    std::cin >> coins;
    std::cout << "price: ";
    std::cin >> price;

    std::cout << "[DEBUG] coins=" << coins << " price=" << price << "\n";
    int left = coins - price;
    std::cout << "[DEBUG] left=" << left << "\n";

    std::cout << (left >= 0 ? "OK\n" : "NOT ENOUGH\n");
    return 0;
}
```

#### 2) Find bug (prints)
```cpp
#include <iostream>

int main() {
    int hp = 50;
    int damage = 20;

    std::cout << "[DEBUG] hp=" << hp << "\n";
    hp = hp - damage;
    std::cout << "[DEBUG] hpAfter=" << hp << "\n";

    std::cout << hp << "\n";
    return 0;
}
```

#### 3) Refactor (bloque → función)
```cpp
#include <iostream>

int applyDamage(int hp, int damage) {
    return hp - damage;
}

int main() {
    std::cout << applyDamage(80, 35) << "\n";
    return 0;
}
```

### En casa (más extensos)

#### 1) Bug hunt (documenta)
```text
Ejemplo de respuesta esperada:
- Bug: coinsLeft salía negativo cuando price * qty > coins
- Hipótesis: cálculo incorrecto o falta validación
- Debug: imprimí coins, price, qty, total, coinsLeft
- Fix: validé coins >= total antes de comprar
```

#### 2) Refactor menu (if/else → switch + funciones)
```text
Solución esperada (estructura):
- function print_menu()
- function handle_option(option)
- main: while(option != EXIT) { print_menu(); read; handle_option(); }
```

#### 3) Edge cases (clamp HP)
```text
Casos recomendados:
- hp=-5 -> 0
- hp=0 -> 0
- hp=50 -> 50
- hp=120 -> 100
```

#### 4) Mini tests (5 pruebas expected/result)
```text
Ejemplo:
1) clamp(140,0,100) expected 100
2) clamp(-2,0,100) expected 0
3) addCoins(10,5) expected 15
4) canBuy(50,50) expected true
5) calculateDamage(10,3) expected 13
```

#### 5) Readability pass
```text
Checklist de solución:
- nombres en inglés
- constantes en SNAKE_CASE
- indentación consistente
- mensajes claros al usuario
```

---