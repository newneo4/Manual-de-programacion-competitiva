## Plantilla de codigo C++
Un ejemplo típico de plantilla de código en C++ para programación competitiva se ve así:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    // la solución viene aquí
}
```

La línea #include al principio del código es una característica del compilador g++ que nos permite incluir toda la biblioteca estándar. Así, no es necesario incluir por separado bibliotecas como iostream, vector y algorithm, sino que están disponibles automáticamente.

La línea using declara que las clases y funciones de la biblioteca estándar pueden ser utilizadas directamente en el código. Sin la línea using tendríamos que escribir, por ejemplo, std::cout, pero ahora basta con escribir cout.

El código puede ser compilado usando el siguiente comando:

```bash
g++ -std=c++11 -O2 -Wall test.cpp -o test
```

Este comando produce un archivo binario test a partir del código fuente test.cpp. El compilador sigue el estándar C++11 (-std=c++11), optimiza el código (-O2) y muestra advertencias sobre posibles errores (-Wall).