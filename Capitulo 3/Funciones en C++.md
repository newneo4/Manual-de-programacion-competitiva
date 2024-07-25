## Funciones en C++

La biblioteca estándar de C++ contiene las siguientes funciones basadas en la búsqueda binaria que funcionan en tiempo logarítmico:

- **`lower_bound`** devuelve un puntero al primer elemento del arreglo cuyo valor es al menos `x`.
- **`upper_bound`** devuelve un puntero al primer elemento del arreglo cuyo valor es mayor que `x`.
- **`equal_range`** devuelve ambos punteros mencionados anteriormente.

Las funciones suponen que el arreglo está ordenado. Si no existe tal elemento, el puntero apunta al elemento después del último elemento del arreglo. Por ejemplo, el siguiente código verifica si un arreglo contiene un elemento con valor `x`:

```cpp
auto k = lower_bound(array, array + n, x) - array;
if (k < n && array[k] == x) {
    // x encontrado en el índice k
}
```

Luego, el siguiente código cuenta el número de elementos cuyo valor es x:

```cpp
auto a = lower_bound(array, array + n, x);
auto b = upper_bound(array, array + n, x);
cout << b - a << "\n";
```

Usando equal_range, el código se vuelve más corto:

```cpp
auto r = equal_range(array, array + n, x);
cout << r.second - r.first << "\n";
```

### Encontrar la solución más pequeña
Un uso importante para la búsqueda binaria es encontrar la posición en la que el valor de una función cambia. Supongamos que deseamos encontrar el valor más pequeño k que es una solución válida para un problema. Se nos da una función `ok(x)` que devuelve true si x es una solución válida y false en caso contrario. Además, sabemos que `ok(x)` es false cuando x < k y true cuando x ≥ k. La situación se ve de la siguiente manera:

| x      | 0   | 1   | · · · | k − 1 | k   | k + 1 | · · · |
|--------|-----|-----|-------|-------|-----|-------|-------|
| ok(x)  | false | false | · · · | false | true | true  | · · · |


Ahora, el valor de k se puede encontrar usando búsqueda binaria:

```cpp
int x = -1;
for (int b = z; b >= 1; b /= 2) {
    while (!ok(x + b)) x += b;
}
int k = x + 1;
```

La búsqueda encuentra el valor más grande de `x` para el cual `ok(x)` es falso. Así, el siguiente valor `k = x + 1` es el valor más pequeño para el cual `ok(k)` es verdadero. La longitud inicial del salto `z` debe ser lo suficientemente grande, por ejemplo, algún valor para el cual sabemos de antemano que `ok(z)` es verdadero.

El algoritmo llama a la función `ok` `O(log z)` veces, por lo que la complejidad total depende de la función `ok`. Por ejemplo, si la función trabaja en tiempo `O(n)`, la complejidad total es `O(n log z)`.

### Encontrar el valor máximo

La búsqueda binaria también se puede usar para encontrar el valor máximo de una función que primero es creciente y luego decreciente. Nuestra tarea es encontrar una posición `k` tal que:

- `f(x) < f(x + 1)` cuando `x < k`, y
- `f(x) > f(x + 1)` cuando `x ≥ k`.

La idea es usar la búsqueda binaria para encontrar el valor más grande de `x` para el cual `f(x) < f(x + 1)`. Esto implica que `k = x + 1` porque `f(x + 1) > f(x + 2)`. El siguiente código implementa la búsqueda:

```cpp
int x = -1;
for (int b = z; b >= 1; b /= 2) {
    while (f(x + b) < f(x + b + 1)) x += b;
}
int k = x + 1;
```

Nota que, a diferencia de la búsqueda binaria ordinaria, aquí no se permite que los valores consecutivos de la función sean iguales. En ese caso, no sería posible saber cómo continuar con la búsqueda.

## Navegación
- [Anterior: Busqueda binaria.md](./Busqueda%20binaria.md)
