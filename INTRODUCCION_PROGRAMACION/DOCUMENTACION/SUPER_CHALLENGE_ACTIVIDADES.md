# 🎮 SUPER CHALLENGE – Actividades por integrante

Este documento describe lo que debe desarrollar cada integrante del equipo en el **Super Challenge (Mini-RPG en C++)**.  
Todas las actividades deben realizarse aplicando los **temas vistos en clase** (tipos de datos, operadores, condicionales, ciclos, arreglos, cadenas, funciones, parámetros, menús avanzados, etc.).

---

## 👨‍💻 Tony – Jugador
**Responsabilidades:**
- Implementar el **perfil del jugador**: nombre, HP, ATK, DEF y estado general.
- Crear funciones para **mostrar estadísticas** del jugador.
- Manejar el **movimiento del jugador** en el mapa (conexión con Bensu).
- Aplicar efectos que modifiquen atributos (ej. recibir daño, curarse).
- Usar **funciones con paso por referencia** para actualizar valores del jugador.
- Validar que los valores (HP, ATK, DEF) nunca sean negativos.

**Temas aplicados:**
- Tipos de datos, entrada/salida.
- Condicionales, operadores.
- Funciones y paso por referencia.
- Cadenas (`string`).

---

## 👩‍💻 Dani – Inventario
**Responsabilidades:**
- Implementar un **inventario con arreglo unidimensional** (máximo 5 slots).
- Solo se puede tener **1 de cada ítem** (no duplicados).
- Crear funciones para:
  - Mostrar inventario en pantalla.
  - Usar objetos (ej. `pocion`, `superpocion`, `furia`).  
  - Validar disponibilidad antes de usarlos.
- Conectar los efectos de los ítems con el jugador (curación, aumento de ATK).
- Asegurar que al usar un ítem se elimine del inventario.

**Temas aplicados:**
- Arreglos unidimensionales.
- Funciones, parámetros por valor y referencia.
- Condicionales.

---

## 👨‍💻 Ludo – Flujo de juego
**Responsabilidades:**
- Controlar el **menú principal** y la **navegación entre opciones**.
- Llamar funciones de:
  - Mostrar perfil del jugador (Tony).
  - Mostrar y gestionar inventario (Dani).
  - Movimiento en el mapa (Bensu).
  - Combate (Johan).
- Implementar **pause/play** del juego (ciclo principal detenido/reanudado).
- Verificar que el juego se repita hasta elegir “Salir”.

**Temas aplicados:**
- Ciclos (`do...while`, `for`).
- Menús avanzados con `switch`.
- Funciones modulares.

---

## 👨‍💻 Johan – Combate
**Responsabilidades:**
- Implementar el sistema de **combate por turnos**.
- Definir al **enemigo** (HP, ATK, DEF).
- Crear función `calcularDanio` para determinar daño mínimo = 1.
- Alternar ataques entre jugador y enemigo hasta que HP <= 0.
- Mostrar mensajes claros de cada turno y del resultado final (victoria/derrota).
- Conectar inventario (curaciones, aumento de ataque) dentro del combate.

**Temas aplicados:**
- Operadores y expresiones.
- Condicionales.
- Ciclos.
- Funciones.

---

## 👨‍💻 Bensu – Mapa
**Responsabilidades:**
- Implementar un **mapa 5x5 con arreglo bidimensional**.
- Colocar al jugador (Tony) y al enemigo en posiciones iniciales.
- Crear función para **mostrar el mapa** en pantalla.
- Controlar el **movimiento del jugador** con W/A/S/D.
- Detectar proximidad con el enemigo y habilitar combate (con Johan).
- Validar bordes para que el jugador no salga del mapa.

**Temas aplicados:**
- Arreglos bidimensionales.
- Ciclos anidados.
- Condicionales.
- Funciones.

---

# ✅ Checklist de cada integrante
- [ ] Programar su módulo aplicando temas de clase.  
- [ ] Probar y compilar su sección antes de integrarla.  
- [ ] Documentar con comentarios en el código.  
- [ ] Coordinarse con Ludo para la integración en el flujo general.  

---
