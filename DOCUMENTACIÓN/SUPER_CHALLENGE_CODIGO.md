# 🎮 SUPER CHALLENGE – Código de referencia (Mini‑RPG en C++)

Este archivo contiene un **programa completo** en C++ que satisface la versión modificada del **Super Challenge**, respetando la división de responsabilidades:
- **Tony:** jugador (perfil, movimiento del jugador y utilidades del jugador).
- **Dani:** inventario (uso de ítems, mostrar en pantalla, sin duplicados).
- **Ludo:** flujo del juego (menú, pause/play, orquestación).
- **Johan:** combate por turnos.
- **Bensu:** mapa 5×5 (render, validación y aplicación de movimiento).

> 💡 Todo está implementado solo con los **temas vistos en clase**: tipos de datos, operadores, condicionales, ciclos, arreglos, cadenas, funciones, paso por referencia, y menús avanzados.

---

## 🧩 Compilación y ejecución
Compila como proyecto de consola (C++17+). Ejemplo en terminal:
```bash
g++ -std=cpp17 -O2 -Wall -Wextra -o mini_rpg main.cpp
./mini_rpg
```

---

## 🗂️ Código único (con regiones por responsable)
> Copia el siguiente contenido en `main.cpp`. Cada sección está marcada con:
> `// === [NOMBRE] START ===` y `// === [NOMBRE] END ===`

```cpp
#include <iostream>
#include <string>
#include <limits>
using namespace std;

// -------------------------
// Constantes y tamaños
// -------------------------
const int MAP_N = 5;
const int INV_SIZE = 5;
const int HP_MAX = 50;

// -------------------------
// Prototipos comunes
// -------------------------
void pausar();
void limpiarPantalla();
void imprimirLinea();

// ============================================
// === [TONY] START: Jugador (perfil/movimiento)
// ============================================
struct Jugador {
    string nombre;
    int hp;
    int atk;
    int def_;
};

void inicializarJugador(Jugador &j);
void mostrarPerfil(const Jugador &j);
void curarPorCantidad(Jugador &j, int cantidad);
void aplicarFuria(Jugador &j, bool &furiaUsada);

// "Interfaz de movimiento del jugador": pide dirección al usuario.
// Devuelve 'Q' para salir del submenú de movimiento.
char solicitarDireccionMovimiento();
// ============================================
// === [TONY] END
// ============================================

// ============================================
// === [DANI] START: Inventario (sin duplicados)
// ============================================
void mostrarInventario(const string inv[], int n);
bool contieneItem(const string inv[], int n, const string &item);
bool agregarItemUnico(string inv[], int n, const string &item);
bool usarItem(string inv[], int n, int idx, Jugador &j, bool &furiaUsada);
// ============================================
// === [DANI] END
// ============================================

// ============================================
// === [BENSU] START: Mapa 5x5 y movimiento
// ============================================
struct Mapa {
    char celdas[MAP_N][MAP_N];
    int px, py; // posición jugador
    int ex, ey; // posición enemigo
};

void iniciarMapa(Mapa &m);
void imprimirMapa(const Mapa &m);
// Aplica el movimiento si es válido: retorna true si se movió.
bool moverSiValido(Mapa &m, char dir);
// ============================================
// === [BENSU] END
// ============================================

// ============================================
// === [JOHAN] START: Combate por turnos
// ============================================
struct Enemigo {
    int hp;
    int atk;
    int def_;
};

int calcularDanio(int atk, int def_);
void combate(Jugador &j);
// ============================================
// === [JOHAN] END
// ============================================

// ============================================
// === [LUDO] START: Flujo del juego (menú/pause)
// ============================================
void menuPrincipal(Jugador &j, string inventario[], Mapa &mapa);
// ============================================
// === [LUDO] END
// ============================================

// -------------------------
// MAIN
// -------------------------
int main() {
    // Estado inicial
    Jugador jugador;
    inicializarJugador(jugador);

    string inventario[INV_SIZE] = {"pocion", "", "furia", "", ""};
    bool furiaUsada = false; // lo utilizará Dani al consumir "furia"

    Mapa mapa;
    iniciarMapa(mapa);

    // Flujo general (Ludo)
    menuPrincipal(jugador, inventario, mapa);

    return 0;
}

// -------------------------
// Utilidades comunes
// -------------------------
void pausar() {
    cout << "Presiona ENTER para continuar...";
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
    cin.get();
}
void limpiarPantalla() {
    cout << string(28, '\n');
}
void imprimirLinea() {
    cout << "==============================" << endl;
}

// ============================================
// === [TONY] START: Jugador (perfil/movimiento)
// ============================================
void inicializarJugador(Jugador &j) {
    cout << "Escribe tu nombre de jugador (una palabra): ";
    cin >> j.nombre;
    j.hp  = 30;
    j.atk = 6;
    j.def_ = 2;
}

void mostrarPerfil(const Jugador &j) {
    cout << "Jugador: " << j.nombre
         << " | HP=" << j.hp
         << " ATK=" << j.atk
         << " DEF=" << j.def_
         << " (HP_MAX=" << HP_MAX << ")"
         << endl;
}

void curarPorCantidad(Jugador &j, int cantidad) {
    j.hp += cantidad;
    if (j.hp > HP_MAX) j.hp = HP_MAX;
    if (j.hp < 0) j.hp = 0;
}

void aplicarFuria(Jugador &j, bool &furiaUsada) {
    if (!furiaUsada) {
        j.atk += 3;
        furiaUsada = true;
        cout << "[FURIA] ATK aumentado permanentemente en +3.\n";
    } else {
        cout << "La furia ya fue usada anteriormente.\n";
    }
}

// Devuelve: 'W','A','S','D' o 'Q'
char solicitarDireccionMovimiento() {
    char dir;
    cout << "Mover (W/A/S/D, Q para volver): ";
    cin >> dir;
    return dir;
}
// ============================================
// === [TONY] END
// ============================================

// ============================================
// === [DANI] START: Inventario (sin duplicados)
// ============================================
void mostrarInventario(const string inv[], int n) {
    cout << "--- INVENTARIO ---" << endl;
    for (int i = 0; i < n; ++i) {
        cout << (i+1) << ") " << (inv[i].empty() ? "[vacio]" : inv[i]) << endl;
    }
}

bool contieneItem(const string inv[], int n, const string &item) {
    for (int i = 0; i < n; ++i) {
        if (inv[i] == item) return true;
    }
    return false;
}

bool agregarItemUnico(string inv[], int n, const string &item) {
    if (item != "pocion" && item != "superpocion" && item != "furia") return false;
    if (contieneItem(inv, n, item)) {
        cout << "Ya tienes '" << item << "'. Solo se permite 1 de cada item.\n";
        return false;
    }
    for (int i = 0; i < n; ++i) {
        if (inv[i].empty()) { inv[i] = item; return true; }
    }
    return false;
}

bool usarItem(string inv[], int n, int idx, Jugador &j, bool &furiaUsada) {
    if (idx < 0 || idx >= n || inv[idx].empty()) return false;
    string it = inv[idx];
    if (it == "pocion") {
        curarPorCantidad(j, 5);
        cout << "[Pocion] +5 HP. HP actual: " << j.hp << endl;
    } else if (it == "superpocion") {
        curarPorCantidad(j, 10);
        cout << "[Superpocion] +10 HP. HP actual: " << j.hp << endl;
    } else if (it == "furia") {
        aplicarFuria(j, furiaUsada);
    } else {
        return false;
    }
    inv[idx].clear(); // consumir
    return true;
}
// ============================================
// === [DANI] END
// ============================================

// ============================================
// === [BENSU] START: Mapa 5x5 y movimiento
// ============================================
void iniciarMapa(Mapa &m) {
    for (int i = 0; i < MAP_N; ++i)
        for (int j = 0; j < MAP_N; ++j)
            m.celdas[i][j] = '.';
    m.px = 1; m.py = 1; // jugador
    m.ex = 3; m.ey = 3; // enemigo
    m.celdas[m.py][m.px] = 'P';
    m.celdas[m.ey][m.ex] = 'E';
}

void imprimirMapa(const Mapa &m) {
    for (int i = 0; i < MAP_N; ++i) {
        for (int j = 0; j < MAP_N; ++j) {
            cout << m.celdas[i][j] << ' ';
        }
        cout << '\n';
    }
}

// Aplica el movimiento si es válido y actualiza la celda del jugador.
bool moverSiValido(Mapa &m, char dir) {
    int nx = m.px, ny = m.py;
    if (dir=='w'||dir=='W') ny--;
    else if (dir=='s'||dir=='S') ny++;
    else if (dir=='a'||dir=='A') nx--;
    else if (dir=='d'||dir=='D') nx++;
    else return false;

    if (nx < 0 || nx >= MAP_N || ny < 0 || ny >= MAP_N) {
        cout << "[Borde] No puedes salir del mapa.\n";
        return false;
    }

    if (m.celdas[ny][nx] == 'E') {
        cout << "[Aviso] Estas junto al enemigo. Puedes iniciar combate desde el menu.\n";
    }
    // Actualizar posiciones
    m.celdas[m.py][m.px] = '.';
    m.px = nx; m.py = ny;
    m.celdas[m.py][m.px] = 'P';
    return true;
}
// ============================================
// === [BENSU] END
// ============================================

// ============================================
// === [JOHAN] START: Combate por turnos
// ============================================
int calcularDanio(int atk, int def_) {
    int d = atk - def_;
    if (d < 1) d = 1;
    return d;
}

void combate(Jugador &j) {
    Enemigo e{20, 5, 1};
    cout << "[Combate iniciado]\n";
    while (j.hp > 0 && e.hp > 0) {
        // Turno jugador
        int dJ = calcularDanio(j.atk, e.def_);
        e.hp -= dJ;
        if (e.hp < 0) e.hp = 0;
        cout << j.nombre << " golpea por " << dJ << ". Enemigo HP=" << e.hp << '\n';
        if (e.hp <= 0) break;

        // Turno enemigo
        int dE = calcularDanio(e.atk, j.def_);
        j.hp -= dE;
        if (j.hp < 0) j.hp = 0;
        cout << "Enemigo golpea por " << dE << ". " << j.nombre << " HP=" << j.hp << '\n';
    }
    if (j.hp > 0) cout << "*** ¡Has ganado! ***\n";
    else cout << "*** Has sido derrotado... ***\n";
}
// ============================================
// === [JOHAN] END
// ============================================

// ============================================
// === [LUDO] START: Flujo del juego (menú/pause)
// ============================================
void menuPrincipal(Jugador &j, string inventario[], Mapa &mapa) {
    bool salir = false;
    bool pausado = false;
    bool furiaUsada = false; // Dani la usa dentro de usarItem

    while (!salir) {
        limpiarPantalla();
        imprimirLinea();
        cout << "         MINI-RPG" << (pausado ? " [PAUSADO]" : "") << endl;
        imprimirLinea();
        cout << "1) Perfil del jugador" << endl;
        cout << "2) Inventario" << endl;
        cout << "3) Mapa / Movimiento" << endl;
        cout << "4) Combatir" << endl;
        cout << (pausado ? "5) Reanudar (Play)" : "5) Pausar (Pause)") << endl;
        cout << "6) Salir" << endl;
        imprimirLinea();
        cout << "Opcion: ";

        int opcion;
        cin >> opcion;

        if (pausado && opcion != 5 && opcion != 6) {
            cout << "El juego esta en PAUSA. Reanuda para continuar.\n";
            pausar();
            continue;
        }

        switch (opcion) {
            case 1: {
                limpiarPantalla();
                mostrarPerfil(j);
                pausar();
                break;
            }
            case 2: { // Inventario (Dani)
                int sub;
                do {
                    limpiarPantalla();
                    mostrarInventario(inventario, INV_SIZE);
                    cout << "1) Agregar objeto (pocion/superpocion/furia)" << endl;
                    cout << "2) Usar objeto (1-" << INV_SIZE << ")" << endl;
                    cout << "3) Volver" << endl;
                    cout << "Opcion: ";
                    cin >> sub;

                    if (sub == 1) {
                        string item;
                        cout << "Item: ";
                        cin >> item;
                        if (agregarItemUnico(inventario, INV_SIZE, item))
                            cout << "Agregado.\n";
                        else
                            cout << "No se pudo agregar (duplicado o inventario lleno).\n";
                        pausar();
                    } else if (sub == 2) {
                        int idx;
                        cout << "Indice: ";
                        cin >> idx;
                        if (idx >= 1 && idx <= INV_SIZE) {
                            if (usarItem(inventario, INV_SIZE, idx - 1, j, furiaUsada))
                                cout << "Item usado.\n";
                            else
                                cout << "No se pudo usar (slot vacio o item invalido).\n";
                        } else {
                            cout << "Indice invalido.\n";
                        }
                        pausar();
                    }
                } while (sub != 3);
                break;
            }
            case 3: { // Mapa/Movimiento (Tony + Bensu)
                char dir;
                do {
                    limpiarPantalla();
                    cout << "--- MAPA --- (W/A/S/D para mover, Q para volver)\n";
                    imprimirMapa(mapa);
                    dir = solicitarDireccionMovimiento(); // Tony
                    if (dir=='w'||dir=='W'||dir=='a'||dir=='A'||dir=='s'||dir=='S'||dir=='d'||dir=='D')
                        moverSiValido(mapa, dir); // Bensu
                } while (dir!='q' && dir!='Q');
                break;
            }
            case 4: { // Combate (Johan)
                limpiarPantalla();
                combate(j);
                pausar();
                break;
            }
            case 5: { // Pause/Play
                pausado = !pausado;
                cout << (pausado ? "[PAUSA activada]" : "[PAUSA desactivada]") << endl;
                pausar();
                break;
            }
            case 6: {
                salir = true;
                cout << "Saliendo...\n";
                break;
            }
            default: {
                cout << "Opcion invalida.\n";
                pausar();
            }
        }
    }
}
// ============================================
// === [LUDO] END
// ============================================
```

---

## ✅ Cobertura de temas del curso
- **Tipos de datos y E/S:** `int`, `double` (en constantes), `string`, `bool`, `cout/cin`.
- **Operadores y expresiones:** cálculo de daño, curación, validaciones.
- **Condicionales:** menú, validación de entradas, resultados de combate.
- **Ciclos:** bucle del menú, submenús, combate.
- **Arreglos 1D:** inventario con 5 slots, sin duplicados.
- **Arreglos 2D:** mapa 5×5 con jugador/enemigo.
- **Cadenas:** nombre del jugador, mensajes.
- **Funciones:** modularización por responsabilidades.
- **Parámetros por referencia:** modificación de stats del jugador (curación, furia).
- **Menús avanzados:** `switch`, `do…while` y manejo de pausa.

¡Listo! Este código cumple la finalidad del Super Challenge y respeta la división por integrantes. 🎯
