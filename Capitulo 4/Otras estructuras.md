# Otras Estructuras

## Bitset

Un `bitset` es un arreglo cuyos valores son 0 o 1. Por ejemplo, el siguiente código crea un `bitset` que contiene 10 elementos:

```cpp
bitset<10> s;
s[1] = 1;
s[3] = 1;
s[4] = 1;
s[7] = 1;
cout << s[4] << "\n"; // 1
cout << s[5] << "\n"; // 0
```

El beneficio de usar bitsets es que requieren menos memoria que los arreglos ordinarios, porque cada elemento en un `bitset` usa solo un bit de memoria. Por ejemplo, si se almacenan n bits en un arreglo int, se utilizarán 32n bits de memoria, pero un bitset correspondiente solo requiere n bits de memoria. Además, los valores de un bitset se pueden manipular de manera eficiente usando operadores de bits, lo que permite optimizar algoritmos que usan conjuntos de bits.

El siguiente código muestra otra forma de crear el bitset anterior:

```cpp
bitset<10> s(string("0010011010")); // de derecha a izquierda
cout << s[4] << "\n"; // 1
cout << s[5] << "\n"; // 0
```

La función `count` devuelve el número de unos en el `bitset`:

```cpp
bitset<10> s(string("0010011010"));
cout << s.count() << "\n"; // 4
```

El siguiente código muestra ejemplos de uso de operaciones con bits:

```cpp
bitset<10> a(string("0010110110"));
bitset<10> b(string("1011011000"));
cout << (a & b) << "\n"; // 0010010000
cout << (a | b) << "\n"; // 1011111110
cout << (a ^ b) << "\n"; // 1001101110
```

## Deque
Un deque es un arreglo dinámico cuyo tamaño se puede cambiar eficientemente en ambos extremos del arreglo. Al igual que un vector, un deque proporciona las funciones push_back y pop_back, pero también incluye las funciones push_front y pop_front que no están disponibles en un vector.

Un deque se puede usar de la siguiente manera:

```cpp
deque<int> d;
d.push_back(5); // [5]
d.push_back(2); // [5,2]
d.push_front(3); // [3,5,2]
d.pop_back(); // [3,5]
d.pop_front(); // [5]
```

La implementación interna de un deque es más compleja que la de un vector, y por esta razón, un deque es más lento que un vector. Sin embargo, tanto agregar como eliminar elementos toman O(1) tiempo en promedio en ambos extremos.

## Stack
Un stack es una estructura de datos que proporciona dos operaciones en O(1): agregar un elemento en la cima y eliminar un elemento de la cima. Solo es posible acceder al elemento superior de un stack.

El siguiente código muestra cómo se puede usar un stack:

```cpp
stack<int> s;
s.push(3);
s.push(2);
s.push(5);
cout << s.top(); // 5
s.pop();
cout << s.top(); // 2
```

## Queue

Una `queue` también proporciona dos operaciones en O(1): agregar un elemento al final de la cola y eliminar el primer elemento de la cola. Solo es posible acceder al primer y al último elemento de una `queue`.

El siguiente código muestra cómo se puede usar una `queue`:

```cpp
queue<int> q;
q.push(3);
q.push(2);
q.push(5);
cout << q.front() << "\n"; // 3
q.pop();
cout << q.front() << "\n"; // 2
```

## Priority Queue
Una priority_queue mantiene un conjunto de elementos. Las operaciones soportadas son la inserción y, dependiendo del tipo de cola, la recuperación y eliminación del elemento mínimo o máximo. La inserción y eliminación toman O(log n) tiempo, y la recuperación toma O(1) tiempo.

Mientras que un conjunto ordenado soporta eficientemente todas las operaciones de una priority_queue, el beneficio de usar una priority_queue es que tiene factores constantes más pequeños. Una priority_queue se implementa generalmente usando una estructura de heap que es mucho más simple que el árbol binario balanceado utilizado en un conjunto ordenado.

Por defecto, los elementos en una priority_queue de C++ están ordenados en orden decreciente, y es posible encontrar y eliminar el elemento más grande en la cola. El siguiente código ilustra esto:

```cpp
priority_queue<int> q;
q.push(3);
q.push(5);
q.push(7);
q.push(2);
cout << q.top() << "\n"; // 7
q.pop();
cout << q.top() << "\n"; // 5
q.pop();
q.push(6);
cout << q.top() << "\n"; // 6
q.pop();
```

Si queremos crear una priority_queue que soporte encontrar y eliminar el elemento más pequeño, podemos hacerlo de la siguiente manera:

```cpp
priority_queue<int, vector<int>, greater<int>> q;
```

## Policy-based Data Structures

El compilador g++ también admite algunas estructuras de datos que no forman parte de la biblioteca estándar de C++. Estas estructuras se llaman estructuras de datos basadas en políticas. Para usar estas estructuras, se deben agregar las siguientes líneas al código:

```cpp
#include <ext/pb_ds/assoc_container.hpp>
using namespace __gnu_pbds;
```

Después de esto, podemos definir una estructura de datos indexed_set que es similar a set, pero que puede ser indexada como un array. La definición para valores de tipo int es la siguiente:

```cpp
typedef tree<int, null_type, less<int>, rb_tree_tag, tree_order_statistics_node_update> indexed_set;
```

Ahora podemos crear un conjunto de la siguiente manera:

```cpp
indexed_set s;
s.insert(2);
s.insert(3);
s.insert(7);
s.insert(9);
```

La especialidad de este conjunto es que tenemos acceso a los índices que los elementos tendrían en un array ordenado. La función find_by_order devuelve un iterador al elemento en una posición dada:

```cpp
auto x = s.find_by_order(2);
cout << *x << "\n"; // 7
```

Y la función order_of_key devuelve la posición de un elemento dado:

```cpp
cout << s.order_of_key(7) << "\n"; // 2
```

Si el elemento no aparece en el conjunto, obtenemos la posición que el elemento tendría en el conjunto:

```cpp
cout << s.order_of_key(6) << "\n"; // 2
cout << s.order_of_key(8) << "\n"; // 3
```

Ambas funciones trabajan en tiempo logarítmico.

## Navegación
- [Anterior: Iteradores y rangos.md](./Iteradores%20y%20rangos.md)
- [Siguiente: Comparacion de ordenacion.md](./Comparacion%20de%20ordenacion.md)
