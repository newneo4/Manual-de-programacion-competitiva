## Problema de la Suma Máxima de Subarreglo

A menudo, hay varios algoritmos posibles para resolver un problema, cada uno con diferentes complejidades temporales. Esta sección discute un problema clásico que tiene una solución directa de O($n^3$). Sin embargo, al diseñar un algoritmo mejor, es posible resolver el problema en O($n^2$) y incluso en O($n$) tiempo.

Dado un arreglo de $n$ números, nuestra tarea es calcular la suma máxima de un subarreglo, es decir, la mayor suma posible de una secuencia de valores consecutivos en el arreglo. El problema es interesante cuando puede haber valores negativos en el arreglo. 

### Ejemplo

Para el arreglo:
$$
-1, 2, 4, -3, 5, 2, -5, 2
$$ 


El subarreglo que produce la suma máxima de 10 es `[2, 4, -3, 5, 2]`.

### Algoritmo 1: Solución Directa (O($n^3$))

Una forma directa de resolver el problema es iterar a través de todos los posibles subarreglos, calcular la suma de valores en cada subarreglo y mantener la suma máxima. A continuación se presenta el código que implementa este algoritmo:

```cpp
int best = 0;
for (int a = 0; a < n; a++) {
    for (int b = a; b < n; b++) {
        int sum = 0;
        for (int k = a; k <= b; k++) {
            sum += array[k];
        }
        best = max(best, sum);
    }
}
cout << best << "\n";
```

En este código, las variables a y b fijan el primer y último índice del subarreglo, y la suma de los valores se calcula en la variable sum. La variable best contiene la máxima suma encontrada durante la búsqueda. La complejidad temporal de este algoritmo es O($n^3$), debido a los tres bucles anidados que recorren el arreglo.

### Algoritmo 2: Optimización (O($n^2$))
Es posible hacer el Algoritmo 1 más eficiente eliminando uno de los bucles. Esto se puede lograr calculando la suma mientras se mueve el extremo derecho del subarreglo. El código resultante es el siguiente:

```cpp
int best = 0;
for (int a = 0; a < n; a++) {
    int sum = 0;
    for (int b = a; b < n; b++) {
        sum += array[b];
        best = max(best, sum);
    }
}
cout << best << "\n";
```

Despues de este cambio el tiempo de complejidad es O($n^2$)

### Algoritmo 3: Solución Óptima (O($n$))

Sorprendentemente, es posible resolver el problema en O($n$) de tiempo, lo que significa que basta con un solo bucle. La idea es calcular, para cada posición del arreglo, la suma máxima de un subarreglo que termina en esa posición. Luego, la respuesta al problema es el máximo de esas sumas.

Consideremos el subproblema de encontrar el subarreglo de máxima suma que termina en la posición `k`. Existen dos posibilidades:

1. El subarreglo solo contiene el elemento en la posición `k`.
2. El subarreglo consiste en un subarreglo que termina en la posición `k − 1`, seguido del elemento en la posición `k`.

En el segundo caso, dado que queremos encontrar un subarreglo con la suma máxima, el subarreglo que termina en la posición `k − 1` también debe tener la suma máxima. Así, podemos resolver el problema de manera eficiente calculando la suma máxima del subarreglo para cada posición final de izquierda a derecha.

El siguiente código implementa el algoritmo:

```cpp
int best = 0, sum = 0;
for (int k = 0; k < n; k++) {
    sum = max(array[k], sum + array[k]);
    best = max(best, sum);
}
cout << best << "\n";
```

Este algoritmo solo contiene un bucle que recorre el arreglo, por lo que la complejidad temporal es O($n$). Este es también el mejor tiempo posible, ya que cualquier algoritmo para el problema debe examinar al menos una vez todos los elementos del arreglo.

### Comparación de Eficiencia

Es interesante estudiar cuán eficientes son los algoritmos en la práctica. La siguiente tabla muestra los tiempos de ejecución de los algoritmos descritos para diferentes valores de `n` en una computadora moderna. En cada prueba, la entrada se generó aleatoriamente. El tiempo necesario para leer la entrada no se midió.

| Tamaño del arreglo `n` | Algoritmo 1 | Algoritmo 2 | Algoritmo 3 |
|------------------------|-------------|-------------|-------------|
| 10²                    | 0.0 s       | 0.0 s       | 0.0 s       |
| 10³                    | 0.1 s       | 0.0 s       | 0.0 s       |
| 10⁴                    | > 10.0 s    | 0.1 s       | 0.0 s       |
| 10⁵                    | > 10.0 s    | 5.3 s       | 0.0 s       |
| 10⁶                    | > 10.0 s    | > 10.0 s    | 0.0 s       |
| 10⁷                    | > 10.0 s    | > 10.0 s    | 0.0 s       |

### Comparación de Eficiencia

La comparación muestra que todos los algoritmos son eficientes cuando el tamaño de la entrada es pequeño, pero los tamaños de entrada más grandes revelan diferencias notables en los tiempos de ejecución de los algoritmos. El Algoritmo 1 se vuelve lento cuando `n = 10⁴`, y el Algoritmo 2 se vuelve lento cuando `n = 10⁵`. Solo el Algoritmo 3 es capaz de procesar incluso las entradas más grandes de manera instantánea.

