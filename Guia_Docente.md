# GUÍA PARA PROFESOR
## Programación Estructurada (C++)

**Lenguaje:** C++ (Consola)  
**Enfoque:** Programación estructurada aplicada a sistemas de videojuegos  
**Duración:** 4 meses  

---

# Tema 1 — Structs avanzados (typedef)

Las estructuras permiten agrupar datos relacionados dentro de una entidad lógica. En programación de videojuegos esto es esencial porque casi todos los sistemas del juego se modelan como entidades: jugadores, enemigos, objetos, misiones o estadísticas.

En este tema el objetivo principal no es únicamente aprender la sintaxis de `struct`, sino desarrollar la habilidad de **modelar entidades del mundo del juego**. Los estudiantes deben aprender a identificar qué atributos pertenecen a una entidad y cómo agruparlos correctamente.

El uso de `typedef` permite crear alias de tipos y reducir ruido sintáctico. Aunque en C++ moderno se utilizan otras técnicas, en un curso de programación estructurada es una herramienta clara y pedagógica.

Es recomendable mostrar ejemplos de entidades del juego que ya conocen: personajes, enemigos, armas o inventarios.

Durante la explicación es importante remarcar que las estructuras **solo almacenan datos**. El comportamiento se manejará con funciones externas.

## Ejemplo 1

```cpp
struct Player
{
    string name;
    int level;
    int health;
};
```

## Ejemplo 2

```cpp
Player hero;

hero.name = "Knight";
hero.level = 5;
hero.health = 100;
```

## Ejemplo 3

```cpp
typedef struct
{
    int damage;
    int durability;
} Weapon;
```

## Ejemplo 4

```cpp
Weapon axe;

axe.damage = 20;
axe.durability = 60;
```

## Ejemplo 5

```cpp
struct Enemy
{
    string name;
    int hp;
    int attack;
};
```

## Ejemplo 6

```cpp
Enemy skeleton;

skeleton.name = "Skeleton";
skeleton.hp = 40;
skeleton.attack = 8;
```

## Desafíos de alumnos resueltos

### En clase 1 — Armor

```cpp
#include <iostream>
using namespace std;

struct Armor
{
    int defense;
    int weight;
};

int main()
{
    Armor leather;
    leather.defense = 8;
    leather.weight = 3;

    cout << "Defense: " << leather.defense << endl;
    cout << "Weight: " << leather.weight << endl;

    return 0;
}
```

### En clase 2 — Skill

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Skill
{
    string name;
    int damage;
};

int main()
{
    Skill fireball;
    fireball.name = "Fireball";
    fireball.damage = 25;

    cout << fireball.name << " - Damage: " << fireball.damage << endl;

    return 0;
}
```

### En clase 3 — NPC

```cpp
#include <iostream>
#include <string>
using namespace std;

struct NPC
{
    string name;
    string dialogue;
};

int main()
{
    NPC merchant;
    merchant.name = "Luna";
    merchant.dialogue = "Welcome to my shop.";

    cout << merchant.name << ": " << merchant.dialogue << endl;

    return 0;
}
```

### Casa 1 — Player

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Player
{
    string name;
    int level;
    int experience;
};

int main()
{
    Player hero;
    hero.name = "Aiden";
    hero.level = 3;
    hero.experience = 120;

    cout << hero.name << " Lv." << hero.level
         << " EXP: " << hero.experience << endl;

    return 0;
}
```

### Casa 2 — Enemy

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Enemy
{
    string name;
    int health;
    int attack;
    int speed;
};

int main()
{
    Enemy goblin;
    goblin.name = "Goblin";
    goblin.health = 35;
    goblin.attack = 9;
    goblin.speed = 12;

    cout << goblin.name << " HP:" << goblin.health
         << " ATK:" << goblin.attack
         << " SPD:" << goblin.speed << endl;

    return 0;
}
```

### Casa 3 — Item

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Item
{
    string name;
    string type;
    int value;
};

int main()
{
    Item potion;
    potion.name = "Potion";
    potion.type = "Healing";
    potion.value = 50;

    cout << potion.name << " - " << potion.type
         << " - Value: " << potion.value << endl;

    return 0;
}
```

### Casa 4 — Dos enemigos

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Enemy
{
    string name;
    int health;
    int attack;
};

int main()
{
    Enemy goblin = {"Goblin", 35, 9};
    Enemy slime = {"Slime", 20, 4};

    cout << goblin.name << " HP:" << goblin.health << " ATK:" << goblin.attack << endl;
    cout << slime.name << " HP:" << slime.health << " ATK:" << slime.attack << endl;

    return 0;
}
```

### Casa 5 — Imprimir jugador completo

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Player
{
    string name;
    int level;
    int health;
    int coins;
};

int main()
{
    Player hero = {"Aiden", 4, 95, 120};

    cout << "Name: " << hero.name << endl;
    cout << "Level: " << hero.level << endl;
    cout << "Health: " << hero.health << endl;
    cout << "Coins: " << hero.coins << endl;

    return 0;
}
```

---

# Tema 2 — Funciones avanzadas

Las funciones permiten dividir un programa en bloques reutilizables. Este tema refuerza la idea de **separación de responsabilidades**, que es fundamental para escribir programas mantenibles.

El objetivo pedagógico es que los estudiantes aprendan a diseñar funciones que representen **acciones del sistema del juego**: calcular daño, actualizar vida o procesar eventos.

Aquí también se introduce con más claridad el **paso por referencia**, ya que será clave para comprender punteros y estructuras dinámicas en los siguientes temas.

Los estudiantes suelen cometer el error de crear funciones demasiado largas o con demasiadas responsabilidades. Es importante mostrar ejemplos de funciones simples y enfocadas.

## Ejemplo 1

```cpp
void show_stats(int hp, int level)
{
    cout << "HP: " << hp << endl;
    cout << "Level: " << level << endl;
}
```

## Ejemplo 2

```cpp
int calculate_damage(int attack, int defense)
{
    int damage = attack - defense;

    if(damage < 0)
        damage = 0;

    return damage;
}
```

## Ejemplo 3

```cpp
void heal_player(int &hp, int amount)
{
    hp += amount;
}
```

## Ejemplo 4

```cpp
bool is_dead(int hp)
{
    return hp <= 0;
}
```

## Ejemplo 5

```cpp
int gain_experience(int current, int gain)
{
    return current + gain;
}
```

## Ejemplo 6

```cpp
void print_enemy(string name)
{
    cout << "Enemy: " << name << endl;
}
```

## Desafíos de alumnos resueltos

### En clase 1 — Imprimir nombre del jugador

```cpp
#include <iostream>
#include <string>
using namespace std;

void print_player_name(string name)
{
    cout << "Player: " << name << endl;
}

int main()
{
    print_player_name("Aiden");
    return 0;
}
```

### En clase 2 — Calcular daño

```cpp
#include <iostream>
using namespace std;

int calculate_damage(int attack, int defense)
{
    int damage = attack - defense;
    if(damage < 0) damage = 0;
    return damage;
}

int main()
{
    cout << calculate_damage(20, 7) << endl;
    return 0;
}
```

### En clase 3 — Aumentar vida

```cpp
#include <iostream>
using namespace std;

void heal_player(int &health)
{
    health += 15;
}

int main()
{
    int health = 50;
    heal_player(health);
    cout << health << endl;
    return 0;
}
```

### Casa 1 — Experiencia de combate

```cpp
#include <iostream>
using namespace std;

int gain_experience(int current_exp, int earned_exp)
{
    return current_exp + earned_exp;
}

int main()
{
    cout << "Total EXP: " << gain_experience(120, 35) << endl;
    return 0;
}
```

### Casa 2 — Verificar enemigo vivo

```cpp
#include <iostream>
using namespace std;

bool is_enemy_alive(int health)
{
    return health > 0;
}

int main()
{
    cout << is_enemy_alive(20) << endl;
    return 0;
}
```

### Casa 3 — Imprimir estadísticas del jugador

```cpp
#include <iostream>
#include <string>
using namespace std;

void print_stats(string name, int level, int health)
{
    cout << "Name: " << name << endl;
    cout << "Level: " << level << endl;
    cout << "Health: " << health << endl;
}

int main()
{
    print_stats("Aiden", 4, 95);
    return 0;
}
```

### Casa 4 — Reducir vida de enemigo

```cpp
#include <iostream>
using namespace std;

void apply_damage(int &enemy_health, int damage)
{
    enemy_health -= damage;
    if(enemy_health < 0) enemy_health = 0;
}

int main()
{
    int enemy_health = 40;
    apply_damage(enemy_health, 12);
    cout << enemy_health << endl;
    return 0;
}
```

### Casa 5 — Daño crítico

```cpp
#include <iostream>
using namespace std;

int critical_damage(int attack, bool critical)
{
    if(critical)
        return attack * 2;
    return attack;
}

int main()
{
    cout << critical_damage(18, true) << endl;
    return 0;
}
```

---

# Tema 3 — Apuntadores

Los apuntadores introducen a los estudiantes al concepto de **direcciones de memoria**. Este tema suele ser uno de los primeros grandes obstáculos conceptuales.

Es importante explicar que un apuntador **no almacena el valor**, sino la dirección donde se encuentra el valor.

Un buen enfoque pedagógico es mostrar el flujo:

variable → dirección de memoria → puntero → desreferenciación.

También es importante explicar cuidadosamente el uso de `&` y `*`, ya que los estudiantes suelen confundir ambos operadores.

Este tema prepara directamente el camino para **estructuras dinámicas**.

## Ejemplo 1

```cpp
int health = 100;
int* ptr = &health;
```

## Ejemplo 2

```cpp
cout << *ptr << endl;
```

## Ejemplo 3

```cpp
*ptr = 75;
```

## Ejemplo 4

```cpp
void damage_player(int* hp)
{
    *hp -= 10;
}
```

## Ejemplo 5

```cpp
int score = 500;
int* score_ptr = &score;
```

## Ejemplo 6

```cpp
cout << score_ptr << endl;
```

## Desafíos de alumnos resueltos

### En clase 1 — Puntero a vida

```cpp
#include <iostream>
using namespace std;

int main()
{
    int health = 100;
    int* ptr = &health;

    cout << ptr << endl;
    return 0;
}
```

### En clase 2 — Imprimir valor desreferenciado

```cpp
#include <iostream>
using namespace std;

int main()
{
    int health = 100;
    int* ptr = &health;

    cout << *ptr << endl;
    return 0;
}
```

### En clase 3 — Modificar valor con puntero

```cpp
#include <iostream>
using namespace std;

int main()
{
    int health = 100;
    int* ptr = &health;

    *ptr = 70;
    cout << health << endl;
    return 0;
}
```

### Casa 1 — Reducir vida con puntero

```cpp
#include <iostream>
using namespace std;

void damage_player(int* health, int damage)
{
    *health -= damage;
    if(*health < 0) *health = 0;
}

int main()
{
    int health = 90;
    damage_player(&health, 20);
    cout << health << endl;
    return 0;
}
```

### Casa 2 — Modificar oro

```cpp
#include <iostream>
using namespace std;

void add_gold(int* gold, int amount)
{
    *gold += amount;
}

int main()
{
    int gold = 50;
    add_gold(&gold, 25);
    cout << gold << endl;
    return 0;
}
```

### Casa 3 — Direcciones de memoria

```cpp
#include <iostream>
using namespace std;

int main()
{
    int health = 100;
    int coins = 20;
    int level = 4;

    cout << &health << endl;
    cout << &coins << endl;
    cout << &level << endl;
    return 0;
}
```

### Casa 4 — Intercambiar valores

```cpp
#include <iostream>
using namespace std;

void swap_values(int* a, int* b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main()
{
    int x = 10, y = 20;
    swap_values(&x, &y);

    cout << x << " " << y << endl;
    return 0;
}
```

### Casa 5 — Modificar estadísticas

```cpp
#include <iostream>
using namespace std;

void level_up(int* health, int* attack)
{
    *health += 20;
    *attack += 5;
}

int main()
{
    int health = 80;
    int attack = 12;

    level_up(&health, &attack);

    cout << "Health: " << health << endl;
    cout << "Attack: " << attack << endl;

    return 0;
}
```

---

# Tema 4 — Recursividad

La recursividad introduce una forma diferente de pensar los problemas: resolver un problema mediante versiones más pequeñas del mismo problema.

Es fundamental que los estudiantes comprendan dos elementos:

- caso base
- llamada recursiva

Si no existe caso base el programa entrará en una recursión infinita.

Es recomendable comenzar con ejemplos simples como factorial o sumatorias antes de mostrar aplicaciones más complejas.

## Ejemplo 1

```cpp
int factorial(int n)
{
    if(n == 1)
        return 1;

    return n * factorial(n - 1);
}
```

## Ejemplo 2

```cpp
int sum(int n)
{
    if(n == 1)
        return 1;

    return n + sum(n - 1);
}
```

## Ejemplo 3

```cpp
void countdown(int n)
{
    if(n == 0)
        return;

    cout << n << endl;
    countdown(n - 1);
}
```

## Ejemplo 4

```cpp
int power(int base, int exp)
{
    if(exp == 0)
        return 1;

    return base * power(base, exp - 1);
}
```

## Ejemplo 5

```cpp
int double_value(int x)
{
    if(x <= 1)
        return 1;

    return 2 * double_value(x - 1);
}
```

## Ejemplo 6

```cpp
void print_levels(int lvl)
{
    if(lvl == 0)
        return;

    cout << lvl << endl;
    print_levels(lvl - 1);
}
```

## Desafíos de alumnos resueltos

### En clase 1 — Niveles del 5 al 1

```cpp
#include <iostream>
using namespace std;

void print_levels(int level)
{
    if(level == 0) return;
    cout << level << endl;
    print_levels(level - 1);
}

int main()
{
    print_levels(5);
    return 0;
}
```

### En clase 2 — Suma del 1 al N

```cpp
#include <iostream>
using namespace std;

int recursive_sum(int n)
{
    if(n == 1) return 1;
    return n + recursive_sum(n - 1);
}

int main()
{
    cout << recursive_sum(5) << endl;
    return 0;
}
```

### En clase 3 — Factorial

```cpp
#include <iostream>
using namespace std;

int factorial(int n)
{
    if(n == 1) return 1;
    return n * factorial(n - 1);
}

int main()
{
    cout << factorial(5) << endl;
    return 0;
}
```

### Casa 1 — Experiencia acumulada

```cpp
#include <iostream>
using namespace std;

int accumulated_exp(int battles)
{
    if(battles == 1) return 10;
    return 10 + accumulated_exp(battles - 1);
}

int main()
{
    cout << accumulated_exp(4) << endl;
    return 0;
}
```

### Casa 2 — Enemigos restantes

```cpp
#include <iostream>
using namespace std;

int remaining_enemies(int total)
{
    if(total == 0) return 0;
    return 1 + remaining_enemies(total - 1);
}

int main()
{
    cout << remaining_enemies(6) << endl;
    return 0;
}
```

### Casa 3 — Daño acumulado

```cpp
#include <iostream>
using namespace std;

int accumulated_damage(int turns)
{
    if(turns == 1) return 8;
    return 8 + accumulated_damage(turns - 1);
}

int main()
{
    cout << accumulated_damage(3) << endl;
    return 0;
}
```

### Casa 4 — Reducir energía

```cpp
#include <iostream>
using namespace std;

void reduce_energy(int energy)
{
    if(energy <= 0)
    {
        cout << 0 << endl;
        return;
    }

    cout << energy << endl;
    reduce_energy(energy - 5);
}

int main()
{
    reduce_energy(20);
    return 0;
}
```

### Casa 5 — Multiplicación con suma

```cpp
#include <iostream>
using namespace std;

int multiply(int a, int b)
{
    if(b == 0) return 0;
    return a + multiply(a, b - 1);
}

int main()
{
    cout << multiply(4, 3) << endl;
    return 0;
}
```

---

# Tema 5 — Algoritmos de ordenamiento y búsqueda

Los algoritmos de ordenamiento organizan datos dentro de una estructura. Esto es útil para ordenar puntuaciones, inventarios o listas de enemigos.

Este tema permite introducir el concepto de **eficiencia algorítmica**, aunque sin profundizar aún en análisis formal.

Se recomienda comenzar con **Bubble Sort**, ya que es fácil de entender visualmente. Posteriormente se pueden presentar algoritmos más eficientes como QuickSort.

Los estudiantes suelen cometer errores en los índices de los ciclos, por lo que es importante revisar cuidadosamente cada implementación.

## Ejemplo 1 — Bubble Sort

```cpp
for(int i=0;i<n-1;i++)
{
    for(int j=0;j<n-i-1;j++)
    {
        if(arr[j] > arr[j+1])
        {
            swap(arr[j],arr[j+1]);
        }
    }
}
```

## Ejemplo 2 — Selection Sort

```cpp
for(int i=0;i<n-1;i++)
{
    int min=i;

    for(int j=i+1;j<n;j++)
        if(arr[j]<arr[min])
            min=j;

    swap(arr[i],arr[min]);
}
```

## Ejemplo 3 — Insertion Sort

```cpp
for(int i=1;i<n;i++)
{
    int key=arr[i];
    int j=i-1;

    while(j>=0 && arr[j]>key)
    {
        arr[j+1]=arr[j];
        j--;
    }

    arr[j+1]=key;
}
```

## Ejemplo 4 — Shell Sort

```cpp
for(int gap = n/2; gap > 0; gap /= 2)
{
    for(int i = gap; i < n; i++)
    {
        int temp = arr[i];
        int j;

        for(j = i; j >= gap && arr[j-gap] > temp; j -= gap)
        {
            arr[j] = arr[j-gap];
        }

        arr[j] = temp;
    }
}
```

## Ejemplo 5 — QuickSort

```cpp
void quickSort(int arr[], int low, int high)
{
    if(low < high)
    {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

## Ejemplo 6 — Búsqueda lineal

```cpp
int search(int arr[], int size, int value)
{
    for(int i=0;i<size;i++)
    {
        if(arr[i]==value)
            return i;
    }

    return -1;
}
```

## Desafíos de alumnos resueltos

### En clase 1 — Bubble Sort con 3 puntuaciones

```cpp
#include <iostream>
using namespace std;

int main()
{
    int scores[3] = {300, 120, 250};

    for(int i = 0; i < 2; i++)
    {
        for(int j = 0; j < 2 - i; j++)
        {
            if(scores[j] > scores[j + 1])
            {
                int temp = scores[j];
                scores[j] = scores[j + 1];
                scores[j + 1] = temp;
            }
        }
    }

    for(int i = 0; i < 3; i++)
        cout << scores[i] << " ";

    return 0;
}
```

### En clase 2 — Insertion Sort con 4 niveles

```cpp
#include <iostream>
using namespace std;

int main()
{
    int levels[4] = {8, 2, 6, 4};

    for(int i = 1; i < 4; i++)
    {
        int key = levels[i];
        int j = i - 1;

        while(j >= 0 && levels[j] > key)
        {
            levels[j + 1] = levels[j];
            j--;
        }

        levels[j + 1] = key;
    }

    for(int i = 0; i < 4; i++)
        cout << levels[i] << " ";

    return 0;
}
```

### En clase 3 — Buscar enemigo en arreglo

```cpp
#include <iostream>
using namespace std;

int main()
{
    int enemy_ids[5] = {10, 20, 30, 40, 50};
    int target = 30;
    int position = -1;

    for(int i = 0; i < 5; i++)
    {
        if(enemy_ids[i] == target)
        {
            position = i;
            break;
        }
    }

    cout << "Position: " << position << endl;
    return 0;
}
```

### Casa 1 — Ranking ordenado

```cpp
#include <iostream>
using namespace std;

int main()
{
    int scores[5] = {540, 120, 980, 300, 410};

    for(int i = 0; i < 4; i++)
    {
        for(int j = 0; j < 4 - i; j++)
        {
            if(scores[j] < scores[j + 1])
            {
                int temp = scores[j];
                scores[j] = scores[j + 1];
                scores[j + 1] = temp;
            }
        }
    }

    for(int i = 0; i < 5; i++)
        cout << scores[i] << " ";

    return 0;
}
```

### Casa 2 — Ordenar daño de enemigos

```cpp
#include <iostream>
using namespace std;

int main()
{
    int damages[5] = {14, 5, 22, 9, 18};

    for(int i = 0; i < 4; i++)
    {
        int min = i;
        for(int j = i + 1; j < 5; j++)
        {
            if(damages[j] < damages[min])
                min = j;
        }

        int temp = damages[i];
        damages[i] = damages[min];
        damages[min] = temp;
    }

    for(int i = 0; i < 5; i++)
        cout << damages[i] << " ";

    return 0;
}
```

### Casa 3 — Búsqueda lineal de ítem

```cpp
#include <iostream>
using namespace std;

int linear_search(int items[], int size, int target)
{
    for(int i = 0; i < size; i++)
    {
        if(items[i] == target)
            return i;
    }
    return -1;
}

int main()
{
    int items[6] = {101, 205, 330, 404, 550, 602};
    cout << linear_search(items, 6, 404) << endl;
    return 0;
}
```

### Casa 4 — Ordenar inventario

```cpp
#include <iostream>
using namespace std;

int main()
{
    int inventory_ids[6] = {12, 3, 25, 7, 18, 1};

    for(int i = 1; i < 6; i++)
    {
        int key = inventory_ids[i];
        int j = i - 1;

        while(j >= 0 && inventory_ids[j] > key)
        {
            inventory_ids[j + 1] = inventory_ids[j];
            j--;
        }

        inventory_ids[j + 1] = key;
    }

    for(int i = 0; i < 6; i++)
        cout << inventory_ids[i] << " ";

    return 0;
}
```

### Casa 5 — Ranking de jugadores

```cpp
#include <iostream>
using namespace std;

int main()
{
    int ranking[5] = {2200, 1850, 3100, 2700, 1990};

    for(int i = 0; i < 4; i++)
    {
        for(int j = 0; j < 4 - i; j++)
        {
            if(ranking[j] < ranking[j + 1])
            {
                int temp = ranking[j];
                ranking[j] = ranking[j + 1];
                ranking[j + 1] = temp;
            }
        }
    }

    for(int i = 0; i < 5; i++)
        cout << ranking[i] << " ";

    return 0;
}
```

---

# Tema 6 — Listas enlazadas

Las listas enlazadas introducen estructuras dinámicas. Cada elemento contiene un valor y un puntero al siguiente nodo.

Este tema requiere especial atención al manejo de memoria dinámica mediante `new` y `delete`.

Los errores más comunes incluyen:

- perder la referencia al primer nodo
- enlazar nodos incorrectamente
- crear ciclos accidentales

## Ejemplo 1

```cpp
struct Node
{
    int value;
    Node* next;
};
```

## Ejemplo 2

```cpp
Node* head = nullptr;
```

## Ejemplo 3

```cpp
Node* newNode = new Node;
```

## Ejemplo 4

```cpp
newNode->value = 10;
newNode->next = nullptr;
```

## Ejemplo 5

```cpp
head = newNode;
```

## Ejemplo 6

```cpp
Node* temp = head;
```

## Desafíos de alumnos resueltos

### En clase 1 — Nodo simple

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* node = new Node;
    node->value = 15;
    node->next = nullptr;

    cout << node->value << endl;

    delete node;
    return 0;
}
```

### En clase 2 — Nodo con puntero

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* node = new Node;
    node->value = 22;
    node->next = nullptr;

    cout << node->value << endl;

    delete node;
    return 0;
}
```

### En clase 3 — Nodo inicial

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* head = new Node;
    head->value = 50;
    head->next = nullptr;

    cout << head->value << endl;

    delete head;
    return 0;
}
```

### Casa 1 — Lista de enemigos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int enemy_id;
    Node* next;
};

int main()
{
    Node* head = new Node{1, nullptr};
    cout << "Enemy ID: " << head->enemy_id << endl;

    delete head;
    return 0;
}
```

### Casa 2 — Insertar tres nodos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* head = new Node{10, nullptr};
    head->next = new Node{20, nullptr};
    head->next->next = new Node{30, nullptr};

    Node* temp = head;
    while(temp != nullptr)
    {
        cout << temp->value << " ";
        temp = temp->next;
    }

    Node* third = head->next->next;
    Node* second = head->next;
    delete third;
    delete second;
    delete head;

    return 0;
}
```

### Casa 3 — Recorrer lista

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* head = new Node{5, nullptr};
    head->next = new Node{10, nullptr};
    head->next->next = new Node{15, nullptr};

    Node* temp = head;
    while(temp != nullptr)
    {
        cout << temp->value << endl;
        temp = temp->next;
    }

    delete head->next->next;
    delete head->next;
    delete head;

    return 0;
}
```

### Casa 4 — Eliminar nodo

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* head = new Node{10, nullptr};
    head->next = new Node{20, nullptr};
    head->next->next = new Node{30, nullptr};

    Node* to_delete = head->next;
    head->next = head->next->next;
    delete to_delete;

    Node* temp = head;
    while(temp != nullptr)
    {
        cout << temp->value << " ";
        temp = temp->next;
    }

    delete head->next;
    delete head;

    return 0;
}
```

### Casa 5 — Lista de inventario

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int item_id;
    Node* next;
};

int main()
{
    Node* head = new Node{101, nullptr};
    head->next = new Node{205, nullptr};
    head->next->next = new Node{330, nullptr};

    Node* temp = head;
    while(temp != nullptr)
    {
        cout << "Item: " << temp->item_id << endl;
        temp = temp->next;
    }

    delete head->next->next;
    delete head->next;
    delete head;

    return 0;
}
```

---

# Tema 7 — Pilas

Las pilas funcionan bajo el principio **LIFO (Last In First Out)**.

En programación de videojuegos pueden usarse para:

- historial de acciones
- sistema de deshacer
- control de estados

## Ejemplo 1

```cpp
struct Node
{
    int value;
    Node* next;
};
```

## Ejemplo 2

```cpp
Node* top = nullptr;
```

## Ejemplo 3

```cpp
Node* newNode = new Node;
```

## Ejemplo 4

```cpp
newNode->value = value;
newNode->next = top;
```

## Ejemplo 5

```cpp
top = newNode;
```

## Ejemplo 6

```cpp
Node* temp = top;
```

## Desafíos de alumnos resueltos

### En clase 1 — Nodo de pila

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* top = new Node{15, nullptr};
    cout << top->value << endl;
    delete top;
    return 0;
}
```

### En clase 2 — Push

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

void push(Node*& top, int value)
{
    Node* newNode = new Node{value, top};
    top = newNode;
}

int main()
{
    Node* top = nullptr;
    push(top, 10);
    cout << top->value << endl;
    delete top;
    return 0;
}
```

### En clase 3 — Mostrar top

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* top = new Node{40, nullptr};
    cout << "Top: " << top->value << endl;
    delete top;
    return 0;
}
```

### Casa 1 — Historial de acciones

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int action_id;
    Node* next;
};

void push(Node*& top, int action_id)
{
    top = new Node{action_id, top};
}

int main()
{
    Node* top = nullptr;
    push(top, 101);
    push(top, 102);

    cout << "Last action: " << top->action_id << endl;

    delete top->next;
    delete top;
    return 0;
}
```

### Casa 2 — Push de habilidades

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int skill_id;
    Node* next;
};

void push(Node*& top, int skill_id)
{
    top = new Node{skill_id, top};
}

int main()
{
    Node* top = nullptr;
    push(top, 7);
    push(top, 9);

    cout << top->skill_id << endl;

    delete top->next;
    delete top;
    return 0;
}
```

### Casa 3 — Pop de acciones

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int action_id;
    Node* next;
};

void push(Node*& top, int action_id)
{
    top = new Node{action_id, top};
}

void pop(Node*& top)
{
    if(top != nullptr)
    {
        Node* temp = top;
        top = top->next;
        delete temp;
    }
}

int main()
{
    Node* top = nullptr;
    push(top, 1);
    push(top, 2);
    pop(top);

    cout << top->action_id << endl;

    delete top;
    return 0;
}
```

### Casa 4 — Mostrar pila

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

void push(Node*& top, int value)
{
    top = new Node{value, top};
}

void print_stack(Node* top)
{
    Node* temp = top;
    while(temp != nullptr)
    {
        cout << temp->value << endl;
        temp = temp->next;
    }
}

int main()
{
    Node* top = nullptr;
    push(top, 10);
    push(top, 20);
    push(top, 30);

    print_stack(top);

    while(top != nullptr)
    {
        Node* temp = top;
        top = top->next;
        delete temp;
    }

    return 0;
}
```

### Casa 5 — Deshacer movimiento

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int position;
    Node* next;
};

void push(Node*& top, int position)
{
    top = new Node{position, top};
}

void undo(Node*& top)
{
    if(top != nullptr)
    {
        Node* temp = top;
        top = top->next;
        delete temp;
    }
}

int main()
{
    Node* top = nullptr;
    push(top, 5);
    push(top, 8);
    push(top, 12);

    undo(top);

    cout << "Current top position: " << top->position << endl;

    while(top != nullptr)
    {
        Node* temp = top;
        top = top->next;
        delete temp;
    }

    return 0;
}
```

---

# Tema 8 — Colas

Las colas siguen el principio **FIFO (First In First Out)**.

Se utilizan en videojuegos para gestionar:

- turnos
- eventos
- procesamiento de acciones

## Ejemplo 1

```cpp
struct Node
{
    int value;
    Node* next;
};
```

## Ejemplo 2

```cpp
Node* front = nullptr;
Node* rear = nullptr;
```

## Ejemplo 3

```cpp
Node* newNode = new Node;
```

## Ejemplo 4

```cpp
newNode->value = value;
newNode->next = nullptr;
```

## Ejemplo 5

```cpp
rear->next = newNode;
rear = newNode;
```

## Ejemplo 6

```cpp
front = front->next;
```

## Desafíos de alumnos resueltos

### En clase 1 — Crear cola

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    cout << "Queue created." << endl;
    return 0;
}
```

### En clase 2 — Insertar elemento

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int value)
{
    Node* newNode = new Node{value, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 15);
    cout << front->value << endl;

    delete front;
    return 0;
}
```

### En clase 3 — Mostrar primer elemento

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int value;
    Node* next;
};

int main()
{
    Node* front = new Node{22, nullptr};
    Node* rear = front;

    cout << "Front: " << front->value << endl;

    delete front;
    return 0;
}
```

### Casa 1 — Sistema de turnos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int enemy_id;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int enemy_id)
{
    Node* newNode = new Node{enemy_id, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 101);
    enqueue(front, rear, 102);

    cout << "Current turn: " << front->enemy_id << endl;

    delete front->next;
    delete front;
    return 0;
}
```

### Casa 2 — Insertar enemigos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int id;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int id)
{
    Node* newNode = new Node{id, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 1);
    enqueue(front, rear, 2);
    enqueue(front, rear, 3);

    cout << front->id << endl;

    delete front->next->next;
    delete front->next;
    delete front;
    return 0;
}
```

### Casa 3 — Atender turno

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int id;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int id)
{
    Node* newNode = new Node{id, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

void dequeue(Node*& front, Node*& rear)
{
    if(front == nullptr) return;

    Node* temp = front;
    front = front->next;
    delete temp;

    if(front == nullptr)
        rear = nullptr;
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 1);
    enqueue(front, rear, 2);
    dequeue(front, rear);

    cout << front->id << endl;

    delete front;
    return 0;
}
```

### Casa 4 — Mostrar cola

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int id;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int id)
{
    Node* newNode = new Node{id, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

void print_queue(Node* front)
{
    Node* temp = front;
    while(temp != nullptr)
    {
        cout << temp->id << endl;
        temp = temp->next;
    }
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 10);
    enqueue(front, rear, 20);
    enqueue(front, rear, 30);

    print_queue(front);

    while(front != nullptr)
    {
        Node* temp = front;
        front = front->next;
        delete temp;
    }

    return 0;
}
```

### Casa 5 — Cola de eventos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int event_id;
    Node* next;
};

void enqueue(Node*& front, Node*& rear, int event_id)
{
    Node* newNode = new Node{event_id, nullptr};

    if(rear == nullptr)
    {
        front = rear = newNode;
        return;
    }

    rear->next = newNode;
    rear = newNode;
}

int main()
{
    Node* front = nullptr;
    Node* rear = nullptr;

    enqueue(front, rear, 2001);
    enqueue(front, rear, 2002);

    cout << "Next event: " << front->event_id << endl;

    delete front->next;
    delete front;
    return 0;
}
```

---

# Tema 9 — Grafos

Los grafos representan relaciones entre nodos conectados mediante aristas.

En videojuegos se utilizan para representar:

- mapas
- caminos
- redes de navegación
- sistemas de misiones

Este tema conecta directamente con problemas de navegación y sistemas de mundo dentro de un juego.

## Ejemplo 1

```cpp
struct Node
{
    int id;
};
```

## Ejemplo 2

```cpp
struct Edge
{
    int from;
    int to;
};
```

## Ejemplo 3

```cpp
Edge edges[10];
```

## Ejemplo 4

```cpp
edges[0].from = 1;
edges[0].to = 2;
```

## Ejemplo 5

```cpp
cout << edges[0].from << " -> " << edges[0].to;
```

## Ejemplo 6

```cpp
struct Graph
{
    int nodes;
    int edges;
};
```

## Desafíos de alumnos resueltos

### En clase 1 — Crear nodo

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int id;
};

int main()
{
    Node a;
    a.id = 1;

    cout << "Node: " << a.id << endl;
    return 0;
}
```

### En clase 2 — Crear conexión

```cpp
#include <iostream>
using namespace std;

struct Edge
{
    int from;
    int to;
};

int main()
{
    Edge e;
    e.from = 1;
    e.to = 2;

    cout << e.from << " -> " << e.to << endl;
    return 0;
}
```

### En clase 3 — Mostrar conexión

```cpp
#include <iostream>
using namespace std;

struct Edge
{
    int from;
    int to;
};

int main()
{
    Edge e = {2, 4};
    cout << e.from << " -> " << e.to << endl;
    return 0;
}
```

### Casa 1 — Mapa de 5 nodos

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int id;
};

int main()
{
    Node nodes[5];

    for(int i = 0; i < 5; i++)
    {
        nodes[i].id = i + 1;
        cout << "Node " << nodes[i].id << endl;
    }

    return 0;
}
```

### Casa 2 — Conectar caminos

```cpp
#include <iostream>
using namespace std;

struct Edge
{
    int from;
    int to;
};

int main()
{
    Edge paths[4] = {
        {1, 2},
        {2, 3},
        {3, 4},
        {4, 5}
    };

    for(int i = 0; i < 4; i++)
        cout << paths[i].from << " -> " << paths[i].to << endl;

    return 0;
}
```

### Casa 3 — Mostrar conexiones

```cpp
#include <iostream>
using namespace std;

struct Edge
{
    int from;
    int to;
};

int main()
{
    Edge edges[3] = {
        {1, 2},
        {1, 3},
        {3, 4}
    };

    for(int i = 0; i < 3; i++)
        cout << edges[i].from << " -> " << edges[i].to << endl;

    return 0;
}
```

### Casa 4 — Simular movimiento

```cpp
#include <iostream>
using namespace std;

struct Edge
{
    int from;
    int to;
};

int main()
{
    Edge edges[4] = {
        {1, 2},
        {2, 3},
        {3, 4},
        {4, 5}
    };

    int current = 1;

    for(int i = 0; i < 4; i++)
    {
        if(edges[i].from == current)
        {
            current = edges[i].to;
            cout << "Moved to node " << current << endl;
        }
    }

    return 0;
}
```

### Casa 5 — Estructura de grafo simple

```cpp
#include <iostream>
using namespace std;

struct Graph
{
    int node_count;
    int edge_count;
};

int main()
{
    Graph map;
    map.node_count = 5;
    map.edge_count = 4;

    cout << "Nodes: " << map.node_count << endl;
    cout << "Edges: " << map.edge_count << endl;

    return 0;
}
```