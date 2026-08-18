# 2 Primeros Pasos

Este capítulo te familiarizará con los entornos de trabajo que se usaremos a lo largo de este libro para pensar sobre el diseño y análisis de algoritmos. Es autónomo como tal, pero incluye muchas referencias de material que introduciremos en el Capítulo 3 y 4. (También contiene muchos resúmenes, para los cuales el Apéndice A muestra como resolver).

Comenzamos por examinar el algoritmo de ordenamiento por inserción para resolver el problema de ordenamiento introducido en el Capítulo 1. Definimos "pseudocódigo" que podría ser familiar para ti si has hecho programación alguna vez, y lo usamos para mostrar cómo debemos especificar nuestros algorimos. Habiendo especificado el algoritmo de ordenamiento por inserción, después comprobamos que ordena correctamente, y analizamos su tiempo de procesamiento. El análisis agrega una notación que se enfoca en cómo ese tiempo incrementa con el número de elementos a ser ordenados. Continuando nuestra discución del ordenamiento por inserción, introducimos la aproximación de divide y conquista al diseño de algoritmos y lo usamos para desarrollar un algoritmo llamado ordenamiento por fusión. Terminamos con un análisis del tiempo de procesamiento del ordenamiento por fusión.

## 2.1 Ordenamiento por inserción

Nuestro primer algoritmo, el de ordenamiento por inserción, resuelve el problema de ordenamiento introducido en el Capítulo 1:

**Entrada:** Una secuencia de $n$ números $\langle a_1, a_2,\dots, a_n \rangle$.

**Salida:** Una permutación (reordenamiento) $\langle a'_1, a'_2, \dots, a'_n \rangle$ de la secuencia de salida tal que $a'_1 \leq a'_2 \leq \dots \leq a'_n$.

Los números que queremos ordenar también son conocidos como **claves**. Aunque conceptualmente estamos ordenando una secuencia, la entrada nos llega en la forma de un arreglo con $n$ elementos.

En este libro, normalmente describimos algoritmos como programas escritos en **pseudocódio** que es similar en muchos aspectos a C, C++, Java, Python o Pascal. Si no conoces sobre cualquiera de estos lenguajes, podrías tener un pequeño problema leyendo nuestros algoritmos. Lo que separa al pseudocódigo del código "real" es que, en pseudocódigo empleamos cualquier método de expresión que sea más claro y conciso a especificar un algoritmo dado. Algunas veces, el método más claro es el Inglés, así que no te sorprendas si te cruzas con una frase o una oración en Inglés incorporada sin una sección de código "real". Otra diferencia entre pseudocódigo y código real es que el pseudocódigo por lo general no se ocupa en cuestiones de ingeniería de software. Aspectos de abstracción de datos, modularidad, y gestión de errores son regularmente ignorados con el propósito de transmitir la esencia del algoritmo más consistentemente. 

Comenzamos con el **ordenamiento por inserción,** el cual es un algoritmo para ordenar un número pequeño de elementos. El ordenamiento por inserción trabaja de la manera en que mucha gente ordena su mano en un juego de cartas. Comenzamos con la mano izquierda vacía y las cartas boca abajo en la mesa. Después, retiramos de la mesa una carta a la vez y la añadimos a la mano izquierda. Para encontrar la posición correcta de una carta, la comparamos con cada una de las cartas que ya tengamos en la mano, de derecha a izquierda, como se ilustra en la Figura 2.1.

![Figura 2.1. Imagen de ejemplo para el ordenamiento de carta en la mano de un juego de cartas](imagenes/Figura2.1.png)

**Figura 2.1** Ordenamiento de una mano de cartas usando el método por inserción.

En todo momento, las cartas mantenidas en la mano izquierda están ordenadas, y esas cartas estaban originalmente en la cima de la pila de cartas en la mesa. 

Presentamos nuestro pseudocódigo para el ordenamiento por inserción como un procedimiento llamado $ORDENAMIENTO-INSERCION$, que toma como parámetro un arreglo $A[1..n]$ conteniendo una secuencia de tamaño $n$ que tiene que ser acomodado en orden. (En el código, el número de $n$ elementos en $A$ es denotado por $A.lenght.$) El algoritmo ordena los números de entrada **en su lugar**: reordena los números dentro del arreglo $A$, con por lo mucho un número constante de ellos guardados fuera del arrego en cualquier momento. El arreglo de entrada $A$ contiene la secuencia ordenada de salida cuando el prodecimiento $ORDENAMIENTO-INSERCION$ termina.

![Figura 2.2. Imagen del proceso que realiza ORDENAMIENTO-INCERSION(A, B, C, D, E y F)](imagenes/Figura2.2.png)

**Figura 2.2** La operación ORDENAMIENTO-INCERSION en el arreglo $A = \langle 5, 2, 4, 6, 1, 3 \rangle$. Los índices aparecen sobre los rectángulos, y los valores guardados en las posiciones del arreglo aparecen dentro de los rectángulos. **(a)-(e)** Las iteraciones del bucle **for** en las líneas 1-8. En cada iteración, el rectángulo negro guarda la *key* tomada de $A[j]$, el cuál es comparado con el valor sombreado a su izquiera en la prueba de la línea 5. Las flechas sombreadas muestran valores del arreglo que se movieron una posición a la derecha en la línea 6, y las flechas negras indican dónde se posiciona *key* en la línea 8. **(f)** El arreglo final ordenado.

```text
ORDENAMIENTO-INSERCION (A)
1   for j = 2 o A.length
2       key = A[j]
3       // Insert A[j] dentro de la secuencia guardada A[1..j - 1].
4       i = j - 1
5       while i > 0 y A[i] > key
6           A[i + 1] = A[i]
7           i = i - 1
8       A[i + 1] = key
```

### Invariantes de bucle y la exactitud del ordenamiento por inserción

La figura 2.2 nos muestra cómo este algoritmo funciona para $A = \langle 5, 2, 4, 6, 1, 3 \rangle$. El índice $j$ indica la "carta actual" siendo agregada a la mano. Al comienzo de cada iteración para el bucle **for**, el cuál es indexado por $j$, el subarreglo que consiste de los elementos $A[1..j - 1]$ constituye las cartas ordenadas actualmente en la mano, y el subarreglo restante $A[j + 1..n]$ corresponde a la pila de cartas que siguen en la mesa. De hecho, los elementos $A[1..j - 1]$ son los elementos *originalemente* en la posición 1 a través de $j - 1$, pero ahora de forma ordenada. Denominamos a estas propiedades de $A[1..j - 1]$ formalmente como una **invariante de bucle:**

Al comienzo de cada iteración para el bucle **for** de las líneas 1-8, el subarreglo $A[1..j - 1]$ consta de los elementos originalemente en $A[1..j - 1]$, pero de forma ordenada.

Utilizamos invariantes de bucle para ayudarnos a entender porqué un algoritmo es correcto. Debemos mostrar tres cosas acerca de una invariante de bucle:

**Inicialización:** Es cierto antes de la primera iteración del bucle.

**Mantenimiento:** Es cierto antes de una iteración del bucle, permanece cierto antes de la siguiente iteración.

**Terminación:** Cuando el bucle finaliza, la invariante nos da una propiedad útil que ayuda a mostrar que el algoritmo es correcto.

Cuando las primeras dos propiedades se mantienen, la invariante del bucle es cierta antes de cada iteración del bucle. (Claro, somos libres de usar hechos establecidos fuera de la invariante del bucle misma para probar que la invariante de bucle permanece cierta antes de cada iteración.) Nota la similitud a la inducción matemática, donde para probar que una propiedad se mantiene, pruebas un caso base y un caso inductivo. Aquí, mostrar que la invariante se mantiene antes de cada iteración corresponde al caso base y mostrar que la invariante se mantiene de iteración a iteración corresponde al caso inductivo. 

La tercera propiedad es, tal vez, la más importante, pues estamos usando la invariante de bucle para mostrar la exactitud. Típicamente, usamos la invariante de bucle junto con la condición que causó la terminación del bucle. La propiedad de terminación es diferente a cómo normalmente la usamos en la inducción matemática, en la que aplicamos el caso inductivo infinitamente; aquí, detenemos la "inducción" cuando el bucle termina.

Veamos cómo estas propiedades se mantienen para el ordenamiento por inserción.

**Inicialización:** Comenzamos por mostrar que la invariante de bucle se mantiene antes de la primera iteración, cuando $j = 2$.[^1] El subarreglo $A[1..j - 1]$, entonces, consiste simplemente solo del elemento $A[1]$ que es, de hecho, el elemento original en $A[1]. Además, este subarreglo está ordenado (trivialmente, claro), los que nos muestra que la invariante de bucle se mantiene antes de la primera iteración del bucle.

[^1]: Cuando el bucle es un bucle **for**, el momento en el que verificamos la invariante de bucle justo antes de la primera iteración está inmediatamente después de la asignación inicial a la variable contador de bucle y justo antes de la primera prueba en el encabezado del bucle. El el caso de $ORDENAMIENTO-INSERCION$, esta vez está después de la asignación de 2 de las variables $j$ pero antes de la primera prueba que determina $j \leq A.length$.

**Mantenimiento:** Después, abordamos la segunda propiedad: mostramos que cada iteración mantiene la invariante del bucle. Informalmente, el cuerrto del bucle **for** funciona moviendo $A[j - 1]$, $A[j - 2]$, A[j - 3], y así en una posición a la derecha hasta que encuentre la posición apropiada para $A[j]$ (líneas 4-7), en la cuál inserta el valor de $A[j]$ (línea 8). El subarreglo $A[1..j]$ entonces, consiste de los elementos originalmente en $A[1..j]$, pero acomodados en orden. El incremento de $j$ para la siguiente iteración del bucle **for** entonces preserva la invariante de bucle.

Un trato más formal de la segunda propiedad requeriría declarar y mostrar una invariante de bucle para el bucle **while** de las líneas 5-7. En este punto, como sea, preferimos no estancarnos en tal formalismo, asímismo confiamos en nuestro análisis informal para mostrar que la segunda propiedad se mantiene para bucles exteriores.

**Terminación:** Finalmente, examinamos qué pasa cuando el bucle termina. La condición que causa que el bucle **for** termina es $j > A.length = n$. Debido a que cada iteración del loop incrementa $j$ en 1, debemos tener $j = n + 1$ en ese momento. Sustituyendo $n + 1$ para $j$ en la redacción de la invariante de bucle, tenemos que el arreglo $A[1..n]$ consiste de elementos originalmente en $A[1..n]$, pero acomodados en orden. Si observamos que el subarreglo $A[1..n]$ es el arreglo completo, concluimos que el arreglo entero está ordenado. Por lo tanto, el algoritmo es correcto.

Usaremos este método de la invariante de bucle para mostrar la exactitud posteriormente en este capítulo, así como en otros capítulos también.

### Convenciones en pseudocódigo

Usamos las siguientes convenciones en nuestro pseudocódigo

- La identación indica estructuras de bloques. Por ejemplo, el cuerpo del bucle **for** que comienza en la línea 1 consiste de las líneas 2-8, y el cuerpo del bucle **while** que comienza en la línea 5 contiene las líneas 6-7 pero no la línea 8. Nuestro estilo de identación aplica también a las declaraciones **if-else**. Usando identación en lugar de los indicadores convencionales de estrucutras de bloques, tales como las declaraciones **begin** y **end**, reduce enormenente el desorden mientras conserva, o incluso mejora, la claridad.

-- TODO : Continuar en la página 17