## Generación de Permutaciones

A continuación, consideramos el problema de generar todas las permutaciones de un conjunto de *n* elementos. Por ejemplo, las permutaciones de {0,1,2} son (0,1,2), (0,2,1), (1,0,2), (1,2,0), (2,0,1) y (2,1,0). Nuevamente, hay dos enfoques: podemos usar la recursión o recorrer las permutaciones de forma iterativa.

### Método 1

Al igual que los subconjuntos, las permutaciones pueden generarse utilizando recursión. La siguiente función `search` recorre las permutaciones del conjunto {0,1,...,n-1}. La función construye un vector `permutation` que contiene la permutación, y la búsqueda comienza cuando la función se llama sin parámetros.

```cpp
void search(){
    if(permutation.size() == n){
        //procesar la permutacion
    }
    else{
        for(int i = 0; i < n; i++){
            if(chosen[i]) continue;
            chosen[i] = true;
            permutation.push_back(i);
            search();
            chosen[i] = false;
            permutation.pop_back();
        }
    }
}
```

Cada llamada a la función agrega un nuevo elemento a `permutation`. El array `chosen` indica qué elementos ya están incluidos en la permutación. Si el tamaño de `permutation` es igual al tamaño del conjunto, se ha generado una permutación.

### Método 2

Otro método para generar permutaciones es comenzar con la permutación {0,1,...,n-1} y usar repetidamente una función que construya la siguiente permutación en orden creciente. La biblioteca estándar de C++ contiene la función `next_permutation` que se puede usar para esto:

```cpp
vector<int>permutations;

for(int i = 0; i < n; i++){
    permutations.push_back(i);
}

do{
    //proccess permutation
}
while(next_permutation(permutation.begin(), permutation.end()));
```

## Navegación

- [Anterior: Generando Subconjuntos.md](./Generando%20Subconjuntos.md)
- [Siguiente: Backtracking.md](./Backtracking.md)
