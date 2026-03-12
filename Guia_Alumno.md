# CURSO --- PROGRAMACIÓN ESTRUCTURADA (C++)

**Lenguaje:** C++ (Consola)\
**Enfoque:** Programación estructurada aplicada a sistemas de
videojuegos\
**Duración:** 4 meses

------------------------------------------------------------------------

# TEMARIO DEL CURSO

## Parte 1 --- Estructuras y memoria

1.  Structs avanzados (typedef)\
2.  Funciones avanzadas\
3.  Apuntadores\
4.  Recursividad\
5.  Algoritmos de ordenamiento y búsqueda

## Parcial 1

**Súper desafío:** Sistema de gestión de entidades de juego.

------------------------------------------------------------------------

## Parte 2 --- Estructuras dinámicas

6.  Listas enlazadas\
7.  Pilas\
8.  Colas\
9.  Grafos

## Parcial 2

**Súper desafío:** Sistema de navegación de mapa usando grafos.

------------------------------------------------------------------------

# GUÍA PARA ALUMNOS

------------------------------------------------------------------------

# Tema 1 --- Structs avanzados (typedef)

Las estructuras (`struct`) permiten agrupar datos relacionados dentro de
una sola entidad. En videojuegos se usan para representar jugadores,
enemigos o ítems.

El uso de `typedef` permite crear un alias del tipo y hacer el código
más claro.

## Ejemplo 1

``` cpp
struct Enemy
{
    string name;
    int health;
};
```

## Ejemplo 2

``` cpp
Enemy goblin;

goblin.name = "Goblin";
goblin.health = 30;
```

## Ejemplo 3

``` cpp
typedef struct
{
    int damage;
    int durability;
} Weapon;
```

## Ejemplo 4

``` cpp
Weapon sword;
sword.damage = 15;
sword.durability = 100;
```

## Ejemplo 5

``` cpp
struct Potion
{
    string name;
    int heal;
};
```

## Ejemplo 6

``` cpp
Potion potion;

potion.name = "Health Potion";
potion.heal = 25;
```

### Desafíos en clase

1.  Crear una estructura `Armor` con defensa y peso.\
2.  Crear una estructura `Skill` con nombre y daño.\
3.  Crear una estructura `NPC` con nombre y diálogo.

### Desafíos para casa

1.  Crear una estructura `Player` con nombre, nivel y experiencia.\
2.  Crear una estructura `Enemy` con nombre, vida, ataque y velocidad.\
3.  Crear una estructura `Item` con nombre, tipo y valor.\
4.  Crear un programa que genere dos enemigos y muestre sus
    estadísticas.\
5.  Crear un sistema que imprima los datos completos de un jugador.

------------------------------------------------------------------------

# Tema 2 --- Funciones avanzadas

Las funciones permiten dividir un programa en partes reutilizables y
organizar mejor la lógica del juego.

## Ejemplo 1

``` cpp
void showPlayerHealth(int health)
{
    cout << "Health: " << health << endl;
}
```

## Ejemplo 2

``` cpp
int calculateDamage(int attack, int defense)
{
    return attack - defense;
}
```

## Ejemplo 3

``` cpp
void healPlayer(int &health)
{
    health += 20;
}
```

## Ejemplo 4

``` cpp
int addScore(int score, int points)
{
    return score + points;
}
```

## Ejemplo 5

``` cpp
void printEnemyName(string name)
{
    cout << name << endl;
}
```

## Ejemplo 6

``` cpp
bool isPlayerAlive(int health)
{
    return health > 0;
}
```

### Desafíos en clase

1.  Crear una función que imprima el nombre de un jugador.\
2.  Crear una función que calcule daño entre dos valores.\
3.  Crear una función que aumente la vida del jugador.

### Desafíos para casa

1.  Crear una función que calcule experiencia obtenida después de un
    combate.\
2.  Crear una función que verifique si un enemigo sigue vivo.\
3.  Crear una función que imprima estadísticas completas del jugador.\
4.  Crear una función que reduzca la vida de un enemigo después de
    recibir daño.\
5.  Crear un sistema de funciones que calcule daño crítico.

------------------------------------------------------------------------

# Tema 3 --- Apuntadores

Un apuntador guarda la dirección de memoria de otra variable.

## Ejemplo 1

``` cpp
int health = 100;
int* ptr = &health;
```

## Ejemplo 2

``` cpp
cout << *ptr << endl;
```

## Ejemplo 3

``` cpp
*ptr = 80;
```

## Ejemplo 4

``` cpp
void damagePlayer(int* health)
{
    *health -= 10;
}
```

## Ejemplo 5

``` cpp
int coins = 50;
int* coin_ptr = &coins;
```

## Ejemplo 6

``` cpp
cout << coin_ptr << endl;
```

### Desafíos en clase

1.  Crear un apuntador a una variable de vida.\
2.  Imprimir el valor usando desreferenciación.\
3.  Modificar un valor usando un apuntador.

### Desafíos para casa

1.  Crear una función que reciba un apuntador a la vida del jugador y
    reduzca daño.\
2.  Crear un sistema que modifique el oro del jugador usando
    apuntadores.\
3.  Mostrar direcciones de memoria de tres variables.\
4.  Crear una función que intercambie dos valores usando apuntadores.\
5.  Crear un sistema que modifique estadísticas del jugador mediante
    punteros.

------------------------------------------------------------------------

# Tema 4 --- Recursividad

Una función recursiva se llama a sí misma y siempre necesita un **caso
base**.

## Ejemplo 1

``` cpp
int factorial(int n)
{
    if(n == 1)
        return 1;

    return n * factorial(n - 1);
}
```

## Ejemplo 2

``` cpp
int sum(int n)
{
    if(n == 1)
        return 1;

    return n + sum(n - 1);
}
```

## Ejemplo 3

``` cpp
void countdown(int n)
{
    if(n == 0)
        return;

    cout << n << endl;
    countdown(n - 1);
}
```

## Ejemplo 4

``` cpp
int doublePoints(int p)
{
    if(p <= 1)
        return 1;

    return 2 * doublePoints(p - 1);
}
```

## Ejemplo 5

``` cpp
void levelDown(int lvl)
{
    if(lvl == 0)
        return;

    cout << lvl << endl;
    levelDown(lvl - 1);
}
```

## Ejemplo 6

``` cpp
int energyDecay(int energy)
{
    if(energy <= 0)
        return 0;

    return energyDecay(energy - 5);
}
```

### Desafíos en clase

1.  Función recursiva que imprima niveles del 5 al 1.\
2.  Función recursiva que sume números del 1 al N.\
3.  Función recursiva que calcule factorial.

### Desafíos para casa

1.  Calcular experiencia acumulada recursivamente.\
2.  Contar enemigos restantes.\
3.  Calcular daño acumulado en turnos.\
4.  Reducir energía hasta cero.\
5.  Multiplicación usando suma recursiva.

------------------------------------------------------------------------

# Tema 5 --- Algoritmos de ordenamiento

## Bubble Sort

``` cpp
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

## Selection Sort

``` cpp
for(int i=0;i<n-1;i++)
{
    int min=i;

    for(int j=i+1;j<n;j++)
        if(arr[j]<arr[min])
            min=j;

    swap(arr[i],arr[min]);
}
```

## Insertion Sort

``` cpp
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

## QuickSort (estructura)

``` cpp
void quickSort(int arr[], int low, int high)
{
    if(low < high)
    {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi-1);
        quickSort(arr, pi+1, high);
    }
}
```

### Desafíos en clase

1.  Ordenar tres puntuaciones con bubble sort.\
2.  Ordenar cuatro niveles con insertion sort.\
3.  Buscar un enemigo en un arreglo.

### Desafíos para casa

1.  Ordenar un ranking de puntuaciones.\
2.  Ordenar daño de enemigos.\
3.  Implementar búsqueda lineal para un ítem.\
4.  Ordenar inventario.\
5.  Crear ranking de jugadores.

------------------------------------------------------------------------

# Tema 6 --- Listas enlazadas

------------------------------------------------------------------------

# Tema 7 --- Pilas

------------------------------------------------------------------------

# Tema 8 --- Colas

------------------------------------------------------------------------

# Tema 9 --- Grafos
