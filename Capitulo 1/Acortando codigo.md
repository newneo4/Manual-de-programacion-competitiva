## Acortando el código

El código corto es ideal en la programación competitiva, porque los programas deben ser escritos lo más rápido posible. Debido a esto, los programadores competitivos a menudo definen nombres más cortos para los tipos de datos y otras partes del código.

### Nombres de Tipos

Usando el comando `typedef`, es posible darle un nombre más corto a un tipo de dato. Por ejemplo, el nombre `long long` puede ser abreviado como `ll`:

```cpp
typedef long long ll;
```

Después de esto, el código

```cpp
long long a = 123456789;
long long b = 987654321;
cout << a * b << "\n";
```

se puede acortar de la siguiente manera:

```cpp
ll a = 123456789;
ll b = 987654321;
cout << a * b << "\n";
```

El comando typedef también se puede usar con tipos más complejos. Por ejemplo, el siguiente código asigna el nombre vi para un vector de enteros y el nombre pi para un par que contiene dos enteros:

```cpp
typedef vector<int> vi;
typedef pair<int, int> pi;
```

### Macros
Otra forma de acortar el código es definir macros. Una macro significa que ciertas cadenas en el código se cambiarán antes de la compilación. En C++, las macros se definen usando la palabra clave #define.

Por ejemplo, podemos definir las siguientes macros:

```cpp
#define F first
#define S second
#define PB push_back
#define MP make_pair
```

Después de esto, el código

```cpp
v.push_back(make_pair(y1, x1));
v.push_back(make_pair(y2, x2));
int d = v[i].first + v[i].second;
```

se puede acortar de la siguiente manera:

```cpp
v.PB(MP(y1, x1));
v.PB(MP(y2, x2));
int d = v[i].F + v[i].S;
```

Una macro también puede tener parámetros, lo que permite acortar bucles y otras estructuras. Por ejemplo, podemos definir la siguiente macro:

```cpp
#define REP(i, a, b) for (int i = a; i <= b; i++)
```

Despues de esto el codigo

```cpp
for (int i = 1; i <= n; i++) {
    search(i);
}
```
se puede acortar de la siguiente manera:

```cpp
REP(i, 1, n) {
    search(i);
}
```

A veces, las macros pueden causar errores que pueden ser difíciles de detectar. Por ejemplo, considera la siguiente macro que calcula el cuadrado de un número:

```cpp
#define SQ(a) a * a
```

Esta macro no siempre funciona como se espera. Por ejemplo, el código

```cpp
cout << SQ(3 + 3) << "\n";
```

corresponde al codigo

```cpp
cout << 3 + 3 * 3 + 3 << "\n"; // 15
```

Una versión mejorada de la macro es la siguiente:

```cpp
#define SQ(a) (a) * (a)
```

Ahora el codigo 

```cpp
cout << SQ(3 + 3) << "\n";
```

corresponde al código

```cpp
cout << (3 + 3) * (3 + 3) << "\n"; // 36
```

## Navegación
- [Anterior: Trabajando con numeros.md](./Trabajando%20con%20numeros.md)
- [Siguiente: Matematicas.md](./Matematicas.md)
