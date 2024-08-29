# Minimización de Sumas

Consideremos un problema en el que se nos dan \(n\) números $a_1, a_2, \ldots, a_n$ y nuestra tarea es encontrar un valor $x$ que minimice la suma

$$
|a_1 - x|^c + |a_2 - x|^c + \cdots + |a_n - x|^c.
$$

Nos enfocamos en los casos $c = 1$ y $c = 2$.

## Caso $c = 1$

En este caso, debemos minimizar la suma

$$
|a_1 - x| + |a_2 - x| + \cdots + |a_n - x|.
$$

Por ejemplo, si los números son $[1, 2, 9, 2, 6]$, la mejor solución es seleccionar $x = 2$, lo que produce la suma

$$
|1 - 2| + |2 - 2| + |9 - 2| + |2 - 2| + |6 - 2| = 12.
$$

En el caso general, la mejor opción para $x$ es la mediana de los números, es decir, el número del medio después de ordenar la lista. Por ejemplo, la lista $[1, 2, 9, 2, 6]$ se convierte en $[1, 2, 2, 6, 9]$ después de ordenar, por lo que la mediana es 2.

La mediana es una elección óptima porque si $x$ es menor que la mediana, la suma se reduce aumentando $x$, y si $x$ es mayor que la mediana, la suma se reduce disminuyendo $x$. Por lo tanto, la solución óptima es que $x$ sea la mediana. Si $n$ es par y hay dos medianas, ambas medianas y todos los valores entre ellas son opciones óptimas.

## Caso $c = 2$

En este caso, debemos minimizar la suma

$$
(a_1 - x)^2 + (a_2 - x)^2 + \cdots + (a_n - x)^2.
$$

Por ejemplo, si los números son $[1, 2, 9, 2, 6]$, la mejor solución es seleccionar $x = 4$, lo que produce la suma

$$
(1 - 4)^2 + (2 - 4)^2 + (9 - 4)^2 + (2 - 4)^2 + (6 - 4)^2 = 46.
$$

En el caso general, la mejor opción para $x$ es el promedio de los números. En el ejemplo, el promedio es $(1 + 2 + 9 + 2 + 6)/5 = 4$. Este resultado se puede derivar presentando la suma de la siguiente manera:

$$
nx^2 - 2x(a_1 + a_2 + \cdots + a_n) + (a_1^2 + a_2^2 + \cdots + a_n^2).
$$

La última parte no depende de $x$, por lo que podemos ignorarla. Las partes restantes forman una función $nx^2 - 2xs$, donde $s = a_1 + a_2 + \cdots + a_n$. Esta es una parábola que se abre hacia arriba con raíces en $x = 0$ y $x = \frac{2s}{n}$, y el valor mínimo es el promedio de las raíces $x = \frac{s}{n}$, es decir, el promedio de los números $a_1, a_2, \ldots, a_n$.

## Navegación

- [Anterior: Programacion de tareas.md](./Programacion.md)
- [Siguiente: Compresion de data.md](./Compresion%20de%20data.md)