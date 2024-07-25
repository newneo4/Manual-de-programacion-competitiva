# Estructuras Set

Un set es una estructura de datos que mantiene una colección de elementos. Las operaciones básicas de los set son la inserción de elementos, la búsqueda y la eliminación.

La biblioteca estándar de C++ contiene dos implementaciones de conjuntos: La estructura `set` se basa en un árbol binario equilibrado y sus operaciones funcionan en tiempo O(log n). La estructura `unordered_set` usa hashing, y sus operaciones funcionan en tiempo O(1) en promedio.

La elección de qué implementación de conjunto usar es a menudo una cuestión de preferencia. El beneficio de la estructura `set` es que mantiene el orden de los elementos y proporciona funciones que no están disponibles en `unordered_set`. Por otro lado, `unordered_set` puede ser más eficiente.

El siguiente código crea un conjunto que contiene enteros y muestra algunas de las operaciones. La función `insert` agrega un elemento al conjunto, la función `count` devuelve el número de ocurrencias de un elemento en el conjunto, y la función `erase` elimina un elemento del conjunto.

```cpp
#include <iostream>
#include <set>

using namespace std;

int main() {
    set<int> s;
    s.insert(3);
    s.insert(1);
    s.insert(4);
    cout << s.count(3) << "\n"; // 1
    cout << s.count(2) << "\n"; // 0
    s.erase(3);
    cout << s.count(3) << "\n"; // 0
    return 0;
}
```

Un conjunto se puede usar principalmente como un vector, pero no es posible acceder a los elementos usando la notación []. El siguiente código crea un conjunto, imprime el número de elementos en él y luego itera a través de todos los elementos:

```cpp
set<int> s = {2, 5, 6, 8};
cout << s.size() << "\n"; // 4

for (auto x : s) {
    cout << x << "\n";
}
```

Una propiedad importante de los conjuntos es que todos sus elementos son distintos. Por lo tanto, la función `count` siempre devuelve 0 (el elemento no está en el conjunto) o 1 (el elemento está en el conjunto), y la función `insert` nunca agrega un elemento al conjunto si ya está allí. El siguiente código ilustra esto:

```cpp
set<int> s;
s.insert(5);
s.insert(5);
s.insert(5);
cout << s.count(5) << "\n"; // 1
```
## Multiset

C++ también contiene las estructuras `multiset` y `unordered_multiset` que, de lo contrario, funcionan como `set` y `unordered_set`, pero pueden contener múltiples instancias de un elemento. Por ejemplo, en el siguiente código se añaden las tres instancias del número 5 a un `multiset`:

```cpp
multiset<int> s;
s.insert(5);
s.insert(5);
s.insert(5);
cout << s.count(5) << "\n"; // 3
```
La funcion `erase` elimina todas las instancias de un elemento dentro del multiset.

```cpp
s.erase(5);
cout << s.count(5) << "\n"; // 0
```
A menudo, solo se debe eliminar una instancia, lo cual se puede hacer de la siguiente manera:

```cpp
s.erase(s.find(5));
cout << s.count(5) << "\n"; // 2
```

## Navegación
- [Anterior: Arreglos dinamicos.md](./Arreglos%20dinamicos.md)
- [Siguiente: Estructuras map.md](./Estructuras%20map.md)
