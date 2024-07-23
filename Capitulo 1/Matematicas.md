## Matemáticas

Las matemáticas juegan un papel importante en la programación competitiva, y no es posible convertirse en un programador competitivo exitoso sin tener buenas habilidades matemáticas. Esta sección discute algunos conceptos y fórmulas matemáticas importantes que se necesitarán más adelante en el libro.

### Fórmulas de Suma

Cada suma de la forma

$$
    \sum_{x=1}^{n} x^k = 1^k + 2^k + 3^k + \ldots + n^k,
$$

donde \( k \) es un número entero positivo, tiene una fórmula en forma cerrada que es un polinomio de grado \( k + 1 \). Por ejemplo:

$$
\sum_{x=1}^{n} x = 1 + 2 + 3 + \ldots + n = \frac{n(n + 1)}{2}
$$

y

$$
\sum_{x=1}^{n} x^2 = 1^2 + 2^2 + 3^2 + \ldots + n^2 = \frac{n(n + 1)(2n + 1)}{6}.
$$

Una progresión aritmética es una secuencia de números en la que la diferencia entre dos números consecutivos es constante. Por ejemplo:

$$
3, 7, 11, 15
$$

## Progresiones Aritméticas y Geométricas

### Progresión Aritmética

Una progresión aritmética es una secuencia de números donde la diferencia entre dos números consecutivos es constante. Por ejemplo:

$$
3, 7, 11, 15
$$

es una progresión aritmética con diferencia constante de 4. La suma de una progresión aritmética se puede calcular usando la fórmula:

$$
a + \cdots + b \quad \text{(donde hay } n \text{ números)} = \frac{n(a + b)}{2}
$$

donde \( a \) es el primer número, \( b \) es el último número y \( n \) es la cantidad de números. Por ejemplo:

$$
3 + 7 + 11 + 15 = \frac{4 \cdot (3 + 15)}{2} = 36
$$

La fórmula se basa en el hecho de que la suma consta de \( n \) números y el valor promedio de cada número es \( \frac{a + b}{2} \).

### Progresión Geométrica

Una progresión geométrica es una secuencia de números donde la razón entre dos números consecutivos es constante. Por ejemplo:

$$
3, 6, 12, 24
$$

es una progresión geométrica con razón constante de 2. La suma de una progresión geométrica se puede calcular usando la fórmula:

$$
a + ak + ak^2 + \cdots + b = \frac{b k - a}{k - 1}
$$

donde \( a \) es el primer número, \( b \) es el último número y la razón entre números consecutivos es \( k \). Por ejemplo:

$$
3 + 6 + 12 + 24 = \frac{24 \cdot 2 - 3}{2 - 1} = 45
$$

Esta fórmula se puede derivar de la siguiente manera. Sea

$$
S = a + ak + ak^2 + \cdots + b
$$

Multiplicando ambos lados por \( k \), obtenemos

$$
kS = ak + ak^2 + ak^3 + \cdots + bk
$$

y resolviendo la ecuación

$$
kS - S = bk - a
$$

se obtiene la fórmula.
$$
1 + 2 + 4 + 8 + \cdots + 2^{n-1} = 2^n - 1
$$
## Casos Especiales y Estimaciones de Sumatorias

### Progresión Geométrica Especial

Un caso especial de la suma de una progresión geométrica es la siguiente fórmula:

$$
1 + 2 + 4 + 8 + \cdots + 2^{n-1} = 2^n - 1
$$

### Suma Armónica

Una suma armónica es una suma de la forma:

$$
\sum_{x=1}^{n} \frac{1}{x} = 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n}
$$

Un límite superior para una suma armónica es $log_2(n) + 1$. Es decir, podemos modificar cada término $\frac{1}{k}$ de manera que k se convierta en la potencia de dos más cercana que no exceda a k.

Por ejemplo, cuando $n = 6$, podemos estimar la suma de la siguiente manera:

$$
1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \frac{1}{5} + \frac{1}{6} \leq 1 + \frac{1}{2} + \frac{1}{2} + \frac{1}{4} + \frac{1}{4} + \frac{1}{4}
$$

Este límite superior consta de $\log_2(n) + 1$ partes ($1$, $2 \cdot \frac{1}{2}$, $4 \cdot \frac{1}{4}$, etc.), y el valor de cada parte es como máximo 1.

## Teoría de Conjuntos

Un conjunto es una colección de elementos. Por ejemplo, el conjunto

$$
X = \{2, 4, 7\}
$$

contiene los elementos 2, 4 y 7. El símbolo $\emptyset$ denota un conjunto vacío, y $|S|$ denota el tamaño de un conjunto $S$, es decir, el número de elementos en el conjunto. Por ejemplo, en el conjunto anterior, $|X| = 3$.

Si un conjunto $S$ contiene un elemento $x$, escribimos $x \in S$, y en caso contrario, escribimos $x \notin S$. Por ejemplo, en el conjunto anterior,

$$
4 \in X \text{ y } 5 \notin X.
$$

Se pueden construir nuevos conjuntos utilizando operaciones de conjuntos:

- La **intersección** $A \cap B$ consiste en los elementos que están en ambos conjuntos $A$ y $B$. Por ejemplo, si $A = \{1, 2, 5\}$ y $B = \{2, 4\}$, entonces

$$
A \cap B = \{2\}.
$$

- La **unión** $A \cup B$ consiste en los elementos que están en $A$, en $B$, o en ambos. Por ejemplo, si $A = \{3, 7\}$ y $B = \{2, 3, 8\}$, entonces

$$
A \cup B = \{2, 3, 7, 8\}.
$$

- El **complemento** $\overline{A}$ consiste en los elementos que no están en $A$. La interpretación de un complemento depende del conjunto universal, que contiene todos los elementos posibles. Por ejemplo, si $A = \{1, 2, 5, 7\}$ y el conjunto universal es $\{1, 2, \ldots, 10\}$, entonces

$$
\overline{A} = \{3, 4, 6, 8, 9, 10\}.
$$

- La **diferencia** $A \setminus B = A \cap \overline{B}$ consiste en los elementos que están en $A$ pero no en $B$. Nota que $B$ puede contener elementos que no están en $A$. Por ejemplo, si

$$
A = \{2, 3, 7, 8\} \text{ y } B = \{3, 5, 8\},
$$

  entonces

$$
A \setminus B = \{2, 7\}.
$$

Si cada elemento de $A$ también pertenece a $S$, decimos que $A$ es un subconjunto de $S$, denotado por $A \subseteq S$. Un conjunto $S$ siempre tiene $2^{|S|}$ subconjuntos, incluido el conjunto vacío. Por ejemplo, los subconjuntos del conjunto $\{2, 4, 7\}$ son

$$
\emptyset, \{2\}, \{4\}, \{7\}, \{2, 4\}, \{2, 7\}, \{4, 7\} \text{ y } \{2, 4, 7\}.
$$

Algunos conjuntos comúnmente usados son $\mathbb{N}$ (números naturales), $\mathbb{Z}$ (enteros), $\mathbb{Q}$ (números racionales) y $\mathbb{R}$ (números reales). El conjunto $\mathbb{N}$ puede definirse de dos maneras, dependiendo de la situación: ya sea $\mathbb{N} = \{0, 1, 2, \ldots\}$ o $\mathbb{N} = \{1, 2, 3, \ldots\}$.

También podemos construir un conjunto usando una regla de la forma

$$
\{ f(n) : n \in S \},
$$

donde $f(n)$ es alguna función. Este conjunto contiene todos los elementos de la forma $f(n)$, donde $n$ es un elemento en $S$. Por ejemplo, el conjunto

$$
X = \{2n : n \in \mathbb{Z} \}
$$

contiene todos los enteros pares.

## Lógica

El valor de una expresión lógica es verdadero (1) o falso (0). Los operadores lógicos más importantes son $\neg$ (negación), $\land$ (conjunción), $\lor$ (disyunción), $\Rightarrow$ (implicación) y $\Leftrightarrow$ (equivalencia). La siguiente tabla muestra los significados de estos operadores:

$$
\begin{array}{ccccc}
A & B & \neg A & \neg B & A \land B & A \lor B & A \Rightarrow B & A \Leftrightarrow B \\
\hline
0 & 0 & 1 & 1 & 0 & 0 & 1 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 & 0 \\
1 & 0 & 0 & 1 & 0 & 1 & 0 & 0 \\
1 & 1 & 0 & 0 & 1 & 1 & 1 & 1 \\
\end{array}
$$

La expresión $\neg A$ tiene el valor opuesto de $A$. La expresión $A \land B$ es verdadera si tanto $A$ como $B$ son verdaderos, y la expresión $A \lor B$ es verdadera si $A$ o $B$ o ambos son verdaderos. La expresión $A \Rightarrow B$ es verdadera si siempre que $A$ sea verdadero, $B$ también lo es. La expresión $A \Leftrightarrow B$ es verdadera si $A$ y $B$ son ambos verdaderos o ambos falsos.

Un predicado es una expresión que es verdadera o falsa dependiendo de sus parámetros. Los predicados suelen ser denotados por letras mayúsculas. Por ejemplo, podemos definir un predicado $P(x)$ que es verdadero exactamente cuando $x$ es un número primo. Usando esta definición, $P(7)$ es verdadero pero $P(8)$ es falso.

Un cuantificador conecta una expresión lógica con los elementos de un conjunto. Los cuantificadores más importantes son $\forall$ (para todo) y $\exists$ (existe). Por ejemplo,

$$
\forall x (\exists y (y < x))
$$

significa que para cada elemento $x$ en el conjunto, existe un elemento $y$ en el conjunto tal que $y$ es menor que $x$. Esto es verdadero en el conjunto de los enteros, pero falso en el conjunto de los números naturales.

Usando la notación descrita arriba, podemos expresar muchos tipos de proposiciones lógicas. Por ejemplo,

$$
\forall x \left((x > 1 \land \neg P(x)) \Rightarrow \left(\exists a (\exists b (a > 1 \land b > 1 \land x = ab))\right)\right)
$$

significa que si un número $x$ es mayor que 1 y no es un número primo, entonces existen números $a$ y $b$ que son mayores que 1 y cuyo producto es $x$. Esta proposición es verdadera en el conjunto de los enteros.

## Funciones

La función $\lfloor x \rfloor$ redondea el número $x$ hacia abajo a un entero, y la función $\lceil x \rceil$ redondea el número $x$ hacia arriba a un entero. Por ejemplo,

$$
\lfloor 3/2 \rfloor = 1 \text{ y } \lceil 3/2 \rceil = 2.
$$

Las funciones $\text{min}(x_1, x_2, \ldots, x_n)$ y $\text{max}(x_1, x_2, \ldots, x_n)$ dan el valor más pequeño y más grande de los valores $x_1, x_2, \ldots, x_n$. Por ejemplo,

$$
\text{min}(1, 2, 3) = 1 \text{ y } \text{max}(1, 2, 3) = 3.
$$

## Factoriales

El factorial $n!$ puede definirse como:

$$
n! = \prod_{x=1}^{n} x = 1 \cdot 2 \cdot 3 \cdots \cdot n
$$

o recursivamente como:

$$
0! = 1
$$

$$
n! = n \cdot (n - 1)!
$$

## Números de Fibonacci

Los números de Fibonacci surgen en muchas situaciones. Pueden definirse recursivamente de la siguiente manera:

$$
f(0) = 0
$$

$$
f(1) = 1
$$

$$
f(n) = f(n - 1) + f(n - 2)
$$

Los primeros números de Fibonacci son:

$$
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, \ldots
$$

También existe una fórmula cerrada para calcular los números de Fibonacci, conocida como la fórmula de Binet:

$$
f(n) = \frac{(1 + \sqrt{5})^n - (1 - \sqrt{5})^n}{2^n \sqrt{5}}
$$

## Logaritmos

El logaritmo de un número $x$ se denota como $\log_k(x)$, donde $k$ es la base del logaritmo. Según la definición, $\log_k(x) = a$ exactamente cuando $k^a = x$.

Una propiedad útil de los logaritmos es que $\log_k(x)$ es el número de veces que debemos dividir $x$ por $k$ antes de llegar al número 1. Por ejemplo, $\log_2(32) = 5$ porque se necesitan 5 divisiones por 2:

$$
32 \rightarrow 16 \rightarrow 8 \rightarrow 4 \rightarrow 2 \rightarrow 1
$$

Los logaritmos son a menudo utilizados en el análisis de algoritmos, ya que muchos algoritmos eficientes dividen algo a la mitad en cada paso. Por lo tanto, podemos estimar la eficiencia de tales algoritmos usando logaritmos.

La fórmula del logaritmo de un producto es:

$$
\log_k(ab) = \log_k(a) + \log_k(b)
$$

y, en consecuencia,

$$
\log_k(x^n) = n \cdot \log_k(x)
$$

Además, la fórmula del logaritmo de un cociente es:

$$
\log_k \left( \frac{a}{b} \right) = \log_k(a) - \log_k(b)
$$

Otra fórmula útil es:

$$
\log_u(x) = \frac{\log_k(x)}{\log_k(u)}
$$

Utilizando la propiedad de los logaritmos, es posible calcular logaritmos en cualquier base si se puede calcular logaritmos en alguna base fija. 

El logaritmo natural $\ln(x)$ de un número x es un logaritmo con base $e \approx 2.71828$.

Otra propiedad útil de los logaritmos es que el número de dígitos de un entero $x$ en base $b$ es:

$$
\left\lfloor \log_b(x) \right\rfloor + 1
$$

Por ejemplo, la representación de 123 en base 2 es 1111011 y $\left\lfloor \log_2(123) \right\rfloor + 1 = 7$.