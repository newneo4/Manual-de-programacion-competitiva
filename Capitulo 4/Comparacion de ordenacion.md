### Comparación con Ordenación

A menudo es posible resolver un problema utilizando estructuras de datos o ordenación. A veces hay diferencias notables en la eficiencia real de estos enfoques, que pueden estar ocultas en sus complejidades de tiempo.

Consideremos un problema en el que se nos dan dos listas A y B que contienen n elementos cada una. Nuestra tarea es calcular el número de elementos que pertenecen a ambas listas.

Para ambos conjuntos. Por ejemplo, para las listas
```code
A = [5, 2, 8, 9, 4] y B = [3, 2, 9, 5]
```
la respuesta es 3 porque los números 2, 5 y 9 pertenecen a ambas listas.

Una solución directa al problema es recorrer todas las parejas de elementos en O(n²) tiempo, pero a continuación nos centraremos en algoritmos más eficientes.

**Algoritmo 1**  
Construimos un conjunto con los elementos que aparecen en A, y después iteramos a través de los elementos de B y verificamos si cada elemento también pertenece a A. Esto es eficiente porque los elementos de A están en un conjunto. Usando la estructura de conjunto, la complejidad temporal del algoritmo es O(n log n).

**Algoritmo 2**  
No es necesario mantener un conjunto ordenado, por lo que en lugar de la estructura de conjunto podemos usar la estructura unordered_set. Esta es una forma fácil de hacer el algoritmo más eficiente, ya que solo tenemos que cambiar la estructura de datos subyacente. La complejidad temporal del nuevo algoritmo es O(n).

**Algoritmo 3**  
En lugar de estructuras de datos, podemos usar ordenación. Primero, ordenamos ambas listas A y B. Después, iteramos a través de ambas listas al mismo tiempo y encontramos los elementos comunes. La complejidad temporal de la ordenación es O(n log n), y el resto del algoritmo funciona en O(n) tiempo, por lo que la complejidad temporal total es O(n log n).

**Comparación de eficiencia**  
La siguiente tabla muestra cuán eficientes son los algoritmos anteriores cuando n varía y los elementos de las listas son enteros aleatorios entre 1 y 10⁹:

| n        | Algoritmo 1 | Algoritmo 2 | Algoritmo 3 |
|----------|-------------|-------------|-------------|
| 10⁶      | 1.5 s       | 0.3 s       | 0.2 s       |
| 2 · 10⁶  | 3.7 s       | 0.8 s       | 0.3 s       |
| 3 · 10⁶  | 5.7 s       | 1.3 s       | 0.5 s       |
| 4 · 10⁶  | 7.7 s       | 1.7 s       | 0.7 s       |
| 5 · 10⁶  | 10.0 s      | 2.3 s       | 0.9 s       |

Los Algoritmos 1 y 2 son iguales excepto por el uso de diferentes estructuras de conjunto. En este problema, esta elección tiene un efecto importante en el tiempo de ejecución, porque el Algoritmo 2 es 4–5 veces más rápido que el Algoritmo 1.

Sin embargo, el algoritmo más eficiente es el Algoritmo 3, que utiliza ordenación. Solo usa la mitad del tiempo en comparación con el Algoritmo 2. Curiosamente, la complejidad temporal de ambos Algoritmo 1 y Algoritmo 3 es O(n log n), pero a pesar de esto, el Algoritmo 3 es diez veces más rápido. Esto se puede explicar por el hecho de que la ordenación es un procedimiento simple y se realiza solo una vez al principio del Algoritmo 3, y el resto del algoritmo funciona en tiempo lineal. Por otro lado, el Algoritmo 1 mantiene un árbol binario balanceado complejo durante todo el algoritmo.

**Prueba del algoritmo**
```cpp
#include <iostream>
#include <vector>
#include <set>
#include <unordered_set>
#include <algorithm>
#include <chrono>
#include <cstdlib>

using namespace std;
using namespace std::chrono;

// Algoritmo 1: Usando std::set
void algorithm1(const vector<int>& A, const vector<int>& B) {
    set<int> setA(A.begin(), A.end());
    for (int b : B) {
        setA.find(b);
    }
}

// Algoritmo 2: Usando std::unordered_set
void algorithm2(const vector<int>& A, const vector<int>& B) {
    unordered_set<int> setA(A.begin(), A.end());
    for (int b : B) {
        setA.find(b);
    }
}

// Algoritmo 3: Usando std::sort
void algorithm3(vector<int> A, vector<int> B) {
    sort(A.begin(), A.end());
    sort(B.begin(), B.end());
    auto itA = A.begin();
    auto itB = B.begin();
    while (itA != A.end() && itB != B.end()) {
        if (*itA == *itB) {
            ++itA;
            ++itB;
        } else if (*itA < *itB) {
            ++itA;
        } else {
            ++itB;
        }
    }
}

int main() {
    vector<int> sizes = {1'000'000, 2'000'000, 3'000'000, 4'000'000, 5'000'000};

    for (int size : sizes) {
        // Generar datos aleatorios
        vector<int> A(size);
        vector<int> B(size);
        for (int i = 0; i < size; ++i) {
            A[i] = rand() % 1'000'000'000 + 1;
            B[i] = rand() % 1'000'000'000 + 1;
        }

        // Algoritmo 1
        auto start = high_resolution_clock::now();
        algorithm1(A, B);
        auto end = high_resolution_clock::now();
        auto duration1 = duration_cast<milliseconds>(end - start).count();

        // Algoritmo 2
        start = high_resolution_clock::now();
        algorithm2(A, B);
        end = high_resolution_clock::now();
        auto duration2 = duration_cast<milliseconds>(end - start).count();

        // Algoritmo 3
        start = high_resolution_clock::now();
        algorithm3(A, B);
        end = high_resolution_clock::now();
        auto duration3 = duration_cast<milliseconds>(end - start).count();

        // Imprimir resultados
        cout << "Size: " << size << "\n";
        cout << "Algoritmo 1: " << duration1 << " ms\n";
        cout << "Algoritmo 2: " << duration2 << " ms\n";
        cout << "Algoritmo 3: " << duration3 << " ms\n";
        cout << "-----------------------------\n";
    }

    return 0;
}
```
Output:
```code
Size: 1000000
Algoritmo 1: 2944 ms
Algoritmo 2: 1370 ms
Algoritmo 3: 810 ms
-----------------------------
Size: 2000000
Algoritmo 1: 7262 ms
Algoritmo 2: 2998 ms
Algoritmo 3: 1885 ms
-----------------------------
Size: 3000000
Algoritmo 1: 11836 ms
Algoritmo 2: 4758 ms
Algoritmo 3: 2924 ms
-----------------------------
Size: 4000000
Algoritmo 1: 17561 ms
Algoritmo 2: 11739 ms
Algoritmo 3: 15002 ms
-----------------------------
Size: 5000000
Algoritmo 1: 98806 ms
Algoritmo 2: 35597 ms
Algoritmo 3: 19902 ms
-----------------------------
```

### Explicación de la Prueba del Algoritmo

A pesar de que la complejidad teórica del Algoritmo 3 (basado en la ordenación) es \(O(n \log n)\) y la de los Algoritmos 1 y 2 (basados en estructuras de conjuntos) es \(O(n \log n)\) y \(O(n)\) respectivamente, el Algoritmo 3 resulta ser más rápido en la práctica. 

**Razones por las que el Algoritmo 3 es más rápido:**

1. **Eficiencia del Ordenamiento:**
   - Aunque la complejidad teórica del Algoritmo 3 es \(O(n \log n)\), el proceso de ordenación es bastante eficiente en la práctica debido a las optimizaciones en los algoritmos de ordenamiento como QuickSort y MergeSort que se utilizan en las implementaciones estándar.
   - Después del paso de ordenación, el algoritmo realiza la comparación en tiempo lineal \(O(n)\), lo que es bastante rápido en comparación con las búsquedas en árboles balanceados o estructuras de conjuntos.

2. **Simplicidad de Implementación:**
   - El Algoritmo 3 utiliza el enfoque de comparación directa sobre listas ordenadas. La comparación secuencial es generalmente más eficiente que la búsqueda en estructuras de datos complejas como árboles balanceados o tablas hash.

3. **Costo de Mantenimiento de Estructuras:**
   - En los Algoritmos 1 y 2, especialmente en el Algoritmo 1 que utiliza `std::set`, se mantiene un árbol binario balanceado durante la ejecución del programa. Esto implica un costo adicional en la gestión de la estructura que no está presente en el Algoritmo 3.
   - El Algoritmo 2, aunque más eficiente que el Algoritmo 1 en términos de complejidad teórica, aún enfrenta el costo de las operaciones de hash y la posible colisión de hash, lo cual puede afectar el rendimiento en prácticas específicas.

En resumen, la combinación de una eficiente ordenación inicial y un proceso de comparación lineal en el Algoritmo 3 ofrece una ventaja práctica significativa sobre los métodos que dependen de estructuras de datos más complejas y costosas en términos de mantenimiento y operaciones.


## Navegación
- [Anterior: Otras estructuras.md](./Otras%20estructuras.md)
