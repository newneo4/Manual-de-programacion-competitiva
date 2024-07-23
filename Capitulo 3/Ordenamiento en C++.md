### Ordenación en C++

Casi nunca es una buena idea usar un algoritmo de ordenación casero en un concurso, porque hay buenas implementaciones disponibles en los lenguajes de programación. Por ejemplo, la biblioteca estándar de C++ contiene la función `sort` que se puede usar fácilmente para ordenar arrays y otras estructuras de datos.

Hay muchos beneficios en usar una función de biblioteca. Primero, ahorra tiempo porque no es necesario implementar la función. En segundo lugar, la implementación de la biblioteca es ciertamente correcta y eficiente: no es probable que una función de ordenación casera sea mejor.

En esta sección veremos cómo usar la función `sort` de C++. El siguiente código ordena un vector en orden ascendente:

```cpp
std::vector<int> v = {4, 2, 5, 3, 5, 8, 3};
std::sort(v.begin(), v.end());
```

Después de la ordenación, el contenido del vector será [2, 3, 3, 4, 5, 5, 8]. El orden de ordenación predeterminado es ascendente, pero es posible un orden inverso de la siguiente manera

```cpp
std::sort(v.rbegin(), v.rend());
```

Un array ordinario se puede ordenar de la siguiente manera:

```cpp
int n = 7; // Tamaño del array
int a[] = {4, 2, 5, 3, 5, 8, 3};
sort(a, a + n);
```
El siguiente código ordena la cadena `s`:

```cpp
string s = "monkey";
sort(s.begin(), s.end());
```

### Operadores de Comparación

La función `sort` requiere que se defina un operador de comparación para el tipo de datos de los elementos que se van a ordenar. Al ordenar, este operador se utilizará siempre que sea necesario determinar el orden de dos elementos.

La mayoría de los tipos de datos en C++ tienen un operador de comparación incorporado, y los elementos de esos tipos se pueden ordenar automáticamente. Por ejemplo, los números se ordenan según sus valores y las cadenas se ordenan en orden alfabético.

Los pares (`pair`) se ordenan principalmente según sus primeros elementos (`first`). Sin embargo, si los primeros elementos de dos pares son iguales, se ordenan según sus segundos elementos (`second`):

```cpp
vector<pair<int, int>> v;
v.push_back({1, 5});
v.push_back({2, 3});
v.push_back({1, 2});
sort(v.begin(), v.end());
```

Después de esto, el orden de los pares es (1, 2), (1, 5) y (2, 3).

De manera similar, las tuplas (`tuple`) se ordenan principalmente por el primer elemento, secundariamente por el segundo elemento, etc.:

```cpp
vector<tuple<int, int, int>> v;
v.push_back({2, 1, 4});
v.push_back({1, 5, 3});
v.push_back({2, 1, 3});
sort(v.begin(), v.end());
```

Después de esto, el orden de las tuplas es (1, 5, 3), (2, 1, 3) y (2, 1, 4).

### Estructuras Definidas por el Usuario
Las estructuras definidas por el usuario no tienen un operador de comparación automáticamente. El operador debe definirse dentro de la estructura como una función operator<, cuyo parámetro es otro elemento del mismo tipo. El operador debe devolver true si el elemento es menor que el parámetro, y false en caso contrario.

Por ejemplo, la siguiente estructura P contiene las coordenadas x e y de un punto. El operador de comparación se define para que los puntos se ordenen principalmente por el valor de x y de manera secundaria por el valor y:

```cpp
struct P {
    int x, y;
    bool operator<(const P &p) {
        if (x != p.x) return x < p.x;
        else return y < p.y;
    }
};
```

### Funciones de Comparación

También es posible proporcionar una función de comparación externa a la función `sort` como una función de retorno de llamada. Por ejemplo, la siguiente función de comparación `comp` ordena cadenas principalmente por longitud y secundariamente por orden alfabético:

```cpp
bool comp(const string& a, const string& b) {
    if (a.size() != b.size()) return a.size() < b.size();
    return a < b;
}
```

Ahora el vector de strings puede ser ordenado de la siguiente manera:

```cpp
sort(v.begin(), v.end(), comp);
```

