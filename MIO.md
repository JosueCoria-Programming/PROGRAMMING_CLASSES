# 📘 Guía del Profesor - Introducción a la Programación en C++

Este documento es tu guía detallada para impartir las clases. Incluye **tema, explicación clara, ejemplos de código y código de los ejercicios**.

---

## Semana 1 - Clase 1: ¿Qué es programar?
**Tema:** Concepto de programación y algoritmos.  
**Explicación:** Programar es dar instrucciones paso a paso a una computadora. Los algoritmos son recetas que resuelven problemas.  

**Ejemplo de código:** *(No aplica, clase conceptual)*

**Ejercicio:** Algoritmo en texto para preparar una bebida.  
**Código:** *(No aplica)*

---

## Semana 1 - Clase 2: CLion y tu primer programa
**Tema:** Instalación y programa básico.  
**Explicación:** Todo programa en C++ inicia con `main()`. La salida se imprime con `cout`.  

**Ejemplo de código:**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hola, mundo!" << endl;
    return 0;
}
```

**Ejercicio:** Programa que imprima nombre, edad y ciudad.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Mi nombre es Ana, tengo 20 años y vivo en CDMX." << endl;
    return 0;
}
```

---

## Semana 2 - Clase 3: Tipos de datos y entrada/salida
**Tema:** Variables y uso de `cin` y `cout`.  
**Explicación:** Existen distintos tipos: `int`, `float`, `string`, `char`. `cin` captura entrada del usuario.  

**Ejemplo de código:**
```cpp
int edad = 20;
float promedio = 8.5;
string nombre = "Ana";
cout << nombre << " tiene " << edad << " años." << endl;
```

**Ejercicio:** Pedir nombre, edad y calificación, mostrar mensaje.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    string nombre;
    int edad;
    float calificacion;

    cout << "Ingresa tu nombre: ";
    cin >> nombre;
    cout << "Ingresa tu edad: ";
    cin >> edad;
    cout << "Ingresa tu calificación: ";
    cin >> calificacion;

    cout << "Hola " << nombre << ", tienes " << edad << " años y tu calificación es " << calificacion << endl;
    return 0;
}
```

---

## Semana 3 - Clase 4: Operadores y expresiones
**Tema:** Operadores aritméticos y comparativos.  
**Explicación:** Permiten cálculos (`+,-,*,/,%`) y comparaciones (`>,<,==,!=`).  

**Ejemplo de código:**
```cpp
int a = 10, b = 3;
cout << "Suma: " << a + b << endl;
cout << "Comparación: " << (a > b) << endl; // 1 = verdadero
```

**Ejercicio:** Recibir 3 números, calcular promedio y mayor.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b, c;
    cout << "Ingresa tres números: ";
    cin >> a >> b >> c;

    float promedio = (a + b + c) / 3.0;
    int mayor = a;
    if (b > mayor) mayor = b;
    if (c > mayor) mayor = c;

    cout << "Promedio: " << promedio << endl;
    cout << "El mayor es: " << mayor << endl;
    return 0;
}
```

---

## Semana 4 - Clase 5: Condicionales
**Tema:** `if`, `else`, `switch`.  
**Explicación:** Sirven para tomar decisiones según condiciones lógicas.  

**Ejemplo de código:**
```cpp
int num = 5;
if (num % 2 == 0) cout << "Es par";
else cout << "Es impar";
```

**Ejercicio:** Verificar par/impar, positivo/negativo y rango.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    cout << "Ingresa un número: ";
    cin >> num;

    if (num % 2 == 0) cout << "El número es par" << endl;
    else cout << "El número es impar" << endl;

    if (num >= 0) cout << "El número es positivo" << endl;
    else cout << "El número es negativo" << endl;

    if (num < 0) cout << "Rango: menor que 0";
    else if (num <= 10) cout << "Rango: entre 0 y 10";
    else cout << "Rango: mayor que 10";

    return 0;
}
```

---

## Semana 5 - Clase 6: Ciclos
**Tema:** `for`, `while`, `do while`.  
**Explicación:** Permiten ejecutar instrucciones repetidamente.  

**Ejemplo de código:**
```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
```

**Ejercicio:** Menú con sumar, restar y salir.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int opcion;
    do {
        cout << "--- Menú ---\n1. Sumar\n2. Restar\n3. Salir\nOpción: ";
        cin >> opcion;

        if (opcion == 1) {
            int x, y;
            cout << "Ingresa dos números: ";
            cin >> x >> y;
            cout << "Resultado: " << x + y << endl;
        } else if (opcion == 2) {
            int x, y;
            cout << "Ingresa dos números: ";
            cin >> x >> y;
            cout << "Resultado: " << x - y << endl;
        }
    } while (opcion != 3);

    return 0;
}
```

---

## Semana 6 - Proyecto Módulo 1: *Adivina el número*
**Tema:** Uso de ciclos, condicionales y generación aleatoria.  
**Explicación:** Se genera un número aleatorio y el usuario debe adivinarlo con pistas.

**Ejemplo de código:**
```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main() {
    srand(time(0));
    int numeroSecreto = rand() % 100 + 1;
    int intento, contador = 0;

    do {
        cout << "Adivina el número (1-100): ";
        cin >> intento;
        contador++;
        if (intento > numeroSecreto) cout << "El número es menor" << endl;
        else if (intento < numeroSecreto) cout << "El número es mayor" << endl;
    } while (intento != numeroSecreto);

    cout << "¡Correcto! Lo adivinaste en " << contador << " intentos." << endl;
    return 0;
}
```

---

## Semana 7 - Clase 7: Arreglos unidimensionales
**Tema:** Listas de datos.  
**Explicación:** Un arreglo almacena múltiples valores del mismo tipo.  

**Ejemplo de código:**
```cpp
int numeros[5] = {1,2,3,4,5};
for (int i = 0; i < 5; i++) {
    cout << numeros[i] << " ";
}
```

**Ejercicio:** Guardar 10 enteros y mostrar su promedio.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int numeros[10];
    int suma = 0;
    for (int i = 0; i < 10; i++) {
        cout << "Ingresa número " << i+1 << ": ";
        cin >> numeros[i];
        suma += numeros[i];
    }
    cout << "Promedio: " << suma / 10.0 << endl;
    return 0;
}
```

---

## Semana 8 - Clase 8: Arreglos bidimensionales
**Tema:** Matrices.  
**Explicación:** Una matriz es una tabla con filas y columnas.  

**Ejemplo de código:**
```cpp
int matriz[2][2] = {{1,2},{3,4}};
cout << matriz[0][0]; // Imprime 1
```

**Ejercicio:** Crear una matriz 3x3, imprimir diagonal y suma total.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int matriz[3][3];
    int suma = 0;
    cout << "Ingresa valores para la matriz 3x3:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cin >> matriz[i][j];
            suma += matriz[i][j];
        }
    }
    cout << "Diagonal: ";
    for (int i = 0; i < 3; i++) cout << matriz[i][i] << " ";
    cout << "\nSuma total: " << suma << endl;
    return 0;
}
```

---

## Semana 9 - Clase 9: Cadenas
**Tema:** Uso de `string`.  
**Explicación:** `string` permite manipular texto completo.  

**Ejemplo de código:**
```cpp
string saludo = "Hola";
string nombre = "Ana";
cout << saludo + " " + nombre;
```

**Ejercicio:** Pedir nombre y apellido, mostrar saludo completo.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

int main() {
    string nombre, apellido;
    cout << "Ingresa tu nombre: ";
    cin >> nombre;
    cout << "Ingresa tu apellido: ";
    cin >> apellido;
    cout << "Hola " << nombre << " " << apellido << ", bienvenido al curso." << endl;
    return 0;
}
```

---

## Semana 10 - Clase 10: Funciones
**Tema:** Modularidad y reutilización.  
**Explicación:** Una función encapsula instrucciones que pueden reutilizarse.  

**Ejemplo de código:**
```cpp
int suma(int a, int b) {
    return a + b;
}
```

**Ejercicio:** Calcular área de triángulo con función.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

float areaTriangulo(float base, float altura) {
    return (base * altura) / 2;
}

int main() {
    float base, altura;
    cout << "Base: ";
    cin >> base;
    cout << "Altura: ";
    cin >> altura;
    cout << "Área: " << areaTriangulo(base, altura) << endl;
    return 0;
}
```

---

## Semana 11 - Clase 11: Parámetros y ámbito
**Tema:** Paso por valor y referencia.  
**Explicación:** Paso por valor copia el dato, paso por referencia lo modifica directamente.  

**Ejemplo de código:**
```cpp
void intercambiar(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}
```

**Ejercicio:** Función que intercambie dos números.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

void intercambiar(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 5, y = 10;
    cout << "Antes: x=" << x << ", y=" << y << endl;
    intercambiar(x, y);
    cout << "Después: x=" << x << ", y=" << y << endl;
    return 0;
}
```

---

## Semana 12 - Clase 12: Menús avanzados
**Tema:** Uso de funciones + estructuras de menú.  
**Explicación:** Combina funciones, condicionales y ciclos para navegar opciones.  

**Ejemplo de código:**
```cpp
void mostrarInfo() {
    cout << "Programa versión 1.0" << endl;
}
```

**Ejercicio:** Menú con 3 opciones: calcular área, mostrar info, salir.  
**Código del ejercicio:**
```cpp
#include <iostream>
using namespace std;

float area(float base, float altura) {
    return base * altura / 2;
}

int main() {
    int opcion;
    do {
        cout << "1. Calcular área\n2. Mostrar info\n3. Salir\nOpción: ";
        cin >> opcion;
        if (opcion == 1) {
            float b, h;
            cout << "Base: ";
            cin >> b;
            cout << "Altura: ";
            cin >> h;
            cout << "Área: " << area(b,h) << endl;
        } else if (opcion == 2) {
            cout << "Información del programa: versión 1.0" << endl;
        }
    } while (opcion != 3);
    return 0;
}
```

---

## Semana 13 - Proyecto Módulo 2: *Sistema de puntuación*
**Tema:** Uso combinado de arreglos, funciones y menús.  
**Explicación:** Se registran jugadores, se simulan turnos y se determina un ganador.

**Ejemplo de código simplificado:**
```cpp
string jugadores[2] = {"Ana", "Luis"};
int puntos[2] = {50,30};
cout << "Ganador: " << jugadores[0];
```

**Ejercicio:** Sistema completo con menú.  
**Código del ejercicio:** *(más extenso, se construye en clase)*

---

## Semana 14 - Clase 13: Repaso general
**Tema:** Reforzamiento de conceptos.  
**Ejercicio:** Invertir arreglo, buscar número y calcular promedio.  
**Código del ejercicio:** *(resolver en clase con participación de alumnos)*

---

## Semana 14 - Clase 14: Taller de depuración
**Tema:** Identificar y corregir errores.  
**Ejercicio:** Tomar un programa anterior, corregir errores y mejorar.  
**Código del ejercicio:** *(depende del programa elegido)*

---

## Semana 15 - Clase 15: Desarrollo de minijuego
**Tema:** Diseño de un prototipo de videojuego en consola.  
**Ejemplo de código:** Trivia básica.
```cpp
cout << "Pregunta: ¿Capital de Francia?\n1. Madrid\n2. París\n3. Roma";
```

**Ejercicio:** Implementar prototipo de trivia o combate por turnos.  
**Código del ejercicio:** *(a definir según elección del grupo)*

---

## Semana 16 - Clase 16: Presentación del proyecto final
**Tema:** Exposición del minijuego completo.  
**Explicación:** Se integran todos los conceptos vistos durante el cuatrimestre.  
**Entrega:** Código completo en GitHub + README con instrucciones y captura de pantalla.

---

✅ Con esta guía tienes explicación, ejemplos y código para todos los temas del cuatrimestre.
