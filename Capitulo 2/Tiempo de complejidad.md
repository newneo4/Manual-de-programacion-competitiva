# Complejidad Temporal

La eficiencia de los algoritmos es crucial en la programación competitiva. Generalmente, es fácil diseñar un algoritmo que resuelva el problema lentamente, pero el verdadero desafío es inventar un algoritmo rápido. Si el algoritmo es demasiado lento, solo obtendrá puntos parciales o ningún punto en absoluto.

La complejidad temporal de un algoritmo estima cuánto tiempo usará el algoritmo para un determinado input. La idea es representar la eficiencia como una función cuyo parámetro es el tamaño del input. Calculando la complejidad temporal, podemos averiguar si el algoritmo es lo suficientemente rápido sin necesidad de implementarlo.

## Reglas de Cálculo

La complejidad temporal de un algoritmo se denota como $O(\cdots)$, donde los puntos suspensivos representan alguna función. Generalmente, la variable $n$ denota el tamaño del input. Por ejemplo, si el input es un arreglo de números, $n$ será el tamaño del arreglo, y si el input es una cadena, $n$ será la longitud de la cadena.

### Bucles

Una razón común por la cual un algoritmo es lento es que contiene muchos bucles que recorren el input. Cuantos más bucles anidados contenga el algoritmo, más lento será.

Si hay $k$ bucles anidados, la complejidad temporal es $O(n^k)$.

Por ejemplo, la complejidad temporal del siguiente código es $O(n)$:

```cpp
for (int i = 1; i <= n; i++) {
    // código
}
```
Y la complejidad temporal del siguiente código es $O(n^2)$:

```cpp
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= n; j++) {
        // código
    }
}
```
### Orden de Magnitud

La complejidad temporal no nos dice el número exacto de veces que se ejecuta el código dentro de un bucle, sino que solo muestra el orden de magnitud. En los siguientes ejemplos, el código dentro del bucle se ejecuta $3n$, $n + 5$ y $\lceil n/2 \rceil$ veces, pero la complejidad temporal de cada código es $O(n)$.

```cpp
for (int i = 1; i <= 3*n; i++) {
    // código
}

for (int i = 1; i <= n+5; i++) {
    // código
}

for (int i = 1; i <= n; i += 2) {
    // código
}
```

Como otro ejemplo, la complejidad temporal del siguiente código es $O(n^2)$:

```cpp
for (int i = 1; i <= n; i++) {
    for (int j = i+1; j <= n; j++) {
        // código
    }
}
```

### Fases
Si el algoritmo consta de fases consecutivas, la complejidad temporal total es la mayor complejidad temporal de una sola fase. La razón de esto es que la fase más lenta suele ser el cuello de botella del código.

Por ejemplo, el siguiente código consta de tres fases con complejidades temporales $O(n)$, $O(n^2)$ y $O(n)$. Por lo tanto, la complejidad temporal total es $O(n^2)$.

```cpp
for (int i = 1; i <= n; i++) {
    // código
}

for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= n; j++) {
        // código
    }
}

for (int i = 1; i <= n; i++) {
    // código
}
```

### Varios Factores

A veces, la complejidad temporal depende de varios factores. En este caso, la fórmula de complejidad temporal contiene varias variables.

Por ejemplo, la complejidad temporal del siguiente código es $O(nm)$:

```cpp
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= m; j++) {
        // código
    }
}
```

### Recursión
La complejidad temporal de una función recursiva depende del número de veces que se llama a la función y la complejidad temporal de una sola llamada. La complejidad temporal total es el producto de estos valores.

Por ejemplo, considera la siguiente función:

```cpp
void f(int n) {
    if (n == 1) return;
    f(n-1);
}
```

La llamada a f(n) causa $n$ llamadas a la función, y la complejidad temporal de cada llamada es $O(1)$. Por lo tanto, la complejidad temporal total es $O(n)$.

Como otro ejemplo, considera la siguiente función:

```cpp
void g(int n) {
    if (n == 1) return;
    g(n-1);
    g(n-1);
}
```

## Recursión

En este caso, cada llamada a la función genera dos llamadas adicionales, excepto cuando $n = 1$. Veamos lo que sucede cuando se llama a `g` con el parámetro $n$. La siguiente tabla muestra las llamadas a la función producidas por esta llamada única:

| Llamada a la función | Número de llamadas |
|----------------------|---------------------|
| $g(n)$               | 1                   |
| $g(n - 1)$           | 2                   |
| $g(n - 2)$           | 4                   |
| $\cdots$             | $\cdots$            |
| $g(1)$               | $2^{n-1}$           |

Basado en esto, la complejidad temporal es:

$$
1 + 2 + 4 + \cdots + 2^{n-1} = 2^n - 1 = O(2^n).
$$

## Navegación
- [Siguiente: Clases de complejidad.md](./Clases%20de%20complejidad.md)
