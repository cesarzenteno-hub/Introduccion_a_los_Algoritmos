# 1 El Papel de los Algoritmos en la Informatica

¿Qué son los algoritmos? ¿Por qué vale la pena estudiarlos? ¿Cuál es el papel
de los algoritmos en relación con otras tecnologías utilizadas en las computadoras? En este capítulo,
responderemos estas preguntas.

## 1.1 Algoritmos

De manera informal, un ***algoritmo*** es cualquier procedimiento computacional bien definido que toma
un valor o un conjunto de valores como ***entrada***  y produce un valor o un conjunto de valores como
***salida*** . Por lo tanto, un algoritmo es una secuencia de pasos computacionales que transforman la
entrada en la salida.
También podemos considerar un algoritmo como una herramienta para resolver un ***problema computacional***  bien especificado. 
El enunciado del problema especifica en términos generales la relación ***entrada/salida*** deseada. 
El algoritmo describe un procedimiento computacional específico para lograr esa relación entrada/salida.
Por ejemplo, podríamos necesitar ordenar una secuencia de números en un orden no decreciente. 
Este problema surge con frecuencia en la práctica y proporciona un terreno fértil para
introducir muchas técnicas de diseño y herramientas de análisis estándar. Así es como definimos formalmente el ***problema de ordenación (sorting problem)***:

Entrada: Una secuencia de $n$ numeros $\langle a_1, a_2,\dots, a_n \rangle$

Salida: Una permutación (reordenación) $\langle a'_1, a'_2, \dots, a'_n \rangle$ de la secuencia de entrada tal que  
$a'_1 \leq a'_2 \leq \dots \leq a'_n.$


Por ejemplo, dada la secuencia de entrada 
$\langle 31, 41, 59, 26, 41, 58 \rangle,$ 
un algoritmo de ordenamiento devuelve como salida la secuencia 
$\langle 26, 31, 41, 41, 58, 59 \rangle.$ 

Dicha secuencia de entrada se denomina una **instancia del problema de ordenamiento**.  
En general, una instancia de un problema consiste en la entrada (que satisface las restricciones impuestas en la definición del problema) 
necesaria para calcular una solución al problema.

Debido a que muchos programas lo usan como un paso intermedio, el ordenamiento es una operación fundamental en las ciencias de la computación. Como resultado, tenemos un gran número de algoritmos a nuestra disposición. Qué algoritmo es mejor aplicar depende – entre otros factores – del número de elementos a ser ordenados, la verificación de si un elemento ya está ordenado de alguna manera, posibles restricciones en los valores del elemento, la arquitectura de la computadora, y el tipo de dispositivo de memoria a utilizar: memoria principal, memoria de disco o incluso memoria de cintas.

Un algoritmo se dice que es **correcto** si, por cada instancia de entrada, finaliza con la salida correcta. Dijimos que un algoritmo correcto **resuelve** el problema computacional planteado. Un algoritmo incorrecto podría no finalizar en absoluto en algunas instancias de entrada, o podría finalizar con una respuesta incorrecta. Contrario a lo que se podría esperar, los algoritmos incorrectos pueden ser útiles a veces, si podemos controlar su tasa de error. Veremos un ejemplo de un algoritmo con una tasa de error controlable en el Capítulo 31 donde estudiamos algoritmos para encontrar números primos largos. De cualquier manera, normalmente nos ocuparemos solo con algoritmos correctos.

Un algoritmo puede ser especificado en inglés, como un programa computacional, o incluso como un diseño de *hardware.* El único requisito es que la especificación debe proveer una descripción precisa del procedimiento computacional que se debe seguir.

### ¿Qué tipos de problemas se resuelven con algoritmos?

El ordenamiento, de ninguna manera, es el único problema computacional para el cual los algoritmos han sido desarrollados. (Probablemente lo sospechaste cuando viste el tamaño de este libro.) Las aplicaciones prácticas de los algoritmos están en todas partes incluyendo los siguientes ejemplos:

- El Proyecto Genoma Humano ha hecho grandes progresos identificando todos los 100,000 genes en el ADN humano, determinando la secuencia de 3,000,000,000 de pares de bases químicas que conforman el ADN humano, almacenando esta información en bases de datos, y desarrollando herramientas para el análisis de datos. Cada uno de estos pasos requiere de algoritmos sofisticados. Aunque las soluciones a los variados problemas involucrados están fuera de la mira de este libro, muchos métodos para resolver esos problemas biológicos usan ideas de múltiples capítulos en él, así permiten a los científicos completar tareas mientras utilizan recursos eficientemente. Las ganancias se traducen en tiempo, tanto de cómputo como humano, económicas y en más información que puede ser extraída con técnicas de laboratorio.

- El Internet permite a las personas alrededor del mundo acceder y recuperar grandes cantidades de información rápidamente. Con la ayuda de ingeniosos algoritmos, sitios en Internet pueden administrar y manipular este enorme volumen de datos. Ejemplos de problemas que hacen esencial el uso de algoritmos incluyen encontrar buenas rutas en las que los datos viajarán (técnicas de resolución cuyos problemas aparecen en el Capítulo 24), y utilizar motores de búsqueda para encontrar páginas rápidamente en las que esa información particular reside (técnicas relacionadas se encuentran en el Capítulo 11 y 32).

- El comercio electrónico permite negociar e intercambiar bienes y servicios electrónicamente, y depende de la privacidad en el tratamiento de sus datos personales tales como números de tarjetas de crédito, contraseñas e informes bancarios. Las principales tecnologías utilizadas en el comercio electrónico incluyen la criptografía de claves públicas y la firma digital (cubiertas en el Capítulo 31), que están basadas en algoritmos numéricos y teoría de números.

- La manufactura y otras empresas comerciales a menudo necesitan asignar recursos muy escasos de la manera más beneficiosa posible. Una empresa petrolera podría desear saber dónde poner sus pozos para maximizar las ganancias perfiladas. Un candidato político podría querer determinar dónde gastar dinero comprando campañas publicitarias para maximizar las oportunidades de ganar una elección. Una aerolínea podría requerir asignar equipos a vuelos de la manera menos costosa posible, asegurándose de que cada vuelo está cubierto y que las regulaciones gubernamentales de los horarios de trabajo del equipo están cumpliéndose. Un proveedor de internet podría desear determinar dónde aplicar recursos adicionales para proveer más eficientemente a sus clientes. Todos estos ejemplos son problemas que pueden ser resueltos utilizando programación lineal, la cual estudiaremos en el Capítulo 29.

Aunque algunos de los detalles de estos ejemplos sobrepasan la mira de este libro, proporcionamos técnicas subyacentes que aplican a estos y otros problemas de esas áreas. También mostramos cómo resolver muchos problemas específicos, incluyendo los siguientes:

- Se nos da un mapa vial en el cual la distancia entre cada par de intersecciones adyacentes está marcada, y deseamos determinar la ruta más corta de una intersección a otra. El número de posibles rutas puede ser enorme, incluso si deshabilitamos rutas que crucen sobre sí mismas. ¿Cómo elegimos cuál de todas las rutas es la más corta? Aquí modelamos un mapa vial (el cuál es por sí un modelo de las rutas actuales) como una gráfica (la cuál se abordará en la Parte VI, Apéndice B), y encontramos la ruta más corta desde un vértice a otro en la gráfica. Veremos cómo resolver este problema eficientemente en el capítulo 24.

- Se nos dan dos secuencias ordenadas de símbolos, $X = \langle x_1, x_2, \dots, x_m \rangle$ y $Y = \langle y_1, y_2, \dots, y_n \rangle$, y deseamos encontrar la subsecuencia común más larga de $X$ y $Y$. Una subsecuencia de $X$ es solo $X$ con alguno (o posiblemente todos o ninguno) de sus elementos removidos. Por ejemplo, una subsecuencia de {A, B, C, D, E, F, G} sería {B, C, E, G}. La longitud de la subsecuencia común más larga de $X$ y $Y$ nos da una medida de qué tan similares son estas dos secuencias entre sí. Por ejemplo, si las dos secuencias son pares de bases en el hilo del ADN, entonces debemos considerarlas similares si tienen una larga subsecuencia común. Si $X$ tiene *m* símbolos y $Y$ tiene *n* símbolos, entonces $X$ y $Y$ tienen $2^m$ y $2^n$ posibles subsecuencias, respectivamente. Seleccionar todas las posibles subsecuencias y compararlas podría tomar mucho tiempo de manera prohibitiva a menos que *m* y *n* sean muy pequeñas. Veremos en el Capítulo 15 cómo usar una técnica general conocida como programación dinámica para resolver este problema con mucha más eficiencia.

- Se nos da un diseño mecánico en términos de una librería de partes, donde cada parte puede incluir instancias de otras partes, y necesitamos listar las partes en orden de manera que cada parte aparezca antes de cualquier parte donde se usa. Si el diseño comprende *n* partes, entonces hay *n*! posibles órdenes, donde *n*! denota la función factorial. Como la función factorial crece más rápido incluso que una función exponencial, no podemos generar de manera factible cada posible orden y verificar si, en ese orden, cada parte aparece antes de las partes que lo están usando (a menos que solo tengamos unas cuantas partes). Este problema es una instancia del ordenamiento topológico, y veremos en el Capítulo 22 cómo resolver este problema de manera eficiente.

- Se nos dan *n* puntos en el plano, y deseamos encontrar la envolvente convexa de esos puntos. La envolvente convexa es el polígono convexo más pequeño que contiene todos los puntos. Intuitivamente, podemos pensar que cada punto está representado por clavos que sobresalen de una tabla. La envolvente convexa estaría representada por una liga ajustada que rodea todos los clavos. Cada clavo alrededor del cual la liga hace una curva es un vértice de la envolvente convexa. (Ver Figura 33.6 en la página 1029 como ejemplo). Cualquiera de los $2^n$ subconjuntos de puntos podría constituir el conjunto de vértices de la envolvente convexa. Saber cuáles puntos son vértices de la envolvente convexa no es suficiente, pues también debemos conocer el orden en el que aparecen. Por lo tanto, hay muchas opciones para el orden de los vértices de la envolvente convexa. El Capítulo 33 proporciona dos buenos métodos para encontrar la envolvente convexa.

Estas listas están lejos de ser exhaustivas (de nuevo, como probablemente has deducido por la extensión de este libro), pero hay dos características comunes a muchos problemas algorítmicos interesantes:

1. Hay múltiples soluciones candidatas, pero la abrumadora mayoría de ellas no resuelven el problema en cuestión. Encontrar la que lo hace, o una que es “mejor”, puede representar un verdadero desafío.

2. Tienen aplicaciones prácticas. De los problemas en la lista de arriba, encontrar la ruta más corta provee un ejemplo simple. Una corporación dedicada al transporte, como una empresa de transporte terrestre o una compañía ferroviaria, tiene intereses financieros en encontrar las rutas más cortas a través de un camino o una red de rieles porque tomar la ruta más corta se traduce en menor mano de obra y costo de combustible. O un nodo de ruta en el Internet podría necesitar encontrar la ruta más corta a través de la red para entregar un mensaje rápidamente. O una persona deseando conducir desde Nueva York hasta Boston podría querer encontrar direcciones de un sitio web apropiado, o podría usar su GPS mientras conduce.

No todos los problemas resueltos por algoritmos tienen un conjunto de soluciones candidatas fácilmente identificable. Por ejemplo, supongamos que se nos da un conjunto de valores numéricos representando muestras de una señal, y queremos calcular la transformada discreta de Fourier. La transformada discreta de Fourier convierte una señal del dominio del tiempo al dominio de la frecuencia, produciendo un conjunto de coeficientes numéricos, para poder determinar la potencia de varias frecuencias en la señal muestreada. Además de estar situada en el corazón del procesamiento de señales, la transformada discreta de Fourier tiene aplicaciones en compresión de datos y la multiplicación de grandes polinomios y números enteros. El Capítulo 30 proporciona un algoritmo eficiente, la transformada rápida de Fourier (normalmente llamada FFT), para este problema, y el capítulo también esboza un diseño de circuito de hardware para calcular la FFT.

### Estructuras de datos

Este libro también contiene muchas estructuras de datos. Una **estructura de datos** es una forma de almacenar y organizar la información con el objetivo de facilitar el acceso y las modificaciones. Ni una sola estructura de datos funciona bien para todos los propósitos, y es importante saber las fortalezas y limitaciones de muchas de ellas.

### Técnica

Aunque se puede usar este libro como un “recetario” para encontrar algoritmos, algún día podrías hallar un problema para el cual no encuentres uno leyendo los algoritmos publicados (muchos de los ejercicios y problemas en este libro, por ejemplo). Este libro te enseñará técnicas de diseño y análisis de algoritmos para que puedas desarrollarlos por tu cuenta; te mostrará cómo demostrar que producen la respuesta correcta y cómo analizar su eficiencia. Diferentes capítulos abordan diferentes aspectos de la resolución de problemas algorítmicos. Algunos capítulos abordan problemas específicos, como encontrar medianas y estadísticos de orden en el Capítulo 9, calcular árboles de expansión mínimos en el Capítulo 23, y determinar un flujo máximo en una red en el Capítulo 26. Otros capítulos abordan las técnicas, como dividir y conquistar en el Capítulo 4, programación dinámica en el Capítulo 15, y análisis amortizado en el Capítulo 17.

### Problemas difíciles

Mucho de este libro es sobre la eficiencia de los algoritmos. Nuestra métrica de la eficiencia es la velocidad, es decir, cuánto tarda un algoritmo en producir un resultado. De cualquier manera, hay algunos problemas para los cuales no se conoce una solución eficiente. El capítulo 34 estudia un subconjunto interesante de estos problemas, que son conocidos como NP-completos.

¿Por qué son interesantes los problemas NP-completos? Primero, aunque no se ha encontrado un algoritmo eficiente para un problema NP-completo, nadie ha probado que un algoritmo eficiente para un problema NP-completo no pueda existir. En otras palabras, nadie sabe si existen o no algoritmos eficientes para los problemas NP-completos. Segundo, el conjunto de problemas NP-completos tiene la remarcable propiedad de que, si un algoritmo eficiente existe para alguno de ellos, entonces existen algoritmos eficientes para todos ellos. Esta relación entre los problemas NP-completos hace que la falta de soluciones eficientes sea aun más tentadora. Tercero, muchos problemas NP-completos son similares, pero no idénticos, a problemas para los que conocemos algoritmos eficientes. Los científicos de la computación están intrigados por cómo un pequeño cambio al planteamiento del problema puede causar un gran cambio en la eficiencia del mejor algoritmo conocido.

Deberías conocer más sobre los problemas NP-completos pues algunos de ellos aparecen con sorprendente frecuencia en aplicaciones reales. Si sientes el llamado para producir un algoritmo eficiente para un problema NP-completo, muy seguramente gastarás mucho tiempo en una búsqueda infructífera. Si puedes demostrar que el problema es NP-completo, puedes, en su lugar, invertir tu tiempo desarrollando un algoritmo eficiente que brinde una buena, pero no la mejor, solución posible.

Como ejemplo concreto, considera una compañía de entregas con un depósito central. Cada día, se cargan los camiones de entrega en el depósito y se envían a repartir las entregas a múltiples direcciones. Al final del día, cada camión debe terminar su ruta en el depósito para que esté listo para ser cargado el día siguiente. Para reducir costos, la compañía requiere generar un orden de paradas de entrega que produzca la menor distancia total recorrida por cada camión. Este problema es el bien conocido “problema del viajante”, y es un problema NP-completo. No tiene algoritmo eficiente conocido. De cualquier manera, bajo ciertas suposiciones, conocemos algoritmos eficientes que proporcionan una distancia total que no está muy alejada de la más corta posible. El Capítulo 35 trata dichos “algoritmos de aproximación”.

### Paralelismo

Por muchos años, pudimos contar con que las velocidades de reloj de los procesadores aumentarían a un ritmo constante. Sin embargo, las limitaciones físicas presentan una barricada para el incremento constante de las velocidades de reloj: debido a que la densidad de potencia crece superlinealmente con la velocidad del reloj, los chips corren el riesgo de fundirse una vez que dicha velocidad alcanza niveles suficientemente elevados. Para mejorar los cálculos por segundo, por lo tanto, los chips son diseñados para contener no solo uno sino varios “núcleos” de procesamiento. Podemos comparar estos computadores multinúcleo con muchos computadores secuenciales en un solo chip; en otras palabras, son un tipo de “computación paralela”. Para obtener el mejor rendimiento de un computador multinúcleo, necesitamos diseñar algoritmos con el paralelismo en mente. El Capítulo 27 presenta un modelo para algoritmos “multihilo”, el cual toma ventaja de los múltiples núcleos. Este modelo tiene ventajas desde un punto de vista teórico, y constituye la base de muchos programas computacionales exitosos, incluyendo un programa campeón de ajedrez.

### Ejercicios

#### 1.1-1

Proporciona un ejemplo de la vida real que requiera un ordenamiento o un ejemplo de la vida real que requiera calcular la envolvente convexa.

#### 1.1-2

Además de la velocidad, ¿qué otra métrica de eficiencia se puede usar en un entorno del mundo real?

#### 1.1-3

Selecciona una estructura de datos que hayas visto anteriormente, menciona sus fortalezas y limitaciones.

#### 1.1-4

¿En qué se parecen el problema del camino más corto y el problema del viajante?\
¿En qué se diferencian?

#### 1.1-5

Plantea un problema del mundo real en el que solo sirva la mejor solución. Después, plantea uno en el que una solución “aproximadamente” óptima sea suficiente.

## 1.2 Los algoritmos como una tecnología

Imagina que las computadoras son infinitamente rápidas y la memoria de cómputo es gratis. ¿Tendrías alguna razón para estudiar algoritmos? La respuesta es sí, aunque no sea por ninguna otra razón que demostrar que los métodos de tu solución finalizan y lo hacen con la respuesta correcta.

Si las computadoras tuvieran velocidad infinita, cualquier método correcto de resolución de problemas serviría. Probablemente querrías que tu implementación sea sin los límites de las buenas prácticas de la ingeniería de software (por ejemplo, tu implementación debe estar bien diseñada y documentada), pero casi siempre usarías cualquier método que sea fácil de implementar.

Por supuesto, las computadoras pueden ser rápidas, pero no son infinitamente rápidas. Y la memoria puede no ser costosa, pero no es gratis. El tiempo de cómputo es, por lo tanto, un recurso limitado, así como el espacio en memoria. Debes usar estos recursos sabiamente, y los algoritmos que son eficientes en términos de tiempo y espacio te ayudarán con eso.

### Eficiencia

Diferentes algoritmos diseñados para resolver el mismo problema a menudo difieren dramáticamente en su eficiencia. Esas diferencias pueden ser mucho más significantes que las diferencias causadas por el hardware y software.

Como un ejemplo, en el Capítulo 2, veremos dos algoritmos de ordenamiento. El primero, conocido como **ordenamiento por inserción,** toma un tiempo de apenas $c_1n^2$ para ordenar $n$ elementos. donde $c_1$ es una constante que no depende de $n$. En otras palabras, toma un tiempo proporcional justo de $n^2$. El segundo, **ordenamiento por fusión,** toma un tiempo de apenas $c_2 lg n$ donde $lg n$ se refiere a $log_2n$ y $c_2$ es otra constante que tampoco depende de $n$. El ordenamiento por inserción normalmente tiene un factor constante más pequeño que el ordenamiento por fusión, así $c_1<c_2$. Veremos que los factores constantes pueden tener un impacto mucho menor en el tiempo de procesamiento que la dependencia del tamaño de entrada de $n$. Vamos a escribir el tiempo de procesamiento del ordenamiento por inserción como $c_1n \cdot n$ y al tiempo de procesamiento del ordenamiento por fusión como $c_2 n \cdot lg n$. Así vemos que mientras el ordenamiento por inserción tiene un factor de $n$ en su tiempo de procesamiento, el odenamiento por fusión tiene un factor de $lgn$, el cual es mucho más pequeño. (Por ejemplo, cuando $n=1000$, $lgn$ es aproximadamente $10$, y cuando $n$ equivale a un millón, $lgn$ es aproximadamente solo $20$.) A pesar de que el ordenamiento por inserción normalemente corre más rápido que el ordenamiento por fusión con tamaños de entrada pequeños, una vez que el tamaño de entrada $n$ se vuelve lo suficientemente grande, la ventaja del ordenamiento por fusión de $lgn$ vs. $n$ hará más que compensar la diferencia en los factores constantes. No importa qué tan pequeño sea $c_1$ con relación a $c_2$, siempre habrá un punto de encrucijada donde el ordenamiento por fusión sea más rápido pasado ese punto.

Para un ejemplo concreto, vamos a enfrentar una computadora rápida (computadora A) corriendo un ordenamiento por inserción contra una computadora lenta (computadora B) corriendo un ordenamiento por fusión. Ambas deben ordenar un arreglo de 10 millones de números. (Aunque 10 millones de números puedan parecer muchos, si son números enteros de 8 bits, entonces la entrada ocuparía cerca de 80 megabites, lo que se ajusta a la memoria incluso de una laptop poco costosa la mayoría de veces). Supón que la computadora A ejecuta 10 mil millones de instrucciones por segundo (más rápido que cualquier computo secuencial sencillo a la fecha de este escrito) y la computadora B ejecuta solo 10 millones de instrucciones por segundo, así que la computadora A es 1000 veces más rápida que la computadora B en poder de cómputo crudo. Para hacer la diferencia un poco más dramática, supongamos que el mejor programador del mundo codifica el algoritmo de ordenamiento por inserción en el lenguaje máquina para la computadora A, y el código que resulta requiere la cantidad de $2n^2$ instrucciones para ordenar $n$ cantidad de números. Supongamos que un simple programador promedio implementa el ordenamiento por fusión, usando un lenguaje de alto nivel con un compilador ineficiente, con el código resultante requiriendo la cantidad de $50n$ lg $n$ instrucciones. Para ordenar 10 millones de números, a la computadora A le toma

$$
\frac{2 \cdot (10^7)^2\ \text{instrucciones}}
{10^{10}\ \text{instrucciones/segundo}} =
20,000\ \text{segundos (mas de 5 horas y media),}
$$

mientras que a la computadora B le toma

$$
\frac {50 \cdot 10^7 lg 10^7\ \text{instrucciones}}
{10^7\ \text{instrucciones/segundo}}
\approx 1163\ \text{segundos (menos de 20 minutos).}
$$

!Si usamos un algoritmo cuyo tiempo de ejecución crece más lento, incluso con un compilador pobre, la computadora B corre más de 17 veces más rápido que la computadora A! La ventaja del ordenamiento por fusión es incluso más pronunciada cuando ordenamos 100 millones de números: mientras que al ordenamiento por inserción le toma más de 23 días, al ordenamiento por fusión le toma menos de cuatro horas. En general, mientras el tamaño del problema crece, también lo hace la ventaja relativa del ordenamiento por fusión.

### Algoritmos y otras tecnologías

El ejemplo anterior nos muestra que debemos considerar algoritmos, como los de hardware de cómputo, como **tecnología.** El rendimiento total del sistema depende tanto de elegir algoritmos eficientes como de elegir hardware rápido. Rápidos avances se están haciendo en otras tecnologías de la computación, así como se están haciendo en algoritmos también.

Podrías preguntarte si los algoritmos son verdaderamente importantes en computadoras contemporáneas a la luz de otras tecnologías avanzadas, tales como

- arquitectura avanzada de computadoras y tecnologías de fabricación,
- de uso sencillo, intuitivo, interfaces gráficas de usuario (GUIs),
- sistemas orientados a objetos,
- tecnologías de integración Web, y
- redes rápidas, tanto alámbricas como inalámbricas.

La respuesta es sí. Aunque algunas aplicaciones no requieren contenido algorítmico explícito al nivel de aplicación (uno simple como una aplicación basada en la web), muchas los utilizan. Por ejemplo, considera un servicio de una aplicación basada en la web que determina como viajar de una locación a otra. Su implementación podría depender de la velocidad del hardware, una interfaz gráfica de usuario, redes de área extensa, y también posiblemente una orientación a objetos. Como sea, también podría requerir algoritmos para ciertas operaciones, tales como encontrar rutas (probablemente usando un algoritmo del camino más corto), renderizado de mapas, e interpolación de direcciones.

Además, incluso una aplicación que no requiere un contenido algorítmico al nivel de aplicación depende de sobremanera de algoritmos. ¿Las aplicaciones dependen de hardware veloz? El diseño de hardware utilizó algoritmos. ¿La aplicación depende de interfaces gráficas de usuario? El diseño de cualquier GUI depende de algoritmos. ¿La aplicación depende de conexiones de red? El enrutamiento en la red depende en gran medida de algoritmos. ¿La aplicación fue escrito en un lenuaje diferente al código máquina? Entonces fue procesado por un compilador, un intérprete, o un ensamblador, todos ellos hacen un uso extenso de algoritmos. Los algoritmos están en el corazón de la mayoría de las tecnologías usadas en la computación contemporánea.

Además, con el crecimiento continuo de las capacidades de las computadoras, las utilizamos para resolver problemas más grandes que nunca antes. Como vimos en la comparación anterior entre el ordenamiento por inserción y el ordenamiento por fusión, es cuando hay problemas de gran tamaño cuando la diferencia entre los algoritmos se vuelven particularmente prominentes.

Tener una base sólida de conocimientos en técnica y algoritmos es una de las características que separan a un programador verdaderamente hábil de los novatos. Con la tecnología computacional moderna, puedes completar ciertas tareas sin saber mucho acerca de algoritmos, pero con un buen trasfondo en algoritmos, puede hacer mucho, mucho más.

### Ejercicios

#### 1.2-1

Proporciona un ejemplo de una aplicación que requiere contenido algorítmico en el nivel de aplicación, y discute la función del algoritmo involucrado.

#### 1.2-2

Supon que estamos comparando implementaciones de ordenamientos de inserción y ordenamientos de fusión en la misma máquina. Para las entradas de tamaño $n$, el ordenamiento de inserción corre en $8n^2$ pasos, mientras que el ordenamiento por fusión corre en $64n\ lg\ n$ pasos. ¿Para cuáles valores de $n$ el ordenamiento por inserción vence al ordenamiento por fusión?

#### 1.2-3

¿Cuál es el valor más pequeño de $n$ tal que un algoritmo cuyo tiempo de procesamiento es $100n^2$ corre más rápido que un algoritmo cuyo tiempo de procesamiento es $2^n$ en la misma máquina?

## Problemas

### 1-1 Comparación de tiempos de procesamiento

Para cada función $f(n)$ y tiempo $t$ en la siguiente tabla, determina el tamaño más grande de $n$ de un problema que puede ser resuelto en tiempo $t$, asumiendo que el algoritmo que resuelve el problema toma $f(n)$ microsegundos.

|             | 1<br>segundo | 1<br>minuto | 1<br>hora | 1<br>día | 1<br>mes | 1<br>año | 1<br>siglo |
|:-----------:|:------------:|:-----------:|:---------:|:--------:|:--------:|:--------:|:----------:|
| $\lg n$     |              |             |           |          |          |          |            |
| $\sqrt{n}$  |              |             |           |          |          |          |            |
| $n$         |              |             |           |          |          |          |            |
| $n\lg n$    |              |             |           |          |          |          |            |
| $n^2$       |              |             |           |          |          |          |            |
| $n^3$       |              |             |           |          |          |          |            |
| $2^n$       |              |             |           |          |          |          |            |
| $n!$        |              |             |           |          |          |          |            |

## Notas del capítulo

Hay muchos textos excelentes para tópicos generales de algoritmos, incluidos los de Aho, Hopcroft, y Ullman [5, 6]; Baase y Van Gelder [28]; Brassard y Bratley [54]; Dasgupta, Papadimitriou, y Vazirani [82]; Goodrich y Tamassia [148]; Hofri [175]; Horowitz, Sahni, y Rajasekaran [181]; Johnsonbaugh y
Schaefer [193]; Kingston [205]; Kleinberg y Tardos [208]; Knuth [209, 210, 211]; Kozen [220]; Levitin [235]; Manber [242]; Mehlhorn [249, 250, 251]; Purdom y Brown [287]; Reingold, Nievergelt, y Deo [293]; Sedgewick [306]; Sedgewick y Flajolet [307]; Skiena [318]; y Wilf [356]. Algunos de los aspectos más prácticos del diseño de algoritmos son discutidos por Bentley [42, 43] y Gonnet [145]. Encuestas dentro del campo de los algoritmos también se pueden encontrar en el *Manual de Ciencia de la Computación Teórica, Volumen A* [342] y el CRC *Manual de Algoritmos y Teoría de la Computación* [25]. Revisiones de algoritmos usados en biología computacional pueden ser encontrados en libros de texto escritos por Gusfield [156], Pevzner [275], Setubal y Meidanis [310], y Waterman [350].
