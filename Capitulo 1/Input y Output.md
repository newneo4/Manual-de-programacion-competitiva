## Entrada y salida estándar

En la mayoría de los concursos, se utilizan flujos estándar para leer la entrada y escribir la salida. En C++, los flujos estándar son `cin` para la entrada y `cout` para la salida. Además, se pueden utilizar las funciones de C `scanf` y `printf`.

La entrada para el programa generalmente consiste en números y cadenas que están separados por espacios y saltos de línea. Se pueden leer desde el flujo `cin` de la siguiente manera:

```cpp
int a, b;
string x;
cin >> a >> b >> x;
```

Este tipo de código siempre funciona, suponiendo que hay al menos un espacio o salto de línea entre cada elemento en la entrada. Por ejemplo, el código anterior puede leer ambas entradas siguientes:

```code
123 456 monkey
```

```code
123 456 
monkey
```

El flujo `cout` se usa para la salida de la siguiente manera:

```cpp
int a = 123, b = 456;
string x = "monkey";
cout << a << " " << b << " " << x << "\n";
```
A veces, la entrada y salida son el punto de interes del programa. Las siguientes líneas al principio del código hacen que la entrada y salida sean más eficientes:

```cpp
ios::sync_with_stdio(0);
cin.tie(0);
```
Ten en cuenta que el salto de línea "\n" es más rápido que endl, porque endl siempre causa una operación de vaciado.

Las funciones de C scanf y printf son una alternativa a los flujos estándar de C++. Por lo general, son un poco más rápidas, pero también son más difíciles de usar. El siguiente código lee dos enteros de la entrada:

```cpp
int a, b;
scanf("%d %d", &a, &b);
```

El siguiente código imprime dos enteros:

```cpp
int a = 123, b = 456;
printf("%d %d\n", a, b);
```

A veces, el programa debe leer una línea completa de la entrada, posiblemente conteniendo espacios. Esto se puede lograr usando la función getline:

```cpp
string s;
getline(cin, s);
```
Si la cantidad de datos es desconocida, el siguiente bucle es útil:

```cpp
while (cin >> x) {
    // código
}
```
Este bucle lee elementos de la entrada uno tras otro, hasta que no haya más datos disponibles en la entrada.

En algunos sistemas de concursos, se utilizan archivos para la entrada y salida. Una solución sencilla para esto es escribir el código como de costumbre usando flujos estándar, pero agregar las siguientes líneas al principio del código:

```cpp
freopen("input.txt", "r", stdin);
freopen("output.txt", "w", stdout);
```

Después de esto, el programa lee la entrada del archivo "input.txt" y escribe la salida en el archivo "output.txt".

## Navegación
- [Anterior: Plantilla de codigo C++.md](./Plantilla%20de%20codigo%20C%2B%2B.md)
- [Siguiente: Trabajando con numeros.md](./Trabajando%20con%20numeros.md)
