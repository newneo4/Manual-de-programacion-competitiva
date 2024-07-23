## Trabajando con números

### Numeros Enteros

El tipo de entero más utilizado en la programación competitiva es `int`, que es un tipo de 32 bits con un rango de valores de −2³¹ a 2³¹ − 1 o aproximadamente −2 × 10⁹ a 2 × 10⁹. Si el tipo `int` no es suficiente, se puede usar el tipo de 64 bits `long long`. Tiene un rango de valores de −2⁶³ a 2⁶³ − 1 o aproximadamente −9 × 10¹⁸ a 9 × 10¹⁸.

El siguiente código define una variable `long long`:

```cpp
long long x = 123456789123456789LL;
```

El sufijo LL significa que el tipo del número es long long.

Un error común al usar el tipo long long es que el tipo int todavía se usa en alguna parte del código. Por ejemplo, el siguiente código contiene un error sutil:

```cpp
int a = 123456789;
long long b = a * a;
cout << b << "\n"; // -1757895751
```

Aunque la variable b es de tipo long long, ambos números en la expresión a * a son de tipo int y el resultado también es de tipo int. Debido a esto, la variable b contendrá un resultado incorrecto. El problema se puede resolver cambiando el tipo de a a long long o cambiando la expresión a (long long)a * a.

Generalmente, los problemas de concurso están configurados para que el tipo long long sea suficiente. Sin embargo, es bueno saber que el compilador g++ también proporciona un tipo de 128 bits __int128_t con un rango de valores de −2¹²⁷ a 2¹²⁷ − 1 o aproximadamente −10³⁸ a 10³⁸. Sin embargo, este tipo no está disponible en todos los sistemas de concurso.

### Aritmetica Modular
Denotamos por x mod m el residuo cuando x se divide por m. Por ejemplo, 17 mod 5 = 2, porque 17 = 3 × 5 + 2.

A veces, la respuesta a un problema es un número muy grande, pero es suficiente mostrarlo “módulo m”, es decir, el residuo cuando la respuesta se divide por m (por ejemplo, “módulo 10⁹ + 7”). La idea es que, incluso si la respuesta real es muy grande, es suficiente usar los tipos int y long long.

Una propiedad importante del residuo es que en adición, sustracción y multiplicación, el residuo se puede tomar antes de la operación:

```cpp
(a + b) mod m = (a mod m + b mod m) mod m
(a - b) mod m = (a mod m - b mod m) mod m
(a · b) mod m = (a mod m · b mod m) mod m
```
Así, podemos tomar el residuo después de cada operación y los números nunca se volverán demasiado grandes.

Por ejemplo, el siguiente código calcula n!, el factorial de n, módulo m:

```cpp
long long x = 1;
for (int i = 2; i <= n; i++) {
    x = (x * i) % m;
}
cout << x % m << "\n";
```
Generalmente, queremos que el residuo esté siempre entre 0 y m − 1. Sin embargo, en C++ y otros lenguajes, el residuo de un número negativo es cero o negativo. Una forma sencilla de asegurarse de que no haya residuos negativos es calcular primero el residuo como de costumbre y luego añadir m si el resultado es negativo:

```cpp
x = x % m;
if (x < 0) x += m;
```

Sin embargo, esto solo es necesario cuando hay sustracciones en el código y el residuo puede volverse negativo.

### Números de punto flotante
Los tipos de punto flotante habituales en la programación competitiva son el double de 64 bits y, como una extensión en el compilador g++, el long double de 80 bits. En la mayoría de los casos, double es suficiente, pero long double es más preciso.

La precisión requerida de la respuesta generalmente se da en la declaración del problema. Una forma sencilla de mostrar la respuesta es usar la función printf y dar el número de decimales en la cadena de formato. Por ejemplo, el siguiente código imprime el valor de x con 9 decimales:

```cpp
printf("%.9f\n", x);
```

Una dificultad al usar números de punto flotante es que algunos números no se pueden representar con precisión como números de punto flotante, y habrá errores de redondeo. Por ejemplo, el resultado del siguiente código es sorprendente:

```cpp
double x = 0.3 * 3 + 0.1;
printf("%.20f\n", x); // 0.99999999999999988898
```

Debido a un error de redondeo, el valor de x es un poco menor que 1, mientras que el valor correcto sería 1.

Es arriesgado comparar números de punto flotante con el operador ==, porque es posible que los valores deberían ser iguales pero no lo sean debido a errores de precisión. Una mejor manera de comparar números de punto flotante es asumir que dos números son iguales si la diferencia entre ellos es menor que ε, donde ε es un número pequeño.

En la práctica, los números se pueden comparar de la siguiente manera (ε = 10⁻⁹):

```cpp
if (abs(a - b) < 1e-9) {
    // a y b son iguales
}
```

Ten en cuenta que, aunque los números de punto flotante son imprecisos, los enteros hasta un cierto límite aún se pueden representar con precisión. Por ejemplo, usando double, es posible representar con precisión todos los enteros cuyo valor absoluto es como máximo 2⁵³.