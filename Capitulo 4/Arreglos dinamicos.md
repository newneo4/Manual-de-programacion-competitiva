# Arreglos Dinámicos

Un arreglo dinámico es un arreglo cuyo tamaño puede cambiar durante la ejecución del programa. El arreglo dinámico más popular en C++ es la estructura de vector, que puede usarse casi como un arreglo ordinario.

El siguiente código crea un vector vacío y agrega tres elementos a él:

```cpp
vector<int> v;
v.push_back(3); // [3]
v.push_back(2); // [3,2]
v.push_back(5); // [3,2,5]
```

Después de esto, los elementos se pueden acceder como en un arreglo ordinario:

```cpp
cout << v[0] << "\n"; // 3
cout << v[1] << "\n"; // 2
cout << v[2] << "\n"; // 5
```

La función size devuelve el número de elementos en el vector. El siguiente código itera a través del vector e imprime todos los elementos en él:

```cpp
for (int i = 0; i < v.size(); i++) {
    cout << v[i] << "\n";
}
```

Una forma más corta de iterar a través de un vector es la siguiente:

```cpp
for (auto x : v) {
    cout << x << "\n";
}
```

La función back devuelve el último elemento en el vector, y la función pop_back elimina el último elemento:

```cpp
vector<int> v;
v.push_back(5);
v.push_back(2);
cout << v.back() << "\n"; // 2
v.pop_back();
cout << v.back() << "\n"; // 5
```

El siguiente código crea un vector con cinco elementos:

```cpp
vector<int> v = {2,4,2,5,1};
```

Otra forma de crear un vector es dando el número de elementos y el valor inicial para cada elemento:

```cpp
// tamaño 10, valor inicial 0
vector<int> v(10);
// tamaño 10, valor inicial 5
vector<int> v(10, 5);
```

La implementación interna de un vector utiliza un arreglo ordinario. Si el tamaño del vector aumenta y el arreglo se vuelve demasiado pequeño, se asigna un nuevo arreglo y todos los elementos se trasladan al nuevo arreglo. Sin embargo, esto no ocurre a menudo y la complejidad temporal promedio de push_back es O(1).

La estructura string también es un arreglo dinámico que se puede usar casi como un vector. Además, hay una sintaxis especial para cadenas que no está disponible en otras estructuras de datos. Las cadenas se pueden combinar usando el símbolo +. La función substr(k, x) devuelve la subcadena que comienza en la posición k y tiene longitud x, y la función find(t) encuentra la posición de la primera aparición de una subcadena t.

El siguiente código presenta algunas operaciones con cadenas:

```cpp
string s = "hello";
string t = "world";
string u = s + " " + t;
cout << u << "\n"; // hello world
cout << u.substr(6, 5) << "\n"; // world
cout << u.find("world") << "\n"; // 6
```

## Navegación
- [Anterior: Estructuras de datos.md](./Estructuras%20de%20datos.md)
- [Siguiente: Estructuras set.md](./Estructuras%20set.md)
