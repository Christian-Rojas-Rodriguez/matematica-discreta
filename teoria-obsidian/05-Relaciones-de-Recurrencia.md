---
tags: [matematica-discreta, tema-5, recurrencias, unsam]
aliases: ["Relaciones de Recurrencia", "Recurrencias", "Tema 5"]
---

# Relaciones de Recurrencia

> [!info] Ubicación en la materia
> Esta unidad enseña a describir sucesiones definiéndolas en función de sus propios términos anteriores y a "despejarlas" hasta obtener una fórmula cerrada. Es la unidad donde más se usa la inducción de [[01-Razonamientos-Categoricos]] como herramienta de verificación, y se conecta con el conteo de subconjuntos de [[03-Redes-y-Algebras-de-Boole]] y con el algoritmo de Euclides de [[04-Congruencias-Euler-Fermat]].

## 1. Introducción y motivación

Hasta ahora, cuando queríamos describir una sucesión de números $a_1, a_2, a_3, \dots$ buscábamos una **fórmula cerrada** (o explícita): una expresión que, dado $n$, nos da $a_n$ directamente, sin necesidad de conocer los términos anteriores. Por ejemplo $a_n = 2n+1$ o $a_n = 3^n$.

Pero hay muchísimas situaciones —sobre todo en conteo combinatorio, en análisis de algoritmos y en modelos de crecimiento— donde es mucho más natural, y muchas veces la única forma razonable, describir el término $n$-ésimo **en función de los términos anteriores**. A esto se le llama una **relación de recurrencia** (o ecuación en diferencias). Algunos ejemplos clásicos que seguramente ya viste en otras materias:

- **Interés compuesto**: si un capital $a_{n-1}$ crece un $c\%$ por período, el capital del período siguiente es $a_n = (1+c)\cdot a_{n-1}$.
- **Sucesión de Fibonacci**: cada conejo nuevo mes nace de los conejos de los dos meses anteriores, $a_n = a_{n-1} + a_{n-2}$.
- **Torres de Hanói**: para mover $n$ discos hacen falta $a_n = 2a_{n-1}+1$ movimientos.
- **Cantidad de subconjuntos** de un conjunto de $n$ elementos: agregar un elemento nuevo duplica la cantidad de subconjuntos, $a_n = 2a_{n-1}$ (esto lo vamos a retomar en la sección 6, conectando con [[03-Redes-y-Algebras-de-Boole]]).

El problema central de la unidad es, entonces, el inverso al de "definir" la sucesión: **dada una relación de recurrencia (más las condiciones iniciales que la completan), encontrar la fórmula cerrada** $a_n = f(n)$ que genera exactamente los mismos valores. Esto tiene un valor práctico enorme: una fórmula cerrada nos permite calcular $a_{1000}$ sin calcular los 999 términos anteriores, y nos permite comparar el crecimiento de distintas sucesiones (algo fundamental, por ejemplo, para comparar la eficiencia de algoritmos recursivos).

El plan de la unidad es:

1. Clasificar las recurrencias según su estructura (orden, grado, linealidad, homogeneidad).
2. Desarrollar un método sistemático para resolver las recurrencias **lineales, de coeficientes constantes**, tanto homogéneas como no homogéneas, de orden 1 y de orden 2.
3. Aprender a **verificar** una solución propuesta mediante inducción, que es la contracara rigurosa de "resolver" la recurrencia.
4. Aprender el **problema inverso**: dada una fórmula cerrada, reconstruir la recurrencia que la genera.

Todo el aparato que vamos a construir depende de una idea muy simple, tomada del álgebra lineal: las recurrencias lineales homogéneas de coeficientes constantes tienen un conjunto de soluciones que se comporta como un espacio vectorial, y eso es lo que garantiza que el método de "proponer $a_n = r^n$" funcione y que la solución que encontremos sea, en verdad, **la única** compatible con las condiciones iniciales dadas.

## 2. Definiciones formales

**Definición (relación de recurrencia).** Una relación de recurrencia para una sucesión $(a_n)_{n \geq n_0}$ es una ecuación que expresa $a_n$ en función de uno o más términos anteriores $a_{n-1}, a_{n-2}, \dots, a_{n-k}$ (y eventualmente de $n$ mismo), válida para todo $n$ mayor o igual a cierto valor. Junto con la recurrencia se deben dar **condiciones iniciales** (los primeros $k$ valores de la sucesión) para que la sucesión quede unívocamente determinada.

**Definición (orden).** El **orden** de una relación de recurrencia es la cantidad de términos anteriores de los que depende $a_n$, es decir, la diferencia entre el índice más alto y el más bajo que aparecen en la ecuación. Si la recurrencia liga $a_n$ con $a_{n-1}, \dots, a_{n-k}$, decimos que es de **orden $k$**.

- $a_n = 3a_{n-1}$ es de orden $1$ (usa un solo término anterior).
- $a_{n+2} = a_{n+1}+a_n$ es de orden $2$ (usa dos términos anteriores; fijate que $a_{n+2}$ y $a_n$ distan $2$ en el índice).

**Definición (grado).** El **grado** de una relación de recurrencia es la mayor potencia con la que aparecen los términos $a_i$ en la ecuación (incluyendo productos entre distintos $a_i$, que suman exponentes). Si todos los $a_i$ aparecen con exponente $1$ y sin multiplicarse entre sí, la recurrencia tiene grado $1$.

> [!warning] Orden $\neq$ Grado
> Son dos ejes de clasificación completamente independientes y es el error de examen más común de esta unidad (ver sección 7). $a_n = a_{n-1}^2 + 3$ es de **orden 1** (solo usa $a_{n-1}$) pero de **grado 2** (porque $a_{n-1}$ está al cuadrado). $a_{n+2} = a_{n+1}+a_n$ es de **orden 2** pero de **grado 1**.

**Definición (linealidad).** Una relación de recurrencia es **lineal** si es de grado $1$: cada término $a_i$ aparece elevado a la primera potencia, no multiplicado por otro $a_j$, y no está dentro de ninguna función no lineal (raíz, exponente, logaritmo, etc. aplicados a $a_i$). En general una recurrencia lineal de orden $k$ tiene la forma
$$c_k(n)\,a_{n+k} + c_{k-1}(n)\,a_{n+k-1} + \dots + c_0(n)\,a_n = f(n).$$

**Definición (homogeneidad).** La recurrencia es **homogénea** si $f(n) = 0$ para todo $n$ (no hay término independiente de la propia sucesión). Es **no homogénea** si $f(n) \neq 0$ (para al menos algún $n$, aunque en la práctica de la materia $f(n)$ suele ser una expresión fija: constante, polinomio, exponencial, etc.).

**Definición (coeficientes constantes).** Los coeficientes $c_i$ son **constantes** si no dependen de $n$ (son números fijos). Si dependieran de $n$ — por ejemplo $a_n = n\cdot a_{n-1}$, que es la recurrencia del factorial — estaríamos frente a una recurrencia de **coeficientes variables**, que queda fuera del método de esta unidad (el factorial se resuelve por otras vías).

En síntesis, el objeto de estudio central de la unidad es la **relación de recurrencia lineal, de coeficientes constantes**, homogénea o no, de orden 1 o de orden 2.

**Definición (ecuación característica).** Dada una recurrencia lineal homogénea de coeficientes constantes de orden $k$,
$$a_{n+k} + p_{k-1}a_{n+k-1} + \dots + p_0 a_n = 0,$$
se llama **ecuación característica** al polinomio de grado $k$ en la variable $x$ que se obtiene reemplazando cada $a_{n+j}$ por $x^j$:
$$x^k + p_{k-1}x^{k-1} + \dots + p_0 = 0.$$
Para orden 2, con la recurrencia escrita como $a_{n+2}+p\,a_{n+1}+q\,a_n = 0$, la ecuación característica es
$$x^2 + px + q = 0.$$
En la sección 3 demostramos por qué esta sustitución es exactamente la correcta (no es un "truco", sale de proponer el ansatz $a_n = r^n$).

**Definición (solución general y solución particular).**
- La **solución general** de una recurrencia lineal de orden $k$ es una familia de sucesiones que depende de $k$ constantes libres ($k_1, \dots, k_k$) y que satisface la recurrencia para *cualquier* valor de esas constantes.
- Una **solución particular** de la ecuación homogénea es cualquier miembro concreto de esa familia (fijando las constantes).
- En el contexto del método de coeficientes indeterminados para no homogéneas, llamamos **solución particular** $a_n^P$ a *una* solución cualquiera (sin constantes libres) de la ecuación no homogénea completa, que se suma después a la solución general de la homogénea $a_n^H$ (ver Teorema de superposición, sección 3).

**Definición (condiciones iniciales).** Son los valores concretos $a_{n_0}, a_{n_0+1}, \dots, a_{n_0+k-1}$ que se dan como dato junto con la recurrencia de orden $k$. Sirven para determinar unívocamente las $k$ constantes libres de la solución general, transformándola en **la** solución (particular, en el sentido de "la única compatible con esos datos") del problema.

## 3. Teoremas y demostraciones

### Teorema 1 (el ansatz $a_n = r^n$ produce exactamente la ecuación característica)

**Enunciado.** Sea la recurrencia lineal homogénea de orden 2 y coeficientes constantes $a_{n+2}+p\,a_{n+1}+q\,a_n = 0$. Para $r \neq 0$, la sucesión $a_n = r^n$ es solución de esta recurrencia **si y solo si** $r$ es raíz de la ecuación característica $x^2+px+q=0$.

**Demostración.** Sustituimos $a_n = r^n$ (y por lo tanto $a_{n+1}=r^{n+1}$, $a_{n+2}=r^{n+2}$) en la recurrencia:
$$r^{n+2} + p\,r^{n+1} + q\,r^n = 0.$$
Como $r \neq 0$, también $r^n \neq 0$, así que podemos sacar $r^n$ como factor común:
$$r^n\left(r^2 + pr + q\right) = 0.$$
Un producto de dos factores es cero si y solo si alguno de los dos es cero. Como $r^n \neq 0$, la igualdad se cumple **si y solo si**
$$r^2+pr+q = 0,$$
que es exactamente la ecuación característica evaluada en $r$. Esto prueba ambas direcciones: si $a_n=r^n$ resuelve la recurrencia, entonces $r$ satisface $r^2+pr+q=0$; y recíprocamente, si $r$ satisface esa ecuación, entonces $r^n(r^2+pr+q) = r^n \cdot 0 = 0$ para todo $n$, así que $a_n=r^n$ resuelve la recurrencia para todo $n$. $\blacksquare$

Esto explica por qué el "paso 1" del método (armar la ecuación característica reemplazando $a_{n+j}$ por $x^j$) no es arbitrario: es simplemente la condición algebraica que hace que el ansatz exponencial funcione.

### Teorema 2 (con raíces distintas, $a_n = k_1 r_1^n + k_2 r_2^n$ es la solución *más general*, no solo *una* solución)

Este es el resultado más importante de la unidad y conviene entenderlo con calma, porque es lo que garantiza que el método "encuentre todas las soluciones posibles" y no se nos escape ninguna.

**Paso 1: el conjunto de soluciones es un espacio vectorial.**

Sea $V$ el conjunto de todas las sucesiones $(a_n)_{n\geq 0}$ que satisfacen $a_{n+2}+p\,a_{n+1}+q\,a_n=0$ para todo $n \geq 0$. Definamos la suma de sucesiones y el producto por escalar término a término, como es usual. Afirmamos que $V$ es un subespacio vectorial del espacio de todas las sucesiones.

En efecto, si $(a_n), (b_n) \in V$ y $\lambda, \mu$ son escalares, entonces la sucesión $(\lambda a_n + \mu b_n)$ también satisface la recurrencia, porque el operador
$$L(a_n) := a_{n+2}+p\,a_{n+1}+q\,a_n$$
es **lineal**: $L(\lambda a_n+\mu b_n) = \lambda a_{n+2}+\mu b_{n+2} + p(\lambda a_{n+1}+\mu b_{n+1}) + q(\lambda a_n + \mu b_n) = \lambda\, L(a_n) + \mu\, L(b_n) = \lambda\cdot 0 + \mu \cdot 0 = 0$. Como la sucesión nula también está en $V$, $V$ es efectivamente un subespacio vectorial.

**Paso 2: $V$ tiene dimensión exactamente 2.**

Consideremos la función $\varphi: V \to \mathbb{R}^2$ dada por $\varphi\big((a_n)\big) = (a_0, a_1)$, que a cada solución le asigna su par de condiciones iniciales. Esta función es lineal (evidente, porque se toman las dos primeras coordenadas).

- **$\varphi$ es inyectiva:** si conocemos $a_0$ y $a_1$, la recurrencia $a_{n+2} = -p\,a_{n+1}-q\,a_n$ determina $a_2$ a partir de $a_1,a_0$; luego $a_3$ a partir de $a_2,a_1$; y así siguiendo (esto es, formalmente, una demostración por inducción). Por lo tanto toda la sucesión completa queda determinada por $(a_0,a_1)$, es decir, dos soluciones con el mismo par $(a_0,a_1)$ son la misma sucesión.
- **$\varphi$ es sobreyectiva:** dado cualquier par $(a_0,a_1) \in \mathbb{R}^2$, podemos *construir* la sucesión que empieza con esos valores y sigue generando términos con la fórmula $a_{n+2}=-pa_{n+1}-qa_n$; esa sucesión, por construcción, pertenece a $V$ y tiene exactamente esas condiciones iniciales.

Entonces $\varphi$ es una transformación lineal biyectiva (un isomorfismo) entre $V$ y $\mathbb{R}^2$, y por lo tanto $\dim V = \dim \mathbb{R}^2 = 2$.

**Paso 3: si $r_1 \neq r_2$, las sucesiones $r_1^n$ y $r_2^n$ forman una base de $V$.**

Por el Teorema 1, ambas $r_1^n$ y $r_2^n$ pertenecen a $V$ (son soluciones). Como $\dim V = 2$, dos elementos de $V$ forman una base si y solo si son linealmente independientes, lo cual equivale a que, para *cualquier* condición inicial $(a_0,a_1)$, exista una **única** combinación $k_1, k_2$ tal que
$$k_1 r_1^0 + k_2 r_2^0 = a_0, \qquad k_1 r_1^1 + k_2 r_2^1 = a_1,$$
es decir, el sistema lineal
$$\begin{cases} k_1 + k_2 = a_0 \\ k_1 r_1 + k_2 r_2 = a_1\end{cases}$$
debe tener solución única. La matriz de este sistema es
$$M = \begin{pmatrix} 1 & 1 \\ r_1 & r_2\end{pmatrix}, \qquad \det M = r_2 - r_1.$$
(Este es el llamado determinante de Vandermonde para dos puntos). El sistema tiene solución única exactamente cuando $\det M \neq 0$, es decir, cuando $r_1 \neq r_2$. Como estamos precisamente en el caso de raíces distintas, el determinante es no nulo, el sistema siempre tiene solución única para cualesquiera $a_0,a_1$, y por lo tanto $\{r_1^n, r_2^n\}$ es base de $V$.

**Conclusión.** Como $\{r_1^n,r_2^n\}$ es base de $V$, *todo* elemento de $V$ (es decir, toda solución posible de la recurrencia) se escribe de manera única como combinación lineal $a_n = k_1 r_1^n + k_2 r_2^n$. Esto es exactamente decir que esta expresión es la solución **más general**: no es "una solución más", es una parametrización que cubre absolutamente todas las soluciones, y además a cada condición inicial le corresponde un único par $(k_1,k_2)$, que es justo el sistema de $2\times 2$ que resolvemos en la práctica. $\blacksquare$

### Teorema 3 (raíz doble: por qué hace falta el término $k_2\, n\, r^n$)

**Enunciado.** Si la ecuación característica $x^2+px+q=0$ tiene una raíz doble $r$ (es decir $x^2+px+q=(x-r)^2$), entonces, además de $a_n=r^n$, la sucesión $a_n = n\, r^n$ también es solución de $a_{n+2}+p\,a_{n+1}+q\,a_n=0$.

**Observación previa.** Que $r$ sea raíz doble de $x^2+px+q$ significa, comparando coeficientes en $x^2+px+q=(x-r)^2=x^2-2rx+r^2$, que
$$p = -2r, \qquad q = r^2, \qquad \text{es decir} \qquad 2r = -p. \tag{$\star$}$$

**Demostración.** Sustituimos $a_n = n\,r^n$ en el lado izquierdo de la recurrencia:
$$(n+2)r^{n+2} + p(n+1)r^{n+1} + q\,n\,r^n.$$
Reagrupamos sacando factor común $r^n$ y separando los términos que llevan $n$ de los que no:
$$= r^n\Big[(n+2)r^2 + p(n+1)r + qn\Big] = r^n\Big[\,n\big(r^2+pr+q\big) + \big(2r^2+pr\big)\,\Big].$$
Ahora usamos dos hechos:
1. Como $r$ es raíz de la ecuación característica, $r^2+pr+q=0$, así que el término que multiplica a $n$ se anula.
2. Queda $r^n(2r^2+pr) = r^n \cdot r \cdot (2r+p) = r^{n+1}(2r+p)$. Por $(\star)$ sabemos que $2r=-p$, es decir $2r+p=0$.

Entonces toda la expresión vale $r^{n+1}\cdot 0 = 0$, para todo $n$. Esto prueba que $a_n=n\,r^n$ satisface la recurrencia. $\blacksquare$

Con el mismo argumento del Teorema 2 (espacio vectorial de dimensión 2), como $r^n$ y $n\,r^n$ son linealmente independientes (no son múltiplo una de la otra, salvo la trivial), forman una base de $V$, y por lo tanto la solución general en el caso de raíz doble es
$$a_n = k_1 r^n + k_2\, n\, r^n.$$
Si uno "olvida" el factor $n$ y propone $a_n=k_1 r^n+k_2 r^n = (k_1+k_2) r^n$, en realidad está usando una sola constante libre disfrazada de dos, y el sistema de condiciones iniciales quedaría, en general, sin solución o indeterminado: es el error más frecuente del tema (ver sección 7).

### Teorema 4 (principio de superposición para recurrencias no homogéneas)

**Enunciado.** Sea $L(a_n) = c_k a_{n+k}+\dots+c_0 a_n$ un operador de recurrencia lineal de coeficientes constantes, y consideremos la ecuación no homogénea $L(a_n) = f(n)$. Si $a_n^H$ es la solución general de la homogénea asociada $L(a_n)=0$, y $a_n^P$ es **una** solución particular cualquiera de $L(a_n)=f(n)$, entonces:

(i) $a_n = a_n^H + a_n^P$ es solución de $L(a_n)=f(n)$, para cualquier elección de las constantes libres de $a_n^H$; y

(ii) **toda** solución de $L(a_n)=f(n)$ tiene esa forma (no hay soluciones "sueltas" que se nos escapen).

**Demostración.**

*(i)* Como $L$ es lineal, $L(a_n^H+a_n^P) = L(a_n^H) + L(a_n^P) = 0 + f(n) = f(n)$. Luego $a_n^H+a_n^P$ resuelve la no homogénea. $\blacksquare$

*(ii)* Sea $b_n$ una solución cualquiera de $L(b_n)=f(n)$ (no necesariamente de la forma propuesta). Definimos $d_n := b_n - a_n^P$. Por linealidad de $L$:
$$L(d_n) = L(b_n) - L(a_n^P) = f(n) - f(n) = 0.$$
Es decir, $d_n$ es solución de la ecuación **homogénea**. Pero ya sabemos (Teoremas 2 y 3) que toda solución de la homogénea es de la forma $a_n^H$ para alguna elección de constantes. Entonces $d_n = a_n^H$ para cierta elección de constantes, y por lo tanto
$$b_n = a_n^P + d_n = a_n^P + a_n^H,$$
que es exactamente la forma buscada. $\blacksquare$

Este teorema es la justificación formal de por qué el método siempre se organiza en "primero la homogénea, después una particular, y se suman": no es una receta arbitraria, es consecuencia directa de la linealidad del operador de recurrencia. También explica por qué **hay que sumar primero** $a_n^H+a_n^P$ y recién *después* usar las condiciones iniciales para hallar $k_1,k_2$: las condiciones iniciales son condiciones sobre $a_n$ completo (homogénea + particular), no sobre $a_n^H$ sola (ver error común en sección 7).

### Teorema 5 (principio de inducción completa como método de verificación)

**Enunciado (principio de inducción, en su forma "fuerte" u ordinaria adaptada a recurrencias de orden $k$).** Sea $P(n)$ la afirmación "$a_n = f(n)$", donde $a_n$ está definida por una recurrencia de orden $k$ con condiciones iniciales $a_{n_0},\dots,a_{n_0+k-1}$. Si:

- **Caso base:** $P(n_0), P(n_0+1),\dots,P(n_0+k-1)$ son verdaderas (es decir, $f$ coincide con las condiciones iniciales dadas), y
- **Paso inductivo:** para todo $h \geq n_0+k-1$, suponiendo que $P(h-k+1),\dots,P(h)$ son verdaderas (**hipótesis inductiva**), se demuestra que $P(h+1)$ es verdadera (**tesis inductiva**),

entonces $P(n)$ es verdadera para todo $n \geq n_0$, es decir, $a_n=f(n)$ para todo $n$.

Este es exactamente el mismo principio lógico que en [[01-Razonamientos-Categoricos]] (lo retomamos con más detalle en la sección 6): un caso base más un paso que "empuja" la verdad de un valor al siguiente, encadenados, cubren **todos** los naturales.

**Demostración completa de un caso concreto** (uno de los ejemplos de exámenes reales): verificar que $a_n = 2-2^n$ es la solución de
$$a_n = 3a_{n-1}-2a_{n-2}, \qquad a_0=1,\ a_1=0.$$

*Caso base* ($n=0$ y $n=1$, porque la recurrencia es de orden 2 y necesita dos condiciones iniciales):
$$f(0) = 2-2^0 = 2-1 = 1 = a_0 \ \checkmark \qquad\qquad f(1) = 2-2^1 = 2-2 = 0 = a_1\ \checkmark$$

*Hipótesis inductiva:* supongamos que para cierto $h \geq 1$ valen $a_{h-1}=2-2^{h-1}$ y $a_h = 2-2^h$.

*Tesis inductiva:* queremos probar que $a_{h+1} = 2-2^{h+1}$.

*Demostración:* como $h+1\geq 2$, la recurrencia original nos dice
$$a_{h+1} = 3a_h - 2a_{h-1}.$$
Reemplazamos por hipótesis inductiva:
$$a_{h+1} = 3\big(2-2^h\big) - 2\big(2-2^{h-1}\big) = 6 - 3\cdot 2^h - 4 + 2\cdot 2^{h-1}.$$
Como $2\cdot 2^{h-1}=2^h$, agrupamos:
$$a_{h+1} = (6-4) + \big(-3\cdot 2^h + 2^h\big) = 2 - 2\cdot 2^h = 2-2^{h+1},$$
que es exactamente la tesis. $\blacksquare$

Por el principio de inducción, $a_n=2-2^n$ para todo $n\geq 0$, confirmando (de manera totalmente independiente del método de la ecuación característica) que la fórmula cerrada es correcta. En la sección 5 vas a ver de dónde salió esa fórmula $2-2^n$ resolviendo la recurrencia paso a paso.

## 4. Fórmulas clave (tabla de repaso rápido)

**Clasificación:**

| Eje | Pregunta que responde | Ejemplo |
|---|---|---|
| Orden | ¿Cuántos términos anteriores usa? | $a_{n+2}=a_{n+1}+a_n$ → orden 2 |
| Grado | ¿Máxima potencia de los $a_i$? | $a_n=a_{n-1}^2+3$ → grado 2 |
| Linealidad | ¿Grado 1, sin productos cruzados? | Lineal si grado 1 |
| Homogeneidad | ¿$f(n)=0$? | $a_n=3a_{n-1}$ homogénea; $a_n=3a_{n-1}+5$ no homogénea |
| Coeficientes constantes | ¿Los $c_i$ dependen de $n$? | $a_n=n\,a_{n-1}$ tiene coeficiente variable |

**Orden 1 lineal homogénea, coef. constantes:** $a_n=c\cdot a_{n-1}\ \Rightarrow\ a_n = c^{\,n-1}\cdot a_1$ (o $a_n=K\cdot c^n$ si se prefiere indexar desde $a_0=K$).

**Orden 2 lineal homogénea, coef. constantes:** $a_{n+2}+p\,a_{n+1}+q\,a_n=0$, característica $x^2+px+q=0$:

| Caso de raíces de $x^2+px+q=0$ | Solución general |
|---|---|
| $r_1 \neq r_2$ (reales distintas) | $a_n = k_1 r_1^{\,n} + k_2 r_2^{\,n}$ |
| $r_1=r_2=r$ (raíz doble) | $a_n = k_1 r^{\,n} + k_2\, n\, r^{\,n}$ |

**No homogénea — forma de la solución particular $a_n^P$ según $f(n)$** (si la forma propuesta coincide con una solución de la homogénea, hay **resonancia**: se multiplica por $n$, o por $n^2$ si hace falta, y se reintenta):

| $f(n)$ | Raíz relevante de la característica | Proponer $a_n^P$ |
|---|---|---|
| Constante $b$ | $1$ no es raíz | $A$ |
| Constante $b$ | $1$ **es** raíz (resonancia) | $A\cdot n$ |
| Lineal $bn+c$ | $1$ no es raíz | $An+B$ |
| Lineal $bn+c$ | $1$ **es** raíz | $An^2+Bn$ |
| Cuadrática $n^2$ (y similares) | $1$ no es raíz | $An^2+Bn+C$ |
| Exponencial $b\cdot s^n$ | $s$ no es raíz | $A\cdot s^n$ |
| Exponencial $b\cdot s^n$ | $s$ **es** raíz simple (resonancia) | $A\cdot n\cdot s^n$ |
| Exponencial $b\cdot s^n$ | $s$ es raíz doble | $A\cdot n^2\cdot s^n$ |

**Esquema de solución general para no homogéneas (Teorema de superposición):**
$$a_n = \underbrace{a_n^H}_{\text{homogénea, con } k_1,k_2} + \underbrace{a_n^P}_{\text{particular, sin constantes}}\ \xrightarrow{\ \text{condiciones iniciales}\ }\ k_1, k_2 \text{ únicos.}$$

**Esquema de verificación por inducción:**

| Paso | Qué hay que hacer |
|---|---|
| Caso base | Verificar $f(n_0)=a_{n_0}$ (y tantos casos base como el orden lo requiera) |
| Hipótesis inductiva | Suponer $a_h=f(h)$ (y $a_{h-1}=f(h-1)$, etc. si el orden es 2 o mayor) |
| Tesis inductiva | Enunciar lo que hay que probar: $a_{h+1}=f(h+1)$ |
| Demostración | Partir de la recurrencia para $a_{h+1}$, reemplazar por hipótesis, operar algebraicamente hasta llegar literalmente a $f(h+1)$ |

**Problema inverso** (de fórmula cerrada a recurrencia): escribir $a_n=f(n)$ y $a_{n-1}=f(n-1)$ (y $a_{n-2}=f(n-2)$ si hace falta), y combinar algebraicamente para cancelar las constantes que no dependen de $k_1,k_2$ hasta dejar una ecuación que solo relacione $a_n, a_{n-1}$ (y $a_{n-2}$).

## 5. Ejemplos resueltos paso a paso

### Ejemplo A — Orden 2 homogénea con raíces distintas

Resolver $a_n = 3a_{n-1}-2a_{n-2}$, con $a_0=1$, $a_1=0$.

**Paso 1 — reescribir y armar la característica.** Escribimos la recurrencia como $a_n - 3a_{n-1}+2a_{n-2}=0$, o equivalentemente (corriendo el índice) $a_{n+2}-3a_{n+1}+2a_n=0$. Reemplazando $a_{n+j}\to x^j$ (Teorema 1):
$$x^2 - 3x + 2 = 0.$$

**Paso 2 — resolver la cuadrática.** Factorizamos: $x^2-3x+2=(x-1)(x-2)$, entonces $r_1=1$, $r_2=2$. Son raíces reales y distintas.

**Paso 3 — solución general.** Por el Teorema 2:
$$a_n = k_1\cdot 1^n + k_2\cdot 2^n = k_1 + k_2\cdot 2^n.$$

**Paso 4 — condiciones iniciales.**
$$a_0 = k_1+k_2 = 1, \qquad a_1 = k_1+2k_2 = 0.$$
Restando la primera a la segunda: $k_2 = -1$. Reemplazando: $k_1 = 1-k_2 = 2$.

**Paso 5 — solución final.**
$$\boxed{a_n = 2 - 2^n}$$

**Verificación rápida:** $a_2$ por recurrencia $=3a_1-2a_0=3(0)-2(1)=-2$; por fórmula $=2-2^2=-2$ ✓. La verificación completa por inducción de esta misma solución ya se hizo en el Teorema 5 de la sección 3.

### Ejemplo B — Orden 2 no homogénea con término exponencial (chequeo de resonancia)

Resolver $a_{n+2}-4a_{n+1}-5a_n = 10\cdot 4^n$, con $a_0=1$, $a_1=7$.

**Paso 1 — resolver la homogénea asociada.** $a_{n+2}-4a_{n+1}-5a_n=0$ da la característica
$$x^2-4x-5=0 \ \Rightarrow\ (x-5)(x+1)=0 \ \Rightarrow\ r_1=5,\ r_2=-1.$$
Raíces distintas, entonces
$$a_n^H = k_1\cdot 5^n + k_2\cdot(-1)^n.$$

**Paso 2 — proponer la particular, chequeando resonancia.** $f(n)=10\cdot 4^n$ es exponencial con base $s=4$. ¿Es $4$ raíz de la característica $x^2-4x-5=0$? Las raíces son $5$ y $-1$; $4$ **no** es raíz, así que **no hay resonancia**. Proponemos directamente
$$a_n^P = A\cdot 4^n.$$

**Paso 3 — reemplazar y despejar $A$.**
$$A\cdot 4^{n+2} - 4\cdot A\cdot 4^{n+1} - 5\cdot A\cdot 4^n = 10\cdot 4^n.$$
Sacando $4^n$ como factor común ($4^{n+2}=16\cdot 4^n$, $4\cdot 4^{n+1}=16\cdot 4^n$):
$$4^n\big(16A - 16A - 5A\big) = 10\cdot 4^n \ \Rightarrow\ -5A = 10 \ \Rightarrow\ A=-2.$$
Entonces $a_n^P = -2\cdot 4^n$.

**Paso 4 — solución general (superposición, Teorema 4).**
$$a_n = k_1\cdot 5^n + k_2\cdot(-1)^n - 2\cdot 4^n.$$

**Paso 5 — condiciones iniciales** (recién ahora, después de sumar la particular):
$$a_0 = k_1+k_2-2 = 1 \ \Rightarrow\ k_1+k_2=3,$$
$$a_1 = 5k_1 - k_2 - 8 = 7 \ \Rightarrow\ 5k_1-k_2=15.$$
Sumando ambas ecuaciones: $6k_1=18 \Rightarrow k_1=3$, y entonces $k_2=3-3=0$.

**Paso 6 — solución final.**
$$\boxed{a_n = 3\cdot 5^n - 2\cdot 4^n}$$

**Verificación:** $a_0=3-2=1$ ✓; $a_1=15-8=7$ ✓; por recurrencia, $a_2=4a_1+5a_0+10\cdot4^0=28+5+10=43$; por fórmula, $a_2=3\cdot25-2\cdot16=75-32=43$ ✓.

> [!tip] Si hubiera habido resonancia
> Si la base $s$ de la exponencial *hubiera coincidido* con alguna raíz (por ejemplo si $f(n)$ fuera $10\cdot 5^n$, con $5$ raíz simple de la característica), la propuesta $A\cdot 5^n$ sería en realidad una solución de la homogénea (múltiplo de $k_1\cdot 5^n$) y al reemplazarla en la ecuación daría $0=10\cdot5^n$, un absurdo. En ese caso corresponde multiplicar por $n$ y proponer $A\cdot n\cdot 5^n$ (ver tabla de la sección 4 y la lógica del Teorema 3).

### Ejemplo C — Problema inverso: de la fórmula cerrada a la recurrencia

Dado que la solución particular (fórmula cerrada) es $a_n = 3\cdot 5^n$, encontrar la relación de recurrencia de orden 1 que la genera.

**Paso 1 — escribir $a_n$ y $a_{n-1}$.**
$$a_n = 3\cdot 5^n, \qquad a_{n-1} = 3\cdot 5^{n-1}.$$

**Paso 2 — armar el cociente para eliminar la constante $3$.**
$$\frac{a_n}{a_{n-1}} = \frac{3\cdot 5^n}{3\cdot 5^{n-1}} = 5^{\,n-(n-1)} = 5.$$
El $3$ se cancela porque aparece multiplicando en numerador y denominador; esto es exactamente lo que se busca en el problema inverso: eliminar la constante libre para quedarnos con una relación entre términos consecutivos.

**Paso 3 — despejar $a_n$.**
$$\boxed{a_n = 5\cdot a_{n-1}}$$
con condición inicial, por ejemplo, $a_0 = 3\cdot 5^0 = 3$ (o equivalentemente $a_1=15$).

**Verificación con los primeros términos:** $a_0=3$, $a_1=5\cdot3=15=3\cdot5^1$ ✓, $a_2=5\cdot15=75=3\cdot5^2$ ✓. Coincide con el patrón "orden 1 homogénea, coeficientes constantes" de la sección 4: $a_n=c\cdot a_{n-1}$ con $c=5$ reproduce $a_n = c^{\,n}\cdot a_0 = 5^n\cdot 3$.

## 6. Conectores con otras unidades

**Con [[01-Razonamientos-Categoricos]] — la verificación por inducción como Generalización Universal iterada.** Cuando en la sección 3 verificamos $a_n=2-2^n$, en el fondo estamos construyendo, para cada $n$ concreto, una cadena de razonamientos válidos que en algún momento aprendiste a formalizar con reglas de inferencia. El caso base $P(0)$ y $P(1)$ juega el rol de premisas comprobadas directamente. El paso inductivo "$P(h-1) \wedge P(h) \Rightarrow P(h+1)$, para todo $h$" es una fórmula universal que, combinada con las premisas base mediante Modus Ponens repetido, permite derivar $P(2)$, luego $P(3)$, luego $P(4)$... El paso final —concluir "$P(n)$ para todo $n$"— es exactamente una **Generalización Universal**: como el paso inductivo se probó para un $h$ arbitrario (sin usar ninguna propiedad particular de $h$), lo que vale para ese $h$ genérico vale para todos. En otras palabras, una demostración por inducción *es* una plantilla de infinitas derivaciones formales (una por cada $n$), comprimida en dos pasos finitos gracias a que el paso inductivo se demuestra de manera genérica.

**Con [[02-Relaciones-de-Equivalencia]] — analogía estructural (débil, no una equivalencia formal).** Acá la conexión es más floja y conviene decirlo honestamente: no hay un teorema que identifique ambas unidades. Lo que sí vale la pena notar es un patrón de *forma de pensar* que se repite: en esta unidad, la solución general de una recurrencia no homogénea se arma **descomponiendo el problema en dos piezas que se combinan** ($a_n = a_n^H + a_n^P$, Teorema 4); en la unidad de relaciones de equivalencia, un conjunto se entiende **descomponiéndolo en piezas** (las clases de equivalencia) que son disjuntas y cuya unión es el conjunto entero (una partición). En ambos casos la estrategia general es "para entender/construir el objeto completo, separalo en partes más simples y after combinalas" — pero mientras que la partición exige que las piezas sean *disjuntas y exhaustivas*, la descomposición $a_n^H+a_n^P$ es una **suma algebraica** (las piezas se combinan aritméticamente, no como una partición de conjuntos). Es una analogía pedagógica sobre el método de "divide y combina", no una equivalencia matemática.

**Con [[03-Redes-y-Algebras-de-Boole]] — el conteo de subconjuntos como recurrencia de orden 1.** Sabemos que $|\mathcal{P}(A)| = 2^n$ cuando $|A|=n$. Esta fórmula cerrada es, en sí misma, la solución de una recurrencia de orden 1: si $a_n$ denota la cantidad de subconjuntos de un conjunto con $n$ elementos, entonces al agregar un elemento nuevo $x$ a un conjunto de $n-1$ elementos, cada subconjunto viejo genera exactamente dos subconjuntos nuevos (el que no incluye a $x$, igual al viejo, y el que sí lo incluye, el viejo más $\{x\}$). Esto da exactamente
$$a_n = 2\cdot a_{n-1}, \qquad a_0=1,$$
que es la recurrencia de orden 1 lineal homogénea de coeficientes constantes de la sección 2, con $c=2$. Aplicando la fórmula de la sección 4, $a_n = c^n \cdot a_0 = 2^n\cdot 1 = 2^n$, recuperando exactamente $|\mathcal{P}(A)|=2^n$. Es un ejemplo perfecto de cómo el pensamiento recurrente (mirar qué pasa al agregar un elemento) *deriva*, y no solo coincide con, un resultado que en el álgebra de Boole se prueba de otra manera (biyección con funciones características, o con cadenas binarias de longitud $n$).

**Con [[04-Congruencias-Euler-Fermat]] — dos recurrencias escondidas.** Primero, el **algoritmo de Euclides** para calcular $\gcd(a,b)$ es, estructuralmente, una recurrencia: si $r_0=a$, $r_1=b$, la relación
$$r_{k+1} = r_{k-1} \bmod r_k$$
define cada resto en función de los dos anteriores, y la particularidad de esta recurrencia es que **no** es de coeficientes constantes lineales en el sentido de esta unidad (usa el operador módulo, que no es lineal), pero comparte con nuestras recurrencias la idea esencial: la sucesión $(r_k)$ está definida recursivamente, y el algoritmo "resuelve" el problema (encontrar el $\gcd$) mostrando que la recurrencia llega a $r_k=0$ en **finitos pasos**, algo que en esta unidad garantizamos con la fórmula cerrada y allá se garantiza acotando el decrecimiento de los restos. Segundo, la **progresión de soluciones principales** de una congruencia lineal $ax\equiv b \pmod n$ con $d=\gcd(a,n)$ soluciones, dadas por
$$x_0,\ x_0+\tfrac{n}{d},\ x_0+2\tfrac{n}{d},\ \dots,\ x_0+(d-1)\tfrac{n}{d},$$
es exactamente una recurrencia lineal de orden 1, homogénea *salvo el término constante* $x_0$: si llamamos $a_k$ a la $k$-ésima solución, entonces
$$a_k = a_{k-1} + \frac{n}{d}, \qquad a_0 = x_0,$$
que es una recurrencia de orden 1 **no homogénea** con $f(k) = n/d$ constante y $c=1$ (la raíz de la característica "$x-1=0$" es $1$, así que hay resonancia y la solución particular es $A\cdot k$ en vez de $A$ constante — exactamente el caso de la fila "constante, raíz=1" de la tabla de la sección 4). Resolviéndola con nuestro método se obtiene $a_k = x_0 + k\cdot\frac{n}{d}$, la fórmula que ya conocías de la otra unidad, ahora deducida como caso particular del método general de recurrencias.

## 7. Errores comunes y trampas del examen

1. **Olvidar el factor $n$ en la raíz doble.** Escribir $a_n=k_1r^n+k_2r^n=(k_1+k_2)r^n$ en vez de $a_n=k_1r^n+k_2\,n\,r^n$. El primer error colapsa dos constantes en una sola, y el sistema de condiciones iniciales queda mal planteado (o directamente sin solución consistente si $a_0\neq a_1/r$ proporcionalmente).

2. **No chequear resonancia antes de proponer $a_n^P$.** Proponer $A\cdot s^n$ cuando $s$ ya es raíz de la característica lleva a una ecuación absurda del tipo $0 = f(n)$ al reemplazar (porque $A\cdot s^n$ resuelve la homogénea, entonces el lado izquierdo da $0$ siempre). Hay que revisar siempre si la forma propuesta "ya está incluida" en $a_n^H$, y si es así, multiplicar por $n$ (o por $n^2$ si con $n$ tampoco alcanza, caso de raíz doble coincidente).

3. **Errores de signo al armar la ecuación característica.** Si la recurrencia está escrita como $a_{n+2}=4a_{n+1}-3a_n$ hay que pasar todo de un lado, $a_{n+2}-4a_{n+1}+3a_n=0$, **antes** de leer los coeficientes $p,q$. Es un clásico invertir el signo de $p$ o de $q$ por no reordenar primero.

4. **Resolver el sistema de condiciones iniciales usando solo $a_n^H$, antes de sumar $a_n^P$.** Por el Teorema 4, las condiciones iniciales son condiciones sobre $a_n = a_n^H+a_n^P$ completo. Si se usan las condiciones iniciales sobre $a_n^H$ solo (olvidando sumar $a_n^P$ evaluada en $n=0,1$), los valores de $k_1,k_2$ quedan mal calculados.

5. **Confundir orden con grado.** Como se remarcó en la sección 2, son ejes independientes; una recurrencia puede ser de orden alto y grado 1 (lineal) o de orden bajo y grado alto (no lineal). El método de esta unidad **solo** aplica a recurrencias lineales.

6. **Verificar la solución en un solo caso base cuando el orden es 2.** Una recurrencia de orden 2 necesita **dos** casos base ($a_0$ y $a_1$, o los dos valores iniciales que correspondan) antes del paso inductivo; verificar solo $n=0$ no alcanza para arrancar la inducción.

7. **Aplicar la tabla de "$f(n)$ constante" sin fijarse si $1$ es raíz.** Es un caso particular del error 2, pero es tan frecuente que merece mención aparte: cuando $f(n)$ es una constante y $x=1$ es raíz de la característica (algo que pasa seguido en recurrencias de conteo), la propuesta correcta es $A\cdot n$, no $A$.

8. **En el problema inverso, no verificar con los primeros términos.** Cancelar constantes algebraicamente puede introducir errores de signo o de índice (confundir $a_{n-1}$ con $a_n$); siempre conviene reemplazar $n=1,2$ en la recurrencia obtenida y chequear contra la fórmula original.

## 8. Preguntas de autoevaluación

1. ¿Cuál es la diferencia formal entre orden y grado de una relación de recurrencia? Dar un ejemplo de una recurrencia de orden 3 y grado 2.
2. Escribir la ecuación característica de $a_{n+2}+5a_{n+1}+6a_n=0$ y resolverla.
3. Demostrar, sustituyendo directamente en la recurrencia, que si $r$ es raíz simple de $x^2+px+q=0$ entonces $a_n=r^n$ es solución (sin mirar el apunte).
4. ¿Por qué el determinante $r_2-r_1$ (Vandermonde) tiene que ser distinto de cero para poder despejar $k_1,k_2$ de manera única a partir de $a_0,a_1$?
5. Resolver $a_{n+2}-6a_{n+1}+9a_n=0$ con $a_0=2$, $a_1=3$ (atención: raíz doble).
6. Para $a_{n+2}-5a_{n+1}+6a_n=2^n$, ¿hay resonancia? Justificar antes de resolver, y después resolverla completa.
7. Dada la fórmula cerrada $a_n=4\cdot 3^n - n$, encontrar una recurrencia (no necesariamente de orden 1) que la genere.
8. Enunciar con precisión el caso base y el paso inductivo para verificar por inducción una solución de una recurrencia de orden 2. ¿Por qué hacen falta dos casos base?
9. Explicar con tus palabras por qué "solución general = homogénea + particular" es consecuencia de la linealidad del operador de recurrencia, y no una regla arbitraria.
10. Sin resolver toda la recurrencia, explicar por qué la solución general de $a_n=2a_{n-1}+3$ debe tener la forma $a_n=k\cdot 2^n - 3$ (pensar en la resonancia y en qué constante particular hace que $A=-A\cdot2-... $ cierre, o resolverla si hace falta para verificar la intuición).

## 9. Referencias

- Teoría original: `../05_relaciones_recurrencia/readme.md`
- Ejercicios resueltos: `../ejercicios-resueltos/tema5_recurrencia.md`
- Volver al índice: [[00-Indice-Matematica-Discreta]]
