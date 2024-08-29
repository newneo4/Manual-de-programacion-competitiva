# Problema de la Moneda

Como primer ejemplo, consideremos un problema donde se nos da un conjunto de monedas y nuestra tarea es formar una suma de dinero  $n$ utilizando las monedas. Los valores de las monedas son $\text{coins} = \{c_1, c_2, \ldots, c_k\}$, y cada moneda puede ser utilizada tantas veces como queramos. ¿Cuál es el número mínimo de monedas necesarias?

Por ejemplo, si las monedas son las monedas de euro (en céntimos)

$$
\{1, 2, 5, 10, 20, 50, 100, 200\}
$$

y $n = 520$, necesitamos al menos cuatro monedas. La solución óptima es seleccionar las monedas 200 + 200 + 100 + 20 cuya suma es 520.

## Algoritmo Voraz

Un algoritmo voraz para este problema siempre selecciona la moneda más grande posible, hasta que se haya construido la suma de dinero requerida. Este algoritmo funciona en el caso del ejemplo, porque primero seleccionamos dos monedas de 200 céntimos, luego una moneda de 100 céntimos y finalmente una moneda de 20 céntimos. ¿Pero, funciona este algoritmo siempre?

Resulta que si las monedas son las monedas de euro, el algoritmo voraz siempre funciona, es decir, siempre produce una solución con el menor número posible de monedas. La corrección del algoritmo se puede demostrar de la siguiente manera:

Primero, cada moneda de 1, 5, 10, 50 y 100 aparece como máximo una vez en una solución óptima, porque si la solución contuviera dos de esas monedas, podríamos reemplazarlas por una moneda de mayor valor y obtener una mejor solución. Por ejemplo, si la solución contiene las monedas 5 + 5, podríamos reemplazarlas por una moneda de 10.

De la misma manera, las monedas de 2 y 20 aparecen como máximo dos veces en una solución óptima, porque podríamos reemplazar monedas 2 + 2 + 2 por monedas 5 + 1, y monedas 20 + 20 + 20 por monedas 50 + 10. Además, una solución óptima no puede contener combinaciones como 2 + 2 + 1 o 20 + 20 + 10, porque podríamos reemplazarlas por monedas de 5 y 50, respectivamente.

Utilizando estas observaciones, podemos demostrar que para cada moneda $x$, no es posible construir de manera óptima una suma de $x$ o cualquier suma mayor utilizando solo monedas que sean más pequeñas que $x$. Por ejemplo, si $x = 100$, la mayor suma óptima utilizando monedas más pequeñas es 50 + 20 + 20 + 5 + 2 + 2 = 99. Por lo tanto, el algoritmo voraz que siempre selecciona la moneda más grande produce la solución óptima.

Este ejemplo muestra que puede ser difícil argumentar que un algoritmo voraz funciona, incluso si el propio algoritmo es simple.

## Caso General

En el caso general, el conjunto de monedas puede contener cualquier tipo de moneda, y el algoritmo voraz no necesariamente produce una solución óptima.

Podemos demostrar que un algoritmo voraz no funciona mostrando un contraejemplo en el cual el algoritmo da una respuesta incorrecta. En este problema, podemos encontrar fácilmente un contraejemplo: si las monedas son \{1, 3, 4\} y la suma objetivo es 6, el algoritmo voraz produce la solución 4 + 1 + 1, mientras que la solución óptima es 3 + 3.

No se sabe si el problema general de la moneda puede resolverse utilizando algún algoritmo voraz. Sin embargo, como veremos en el Capítulo 7, en algunos casos, el problema general puede resolverse eficientemente utilizando un algoritmo de programación dinámica que siempre da la respuesta correcta.

## Navegación

- [Anterior: Algoritmos Greedy.md](./Algoritmos%20Greedy.md)
- [Siguiente: Programacion.md](./Programacion.md)