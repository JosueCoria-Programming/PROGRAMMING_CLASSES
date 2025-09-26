# Tema 1: Uso de Markdown

## Introducción
Markdown es un lenguaje de marcado ligero que se utiliza para dar formato a documentos de texto plano.  
Permite agregar títulos, listas, imágenes, tablas y bloques de código de forma sencilla.  
Se usa ampliamente en **GitHub** y en la documentación de proyectos.

## Demostración
Ejemplo de README básico en Markdown:

```markdown
# Mi Primer Proyecto en Markdown

> Usa este archivo como plantilla para tus tareas de la clase.

## Índice
- [Descripción](#descripción)
- [Instalación](#instalación)
- [Uso](#uso)
- [Ejemplo de código](#ejemplo-de-código)
- [Resultados esperados](#resultados-esperados)
- [Tabla de características](#tabla-de-características)
- [Tareas (checklist)](#tareas-checklist)
- [Créditos](#créditos)
- [Licencia](#licencia)
```

## Desafío
**Objetivo:** que los alumnos creen un archivo README.md con las siguientes secciones:
- Título del proyecto
- Descripción breve
- Pasos de instalación
- Uso del programa
- Ejemplo de salida
- Tabla de características
- Checklist de tareas

---

# Tema 2: Uso de GitHub

## Introducción
GitHub es una plataforma para gestionar proyectos con control de versiones (**Git**).  
Permite trabajar en equipo, subir código, llevar historial de cambios y documentar.

## Demostración
Pasos para crear un repositorio:

1. Inicia sesión en GitHub.
2. Haz clic en **New Repository**.
3. Escribe un nombre y una descripción.
4. Selecciona *Initialize with README*.
5. Realiza el primer commit.

## Desafío
**Objetivo:** que los alumnos creen un repositorio con un README.md inicial y lo suban a GitHub.

---

# Tema 3: ¿Qué es programar? + Diagramas de flujo

## Introducción
**Programar** es darle instrucciones a una computadora para resolver problemas.  
Un **algoritmo** es un conjunto de pasos finitos y ordenados que permiten obtener un resultado.  
Un **diagrama de flujo** es una representación gráfica de un algoritmo.

## Demostración
Ejemplo de algoritmo para sumar dos números (diagrama de flujo simple):
- Inicio
- Leer A y B
- Calcular C = A + B
- Mostrar C
- Fin

## Desafío
**Objetivo:** que los alumnos diseñen un diagrama de flujo que determine si alguien es mayor de edad.

---

# Tema 4: CLion y tu primer programa

## Introducción
CLion es un IDE que facilita escribir, compilar y depurar programas en C++.  
Un programa mínimo en C++ necesita:

- `#include <iostream>` → para usar entrada/salida.
- `using namespace std;` → para simplificar nombres.
- `int main()` → función principal.
- `cout` → mostrar datos en pantalla.

## Demostración
Código de “Hola mundo”:

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hola mundo!" << endl;
    return 0;
}
```

## Desafío
Pedir al usuario su nombre y mostrar un saludo.

---

# Tema 5: Tipos de datos y entrada/salida

## Introducción
En programación, los **tipos de datos** son las categorías que definen qué clase de valores puede almacenar una variable y qué operaciones podemos hacer con ella.

En C++ los principales son:
- **Enteros (`int`)** → números sin decimales (ej. 5, -12, 1000).
- **Decimales (`float` o `double`)** → números con decimales (ej. 3.14, -0.5).
    - `float`: precisión simple.
    - `double`: doble precisión, más exacto.
- **Carácter (`char`)** → un solo símbolo entre comillas simples (ej. `'a'`, `'7'`, `'#'`).
- **Cadena (`string`)** → texto más largo (ej. `"Hola"`, `"123abc"`).
- **Booleano (`bool`)** → solo dos valores: `true` o `false`.

📌 **Variables**  
Una variable es un espacio en memoria con un nombre donde guardamos un dato.  
Se declara con la forma:

```cpp
tipo nombre = valor_inicial;
```

Ejemplos:
```cpp
int edad = 20;
double pi = 3.1416;
char inicial = 'J';
string nombre = "Ana";
bool encendido = true;
```

📌 **Entrada y salida de datos**
- **Salida (`cout`)** → mostrar texto o valores.
```cpp
cout << "Hola mundo" << endl;
```  
- **Entrada (`cin`)** → leer información desde consola.
```cpp
cin >> edad;
```

## Demostración
Ejemplo en CLion: pedir al usuario su nombre y edad, y luego mostrar un mensaje.

```cpp
#include <iostream>
using namespace std;

int main() {
    string nombre;
    int edad;

    cout << "Escribe tu nombre: ";
    cin >> nombre;   // Entrada de cadena (sin espacios)

    cout << "Escribe tu edad: ";
    cin >> edad;     // Entrada de número entero

    cout << "Hola " << nombre << ", tienes " << edad << " años." << endl;
    return 0;
}
```

📌 **Explicación paso a paso:**
- `string nombre;` → guarda texto.
- `int edad;` → guarda número entero.
- `cin >> nombre;` → lee la entrada.
- `cout << ...;` → muestra el mensaje concatenado.

📌 **Nota:** `cin >> nombre` solo lee palabras sin espacios. Para frases completas se usa `getline(cin, nombre);`.

**Salida esperada en consola:**
```
Escribe tu nombre: Ana
Escribe tu edad: 22
Hola Ana, tienes 22 años.
```

## Desafío
**Objetivo:** practicar la declaración de variables, el uso de diferentes tipos de datos y el manejo de entrada/salida.

**Reto:** crea un programa que:
1. Pida al usuario:
    - Nombre (string)
    - Edad (int)
    - Altura (double)
    - Inicial de su apellido (char)
2. Muestre un mensaje como este:
```
Hola Ana, tienes 22 años.
Mides 1.65 metros y tu apellido empieza con 'G'.
```

**Ejemplo de salida esperada:**
```
Escribe tu nombre: Ana
Escribe tu edad: 22
Escribe tu altura en metros (ejemplo 1.65): 1.65
Escribe la inicial de tu apellido: G
Hola Ana, tienes 22 años.
Mides 1.65 metros y tu apellido empieza con 'G'.
```

---

# Tema 6: Operadores y expresiones

## Introducción
Un **operador** es un símbolo que indica realizar una operación sobre valores (operandos).  
Una **expresión** combina operandos y operadores para producir un resultado.

Tipos de operadores:
- **Aritméticos:** `+`, `-`, `*`, `/`, `%`
- **Relacionales:** `==`, `!=`, `<`, `>`, `<=`, `>=`
- **Lógicos:** `&&`, `||`, `!`
- **Asignación:** `=`, `+=`, `-=`, `*=`, `/=`, `%=`

Ejemplo de expresión:
```cpp
int resultado = (3 + 5) * 2; // resultado = 16
```

## Demostración
Ejemplo de programa usando operadores:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 3;

    cout << "a + b = " << (a + b) << endl;
    cout << "a - b = " << (a - b) << endl;
    cout << "a * b = " << (a * b) << endl;
    cout << "a / b = " << (a / b) << endl;
    cout << "a % b = " << (a % b) << endl;

    cout << "¿a > b? " << (a > b) << endl;
    cout << "¿a < b? " << (a < b) << endl;

    bool resultado = (a > 5 && b < 5);
    cout << "¿a > 5 Y b < 5? " << resultado << endl;

    return 0;
}
```

**Output esperado:**
```
a + b = 13
a - b = 7
a * b = 30
a / b = 3
a % b = 1
¿a > b? 1
¿a < b? 0
¿a > 5 Y b < 5? 1
```

📌 **Nota:** `1 = true`, `0 = false`.

## Desafío
**Objetivo:** practicar operadores aritméticos, relacionales y lógicos.

**Reto:** crea un programa que:
1. Pida dos enteros.
2. Calcule y muestre: suma, resta, multiplicación, división, módulo.
3. Compare e imprima: “primer mayor”, “segundo mayor” o “iguales”.
4. Evalúe condición lógica: “Ambos positivos” o “Al menos uno no positivo”.

**Ejemplo de salida:**
```
Ingresa el primer numero: 8
Ingresa el segundo numero: 3
Suma: 11
Resta: 5
Multiplicacion: 24
Division: 2
Modulo: 2
El primer numero es mayor.
Ambos numeros son positivos.
```

---

# Tema 7: Condicionales

## Introducción
Un **condicional** permite que el programa tome decisiones.

Tipos:
- `if`
- `if...else`
- `if...else if...else`
- `switch`

📌 **Regla:** las condiciones siempre se evalúan como `true (1)` o `false (0)`.

## Demostración
Ejemplo: verificar la edad.

```cpp
#include <iostream>
using namespace std;

int main() {
    int edad;
    cout << "Ingresa tu edad: ";
    cin >> edad;

    if (edad >= 18) {
        cout << "Eres mayor de edad" << endl;
    } else {
        cout << "Eres menor de edad" << endl;
    }

    return 0;
}
```

**Salida esperada:**
```
Ingresa tu edad: 20
Eres mayor de edad

Ingresa tu edad: 15
Eres menor de edad
```

## Desafío
**Objetivo:** practicar condicionales encadenados.

**Reto:** crea un programa que:
1. Pida una calificación 0–100.
2. Muestre:
    - 90–100 → Excelente
    - 70–89 → Aprobado
    - 0–69 → Reprobado
    - Otro → Inválido

**Salida esperada:**
```
Ingresa tu calificacion (0 - 100): 95
Excelente
```

**Errores comunes:**
- Usar varios `if` en lugar de `else if`.
- No validar rangos.

---

# Tema 8: Ciclos

## Introducción
Un **ciclo** permite repetir instrucciones.

Tipos:
- `while`
- `do...while`
- `for`

📌 **Diferencia clave:**
- `while`: repite mientras condición sea verdadera.
- `do...while`: ejecuta al menos una vez.
- `for`: repite un número de veces definido.

## Demostración
Ejemplo: mostrar 1–5 con todos los ciclos.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;

    cout << "Ejemplo con while:" << endl;
    while (i <= 5) {
        cout << i << " ";
        i++;
    }

    cout << endl << "Ejemplo con do...while:" << endl;
    int j = 1;
    do {
        cout << j << " ";
        j++;
    } while (j <= 5);

    cout << endl << "Ejemplo con for:" << endl;
    for (int k = 1; k <= 5; k++) {
        cout << k << " ";
    }

    return 0;
}
```

**Salida esperada:**
```
Ejemplo con while:
1 2 3 4 5
Ejemplo con do...while:
1 2 3 4 5
Ejemplo con for:
1 2 3 4 5
```

## Desafío
**Objetivo:** practicar los tres tipos de ciclos.

**Reto:** crea un programa que:
1. Pida un número positivo N.
2. Muestre números de 1 a N con `for`.
3. Calcule la suma 1–N con `while`.
4. Pregunte repetir con `do...while`.

**Ejemplo de salida esperada:**
```
Ingresa un numero positivo: 5
Numeros del 1 al 5:
1 2 3 4 5
La suma de 1 hasta 5 es: 15
¿Quieres repetir el programa? (S/N): N
```

**Errores comunes:**
- Ciclos infinitos (olvidar `i++`).
- Condiciones mal escritas.
- No validar entrada.

---

# Tema 9: Arreglos unidimensionales

## Introducción
Un **arreglo** (array o vector) es una colección de datos del mismo tipo, almacenados de manera contigua en memoria y accesibles mediante un índice.

📌 **Características principales:**
- Todos los elementos son del mismo tipo de dato.
- El índice empieza en **0**.
- Se pueden recorrer con ciclos (`for`, `while`).

**Declaración:**
```cpp
tipo nombre[tamaño];
```

Ejemplo:
```cpp
int numeros[5];   // arreglo de 5 enteros
```

**Inicialización:**
```cpp
int numeros[5] = {10, 20, 30, 40, 50};
```

**Acceso a elementos:**
```cpp
cout << numeros[0];   // imprime 10
cout << numeros[4];   // imprime 50
```

📌 Importante: acceder a un índice fuera del rango provoca errores o comportamientos inesperados.

## Demostración
Ejemplo: guardar y mostrar 5 números enteros.

```cpp
#include <iostream>
using namespace std;

int main() {
    int numeros[5];  // arreglo de 5 enteros

    // Guardar valores
    numeros[0] = 10;
    numeros[1] = 20;
    numeros[2] = 30;
    numeros[3] = 40;
    numeros[4] = 50;

    // Mostrar valores
    cout << "Contenido del arreglo:" << endl;
    for (int i = 0; i < 5; i++) {
        cout << "Elemento " << i << ": " << numeros[i] << endl;
    }

    return 0;
}
```

**Salida esperada:**
```
Contenido del arreglo:
Elemento 0: 10
Elemento 1: 20
Elemento 2: 30
Elemento 3: 40
Elemento 4: 50
```

## Desafío
**Objetivo:** practicar cómo declarar un arreglo, llenarlo con datos ingresados por el usuario y recorrerlo con un ciclo.

**Reto:** crea un programa que:
1. Declare un arreglo de 5 enteros.
2. Pida al usuario que ingrese 5 números.
3. Guarde cada número en el arreglo.
4. Muestre todos los números ingresados.
5. Calcule y muestre el promedio.

**Ejemplo de salida esperada:**
```
Ingresa 5 numeros:
Numero 1: 10
Numero 2: 20
Numero 3: 30
Numero 4: 40
Numero 5: 50
Los numeros ingresados son: 10 20 30 40 50
El promedio es: 30
```

**Errores comunes:**
- Usar índices incorrectos.
- No inicializar variables.
- Confundir número de elementos con índice máximo.

---

# Tema 10: Arreglos bidimensionales

## Introducción
Un **arreglo bidimensional** (matriz) es como una tabla de filas y columnas con datos del mismo tipo.

📌 **Características:**
- Declaración con dos dimensiones (filas y columnas).
- Se accede con dos índices `[fila][columna]`.
- Índices inician en 0.

**Ejemplo de declaración:**
```cpp
int matriz[3][2];   // 3 filas, 2 columnas
```

**Inicialización:**
```cpp
int matriz[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

**Acceso a elementos:**
```cpp
cout << matriz[0][0];   // imprime 1
cout << matriz[1][2];   // imprime 6
```

📌 Se recorren con dos ciclos anidados.

## Demostración
Ejemplo: llenar una matriz de 2x3 con números y mostrarla.

```cpp
#include <iostream>
using namespace std;

int main() {
    int matriz[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    cout << "Contenido de la matriz:" << endl;
    for (int i = 0; i < 2; i++) {          // recorre filas
        for (int j = 0; j < 3; j++) {      // recorre columnas
            cout << matriz[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

**Salida esperada:**
```
Contenido de la matriz:
1 2 3
4 5 6
```

## Desafío
**Objetivo:** practicar creación y recorrido de matrices.

**Reto:** crea un programa que:
1. Declare una matriz de 3x3.
2. Pida al usuario los 9 valores.
3. Muestre la matriz en forma de tabla.
4. Calcule la suma de todos los elementos.

**Ejemplo de salida esperada:**
```
Matriz ingresada:
1 2 3
4 5 6
7 8 9

La suma total de los elementos es: 45
```

**Errores comunes:**
- Confundir orden de índices.
- No reiniciar acumuladores.
- No usar ciclos anidados.

---

# Tema 11: Cadenas

## Introducción
Una **cadena** (`string`) es una secuencia de caracteres.

Ejemplos: `"Hola"`, `"12345"`, `"Programar es divertido!"`.

En C++ podemos usar:
- **string** (más moderno y recomendado).
- **char[]** (forma clásica en C).

📌 **Operaciones comunes:**
- Concatenar:
```cpp
string saludo = "Hola " + nombre;
```  
- Longitud:
```cpp
cout << saludo.length();
```  
- Acceso a carácter:
```cpp
cout << saludo[0]; // primer carácter
```  

📌 **Entrada de cadenas:**
- `cin >> nombre;` → solo una palabra.
- `getline(cin, nombre);` → una línea completa (con espacios).

## Demostración
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string nombre;
    cout << "Escribe tu nombre completo: ";
    getline(cin, nombre);

    cout << "Hola, " << nombre << "! Bienvenido." << endl;
    cout << "Tu nombre tiene " << nombre.length() << " caracteres." << endl;
    cout << "La primera letra es: " << nombre[0] << endl;

    return 0;
}
```

**Ejemplo de salida:**
```
Escribe tu nombre completo: Ana Lopez
Hola, Ana Lopez! Bienvenido.
Tu nombre tiene 9 caracteres.
La primera letra es: A
```

## Desafío
**Objetivo:** practicar lectura de cadenas, longitud, acceso a caracteres y concatenación.

**Reto:** crea un programa que:
1. Pida nombre completo.
2. Pida ciudad favorita.
3. Muestre información en varias líneas:
```
Hola, [nombre].
Tu nombre tiene [X] caracteres.
La primera letra es [letra].
Tu ciudad favorita es [ciudad].
```

**Errores comunes:**
- Usar `cin >>` cuando se necesita capturar espacios.
- No incluir `<string>`.

---

# Tema 12: Funciones

## Introducción
Una **función** es un bloque de código que realiza una tarea.  
Permite reutilizar código, organizar programas y facilitar depuración.

**Estructura:**
```cpp
tipo_retorno nombre(parámetros) {
    // instrucciones
    return valor; // si no es void
}
```

Ejemplo:
```cpp
int sumar(int a, int b) { return a + b; }
void saludar() { cout << "Hola"; }
```

## Demostración
```cpp
#include <iostream>
using namespace std;

// Función que suma dos enteros
int sumar(int a, int b) { return a + b; }

// Función que muestra saludo
void saludar() { cout << "Bienvenido!" << endl; }

int main() {
    saludar();
    int x = 5, y = 7;
    cout << "La suma es: " << sumar(x,y) << endl;
    return 0;
}
```

**Salida esperada:**
```
Bienvenido!
La suma es: 12
```

## Desafío
**Objetivo:** entender funciones con y sin retorno.

**Reto:** crea un programa que:
1. Tenga una función `calcularAreaRectangulo(base, altura)`.
2. Tenga una función `mostrarResultado(area)`.
3. Pida base y altura al usuario.
4. Muestre el área.

**Ejemplo de salida:**
```
Base: 5
Altura: 3
El area es: 15
```

**Errores comunes:**
- Olvidar tipo de retorno.
- Llamar funciones antes de declararlas.

---

# Tema 13: Parámetros y ámbito (Paso por valor y referencia)

## Introducción
Cuando usamos funciones, podemos enviarles datos a través de parámetros.  
La forma en que esos parámetros son recibidos en la función afecta cómo se comportan las variables.

### 📌 Paso por valor
- Se envía **una copia** del dato a la función.
- Si la función lo modifica, el valor original **no cambia**.

```cpp
void duplicar(int x) {
    x = x * 2;   // solo cambia dentro de la función
}
```

### 📌 Paso por referencia
- Se envía la **dirección de memoria** del dato.
- Si la función lo modifica, el valor original **sí cambia**.

En C++ se indica con el símbolo `&`.

```cpp
void duplicar(int &x) {
    x = x * 2;   // cambia el valor original
}
```

### 📌 Ámbito (scope)
El ámbito define dónde existe una variable:
- **Local:** solo existe dentro de una función o bloque.
- **Global:** definida fuera de cualquier función, accesible desde todo el programa.

## Demostración
Ejemplo comparando paso por valor y paso por referencia:

```cpp
#include <iostream>
using namespace std;

void porValor(int x) {
    x = x + 10;
    cout << "Dentro de la funcion (por valor): " << x << endl;
}

void porReferencia(int &x) {
    x = x + 10;
    cout << "Dentro de la funcion (por referencia): " << x << endl;
}

int main() {
    int numero = 5;

    porValor(numero);
    cout << "Despues de funcion porValor: " << numero << endl;

    porReferencia(numero);
    cout << "Despues de funcion porReferencia: " << numero << endl;

    return 0;
}
```

**Salida esperada:**
```
Dentro de la funcion (por valor): 15
Despues de funcion porValor: 5
Dentro de la funcion (por referencia): 15
Despues de funcion porReferencia: 15
```

📌 Observa:
- Con paso por valor, el número en `main()` no cambia.
- Con paso por referencia, sí cambia.

## Desafío
**Objetivo del desafío:** que el alumno entienda la diferencia entre paso por valor y paso por referencia, y cómo afecta a las variables.

**Reto:** crea un programa que:
1. Defina una función `intercambiarPorValor(int a, int b)` que intente intercambiar dos números (usando paso por valor).
2. Defina otra función `intercambiarPorReferencia(int &a, int &b)` que realmente los intercambie.
3. Desde `main()`, pida al usuario dos números y pruebe ambas funciones.

**Ejemplo de salida esperada:**
```
Ingresa el primer numero: 4
Ingresa el segundo numero: 7

Intento de intercambio por valor...
Resultado: x = 4, y = 7

Intercambio por referencia...
Resultado: x = 7, y = 4
```

**Errores comunes a evitar:**
- Olvidar el `&` en paso por referencia.
- Intentar devolver cambios de una función por valor y esperar que se guarden.
- Confundir variables locales con globales.

---

# Tema 14: Menús avanzados (Uso de funciones + estructuras de menú)

## Introducción
En muchos programas necesitamos dar al usuario varias opciones para elegir qué acción realizar.  
La forma más común es un **menú interactivo**, donde el usuario selecciona una opción escribiendo un número o una letra.

### 📌 Características de un menú avanzado
- Se organiza en forma de lista (1, 2, 3, …).
- Se repite hasta que el usuario elija “Salir”.
- Cada opción se implementa como una función independiente.
- Usa ciclos y condicionales para controlar el flujo.

**Estructura general de un menú en C++:**
1. Mostrar opciones en pantalla.
2. Leer la opción del usuario.
3. Usar `switch` o `if` para decidir qué acción ejecutar.
4. Repetir el proceso hasta que se elija salir.

## Demostración
Ejemplo de un menú simple con funciones:

```cpp
#include <iostream>
using namespace std;

void saludar() {
    cout << "Hola! Bienvenido al programa." << endl;
}

void mostrarFecha() {
    cout << "Hoy es un gran dia para programar! :)" << endl;
}

int main() {
    int opcion;
    do {
        cout << "\n--- MENU PRINCIPAL ---" << endl;
        cout << "1. Saludar" << endl;
        cout << "2. Mostrar fecha (ejemplo)" << endl;
        cout << "3. Salir" << endl;
        cout << "Elige una opcion: ";
        cin >> opcion;

        switch (opcion) {
            case 1: saludar(); break;
            case 2: mostrarFecha(); break;
            case 3: cout << "Saliendo del programa..." << endl; break;
            default: cout << "Opcion no valida!" << endl;
        }
    } while (opcion != 3);

    return 0;
}
```

**Salida esperada (ejemplo):**
```
--- MENU PRINCIPAL ---
1. Saludar
2. Mostrar fecha (ejemplo)
3. Salir
Elige una opcion: 1
Hola! Bienvenido al programa.

--- MENU PRINCIPAL ---
1. Saludar
2. Mostrar fecha (ejemplo)
3. Salir
Elige una opcion: 3
Saliendo del programa...
```

## Desafío
**Objetivo del desafío:** que el alumno diseñe un menú avanzado usando funciones, donde cada opción realice una acción distinta y el programa se repita hasta que el usuario decida salir.

**Reto:** crea un programa que muestre un menú con estas opciones:
1. Calcular el cuadrado de un número (usar función).
2. Calcular el promedio de 3 números (usar función).
3. Mostrar un mensaje personalizado (usar función).
4. Salir.

El menú debe repetirse hasta que el usuario elija la opción 4.

**Ejemplo de salida esperada:**
```
--- MENU AVANZADO ---
1. Calcular el cuadrado de un numero
2. Calcular el promedio de 3 numeros
3. Mostrar mensaje
4. Salir
Elige una opcion: 1
Ingresa un numero: 6
El cuadrado de 6 es 36

--- MENU AVANZADO ---
1. Calcular el cuadrado de un numero
2. Calcular el promedio de 3 numeros
3. Mostrar mensaje
4. Salir
Elige una opcion: 4
Saliendo del programa...
```

**Errores comunes a evitar:**
- No validar entradas (ej. letras en lugar de números).
- Escribir todo el código en `main()` sin funciones.
- Olvidar `break;` en cada `case`.

---
