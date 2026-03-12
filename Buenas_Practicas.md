# GUÍA DE BUENAS PRÁCTICAS
## Programación estructurada avanzada en C++

---

# 1. Nombres claros y consistentes

## Por qué existe esta regla

Los programas se leen muchas más veces de las que se escriben.
Un nombre mal elegido obliga al lector a descifrar qué hace el código.

Los nombres claros reducen errores y facilitan el mantenimiento.

---

## Regla

- Variables y funciones deben tener **nombres descriptivos**
- Usar **inglés**
- Mantener una convención consistente

Ejemplo recomendado:

player_health
enemy_count
calculate_damage()

---

## Ejemplo incorrecto


int a;
int x;
void f();


---

## Ejemplo correcto


int player_health;
int enemy_count;

void calculate_damage();


---

# 2. Una función debe tener una sola responsabilidad

## Por qué existe esta regla

Las funciones demasiado grandes se vuelven difíciles de entender, probar y modificar.

Dividir la lógica permite:
- reutilizar código
- aislar errores
- mejorar la claridad

---

## Ejemplo incorrecto


void game_system()
{
// combate
// inventario
// guardado
// IA
}


---

## Ejemplo correcto


void combat_system();
void inventory_system();
void save_game();
void enemy_ai();


---

# 3. Evitar números mágicos

## Por qué existe esta regla

Los números incrustados en el código hacen que el programa sea difícil de modificar.

Si el valor cambia, puede ser necesario buscarlo en múltiples lugares.

---

## Ejemplo incorrecto


if(player_health < 20)


---

## Ejemplo correcto


const int CRITICAL_HEALTH = 20;

if(player_health < CRITICAL_HEALTH)


---

# 4. Inicializar siempre la memoria

## Por qué existe esta regla

Las variables no inicializadas contienen **basura de memoria**.

Esto provoca comportamientos impredecibles.

---

## Ejemplo incorrecto


int damage;
cout << damage;


---

## Ejemplo correcto


int damage = 0;
cout << damage;


---

# 5. Manejo responsable de memoria dinámica

## Por qué existe esta regla

Cuando se usa `new`, el programador es responsable de liberar la memoria.

No hacerlo genera **memory leaks**.

---

## Regla fundamental

Cada `new` debe tener su correspondiente `delete`.

---

## Ejemplo incorrecto


Enemy* enemy = new Enemy;


---

## Ejemplo correcto


Enemy* enemy = new Enemy;

/* uso del enemigo */

delete enemy;


---

# 6. Mantener punteros seguros

## Por qué existe esta regla

Los punteros pueden apuntar a memoria inválida o liberada.

Esto genera **errores críticos o crashes**.

---

## Regla

Después de liberar memoria, el puntero debe ponerse en `nullptr`.

---

## Ejemplo


delete enemy;
enemy = nullptr;


---

# 7. Evitar duplicación de código

## Por qué existe esta regla

La duplicación multiplica los errores.

Si una regla cambia, habría que modificar el mismo código en muchos lugares.

---

## Ejemplo incorrecto


player_hp -= damage;
enemy_hp -= damage;
boss_hp -= damage;


---

## Ejemplo correcto


void apply_damage(int &target_hp, int damage)
{
target_hp -= damage;
}


---

# 8. Mantener estructuras de datos coherentes

## Por qué existe esta regla

Cuando se usan listas, pilas o colas, el estado de los nodos debe mantenerse consistente.

Errores comunes incluyen:
- nodos perdidos
- referencias incorrectas
- ciclos accidentales

---

## Ejemplo conceptual

Nodo correcto:


node->next = nullptr;


Nodo incorrecto:


node->next = node;


---

# 9. Código legible antes que código “ingenioso”

## Por qué existe esta regla

El código excesivamente compacto puede ser difícil de entender.

En ingeniería real, la claridad siempre es preferible.

---

## Ejemplo difícil de leer


x+=y*z-a/b;


---

## Ejemplo claro


int damage = y * z;
int reduction = a / b;

x += damage - reduction;


---

# 10. Probar el código constantemente

## Por qué existe esta regla

Esperar hasta el final para probar el programa vuelve difícil encontrar errores.

La práctica correcta es probar cada sistema conforme se desarrolla.

---

## Recomendación

- probar funciones individualmente
- probar estructuras con casos simples
- verificar memoria liberada correctamente