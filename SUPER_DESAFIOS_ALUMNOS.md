# Súper Desafíos (Exámenes) — INTRODUCCIÓN A LA PROGRAMACIÓN (C++)
**Institución:**   
**Profesor:** Josue Coria  
**Lenguaje:** C++ (Consola)

> Todos los súper desafíos están orientados a **resolver sistemas concretos de videojuegos** en consola.  
> Entrega: `main.cpp` + repositorio en GitHub.

---

# Parcial 1 — *Console Game Core*

## Objetivo general
Construir un **núcleo jugable en consola** con menú, estadísticas del jugador y al menos un sistema funcional (combate o tienda), usando únicamente los temas vistos en la **primera mitad del curso**.

## Alcance permitido
- `cout / cin`
- Variables y operaciones
- `if / else`, `switch`
- Ciclos (`while` / `for`)
- Funciones básicas

---

## Modalidades

### Individual
**Sistema mínimo requerido**
- Menú principal (loop) con opciones:
  - Ver estadísticas
  - Combate simple (resta HP)
  - Tienda simple (resta monedas)
  - Salir
- HP nunca puede ser negativo
- El programa debe **seguir corriendo** hasta que el usuario elija salir

---

### Pareja
**Sistema requerido**
- Todo lo del individual, más:
  - Sistema de curación
  - Al menos 2 tipos de combate (ej. normal / crítico)
- Uso obligatorio de **funciones** para evitar duplicación

**Roles sugeridos**
- Persona A: Menús + flujo general
- Persona B: Combate + tienda

---

### Grupo (3–6 personas)
**Sistema requerido**
- Todo lo anterior, más:
  - Sistema de dificultad (easy/normal/hard)
  - Ajuste dinámico de daño según dificultad
  - Pantalla de resumen al salir

**Roles sugeridos**
- UI / Menús
- Combate
- Economía (tienda / monedas)
- Integración
- QA / pruebas (documenta casos)

---

# Parcial 2 — *Console Game Extended*

## Objetivo general
Extender el juego del Parcial 1 con **persistencia, datos estructurados y mayor complejidad**, simulando un pequeño proyecto real.

## Alcance permitido
- Todo lo del Parcial 1
- `struct`
- `vector`
- Archivos (`ifstream / ofstream`)
- Strings (`getline`, `find`, `substr`)

---

## Modalidades

### Individual
**Sistema mínimo requerido**
- Inventario dinámico (`vector`)
- Guardar y cargar:
  - HP
  - Monedas
  - Inventario
- Menú con opción Save / Load

---

### Pareja
**Sistema requerido**
- Todo lo del individual, más:
  - Sistema de enemigos con `struct`
  - Combate que afecte structs
  - Al menos 2 archivos distintos (player / inventory)

**Roles sugeridos**
- Persona A: Player + Save/Load
- Persona B: Enemigos + combate

---

### Grupo (3–6 personas)
**Sistema requerido**
- Todo lo anterior, más:
  - Sistema de quests (vector + struct)
  - Registro de progreso en archivo
  - Menú de administración (stats, inventory, quests)

**Roles sugeridos**
- Gameplay (combate / quests)
- Datos (structs)
- Persistencia (archivos)
- UI / navegación
- Integración
- QA / documentación

---

## Entregables
- Repositorio GitHub con:
  - `/src/main.cpp`
  - `README.md` (cómo compilar y jugar)
- Historial mínimo de **commits reales**
- Defensa oral del código (explicación + ajustes)

---
