# Números de Fibonacci y su complejidad.
La llamada sucesión de los números de Fibonacci
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ... 
que aparece por primera vez en el célebre, Liber abaci (1202), publicado por Leonardo Pisano, como solución a un problema de reproducción de conejos, satisface la ecuación en recurrencia lineal
Fn = Fn-1 + Fn-2 
donde F1 = 1 = F2

Claramente, no es la única sucesión de números, solución de la misma ecuación en recurrencia. Por ejemplo, la sucesión 
1, 3, 4, 7, 11, 18, 29, 47, 76, ... 
llamados los números de Lucas (matemático francés, 1842-1891). También satisfacen la misma ecuación en recurrencia. Pero la diferencia está en los dos primeros términos, que en este caso son F1 = 1 ; F2 = 3.

Como los siguientes valores de una tal sucesión F1, F2, F3, ... están determinados por los dos primeros. Hay tantas sucesiones solución como parejas de números F1 = a ; F2 = b.

## Programación recursiva
Si queremos programar una función que calcule el n-ésimo término, Fn, de una de estas soluciones. La primera aproximación es precísamente recursiva. Por ejemplo, hoy día, casi todos los lenguajes de alto nivel, admiten las tres siguientes líneas que implementan el cálculo de los números de Fibonacci, con pocas diferencias de sintaxis

F(1) = 1;

F(2) = 1;

F(n) = F(n-1) + F(n-2);

El problema es su complejidad. No sólo en espacio. Ya que todas las llamadas anteriores, a la propia función, han de recordarse, calcularse y asignarse para poder hallar F(n). Sino también en número de operaciones elementales. Que se traduce en complejidad de tiempo. Ya que se suman todas las operaciones elementales necesarias para calcular todos los anteriores.

Veamos una aproximación ingenua, pero precisa, al cálculo de la complejidad de la función recursiva anterior. Si llamamos S(n) al número de sumas necesarias para hallar F(n). Para los primeros valores se tiene 
S(1) = 0 = S(2), S(3)=1, S(4) = 2, S(5) = 4, S(6) = 7, ... 
y en general por inducción, el número de sumas para calcular F(n) es igual a 
S(n) = S(n-1) + S(n-2) + 1 
Su crecimiento es mas rápido que el la función original. Ya que se obtiene cláramente por inducción que 
F(n-2) < S(n)

## Complejidad exponencial: explicación
Para explicar la complejidad exponencial, calcularemos las raíces de la ecuación característica asociada a la ecuación en recurrencia F(n) = F(n-1) + F(n-2). 
X^2 = x + 1 
o sea, las raíces de x^2 - x - 1 = 0

Una de ellas, es el llamado número de oro (Golden Ratio), cuyo valor aproximado es 1.61803 y su valor exacto es c = (1+√5)/2.

Se verifica c^2 = c + 1 y por tanto, para todo n mayor que dos, también 
C^n = c^n-1 + c^n-2

O sea, la progresión geométrica {cn} satisface la misma ecuación en recurrencia que la función de Fibonacci F(n) = F(n-1) + F(n-2). Ahora, por inducción

Como, c^0 = 1 = F(2), c = c^1 < 2 = F(3). 
obtenemos que c^n-2 < F(n)

En conclusión, la función de Fibonacci crece, como mínimo, exponencialmente. Ahora, enlazando las dos desigualdades, para todo n se tiene

C^n-4 < F(n-2) < S(n)

y también la función S(n) crece, como mínimo, exponencialmente.

Por tanto, la programación recursiva de la función de Fibonacci tiene una complejidad, como mínimo, exponencial. Y eso, independientemente, de lo bien que gestiene el compilador o intérprete correspondiente la programación recursiva.

### Referencia:
https://www.ugr.es/~eaznar/fibo.htm
