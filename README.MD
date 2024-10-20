[1. Estructura básica de un programa en C](#1)

[2. Tipos de datos básicos](#2)

[3. Modificadores de tipo](#3)

[4. Operadores básicos](#4)

[5. Control de flujo](#5)

[6. Funciones](#6)

[7. Arreglos](#7)

[8. Punteros](#8)

[9. E/S básica](#9)

[10. Estructuras (struct)](#10)

[11. Manejo de memoria dinámica](#11)

[12. Archivos](#12)

[13. Macros y constantes](#13)

[14. Manejo de errores con errno](#14)

[15. Compilación](#15)

[16. Bibliotecas estándar útiles](#16)




<div id='1'></div>

# 1. Estructura básica de un programa en C:

Todo programa en C sigue una estructura básica, que incluye la inclusión de bibliotecas necesarias y la definición de una función principal, main(). Esta es la función que se ejecuta primero cuando comienza el programa.

```c
#include <stdio.h>    // Librería estándar para entrada/salida

int main() {
    // Código aquí
    return 0;
}
```
- `#include <stdio.h>`: Esta línea incluye la biblioteca estándar de C, que contiene funciones para operaciones de entrada y salida, como `printf()` y `scanf()`. Dependiendo de tus necesidades, puedes incluir otras bibliotecas como `<math.h>` para funciones matemáticas o `<string.h>` para manipulación de cadenas.

- `int main()`: La función `main()` es el punto de entrada de todo programa en C. Cuando ejecutas tu programa, el código dentro de esta función es lo primero que se ejecuta.

- `return 0;`: Esto indica que el programa finalizó correctamente. Retornar un valor en la función `main()` es opcional en algunos compiladores modernos, pero es una buena práctica.


<div id='2'></div>

# 2. Tipos de datos básicos:

El lenguaje C cuenta con una serie de tipos de datos primitivos que puedes utilizar para almacenar valores. Los tipos de datos varían en tamaño y rango, lo cual es importante para la optimización del uso de memoria.

| Tipo     | Tamaño (bits) | Rango |
|----------|---------------|-------|
| `int`    | 16/32         | -32,768 a 32,767 (16 bits) / -2,147,483,648 a 2,147,483,647 (32 bits) |
| `float`  | 32            | Aproximadamente 3.4E-38 a 3.4E+38 |
| `double` | 64            | Aproximadamente 1.7E-308 a 1.7E+308 |
| `char`   | 8             | 0 a 255 (sin signo) o -128 a 127 (con signo) |
| `void`   | -             | No tiene valor, se usa en funciones que no devuelven un valor | 

- `int`: Se usa para almacenar números enteros. El tamaño de int depende de la arquitectura de la máquina (16 o 32 bits).
- `float`: Almacena números de coma flotante de precisión simple (32 bits).
- `double`: Almacena números de coma flotante de doble precisión (64 bits), útil cuando se requiere más exactitud.
- `char`: Utilizado para almacenar caracteres simples o enteros pequeños. Normalmente ocupa 1 byte.
- `void`: No almacena valores, y se usa en funciones que no necesitan devolver ningún valor.

<div id='3'></div>

# 3. Modificadores de tipo:

Los modificadores de tipo se utilizan para alterar el rango y las propiedades de los tipos de datos básicos. Algunos ejemplos son `short`, `long`, `signed`, y `unsigned`.

- `short`: Limita el rango de enteros, reduciendo el tamaño de almacenamiento. Por ejemplo, short int normalmente tiene un rango menor que int.

- `long`: Aumenta el rango de enteros, útil para números grandes. Ejemplo: long int o long long int.

- `unsigned`: Hace que un tipo de dato solo acepte números positivos. Por ejemplo, unsigned int puede almacenar solo números positivos y extender el rango positivo al eliminar los números negativos.

```c
unsigned int x = 50000;  // Solo números positivos
long long int y = 100000000000;  // Gran rango de números enteros
```

<div id='4'></div>

# 4. Operadores básicos:
C utiliza una variedad de operadores para realizar cálculos y comparaciones entre valores. Estos operadores son similares a los encontrados en otros lenguajes de programación.
| Operador  | Descripción                   | Ejemplo   |
|-----------|-------------------------------|-----------|
| `+`       | Suma                          | `a + b`   |
| `-`       | Resta                         | `a - b`   |
| `*`       | Multiplicación                | `a * b`   |
| `/`       | División                      | `a / b`   |
| `%`       | Módulo                        | `a % b`   |
| `++`      | Incremento                    | `a++`     |
| `--`      | Decremento                    | `a--`     |
| `==`      | Igualdad                      | `a == b`  |
| `!=`      | Desigualdad                   | `a != b`  |
| `> / <`   | Mayor / Menor que             | `a > b`   |
| `>= / <=` | Mayor o igual / Menor o igual | `a<=b`    |



<div id='5'></div>

# 5. Control de flujo:
Los bloques de control de flujo permiten alterar la secuencia en que se ejecutan las instrucciones en un programa.

- <b>Condicionales:</b>
Los condicionales son fundamentales para decidir si ejecutar o no un bloque de código basado en ciertas condiciones.

    - `if`, `else if`, `else`:
        ```c
        if (condicion) {
            // Se ejecuta si la condición es verdadera
        } else if (otra_condicion) {
            // Se ejecuta si otra_condicion es verdadera
        } else {
            // Se ejecuta si ninguna condición es verdadera
        }
        ```

    - `Switch-case`:
    El switch-case es útil cuando se tienen múltiples opciones y deseas evitar una larga cadena de if-else.
        ```c
        int opcion = 2;
        switch (opcion) {
            case 1:
                printf("Caso 1\n");
                break;
            case 2:
                printf("Caso 2\n");
                break;
            default:
                printf("Opción no válida\n");
        }
        ```

- <b>Bucles:</b>
Los bucles permiten ejecutar repetidamente un bloque de código.

    - `while`: Ejecuta el bloque de código mientras la condición sea verdadera.
        ```c
        int i = 0;
        while (i < 10) {
            printf("%d\n", i);
            i++;
        }
        ```

    - `do-while`: Similar a while, pero ejecuta el bloque al menos una vez antes de verificar la condición.
        ```c
        int i = 0;
        do {
            printf("%d\n", i);
            i++;
        } while (i < 10);
        ```

    - `for`: Útil cuando se conoce el número exacto de iteraciones. Combina inicialización, condición, e incremento en una sola línea.
        ```c
        for (int i = 0; i < 10; i++) {
            printf("%d\n", i);
        }
        ```


<div id='6'></div>

# 6. Funciones:
Las funciones permiten dividir el código en bloques reutilizables. Cada función tiene un tipo de retorno y puede aceptar parámetros de entrada.
```c
tipo_retorno nombre_funcion(tipo1 arg1, tipo2 arg2) {
    // Cuerpo de la función
    return valor; // Si tipo_retorno no es void
}
```
<b>Ejemplo:</b>

```c
int sumar(int a, int b) {
    return a + b;
}

int main() {
    int resultado = sumar(5, 10);
    printf("Resultado: %d", resultado);
}
```

- <b>Parámetros:</b> Son las entradas que la función espera. En este caso, `sumar()` recibe dos enteros y devuelve su suma.
- <b>Tipo de retorno:</b> En este ejemplo, el tipo de retorno es `int`, ya que la función devuelve un número entero.


<div id='7'></div>

# 7. Arreglos:

Los arreglos son colecciones de datos del mismo tipo almacenados en ubicaciones de memoria consecutivas.
- <b>Unidimensionales:</b>
Los arreglos unidimensionales son simples listas de elementos.
    ```c
    int numeros[5] = {1, 2, 3, 4, 5};    // Declaración e inicialización
    ```
    <b>Acceso a elementos:</b> Los elementos de un arreglo se acceden mediante índices, comenzando desde 0.
    ```c
    printf("%d", numeros[0]);  // Imprime el primer elemento (1)
    ```



- <b>Multidimensionales:</b>
Los arreglos multidimensionales permiten crear estructuras más complejas, como matrices.
    ```c
    int matriz[2][3] = {{1, 2, 3}, {4, 5, 6}};
    ```


<div id='8'></div>

# 8. Punteros:
Un puntero es una variable que almacena la dirección de otra variable. Son una característica fundamental de C y permiten manipular directamente la memoria.

<b>Declaración y uso:</b>
```c
int x = 10;
int *p = &x;    // p apunta a la dirección de x

printf("%d", *p);  // Imprime el valor de x (10)
```

- `&x`: El operador `&` obtiene la dirección de la variable `x`.
- `*p`: El operador `*` accede al valor almacenado en la dirección a la que apunta el puntero `p`.

<b>Punteros y funciones:</b>
Los punteros se usan para pasar variables por referencia a funciones, lo que permite modificar el valor de las variables originales.

```c
void cambiar_valor(int *p) {
    *p = 20;    // Cambia el valor de la variable que apunta p
}
```


<div id='9'></div>

# 9. E/S básica:
C ofrece funciones estándar para realizar operaciones de entrada y salida, como leer del teclado y escribir en la pantalla.

<b>Impresión en pantalla con `printf`:</b>
```c
printf("Hola, %s! Tienes %d años.\n", "Mundo", 25);
```

- `%d`: Especifica que el valor es un entero.
- `%s`: Especifica que el valor es una cadena de caracteres (string).



<b>Lectura desde el teclado con `scanf`:</b>
```c
int edad;
scanf("%d", &edad);
```
`scanf` permite leer datos desde el teclado y almacenarlos en una variable. Es importante usar el símbolo `&` para pasar la dirección de la variable donde se almacenará el valor.



<div id='10'></div>

# 10. Estructuras (`struct`):
Una estructura (`struct`) permite agrupar varios tipos de datos bajo un mismo nombre.

<b>Declaración de una estructura:</b>
```c
struct Persona {
    char nombre[50];
    int edad;
};
```

<b>Uso de estructuras:</b>
```c
struct Persona p1 = {"Juan", 25};
printf("%s tiene %d años.", p1.nombre, p1.edad);
```

<div id='11'></div>

# 11. Manejo de memoria dinámica:
C proporciona funciones para gestionar la memoria de manera dinámica, lo que permite asignar y liberar memoria durante la ejecución del programa.

- `malloc`: Reserva un bloque de memoria del tamaño especificado.
- `free`: Libera el bloque de memoria previamente asignado.
```c
int *p = (int*) malloc(5 * sizeof(int));  // Asignar memoria para 5 enteros
if (p == NULL) {
    printf("Error de asignación de memoria.");
}
free(p);  // Liberar la memoria asignada
```


<div id='12'></div>

# 12. Archivos

El lenguaje C también permite trabajar con archivos, abriéndolos, escribiendo en ellos y leyendo de ellos.

<b>Apertura y cierre de archivos:</b>
```c
FILE *archivo = fopen("datos.txt", "r");
if (archivo == NULL) {
    printf("Error al abrir el archivo.");
}
fclose(archivo);
```
- `fopen()`: Abre un archivo. Los modos comunes son r (lectura), w (escritura), y a (adjuntar).
- `fclose()`: Cierra el archivo para liberar recursos.

Escritura y lectura en archivos:
```c
FILE *archivo = fopen("datos.txt", "w");
fprintf(archivo, "Escribiendo en el archivo.\n");
fclose(archivo);
```

- `fprintf()`: Similar a `printf()`, pero escribe en un archivo en lugar de en la consola.



<div id='13'></div>

# 13. Macros y constantes
Las macros son fragmentos de código que se expanden antes de la compilación. Las constantes, por otro lado, son valores fijos que no cambian.

<b>Definición de macros:</b>
```c
#define PI 3.14159
#define AREA_CIRCULO(r) (PI * (r) * (r))
```
- `#define`: Se utiliza para definir macros, que son fragmentos de código que el preprocesador sustituye antes de compilar el programa.

<b>Uso de `const`:</b>

```c
const int MAX = 100;
```


<div id='14'></div>

# 14. Manejo de errores con `errno`
C proporciona la variable global errno para detectar errores al ejecutar operaciones del sistema, como abrir archivos o asignar memoria.
```c
#include <errno.h>
#include <string.h>

FILE *archivo = fopen("archivo.txt", "r");
if (archivo == NULL) {
    printf("Error: %s\n", strerror(errno));  // Imprime el error
}
```
- `errno`: Variable que almacena el código de error.
- `strerror()`: Convierte un código de error en un mensaje legible.



<div id='15'></div>

# 15. Compilación
Una vez que escribes tu programa en C, debes compilarlo para convertirlo en un archivo ejecutable. Para ello se usa un compilador como gcc.

<b>Para compilar en Linux o MacOS:</b>
```bash
gcc programa.c -o programa
./programa
```
<b>Para compilar en Windows:</b>
```bash
gcc programa.c -o programa.exe
programa.exe
```
# 16. Bibliotecas estándar útiles
C cuenta con una amplia gama de bibliotecas estándar que ofrecen funciones para diversas operaciones.

- `<stdio.h>`: Entrada y salida estándar (funciones como `printf` y `scanf`).
- `<stdlib.h>`: Funciones de utilidad, conversión de tipos, memoria dinámica, control de procesos.
- `<string.h>`: Funciones para manipulación de cadenas, como `strlen`, `strcpy`, y `strcmp`.
- `<math.h>`: Funciones matemáticas como `sqrt()`, `pow()`, y `sin()`.
- `<time.h>`: Funciones para manipular y obtener el tiempo actual.