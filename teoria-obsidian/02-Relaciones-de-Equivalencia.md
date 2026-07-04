---
tags: [matematica-discreta, tema-2, relaciones, unsam]
aliases: ["Relaciones de Equivalencia", "Tema 2"]
---

# Relaciones de Equivalencia

> [!info] Ubicación en la materia
> Esta unidad retoma las herramientas lógicas de [[01-Razonamientos-Categoricos]] para construir demostraciones formales, y sienta la base estructural (clases, cociente, partición) que [[04-Congruencias-Euler-Fermat]] usa sin volver a explicar. Es, junto con las relaciones de orden de [[03-Redes-y-Algebras-de-Boole]], una de las dos grandes familias de relaciones binarias "bien portadas" que aparecen en toda la materia.

## 1. Introducción y motivación

Cuando trabajamos con conjuntos, muchas veces no nos interesa la identidad exacta de cada elemento, sino si dos elementos "se comportan igual" respecto de alguna propiedad. Por ejemplo:

- En aritmética, no siempre importa si un número es el 7 o el 14; a veces solo importa su resto al dividir por 3 (ambos dejan resto 1, entonces "son lo mismo" módulo 3).
- En geometría, dos triángulos pueden ser distintos como conjuntos de puntos pero "iguales" en el sentido de ser semejantes o congruentes.
- En programación, dos fracciones distintas como $2/4$ y $3/6$ representan "el mismo" número racional.

En todos estos casos hay una idea común: agrupar elementos de un conjunto en función de una noción de "igualdad relajada" que no es la igualdad estricta ($=$) sino una relación que se comporta de manera parecida a la igualdad. Esa relación necesita cumplir tres propiedades intuitivas para que el agrupamiento tenga sentido:

1. Todo elemento debe estar relacionado consigo mismo (reflexividad): si agrupamos por "mismo resto módulo 3", un número tiene el mismo resto que él mismo.
2. Si $x$ está agrupado con $y$, entonces $y$ debe estar agrupado con $x$ (simetría): el orden en que comparamos no debería importar.
3. Si $x$ está agrupado con $y$, e $y$ está agrupado con $z$, entonces $x$ debe estar agrupado con $z$ (transitividad): si $x$ e $y$ "son lo mismo" e $y$ y $z$ "son lo mismo", entonces $x$ y $z$ también deberían serlo.

Una relación binaria que cumple estas tres propiedades se llama **relación de equivalencia**, y es exactamente la herramienta matemática que formaliza la idea de "agrupar por igualdad relajada". El resultado de agrupar es una **partición** del conjunto original: el conjunto queda dividido en "cajones" disjuntos que en conjunto lo cubren completamente, donde cada cajón (llamado **clase de equivalencia**) contiene a todos los elementos que son "lo mismo" entre sí según la relación.

Esta unidad es central en la materia porque:

- Da el marco formal para practicar demostraciones rigurosas con cuantificadores (conectando con [[01-Razonamientos-Categoricos]]).
- Es la base conceptual exacta sobre la que se construyen las congruencias módulo $n$ y el conjunto $\mathbb{Z}_n$ (ver [[04-Congruencias-Euler-Fermat]]).
- Sirve de contraste con las relaciones de orden parcial que se ven en [[03-Redes-y-Algebras-de-Boole]], mostrando que "parecerse a la igualdad" (simetría) y "parecerse a $\le$" (antisimetría) son caminos estructuralmente opuestos.

## 2. Definiciones formales

### 2.1 Relación binaria

Dado un conjunto $A$, una **relación binaria** $R$ en $A$ es un subconjunto del producto cartesiano $A \times A$:

$$R \subseteq A \times A$$

Si el par ordenado $(x,y) \in R$, decimos que "$x$ está relacionado con $y$" y lo notamos $xRy$. Si $(x,y) \notin R$, escribimos $x\not Ry$ o $\lnot(xRy)$.

Es fundamental no confundir $R$ (el conjunto de pares) con $xRy$ (la proposición que dice que el par $(x,y)$ pertenece a $R$). Todas las propiedades que siguen se enuncian sobre proposiciones $xRy$, cuantificando sobre los elementos de $A$.

### 2.2 Propiedad reflexiva

$R$ es **reflexiva** en $A$ si:

$$\forall x \in A: \; xRx$$

Es decir, todo elemento de $A$, sin excepción, debe estar relacionado consigo mismo. Alcanza con que un solo elemento de $A$ no cumpla $xRx$ para que $R$ **no** sea reflexiva.

### 2.3 Propiedad simétrica

$R$ es **simétrica** en $A$ si:

$$\forall x,y \in A: \; xRy \rightarrow yRx$$

Es una implicación condicional: no se afirma que "todo par de elementos está relacionado en ambos sentidos", sino que **si** $x$ está relacionado con $y$, **entonces** necesariamente $y$ está relacionado con $x$. Si $x \not R y$, la propiedad no exige nada sobre $yRx$ (la implicación es verdadera trivialmente).

### 2.4 Propiedad transitiva

$R$ es **transitiva** en $A$ si:

$$\forall x,y,z \in A: \; (xRy \land yRz) \rightarrow xRz$$

De nuevo es condicional: si existe una "cadena" $x \to y \to z$ dentro de la relación, entonces debe existir también el "atajo" directo $x \to z$.

### 2.5 Relación de equivalencia

$R$ es una **relación de equivalencia** en $A$ si es reflexiva, simétrica y transitiva simultáneamente. Se suele notar $x \equiv y$ o $x \sim y$ en vez de $xRy$ cuando se sabe que $R$ es de equivalencia, precisamente para resaltar el parecido con la igualdad.

### 2.6 Criterios con matriz de la relación

Si $A = \{a_1, \dots, a_n\}$ es finito, $R$ se representa con una matriz booleana $M = (m_{ij})$ de $n \times n$, donde:

$$m_{ij} = 1 \iff a_i R a_j$$

Los tres criterios matriciales son:

- **Reflexiva** $\iff$ toda la diagonal principal de $M$ está formada por unos: $m_{ii}=1$ para todo $i$. Esto es exactamente la traducción de "todo elemento está relacionado consigo mismo" a coordenadas de matriz.
- **Simétrica** $\iff$ $M = M^{t}$ (la matriz es igual a su transpuesta). Esto ocurre porque $m_{ij}=1 \iff a_iRa_j$ y $m_{ji}=1 \iff a_jRa_i$; pedir que ambos valores coincidan siempre es exactamente pedir que $a_iRa_j \rightarrow a_jRa_i$ para todo par de índices.
- **Transitiva** $\iff$ $M^2 \le M$ (usando **producto booleano**, donde la suma es OR y el producto es AND, y $\le$ se entiende entrada a entrada). En la sección 3.4 se demuestra en detalle por qué esto funciona, pero la idea intuitiva es: la entrada $(i,j)$ de $M^2$ vale 1 si y solo si existe algún $k$ intermedio tal que $a_iRa_k$ y $a_kRa_j$ (es decir, existe una cadena de longitud 2 de $a_i$ a $a_j$). Pedir $M^2 \le M$ es exactamente pedir que, cada vez que exista esa cadena intermedia, también exista la relación directa $a_iRa_j$ — que es la definición de transitividad.

### 2.7 Criterios con digrafo

Representando $R$ como un grafo dirigido (digrafo) donde los vértices son los elementos de $A$ y hay una flecha de $a$ a $b$ si $aRb$:

- **Reflexiva** $\iff$ todo vértice tiene un lazo (una flecha que sale y vuelve a él mismo).
- **Simétrica** $\iff$ toda flecha tiene su "vuelta": si hay flecha de $a$ a $b$, hay flecha de $b$ a $a$ (en la práctica, se dibujan como aristas no dirigidas o dobles).
- **Transitiva** $\iff$ cada vez que hay un camino (de cualquier longitud, siguiendo flechas) de $a$ a $b$, hay también flecha directa de $a$ a $b$. Esto es la versión gráfica exacta del criterio matricial: un camino de $a$ a $b$ que pasa por vértices intermedios corresponde a una cadena de relaciones, y transitividad aplicada repetidamente colapsa esa cadena en un único paso directo.

### 2.8 Clase de equivalencia

Sea $R$ una relación de equivalencia en $A$ y sea $x \in A$. La **clase de equivalencia** de $x$ es el conjunto de todos los elementos de $A$ relacionados con $x$:

$$\bar{x} = [x] = \{ y \in A \mid xRy \}$$

Notación: $\bar{x}$ y $[x]$ son intercambiables; en esta unidad usamos preferentemente $\bar{x}$.

### 2.9 Conjunto cociente

El **conjunto cociente** de $A$ por $R$ es el conjunto formado por todas las clases de equivalencia distintas:

$$A/R = \{ \bar{x} \mid x \in A \}$$

Notar que $A/R$ es un conjunto de conjuntos (cada elemento de $A/R$ es a su vez un subconjunto de $A$).

### 2.10 Partición

Una familia de subconjuntos $\{A_1, A_2, \dots, A_k\}$ de $A$ es una **partición** de $A$ si cumple simultáneamente:

1. **No vacíos:** $A_i \neq \emptyset$ para todo $i$.
2. **Disjuntos dos a dos:** $A_i \cap A_j = \emptyset$ para todo $i \neq j$.
3. **Cobertura total:** $A_1 \cup A_2 \cup \dots \cup A_k = A$.

Intuitivamente, una partición reparte $A$ en "cajones" que no se superponen y que entre todos no dejan ningún elemento afuera.

## 3. Teoremas y demostraciones

### 3.1 Teorema: la congruencia módulo $n$ es relación de equivalencia

**Enunciado.** Sea $n \in \mathbb{Z}^+$ fijo. Definimos en $\mathbb{Z}$ la relación $R$ por:

$$xRy \iff n \mid (x-y)$$

(léase: "$n$ divide a $x-y$", es decir, existe $k \in \mathbb{Z}$ tal que $x - y = nk$). Entonces $R$ es una relación de equivalencia en $\mathbb{Z}$.

**Demostración.**

*Reflexividad.* Sea $x \in \mathbb{Z}$ arbitrario. Queremos ver $xRx$, es decir, $n \mid (x-x)$. Calculamos:

$$x - x = 0 = n \cdot 0$$

Como $0 \in \mathbb{Z}$, existe un entero (a saber, $0$) tal que $x-x = n\cdot 0$, luego por definición $n \mid (x-x)$. Por lo tanto $xRx$. Como $x$ era un elemento arbitrario de $\mathbb{Z}$, esto vale para todo $x \in \mathbb{Z}$. $\therefore R$ es reflexiva. $\blacksquare$

*Simetría.* Sean $x,y \in \mathbb{Z}$ tales que $xRy$ (hipótesis). Por definición de $R$, esto significa que $n \mid (x-y)$, es decir, existe $k \in \mathbb{Z}$ tal que:

$$x - y = nk$$

Multiplicando ambos miembros por $-1$:

$$-(x-y) = -(nk) \implies y - x = n(-k)$$

Como $k \in \mathbb{Z}$, también $-k \in \mathbb{Z}$. Entonces existe un entero (a saber, $-k$) tal que $y-x = n(-k)$, es decir, $n \mid (y-x)$. Por definición de $R$, esto es exactamente $yRx$. $\therefore R$ es simétrica. $\blacksquare$

*Transitividad.* Sean $x,y,z \in \mathbb{Z}$ tales que $xRy \land yRz$ (hipótesis). Por definición de $R$:

$$xRy \implies x - y = nk \quad \text{para algún } k \in \mathbb{Z}$$
$$yRz \implies y - z = nt \quad \text{para algún } t \in \mathbb{Z}$$

Sumamos miembro a miembro ambas igualdades:

$$(x-y) + (y-z) = nk + nt$$

El miembro izquierdo se simplifica (el $y$ se cancela):

$$x - z = n(k+t)$$

Como $k,t \in \mathbb{Z}$, también $k+t \in \mathbb{Z}$. Luego existe un entero (a saber, $k+t$) tal que $x - z = n(k+t)$, es decir, $n \mid (x-z)$. Por definición de $R$, esto es $xRz$. $\therefore R$ es transitiva. $\blacksquare$

Como $R$ es reflexiva, simétrica y transitiva, **$R$ es una relación de equivalencia en $\mathbb{Z}$.** A esta relación se la llama **congruencia módulo $n$** y se nota $x \equiv y \pmod{n}$. Ver [[04-Congruencias-Euler-Fermat]] para todo lo que se construye a partir de acá.

### 3.2 Teorema de buena definición de las clases de equivalencia

Sea $R$ una relación de equivalencia en $A$, y sean $x,y \in A$.

**Parte A. Si $xRy$, entonces $\bar{x} = \bar{y}$.**

*Demostración (por doble inclusión).*

Hipótesis: $xRy$.

($\subseteq$) Sea $z \in \bar{x}$ arbitrario. Por definición de clase, $z \in \bar{x}$ significa $xRz$. Por simetría de $R$ aplicada a la hipótesis $xRy$, tenemos $yRx$. Ahora tenemos $yRx$ y $xRz$; por transitividad de $R$, se deduce $yRz$. Pero $yRz$ es exactamente la condición para que $z \in \bar{y}$ (por definición de clase de $y$). Como $z$ era arbitrario en $\bar{x}$, concluimos $\bar{x} \subseteq \bar{y}$.

($\supseteq$) Sea $z \in \bar{y}$ arbitrario. Por definición de clase, $z \in \bar{y}$ significa $yRz$. Como $xRy$ (hipótesis) y $yRz$, por transitividad se deduce $xRz$. Pero $xRz$ es exactamente la condición para que $z \in \bar{x}$. Como $z$ era arbitrario en $\bar{y}$, concluimos $\bar{y} \subseteq \bar{x}$.

De $\bar{x} \subseteq \bar{y}$ y $\bar{y} \subseteq \bar{x}$ se concluye, por definición de igualdad de conjuntos, que $\bar{x} = \bar{y}$. $\blacksquare$

**Parte B. Si $\lnot(xRy)$, entonces $\bar{x} \cap \bar{y} = \emptyset$.**

*Demostración (por contrarrecíproco / contradicción).* Supongamos, por el absurdo, que $\bar{x} \cap \bar{y} \neq \emptyset$. Entonces existe algún $z \in \bar{x} \cap \bar{y}$, es decir:

$$z \in \bar{x} \implies xRz \qquad \text{y} \qquad z \in \bar{y} \implies yRz$$

Por simetría de $R$ aplicada a $yRz$, obtenemos $zRy$. Ahora tenemos $xRz$ y $zRy$; por transitividad de $R$, se deduce $xRy$. Pero esto contradice la hipótesis $\lnot(xRy)$. Como llegamos a un absurdo, la suposición $\bar{x} \cap \bar{y} \neq \emptyset$ es falsa. $\therefore \bar{x} \cap \bar{y} = \emptyset$. $\blacksquare$

**Corolario (contrapositivo de la Parte B).** Si $\bar{x} \cap \bar{y} \neq \emptyset$, entonces $xRy$ (y por Parte A, $\bar{x}=\bar{y}$). Esto justifica el resultado clave: **dos clases de equivalencia son iguales o son disjuntas, nunca se solapan parcialmente.** Esta dicotomía es la que hace que las clases formen una partición.

**Corolario (representante arbitrario).** De la Parte A se deduce que cualquier elemento de una clase puede usarse como "representante": si $w \in \bar{x}$, entonces $xRw$, y por Parte A, $\bar{x} = \bar{w}$. Por eso decimos, por ejemplo, que la clase $\{\dots,-3,0,3,6,\dots\}$ módulo 3 se puede escribir indistintamente como $\bar{0}$, $\bar{3}$, $\overline{-3}$, etc.

### 3.3 Teorema Fundamental de las relaciones de equivalencia

**Enunciado.** $R$ es una relación de equivalencia en $A$ $\iff$ $A/R$ es una partición de $A$.

**Demostración, dirección ($\Rightarrow$).** Supongamos que $R$ es una relación de equivalencia en $A$. Queremos ver que $A/R = \{\bar{x} \mid x \in A\}$ cumple las tres condiciones de partición.

*(i) No vacíos.* Sea $\bar{x} \in A/R$ arbitraria. Por reflexividad de $R$, $xRx$, y por definición de clase, esto significa $x \in \bar{x}$. Luego $\bar{x} \neq \emptyset$ (tiene al menos al elemento $x$).

*(ii) Disjuntas dos a dos.* Sean $\bar{x}, \bar{y} \in A/R$ con $\bar{x} \neq \bar{y}$. Queremos ver $\bar{x} \cap \bar{y} = \emptyset$. Razonamos por contrarrecíproco de la Parte A del teorema 3.2: si fuera $xRy$, por la Parte A tendríamos $\bar{x} = \bar{y}$, contradiciendo la hipótesis $\bar{x} \neq \bar{y}$. Luego debe ser $\lnot(xRy)$, y por la Parte B del teorema 3.2, $\bar{x} \cap \bar{y} = \emptyset$.

*(iii) Cobertura total.* Queremos ver $\bigcup_{x \in A} \bar{x} = A$. La inclusión $\bigcup_{x\in A} \bar x \subseteq A$ es trivial porque cada $\bar x$ es subconjunto de $A$ (las clases se definen como subconjuntos de $A$). Para la otra inclusión, sea $a \in A$ arbitrario; por (i) sabemos $a \in \bar{a}$, y $\bar{a}$ es uno de los conjuntos de la unión, luego $a \in \bigcup_{x\in A} \bar{x}$. Como $a$ era arbitrario, $A \subseteq \bigcup_{x\in A}\bar x$.

De (i), (ii) y (iii), $A/R$ es una partición de $A$. $\blacksquare$

**Demostración, dirección ($\Leftarrow$).** Supongamos que $P = \{A_1, \dots, A_k\}$ es una partición de $A$. Definimos la relación:

$$xRy \iff x \text{ e } y \text{ pertenecen al mismo bloque } A_i \text{ de la partición}$$

Queremos ver que $R$ es de equivalencia y que además $A/R = P$.

*Reflexividad.* Sea $x \in A$ arbitrario. Como $P$ es partición, por la condición de cobertura total, $x$ pertenece a algún bloque $A_i$. Entonces $x$ y $x$ están en el mismo bloque $A_i$, luego $xRx$.

*Simetría.* Sean $x,y \in A$ con $xRy$. Por definición de $R$, $x$ e $y$ están en el mismo bloque $A_i$. Pero entonces, trivialmente, $y$ y $x$ también están en ese mismo bloque $A_i$, luego $yRx$.

*Transitividad.* Sean $x,y,z \in A$ con $xRy \land yRz$. Por $xRy$, $x$ e $y$ están en el mismo bloque, digamos $A_i$. Por $yRz$, $y$ y $z$ están en el mismo bloque, digamos $A_j$. Como $y \in A_i$ y $y \in A_j$, tenemos $y \in A_i \cap A_j$, es decir $A_i \cap A_j \neq \emptyset$. Pero por la condición de disjunción de la partición, dos bloques distintos tienen intersección vacía; como la intersección no es vacía, debe ser $A_i = A_j$. Entonces $x, y, z$ están todos en el mismo bloque $A_i$, en particular $x$ y $z$ están en el mismo bloque, luego $xRz$.

Por lo tanto $R$ es una relación de equivalencia.

*Además, $A/R = P$.* Sea $A_i \in P$ un bloque cualquiera, no vacío por definición de partición, así que tomemos $x \in A_i$. Afirmamos $\bar{x} = A_i$: si $y \in A_i$, entonces $x$ e $y$ están en el mismo bloque $A_i$, luego $xRy$, luego $y \in \bar x$; recíprocamente si $y \in \bar x$ entonces $xRy$, es decir $x$ e $y$ están en un mismo bloque, que por unicidad de bloque conteniendo a $x$ debe ser $A_i$, luego $y \in A_i$. Así $\bar x = A_i$, y como cada bloque de $P$ es la clase de cualquiera de sus elementos, y cada clase de $A/R$ coincide con algún bloque (por el mismo argumento aplicado a un representante), se concluye $A/R = P$. $\blacksquare$

Esta doble implicación es lo que se conoce como **Teorema Fundamental**: da una relación de equivalencia y obtenés una partición; dale una partición y obtenés (de manera única) una relación de equivalencia. Son, en esencia, dos maneras de mirar el mismo objeto.

### 3.4 Por qué $M^2 \le M$ caracteriza la transitividad

Recordemos que el **producto booleano** de dos matrices $0$-$1$ de tamaño $n\times n$, $M \odot M = M^{2}$, se define entrada a entrada como:

$$(M^2)_{ij} = \bigvee_{k=1}^{n} \left( m_{ik} \land m_{kj} \right)$$

es decir, usando OR en vez de suma y AND en vez de producto usual.

**Interpretación combinatoria.** $(M^2)_{ij} = 1$ si y solo si existe **al menos un** índice $k \in \{1,\dots,n\}$ tal que $m_{ik}=1$ y $m_{kj}=1$, es decir, tal que $a_i R a_k$ **y** $a_k R a_j$. En otras palabras, $(M^2)_{ij}=1$ codifica exactamente la existencia de un elemento intermedio $a_k$ que conecta a $a_i$ con $a_j$ en dos pasos (esto es la composición de la relación $R$ consigo misma, $R \circ R$).

**Demostración de la equivalencia.**

($\Rightarrow$) Supongamos $R$ transitiva y veamos $M^2 \le M$. Sea $(i,j)$ tal que $(M^2)_{ij}=1$. Por la interpretación anterior, existe $k$ con $a_iRa_k$ y $a_kRa_j$. Por transitividad de $R$ (aplicada con $x=a_i, y=a_k, z=a_j$), se deduce $a_iRa_j$, es decir $m_{ij}=1$. Como esto vale para toda entrada donde $(M^2)_{ij}=1$, se cumple $M^2 \le M$ (cada 1 de $M^2$ tiene un 1 correspondiente en $M$).

($\Leftarrow$) Supongamos $M^2 \le M$ y veamos que $R$ es transitiva. Sean $x,y,z \in A$ (correspondientes a índices $i,k,j$) tales que $xRy \land yRz$, es decir $m_{ik}=1$ y $m_{kj}=1$. Entonces, por definición del producto booleano, $(M^2)_{ij} = \bigvee_k (m_{ik}\land m_{kj}) \ge m_{ik}\land m_{kj} = 1$, luego $(M^2)_{ij}=1$. Por hipótesis $M^2 \le M$, se deduce $m_{ij}=1$, es decir $xRz$. Como $x,y,z$ eran arbitrarios cumpliendo la hipótesis, $R$ es transitiva. $\blacksquare$

En resumen: **$M^2$ es la matriz de "existe un camino de longitud 2"**, y pedir $M^2 \le M$ es pedir que todo camino de longitud 2 ya esté cubierto por un camino directo de longitud 1 — que es exactamente la definición de transitividad trasladada a matrices.

## 4. Fórmulas clave (tabla de repaso rápido)

| Concepto | Definición formal | Criterio matricial | Criterio en digrafo |
|---|---|---|---|
| Reflexiva | $\forall x \in A: xRx$ | Diagonal de $M$ toda en 1 | Todo vértice tiene lazo |
| Simétrica | $\forall x,y \in A: xRy \to yRx$ | $M = M^t$ | Toda flecha tiene su vuelta |
| Transitiva | $\forall x,y,z \in A: (xRy \land yRz) \to xRz$ | $M^2 \le M$ (producto booleano) | Todo camino $a\to b$ implica flecha directa $a\to b$ |
| Relación de equivalencia | Reflexiva + Simétrica + Transitiva | Diagonal en 1, $M=M^t$, $M^2\le M$ | Lazos + vueltas + caminos colapsados |
| Clase de equivalencia | $\bar{x} = \{y \in A \mid xRy\}$ | Fila $i$ de $M$ con 1s marca los elementos de $\bar{x_i}$ | Vértices alcanzables (y que alcanzan) a $x$ |
| Conjunto cociente | $A/R = \{\bar{x} \mid x \in A\}$ | — | — |
| Partición | $A_i \neq \emptyset$, $A_i \cap A_j = \emptyset$ ($i\neq j$), $\bigcup A_i = A$ | — | — |
| Teorema Fundamental | $R$ equivalencia en $A$ $\iff$ $A/R$ partición de $A$ | — | — |

## 5. Ejemplos resueltos paso a paso

### Ejemplo (a): demostrar que una relación dada por fórmula es de equivalencia

**Relación:** en $\mathbb{R}$, $xRy \iff x^2 - 5x = y^2 - 5y$.

**Reflexividad.** Sea $x \in \mathbb{R}$ arbitrario. Queremos ver $xRx$, es decir, $x^2-5x = x^2-5x$. Esto es una igualdad trivial (todo número es igual a sí mismo), por lo tanto se cumple para cualquier $x$. $\therefore R$ es reflexiva.

**Simetría.** Sean $x,y \in \mathbb{R}$ tales que $xRy$ (hipótesis), es decir:

$$x^2 - 5x = y^2 - 5y$$

La igualdad numérica es simétrica como relación lógica: si $A=B$ entonces $B=A$. Aplicando esto:

$$y^2 - 5y = x^2 - 5x$$

que es exactamente la condición $yRx$. $\therefore R$ es simétrica.

**Transitividad.** Sean $x,y,z \in \mathbb{R}$ tales que $xRy \land yRz$ (hipótesis), es decir:

$$x^2-5x = y^2-5y \qquad \text{y} \qquad y^2-5y = z^2-5z$$

Por transitividad de la igualdad numérica (si $A=B$ y $B=C$ entonces $A=C$):

$$x^2-5x = z^2-5z$$

que es exactamente la condición $xRz$. $\therefore R$ es transitiva.

Como $R$ cumple las tres propiedades, **$R$ es relación de equivalencia en $\mathbb{R}$**.

**Hallando las clases.** Fijemos $x=0$. Buscamos $\bar{0} = \{y \in \mathbb{R} \mid 0^2-5\cdot 0 = y^2-5y\}$, es decir $y^2-5y=0$, o sea $y(y-5)=0$, luego $y=0$ o $y=5$. Entonces:

$$\bar{0} = \{0,5\}$$

Esto ilustra que, en general, las clases de esta relación son conjuntos de a lo sumo dos elementos: para $x$ fijo, buscamos $y$ tal que $y^2-5y = x^2-5x$, es decir $y^2-5y-(x^2-5x)=0$. Pensando esto como ecuación cuadrática en $y$: $y^2 -5y - (x^2-5x) = 0$. Una raíz es obviamente $y=x$ (porque $x^2-5x-(x^2-5x)=0$). Por Gauss/factor, la otra raíz $y'$ cumple $y + y' = 5$ (suma de raíces $=-(-5)/1=5$), luego $y' = 5-x$. Entonces, en general:

$$\bar{x} = \{x, \, 5-x\}$$

(los dos elementos coinciden, formando una clase de un solo elemento, cuando $x = 5-x$, es decir $x=2{,}5$). Por ejemplo $\bar{2} = \{2,3\}$, $\bar{1}=\{1,4\}$, $\bar{2{,}5}=\{2{,}5\}$. El conjunto cociente $\mathbb{R}/R$ tiene tantas clases como pares $\{x,5-x\}$ distintos, es decir, se identifica naturalmente con el intervalo $[2{,}5, +\infty)$ o $(-\infty, 2{,}5]$ tomando siempre el representante correspondiente.

### Ejemplo (b): hallar clases y cociente con el método práctico

**Relación en un conjunto finito.** $A = \{1,2,3,4,5,6\}$, $xRy \iff 3 \mid (x-y)$ (es la congruencia módulo 3 restringida a $A$; ya sabemos por el Teorema 3.1 que es de equivalencia).

Aplicamos el método práctico:

1. Tomamos $x_1 = 1$. Buscamos todos los $y \in A$ tales que $3 \mid (1-y)$: $y=1$ ($1-1=0=3\cdot0$ ✓), $y=4$ ($1-4=-3=3\cdot(-1)$ ✓). Los demás no cumplen ($1-2=-1$, no; $1-3=-2$, no; $1-5=-4$, no; $1-6=-5$, no). Entonces $\bar{1} = \{1,4\}$.
2. Tomamos $x_2 = 2$ (no cubierto por $\bar 1$). Buscamos $y$ con $3\mid(2-y)$: $y=2$ ($0$✓), $y=5$ ($2-5=-3$✓). Entonces $\bar{2}=\{2,5\}$.
3. Tomamos $x_3=3$ (no cubierto por $\bar1$ ni $\bar2$). Buscamos $y$ con $3\mid(3-y)$: $y=3$($0$✓), $y=6$($3-6=-3$✓). Entonces $\bar{3}=\{3,6\}$.
4. Ya cubrimos $\{1,4\}\cup\{2,5\}\cup\{3,6\} = \{1,2,3,4,5,6\}=A$. No quedan elementos sin clasificar.

Entonces:

$$A/R = \{\{1,4\},\{2,5\},\{3,6\}\}$$

**Verificación de partición.** Los tres bloques son no vacíos; son disjuntos dos a dos ($\{1,4\}\cap\{2,5\}=\emptyset$, etc.); y su unión es $A$. Por lo tanto $A/R$ es efectivamente una partición de $A$, consistente con el Teorema Fundamental.

**Ejemplo adicional en $\mathbb{Z}$ completo (referencia).** Con la misma relación pero en $\mathbb{Z}$ (no restringida a $A$), el conjunto cociente es infinito en elementos "adentro" de cada clase pero tiene solo 3 clases:

$$\mathbb{Z}/{\equiv_3} = \{\bar 0, \bar 1, \bar 2\}, \quad \bar 0 = \{\dots,-3,0,3,6,\dots\},\ \bar 1=\{\dots,-2,1,4,7,\dots\},\ \bar 2=\{\dots,-1,2,5,8,\dots\}$$

### Ejemplo (c): verificar equivalencia usando matriz

Sea $A = \{1,2,3\}$ y $R$ dada por $R = \{(1,1),(2,2),(3,3),(1,2),(2,1)\}$ (es decir, $1$ y $2$ están relacionados entre sí y cada elemento consigo mismo; $3$ solo consigo mismo).

**Matriz de $R$** (filas y columnas en el orden $1,2,3$):

$$M = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}$$

**Verificación de reflexividad.** La diagonal principal es $m_{11}=1, m_{22}=1, m_{33}=1$: todos 1. ✓ Reflexiva.

**Verificación de simetría.** Comparamos $M$ con $M^t$:

$$M^t = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} = M$$

Son idénticas. ✓ Simétrica.

**Verificación de transitividad ($M^2 \le M$, producto booleano).** Calculamos entrada por entrada, con $(M^2)_{ij} = \bigvee_k (m_{ik}\land m_{kj})$:

- $(M^2)_{11} = (m_{11}\land m_{11}) \lor (m_{12}\land m_{21}) \lor (m_{13}\land m_{31}) = (1\land1)\lor(1\land1)\lor(0\land0) = 1$
- $(M^2)_{12} = (m_{11}\land m_{12})\lor(m_{12}\land m_{22})\lor(m_{13}\land m_{32}) = (1\land1)\lor(1\land1)\lor(0\land0)=1$
- $(M^2)_{13} = (m_{11}\land m_{13})\lor(m_{12}\land m_{23})\lor(m_{13}\land m_{33}) = (1\land0)\lor(1\land0)\lor(0\land1)=0$
- $(M^2)_{21} = 1$ (simétrico al cálculo de $(M^2)_{12}$ por simetría de $M$)
- $(M^2)_{22} = 1$, $(M^2)_{23}=0$, $(M^2)_{31}=0$, $(M^2)_{32}=0$, $(M^2)_{33} = (m_{31}\land m_{13})\lor(m_{32}\land m_{23})\lor(m_{33}\land m_{33}) = 0\lor0\lor1=1$

Entonces:

$$M^2 = \begin{pmatrix} 1&1&0\\1&1&0\\0&0&1 \end{pmatrix} = M$$

Como $M^2 = M$, en particular $M^2 \le M$ (toda entrada de $M^2$ que es 1 también es 1 en $M$; de hecho coinciden exactamente). ✓ Transitiva.

Como las tres condiciones matriciales se cumplen, **$R$ es relación de equivalencia en $A=\{1,2,3\}$**, con clases $\bar1=\bar2=\{1,2\}$ y $\bar3=\{3\}$, dando la partición $A/R = \{\{1,2\},\{3\}\}$.

## 6. Conectores con otras unidades

**Con [[01-Razonamientos-Categoricos]].** Cada una de las tres demostraciones de la sección 3 sigue al pie de la letra la estructura de un razonamiento categórico formal: se abre con un cuantificador universal ("sea $x \in A$ arbitrario", "sean $x,y \in A$ tales que..."), se toma una hipótesis (en simetría y transitividad, una implicación condicional cuyo antecedente se asume), se aplican reglas de inferencia (sustitución, transitividad de la igualdad, modus ponens) y se llega a la tesis. En particular, la frase "sea $x \in A$ arbitrario" **es** una aplicación de la regla de **Generalización Universal**: probamos la propiedad para un elemento genérico (no fijo, no elegido con propiedades especiales) y de ahí concluimos que vale para *todos* los elementos de $A$. Confundir "arbitrario" con "un valor particular que yo elijo" invalida la demostración — es el mismo error lógico que se señala en la Unidad 1 al estudiar cuantificadores.

**Con [[03-Redes-y-Algebras-de-Boole]].** Las relaciones de equivalencia y las relaciones de **orden parcial** comparten dos de sus tres propiedades definitorias (reflexividad y transitividad), pero difieren radicalmente en la tercera: donde la equivalencia pide **simetría** ($xRy \to yRx$), el orden parcial pide **antisimetría** ($xRy \land yRx \to x=y$). Estas dos condiciones son, salvo en la diagonal, mutuamente excluyentes: si $R$ es simétrica y además antisimétrica, entonces para todo par $x\ne y$ con $xRy$, simetría da $yRx$, y antisimetría aplicada a $xRy \land yRx$ fuerza $x=y$, contradicción. Por lo tanto, **la única relación que puede ser simultáneamente de equivalencia y de orden parcial (en un conjunto con más de un elemento) es la igualdad pura ($R=\{(x,x): x\in A\}$)**, que es un caso degenerado sin relaciones "cruzadas" entre distintos elementos. Esto explica por qué en una relación de orden como $\le$ en $\mathbb{R}$, tener $x\le y$ con $x\ne y$ excluye automáticamente $y \le x$: el orden avanza en una sola dirección, mientras que la equivalencia no distingue direcciones.

**Con [[04-Congruencias-Euler-Fermat]].** Este es el vínculo más fuerte y directo de toda la unidad: la **congruencia módulo $n$**, demostrada como relación de equivalencia en la sección 3.1, es exactamente la relación que da nombre y estructura al tema de Congruencias. El conjunto $\mathbb{Z}_n$ que se usa constantemente para resolver ecuaciones del tipo $ax \equiv b \pmod n$ **es literalmente el conjunto cociente** definido acá:

$$\mathbb{Z}_n = \mathbb{Z}/{\equiv_n} = \{\bar 0, \bar 1, \dots, \overline{n-1}\}$$

Cada "clase residual módulo $n$" que se usa en Congruencias (el conjunto de todos los enteros que dejan el mismo resto al dividir por $n$) es, sin ningún cambio de definición, una clase de equivalencia $\bar{x} = \{y \in \mathbb{Z} : n \mid (x-y)\}$ tal como se definió en la sección 2.8. Cuando en Congruencias se "opera con clases" (se suma, se multiplica, se despeja $x$ en $ax\equiv b$), en el fondo se está trabajando dentro del conjunto cociente $A/R$, aprovechando que el Teorema de buena definición (sección 3.2) garantiza que no importa qué representante de la clase se use para hacer la cuenta: el resultado (la clase resultante) es siempre el mismo.

**Con [[05-Relaciones-de-Recurrencia]].** Acá el vínculo es más débil y conviene ser honesto al respecto: no hay una relación matemática directa entre relaciones de equivalencia y relaciones de recurrencia, son temas estructuralmente distintos. Sin embargo, hay una analogía conceptual útil para memorizar: el concepto de **partición** (descomponer un conjunto en piezas disjuntas que, combinadas, reconstruyen el todo) reaparece de forma análoga cuando en Recurrencias se escribe la solución general de una recurrencia lineal no homogénea como:

$$a_n = a_n^{(h)} + a_n^{(p)}$$

es decir, solución homogénea más solución particular. No es una partición en sentido conjuntista estricto (no estamos particionando un conjunto de elementos en bloques disjuntos), pero la *estructura de pensamiento* es la misma: se separa un problema en "piezas" que, combinadas de manera específica, reconstruyen el objeto completo. Vale la pena tenerlo presente como recurso mnemotécnico, no como un teorema formal compartido entre ambas unidades.

## 7. Errores comunes y trampas del examen

1. **Confundir "arbitrario" con "un caso particular".** Al probar reflexividad, muchos alumnos prueban $xRx$ para un valor específico (por ejemplo $x=5$) en vez de dejar $x$ genérico y usar solo su pertenencia a $A$. Un solo caso particular nunca prueba un cuantificador universal.

2. **Confundir una clase de equivalencia con un elemento.** $\bar{x}$ es un **conjunto** (subconjunto de $A$), no un elemento de $A$. Escribir cosas como "$\bar{1} = 4$" en vez de "$\bar 1 = \{1,4\}$" es un error de tipo, no solo de notación.

3. **No verificar que las clases halladas cubran TODO el conjunto.** Es común calcular un par de clases, ver que dan una partición "razonable" y no chequear explícitamente que todo elemento de $A$ quedó clasificado en alguna. El método práctico de la sección 2 exige repetir el paso hasta agotar $A$ explícitamente.

4. **Error de signo en la demostración de simetría.** Al despejar de $x-y=nk$ hacia $y-x=n(-k)$, es un clásico invertir mal el signo (escribir $y-x=nk$ en vez de $n(-k)$), lo cual rompe la prueba aunque la idea general esté bien encaminada.

5. **Confundir $R$ con $R^{-1}$ (la relación inversa).** $R^{-1} = \{(y,x) : (x,y)\in R\}$. Cuando $R$ es simétrica, $R = R^{-1}$, pero en general no lo son, y usar $R^{-1}$ donde corresponde $R$ (o viceversa) al plantear una demostración lleva a probar la propiedad equivocada.

6. **Creer que toda relación reflexiva y transitiva ya es de equivalencia.** Falta la simetría: una relación de orden parcial (reflexiva + antisimétrica + transitiva) cumple dos de las tres propiedades pero no es de equivalencia salvo en el caso trivial (ver sección 6).

7. **Verificar transitividad "a ojo" en vez de sistemáticamente.** En relaciones dadas por extensión (como conjuntos de pares) conviene armar la matriz y calcular $M^2$ explícitamente en vez de intentar verificar caso por caso "a mano", donde es fácil saltearse una terna $(x,y,z)$.

8. **Pensar que $A/R$ y $R$ son el mismo objeto.** $R \subseteq A\times A$ es una relación (conjunto de pares); $A/R$ es un conjunto de subconjuntos de $A$ (el cociente). Son objetos de "tipo" distinto, aunque uno se construye a partir del otro.

## 8. Preguntas de autoevaluación

1. Enunciá con cuantificadores las tres propiedades (reflexiva, simétrica, transitiva) y explicá con tus palabras por qué simetría y transitividad son implicaciones condicionales y no afirmaciones universales sin hipótesis.
2. ¿Por qué la reflexividad no puede probarse "por partes" (para algunos elementos sí y para otros ya se ve)? Justificá usando la definición formal.
3. Demostrá que la relación en $\mathbb{Z}$ dada por $xRy \iff x^2=y^2$ es de equivalencia, y hallá $\bar 3$ y $\bar 0$.
4. Dado $A=\{a,b,c,d\}$ y la partición $\{\{a,b\},\{c\},\{d\}\}$, escribí explícitamente la relación de equivalencia $R\subseteq A\times A$ que la genera (como conjunto de pares) y su matriz asociada.
5. Explicá con tus palabras por qué $M^2 \le M$ (y no $M^2 = M$) es la condición correcta para transitividad. ¿En qué caso especial se da la igualdad $M^2=M$?
6. Si $R$ es de equivalencia en $A$ con $|A|=10$ y $A/R$ tiene exactamente 3 clases, ¿qué podés afirmar (o no) sobre los tamaños de esas clases?
7. Probá el corolario: si $\bar x \cap \bar y \neq \emptyset$ entonces $\bar x = \bar y$, sin repetir literalmente la demostración de la sección 3.2 (intentá una demostración directa, no por contrarrecíproco).
8. ¿Puede una relación ser simétrica y antisimétrica a la vez sin ser la igualdad pura? Fundamentá usando la definición de ambas propiedades.
9. Dada la relación en $\mathbb{R}^2$ (pares del plano) $((x_1,y_1)) R ((x_2,y_2)) \iff x_1+y_1 = x_2+y_2$, probá que es de equivalencia y describí geométricamente sus clases de equivalencia.
10. ¿Por qué decimos que $\mathbb{Z}_n$ "es" el conjunto cociente $\mathbb{Z}/\equiv_n$ y no simplemente "se parece" a él? Relacioná tu respuesta con el Teorema de buena definición de la sección 3.2.

## 9. Referencias

- Teoría original: `../02_relaciones_equivalencia/readme.md`
- Ejercicios resueltos: `../ejercicios-resueltos/tema2_equivalencia.md`

---
Volver al índice: [[00-Indice-Matematica-Discreta]]
