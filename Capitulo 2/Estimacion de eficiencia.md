## Estimación de la Eficiencia

Calcular la complejidad temporal de un algoritmo permite verificar, antes de implementar el algoritmo, si es lo suficientemente eficiente para el problema. El punto de partida para las estimaciones es el hecho de que una computadora moderna puede realizar algunos cientos de millones de operaciones por segundo.

Por ejemplo, supongamos que el tiempo límite para un problema es de un segundo y el tamaño de la entrada es $n = 10^5$. Si la complejidad temporal es O($n^2$), el algoritmo realizará aproximadamente $(10^5)^2 = 10^{10}$ operaciones. Esto debería tomar al menos unos segundos, por lo que el algoritmo parece ser demasiado lento para resolver el problema.

Por otro lado, dado el tamaño de la entrada, podemos intentar adivinar la complejidad temporal requerida del algoritmo que resuelve el problema. La siguiente tabla contiene algunas estimaciones útiles asumiendo un límite de tiempo de un segundo.

| Tamaño de entrada | Complejidad temporal requerida |
|-------------------|--------------------------------|
| $n \leq 10$       | O($n!$)                         |
| $n \leq 20$       | O($2^n$)                        |
| $n \leq 500$      | O($n^3$)                        |
| $n \leq 5000$     | O($n^2$)                        |
| $n \leq 10^6$     | O($n \log n$) o O($n$)          |
| $n$ es grande     | O(1) o O($\log n$)              |

Por ejemplo, si el tamaño de la entrada es $n = 10^5$, es probable que se espere que la complejidad temporal del algoritmo sea O($n$) o O($n \log n$). Esta información facilita el diseño del algoritmo, ya que descarta enfoques que producirían un algoritmo con una complejidad temporal peor.

Aún así, es importante recordar que la complejidad temporal es solo una estimación de la eficiencia, ya que oculta los factores constantes. Por ejemplo, un algoritmo que se ejecuta en tiempo O($n$) puede realizar $n/2$ o $5n$ operaciones. Esto tiene un efecto importante en el tiempo de ejecución real del algoritmo.