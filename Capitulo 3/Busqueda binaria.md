## Búsqueda Binaria

Un método general para buscar un elemento en un arreglo es usar un bucle `for` que itere a través de los elementos del arreglo. Por ejemplo, el siguiente código busca un elemento `x` en un arreglo:

```cpp
for (int i = 0; i < n; i++) {
    if (array[i] == x) {
        // x encontrado en el índice i
    }
}
```

La complejidad temporal de este enfoque es O(n), porque en el peor caso es necesario revisar todos los elementos del arreglo. Si el orden de los elementos es arbitrario, este es también el mejor enfoque posible, ya que no hay información adicional disponible sobre dónde en el arreglo deberíamos buscar el elemento x.

Sin embargo, si el arreglo está ordenado, la situación es diferente. En este caso, es posible realizar la búsqueda mucho más rápido, ya que el orden de los elementos en el arreglo guía la búsqueda. El siguiente algoritmo de búsqueda binaria busca eficientemente un elemento en un arreglo ordenado en O(log n) tiempo.

### Método 1

La forma habitual de implementar la búsqueda binaria se asemeja a buscar una palabra en un diccionario. La búsqueda mantiene una región activa en el arreglo, que inicialmente contiene todos los elementos del arreglo. Luego, se realizan una serie de pasos, cada uno de los cuales divide a la mitad el tamaño de la región.

En cada paso, la búsqueda revisa el elemento del medio de la región activa. Si el elemento del medio es el elemento objetivo, la búsqueda termina. De lo contrario, la búsqueda continúa recursivamente hacia la mitad izquierda o derecha de la región, dependiendo del valor del elemento del medio.

La idea anterior se puede implementar de la siguiente manera:

```cpp
int a = 0, b = n-1;
while (a <= b) {
    int k = (a+b)/2;
    if (array[k] == x) {
        // x encontrado en el índice k
    }
    if (array[k] > x) b = k-1;
    else a = k+1;
}
```

En esta implementación, la región activa es a . . . b, y al principio la región es 0 . . . n - 1. El algoritmo reduce a la mitad el tamaño de la región en cada paso, por lo que la complejidad temporal es O(log n).

### Método 2

Un método alternativo para implementar la búsqueda binaria se basa en una manera eficiente de iterar a través de los elementos del arreglo. La idea es hacer saltos y reducir la velocidad cuando nos acercamos al elemento objetivo.

La búsqueda recorre el arreglo de izquierda a derecha, y la longitud inicial del salto es `n/2`. En cada paso, la longitud del salto se reduce a la mitad: primero `n/4`, luego `n/8`, `n/16`, etc., hasta que finalmente la longitud es 1. Después de los saltos, o se ha encontrado el elemento objetivo o sabemos que no aparece en el arreglo.

El siguiente código implementa la idea anterior:

```cpp
int k = 0;
for (int b = n/2; b >= 1; b /= 2) {
    while (k+b < n && array[k+b] <= x) k += b;
}
if (array[k] == x) {
    // x encontrado en el índice k
}
```

Durante la búsqueda, la variable b contiene la longitud actual del salto. La complejidad temporal del algoritmo es O(log n), porque el código en el bucle while se ejecuta como máximo dos veces para cada longitud de salto.