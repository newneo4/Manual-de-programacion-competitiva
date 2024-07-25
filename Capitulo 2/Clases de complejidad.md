## Clases de Complejidad

La siguiente lista contiene las complejidades temporales comunes de los algoritmos:

- **O(1)**: El tiempo de ejecución de un algoritmo de tiempo constante no depende del tamaño de la entrada. Un algoritmo típico de tiempo constante es una fórmula directa que calcula la respuesta.

- **O(log n)**: Un algoritmo logarítmico a menudo divide el tamaño de la entrada a la mitad en cada paso. El tiempo de ejecución de tal algoritmo es logarítmico, porque $\log_2 n$ equivale al número de veces que se debe dividir $n$ por 2 para obtener 1.

- **O(√n)**: Un algoritmo de raíz cuadrada es más lento que O(log n) pero más rápido que O(n). Una propiedad especial de las raíces cuadradas es que $\sqrt{n} = \frac{n}{\sqrt{n}}$, por lo que la raíz cuadrada $\sqrt{n}$ se encuentra, en cierto sentido, en el medio de la entrada.

- **O(n)**: Un algoritmo lineal recorre la entrada un número constante de veces. Esta es a menudo la mejor complejidad temporal posible, ya que generalmente es necesario acceder a cada elemento de entrada al menos una vez antes de reportar la respuesta.

- **O(n log n)**: Esta complejidad temporal a menudo indica que el algoritmo ordena la entrada, porque la complejidad temporal de los algoritmos de ordenamiento eficientes es O(n log n). Otra posibilidad es que el algoritmo utiliza una estructura de datos en la que cada operación toma tiempo O(log n).

- **O(n²)**: Un algoritmo cuadrático a menudo contiene dos bucles anidados. Es posible recorrer todos los pares de elementos de entrada en tiempo O(n²).

- **O(n³)**: Un algoritmo cúbico a menudo contiene tres bucles anidados. Es posible recorrer todos los tripletas de los elementos de entrada en tiempo O(n³).

- **O(2^n)**: Esta complejidad temporal a menudo indica que el algoritmo itera a través de todos los subconjuntos de los elementos de entrada. Por ejemplo, los subconjuntos de {1, 2, 3} son: $\emptyset$, {1}, {2}, {3}, {1, 2}, {1, 3}, {2, 3} y {1, 2, 3}.

- **O(n!)**: Esta complejidad temporal a menudo indica que el algoritmo itera a través de todas las permutaciones de los elementos de entrada. Por ejemplo, las permutaciones de {1, 2, 3} son: (1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2) y (3, 2, 1).

Un algoritmo es **polinómico** si su complejidad temporal es como máximo O(n^k), donde k es una constante. Todas las complejidades temporales anteriores, excepto O(2^n) y O(n!), son polinómicas. En la práctica, la constante k suele ser pequeña, por lo que una complejidad temporal polinómica significa que el algoritmo es eficiente.

La mayoría de los algoritmos en este libro son polinómicos. Sin embargo, hay muchos problemas importantes para los cuales no se conoce ningún algoritmo polinómico, es decir, nadie sabe cómo resolverlos de manera eficiente. Los problemas NP-duros son un conjunto importante de problemas para los cuales no se conoce ningún algoritmo polinómico.

## Navegación
- [Anterior: Tiempo de complejidad.md](./Tiempo%20de%20complejidad.md)
- [Siguiente: Estimacion de eficiencia.md](./Estimacion%20de%20eficiencia.md)
