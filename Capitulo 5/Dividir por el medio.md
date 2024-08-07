## Encuentro en el Medio

El "Encuentro en el Medio" es una técnica en la que el espacio de búsqueda se divide en dos partes de tamaño aproximadamente igual. Se realiza una búsqueda separada para cada una de las partes y, finalmente, se combinan los resultados de las búsquedas.

La técnica puede utilizarse si existe una forma eficiente de combinar los resultados de las búsquedas. En tal situación, las dos búsquedas pueden requerir menos tiempo que una búsqueda grande. Típicamente, podemos reducir un factor de $2^n$ a un factor de $2^{n/2}$ utilizando la técnica de encuentro en el medio.

Como ejemplo, consideremos un problema donde se nos da una lista de $n$ números y un número $x$, y queremos averiguar si es posible elegir algunos números de la lista de manera que su suma sea $x$. Por ejemplo, dada la lista [2,4,5,9] y $x = 15$, podemos elegir los números [2,4,9] para obtener $2 + 4 + 9 = 15$. Sin embargo, si $x = 10$ para la misma lista, no es posible formar la suma.

Un algoritmo simple para el problema es recorrer todos los subconjuntos de los elementos y comprobar si la suma de alguno de los subconjuntos es $x$. El tiempo de ejecución de tal algoritmo es $O(2^n)$, porque hay $2^n$ subconjuntos. Sin embargo, utilizando la técnica de encuentro en el medio, podemos lograr un algoritmo más eficiente con una complejidad temporal de $O(2^{n/2})$. Note que $O(2^n)$ y $O(2^{n/2})$ son complejidades diferentes porque $2^{n/2}$ es mucho menor que $2^n$.

La idea es dividir la lista en dos listas $A$ y $B$ de manera que ambas listas contengan aproximadamente la mitad de los números. La primera búsqueda genera todos los subconjuntos de $A$ y almacena sus sumas en una lista $S_A$. De manera correspondiente, la segunda búsqueda crea una lista $S_B$ a partir de $B$. Después de esto, basta con comprobar si es posible elegir un elemento de $S_A$ y otro de $S_B$ de manera que su suma sea $x$. Esto es posible exactamente cuando existe una forma de formar la suma $x$ utilizando los números de la lista original.

Por ejemplo, supongamos que la lista es [2,4,5,9] y $x = 15$. Primero, dividimos la lista en $A = [2,4]$ y $B = [5,9]$. Después de esto, creamos las listas $S_A = [0,2,4,6]$ y $S_B = [0,5,9,14]$. En este caso, la suma $x = 15$ es posible de formar, porque $S_A$ contiene la suma 6, $S_B$ contiene la suma 9, y $6 + 9 = 15$. Esto corresponde a la solución [2,4,9].

Podemos implementar el algoritmo de manera que su complejidad temporal sea $O(2^{n/2})$. Primero, generamos listas ordenadas $S_A$ y $S_B$, lo que se puede hacer en tiempo $O(2^{n/2})$ utilizando una técnica similar a la fusión. Después de esto, dado que las listas están ordenadas, podemos comprobar en tiempo $O(2^{n/2})$ si la suma $x$ puede ser creada a partir de $S_A$ y $S_B$.

## Navegación

- [Anterior: Pruning the Search.md](./Pruning%20the%20Search.md)