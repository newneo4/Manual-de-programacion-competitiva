# Estructuras Map

Un mapa es un arreglo generalizado que consiste en pares clave-valor. Mientras que las claves en un arreglo ordinario son siempre los enteros consecutivos 0, 1, ..., n - 1, donde n es el tamaño del arreglo, las claves en un mapa pueden ser de cualquier tipo de dato y no tienen que ser valores consecutivos.

La biblioteca estándar de C++ contiene dos implementaciones de mapas que corresponden a las implementaciones de conjuntos: la estructura `map` se basa en un árbol binario equilibrado y el acceso a los elementos toma tiempo O(log n), mientras que la estructura `unordered_map` usa hashing y el acceso a los elementos toma tiempo O(1) en promedio.

El siguiente código crea un mapa donde las claves son cadenas y los valores son enteros:

```cpp
map<string, int> m;
m["monkey"] = 4;
m["banana"] = 3;
m["harpsichord"] = 9;
cout << m["banana"] << "\n"; // 3
```

Si se solicita el valor de una clave pero el mapa no la contiene, la clave se agrega automáticamente al mapa con un valor predeterminado. Por ejemplo, en el siguiente código, la clave "aybabtu" con valor 0 se agrega al mapa:

```cpp
map<string, int> m;
cout << m["aybabtu"] << "\n"; // 0
```

La función `count` verifica si una clave existe en un mapa:

```cpp
if (m.count("aybabtu")) {
    // La clave existe
}
```

El siguiente codigo imprime todas las claves y valores en un mapa

```cpp
for (auto x : m) {
cout << x.first << " " << x.second << "\n";
}
```

