---
tags: [matematica-discreta, tema-3, ordenes, retículos, algebra-de-boole, unsam]
aliases: ["Redes y Álgebras de Boole", "Retículos", "Tema 3"]
---

# Redes y Álgebras de Boole

> [!info] Ubicación en la materia
> Esta unidad formaliza la noción de "orden" entre elementos de un conjunto y culmina en las álgebras de Boole, que son la estructura algebraica que sostiene la lógica proposicional de [[01-Razonamientos-Categoricos]]. Además, el ejemplo estrella $(D_n; |)$ conecta directamente con la divisibilidad y la factorización prima que se explota en [[04-Congruencias-Euler-Fermat]].

## 1. Introducción y motivación

Hasta ahora, en la materia, trabajamos con relaciones que "igualaban" o "agrupaban" elementos: las relaciones de equivalencia (ver [[02-Relaciones-de-Equivalencia]]) parten un conjunto en clases donde todos los elementos de una clase son, en algún sentido, "lo mismo". Ahora cambiamos el objetivo: en vez de agrupar, queremos **comparar y jerarquizar**. Eso es exactamente lo que hace una relación de orden.

La idea intuitiva es simple y aparece todo el tiempo en la vida cotidiana y en la matemática:

- "$a$ divide a $b$" ordena los números naturales según divisibilidad.
- "$A$ está contenido en $B$" ordena los subconjuntos de un conjunto.
- "$a$ es menor o igual que $b$" ordena los números reales.

Lo que tienen en común estas tres relaciones es que son reflexivas, antisimétricas y transitivas. Esa terna de propiedades es la definición de **orden parcial**, y el conjunto con esa relación se llama **conjunto parcialmente ordenado** (poset, del inglés *partially ordered set*).

Ahora bien, en un orden parcial no siempre se pueden comparar dos elementos cualesquiera (por eso "parcial": pensá en $2$ y $3$ con la divisibilidad, ninguno divide al otro). Cuando el conjunto ordenado tiene la propiedad extra de que **cualquier par de elementos tiene supremo e ínfimo**, la estructura se vuelve mucho más rica y se llama **red** o **retículo** (*lattice*). Las redes son el escalón intermedio hacia el objetivo final de la unidad: el **álgebra de Boole**, que es la estructura que subyace a la lógica proposicional, los circuitos digitales, la teoría de conjuntos y —como vamos a ver en el ejemplo transversal $(D_n;|)$— a la aritmética de la divisibilidad.

El recorrido de la unidad es, en definitiva:

$$\text{Orden parcial} \;\longrightarrow\; \text{Red (ordenada o algebraica)} \;\longrightarrow\; \text{Red distributiva} \;\longrightarrow\; \text{Red complementada} \;\longrightarrow\; \text{Álgebra de Boole}$$

Cada flecha agrega una propiedad más, y el álgebra de Boole es la intersección de "distributiva" y "complementada". Entender bien esta cadena de definiciones —y sobre todo saber **verificarlas en ejemplos concretos** como $(D_n;|)$ y $(\mathcal{P}(A);\subseteq)$— es la clave para este tema en el final.

## 2. Definiciones formales

### 2.1 Relación de orden parcial

Sea $A$ un conjunto y $R \subseteq A \times A$ una relación binaria. Decimos que $R$ es una **relación de orden parcial** (o simplemente de orden) si cumple simultáneamente:

- **Reflexiva:** $\forall x \in A: x R x$.
- **Antisimétrica:** $\forall x, y \in A: (xRy \land yRx) \Rightarrow x = y$.
- **Transitiva:** $\forall x,y,z \in A: (xRy \land yRz) \Rightarrow xRz$.

Cuando $R$ es de orden, se anota habitualmente $x \preceq y$ en lugar de $xRy$, y al par $(A; \preceq)$ se lo llama **conjunto parcialmente ordenado** o **poset**.

> [!note] "Parcial" no es un defecto
> Se llama *parcial* porque no se exige que todo par de elementos sea comparable. Si además se cumple que $\forall x,y \in A: x\preceq y \lor y \preceq x$ (es decir, **todo** par es comparable), el orden se llama **orden total** (o cadena). $(\mathbb{N};\leq)$ es un orden total; $(D_{30};|)$, en cambio, es solo parcial: $2$ y $3$ no son comparables entre sí.

### 2.2 Diagrama de Hasse

El **diagrama de Hasse** es la representación gráfica estándar de un poset finito. Se construye así:

1. Los elementos se dibujan como puntos, ubicando **abajo** a los "menores" y **arriba** a los "mayores" (según $\preceq$).
2. Se traza una línea entre $x$ e $y$ (con $x$ abajo, $y$ arriba) únicamente si $x$ es **cubierto** por $y$, es decir, $x \prec y$ (estrictamente) y no existe ningún $z$ con $x \prec z \prec y$. A esto se le llama **relación de cobertura**.
3. **No se dibujan lazos** (la reflexividad $xRx$ se da por sabida en todo poset, no aporta información visual).
4. **No se dibujan flechas ni relaciones que se deduzcan por transitividad.** Si $x \preceq y$ y $y \preceq z$, ya sabemos por transitividad que $x \preceq z$; dibujar esa tercera línea sería redundante, porque el diagrama la reconstruye subiendo por las líneas ya trazadas.
5. **No se dibujan puntas de flecha**, porque la dirección siempre es "de abajo hacia arriba" por convención.

La justificación formal de por qué esta simplificación es **válida** (es decir, por qué no se pierde información) es que reflexividad y transitividad son propiedades *derivables*: conociendo únicamente las relaciones de cobertura, la reflexividad se repone trivialmente ($x \preceq x$ siempre) y el resto de las relaciones $x \preceq y$ (con $x\neq y$, no cubertura directa) se reconstruyen siguiendo una cadena ascendente de segmentos del diagrama. En otras palabras, el diagrama de Hasse codifica exactamente la **cobertura**, y el orden completo es la clausura reflexivo-transitiva de esa cobertura.

### 2.3 Elementos notables de un poset

Sea $(A;\preceq)$ un poset y $S \subseteq A$ (podemos tomar $S = A$ como caso particular).

- **Mínimo de $A$** (se anota $0_A$): un elemento $0_A \in A$ tal que $\forall x \in A: 0_A \preceq x$. Es decir, es **menor o igual que todos**, y debe ser comparable con cada elemento.
- **Máximo de $A$** (se anota $1_A$): un elemento $1_A \in A$ tal que $\forall x \in A: x \preceq 1_A$.
- **Elemento minimal:** $m \in A$ es minimal si **no existe** $x \in A$ con $x \prec m$ (es decir, nadie es estrictamente menor que él). Puede haber varios minimales, y no necesita ser comparable con todos los elementos.
- **Elemento maximal:** $M \in A$ es maximal si **no existe** $x \in A$ con $M \prec x$.
- **Cota superior de $S$:** $c \in A$ (no necesariamente en $S$) tal que $\forall s \in S: s \preceq c$.
- **Cota inferior de $S$:** $c \in A$ tal que $\forall s \in S: c \preceq s$.
- **Supremo de $S$** ($\sup S$): la **menor** de las cotas superiores de $S$, es decir, una cota superior $c$ tal que para toda otra cota superior $c'$ de $S$ se cumple $c \preceq c'$.
- **Ínfimo de $S$** ($\inf S$): la **mayor** de las cotas inferiores de $S$.

> [!important] Relaciones clave entre estos conceptos
> - Si existe el **mínimo**, es **único**, y además es el **único elemento minimal** del conjunto (recíprocamente, si hay un único minimal esto NO garantiza que sea mínimo, salvo casos particulares — ver la sección de errores comunes). Análogamente para máximo y maximal.
> - Si $\sup S \in S$, entonces $\sup S$ es directamente el **máximo** de $S$.
> - Si $\inf S \in S$, entonces $\inf S$ es directamente el **mínimo** de $S$.
>
> Estas relaciones no son "trucos" sueltos: se demuestran formalmente en la sección 3.

### 2.4 Red (retículo) — definición ordenada

$(A;\preceq)$ es una **red** (o retículo, *lattice*) si es un poset en el que **para todo par de elementos** $a,b \in A$ existen $\sup\{a,b\}$ e $\inf\{a,b\}$ dentro de $A$.

Notación estándar:
$$a \lor b := \sup\{a,b\} \qquad a \land b := \inf\{a,b\}$$

Se lee $a \lor b$ como "$a$ join $b$" o "$a$ unión $b$" (sup) y $a \land b$ como "$a$ meet $b$" o "$a$ intersección $b$" (inf).

> [!tip] Cómo verificar en la práctica si algo es red
> Alcanza con revisar los **pares incomparables** (los pares comparables automáticamente tienen sup e inf: si $a \preceq b$, entonces $a \lor b = b$ y $a \land b = a$, como se demuestra en la sección 3). Además:
> - Si el poset tiene **más de un elemento maximal** o **más de un elemento minimal**, **no puede ser red** (porque dos maximales distintos no tienen cota superior común dentro del conjunto, así que no puede existir supremo).
> - Tener único maximal y único minimal es **necesario pero no suficiente**: hace falta además que cada par incomparable tenga sup e inf bien definidos (únicos).

### 2.5 Red algebraica — definición equivalente

Una estructura $(A; \ast; \ast')$ con dos operaciones binarias cerradas se llama **red algebraica** si $\ast$ y $\ast'$ cumplen:

- **Cerradas:** $a \ast b \in A$ y $a \ast' b \in A$ para todo $a,b \in A$.
- **Asociativas:** $(a\ast b)\ast c = a \ast (b \ast c)$ (ídem para $\ast'$).
- **Conmutativas:** $a \ast b = b \ast a$ (ídem para $\ast'$).
- **Idempotentes:** $a \ast a = a$ (ídem para $\ast'$).
- **Absorción mutua:** $a \ast (a \ast' b) = a$ y $a \ast' (a \ast b) = a$.

El **teorema de equivalencia** (que enunciamos y usamos, con la idea de la demostración en la sección 3) dice que **toda red ordenada es una red algebraica y viceversa**:

- De ordenada a algebraica: se toma $\ast = \lor$ (sup) y $\ast' = \land$ (inf); las cinco propiedades se heredan de las propiedades de sup/inf.
- De algebraica a ordenada: se define $a \preceq b \iff a \land b = a$ (equivalentemente $a \lor b = b$), y se prueba que este $\preceq$ es efectivamente un orden parcial donde $\land$ e $\lor$ coinciden con ínfimo y supremo.

Esto es clave porque permite **atacar un mismo objeto desde dos ángulos**: a veces conviene pensar en términos de diagrama de Hasse y comparaciones, y otras veces conviene operar algebraicamente con $\lor$ y $\land$ como si fueran una suma y un producto.

### 2.6 Complemento

Sea $(A;\preceq)$ una red que posee mínimo $0_A$ y máximo $1_A$. Un **complemento** de $a \in A$ es un elemento $\bar a \in A$ tal que:

$$a \land \bar a = 0_A \qquad \text{y} \qquad a \lor \bar a = 1_A$$

Importante: un elemento puede tener **cero, uno o varios** complementos, según la red. La existencia y unicidad del complemento es uno de los ejes centrales del tema (ver Teorema 3.3).

### 2.7 Red complementada

$(A;\preceq)$ es una **red complementada** si tiene $0_A$ y $1_A$, y **todo** elemento de $A$ tiene **al menos un** complemento (no necesariamente único).

### 2.8 Red distributiva

$(A;\preceq)$ es una **red distributiva** si $\forall a,b,c \in A$ se cumplen **ambas** leyes distributivas:

$$a \lor (b \land c) = (a \lor b) \land (a \lor c)$$
$$a \land (b \lor c) = (a \land b) \lor (a \land c)$$

(En una red cualquiera vale siempre una desigualdad, pero la igualdad exacta es la propiedad extra que caracteriza a las distributivas.)

**Criterio visual (para redes finitas):** una red finita es distributiva si y solo si **no contiene** una subred isomorfa al **pentágono** $N_5$ ni al **diamante de 3 átomos** $M_3$. $N_5$ es la red de 5 elementos con una cadena lateral de longitud 2 y otra de longitud 1 entre el mismo mínimo y máximo; $M_3$ es la red con mínimo, máximo y exactamente 3 elementos intermedios mutuamente incomparables.

### 2.9 Álgebra de Boole — dos definiciones equivalentes

**Definición como red:** un **álgebra de Boole** es una red que es simultáneamente **distributiva** y **complementada** (y por lo tanto tiene $0$ y $1$).

**Definición como estructura algebraica:** $(B; \lor; \land)$ es un álgebra de Boole si:

- $\lor$ y $\land$ son cerradas y conmutativas.
- $\lor$ y $\land$ son **distributivas entre sí** (ambas leyes de 2.8).
- Existen neutros $0_B$ (neutro de $\lor$: $a \lor 0_B = a$) y $1_B$ (neutro de $\land$: $a \land 1_B = a$).
- Todo elemento $a$ tiene un complemento $\bar a$ tal que $a \lor \bar a = 1_B$ y $a \land \bar a = 0_B$.

**¿Por qué son equivalentes?** Porque toda red (ordenada) es a la vez una red algebraica (sección 2.5): el orden $\preceq$ se recupera de $\lor,\land$ y viceversa. Pedir "distributiva + complementada" en el lenguaje de orden es exactamente pedir las leyes distributivas y la existencia de complementos en el lenguaje algebraico. Ambas caras describen el mismo objeto matemático; en los ejercicios se suele usar la que más convenga: la de orden para dibujar Hasse y razonar visualmente, la algebraica para hacer cuentas con $\lor,\land,\bar{\,\cdot\,}$.

Casos canónicos de álgebra de Boole:

- $(\{0,1\}; +; \cdot)$, el álgebra de Boole de la lógica proposicional (la más chica posible, con 2 elementos).
- $(\mathcal{P}(A); \subseteq)$ para cualquier conjunto finito $A$, con $\lor=\cup$, $\land=\cap$, complemento $\bar X = A - X$.
- $(D_n; |)$ cuando $n$ es **libre de cuadrados** (producto de primos distintos).

## 3. Teoremas y demostraciones

### Teorema 3.1 — Si $a \preceq b$, entonces $a \lor b = b$ y $a \land b = a$

**Enunciado.** Sea $(A;\preceq)$ una red y $a,b \in A$ con $a \preceq b$. Entonces $\sup\{a,b\} = b$ e $\inf\{a,b\} = a$.

**Demostración.**

*Parte 1: $a \lor b = b$.* Queremos ver que $b$ es la menor cota superior de $\{a,b\}$.

- $b$ es cota superior de $\{a,b\}$: en efecto, $a \preceq b$ (hipótesis) y $b \preceq b$ (reflexividad). Luego $b$ cumple $a\preceq b$ y $b \preceq b$, es decir, es cota superior del conjunto $\{a,b\}$.
- $b$ es la **menor** cota superior: sea $c$ cualquier otra cota superior de $\{a,b\}$. Por definición de cota superior, $a \preceq c$ y $b \preceq c$. En particular ya tenemos $b \preceq c$, que es exactamente lo que necesitamos para decir que $b$ es menor o igual que cualquier otra cota superior $c$.

Como $b$ es cota superior y es menor o igual que cualquier otra cota superior, $b = \sup\{a,b\} = a \lor b$. $\blacksquare$

*Parte 2: $a \land b = a$.* Análogamente:

- $a$ es cota inferior de $\{a,b\}$: $a \preceq a$ (reflexividad) y $a \preceq b$ (hipótesis).
- $a$ es la **mayor** cota inferior: sea $c$ cualquier otra cota inferior de $\{a,b\}$; entonces $c \preceq a$ y $c \preceq b$. En particular $c \preceq a$, que es lo que se necesita para que $a$ sea mayor o igual que cualquier otra cota inferior.

Luego $a = \inf\{a,b\} = a \land b$. $\blacksquare$

### Teorema 3.2 — Equivalencia $a \preceq b \iff a \lor b = b \iff a \land b = a$

**Demostración.**

**($a\preceq b \Rightarrow a \lor b = b$ y $a \land b = a$):** es exactamente el Teorema 3.1.

**($a \lor b = b \Rightarrow a \preceq b$):** Por definición, $a \lor b = \sup\{a,b\}$ es en particular una **cota superior** de $\{a,b\}$, así que $a \preceq \sup\{a,b\}$. Si $a \lor b = b$, sustituyendo obtenemos $a \preceq b$. $\blacksquare$

**($a \land b = a \Rightarrow a \preceq b$):** Por definición, $a\land b = \inf\{a,b\}$ es cota inferior de $\{a,b\}$, así que $\inf\{a,b\} \preceq b$. Si $a \land b = a$, sustituyendo, $a \preceq b$. $\blacksquare$

**($a \lor b = b \Rightarrow a \land b = a$, y recíproco):** se sigue de que ambas son equivalentes a $a\preceq b$ (transitividad de "$\iff$": ambas afirmaciones equivalen a la misma tercera).

Esta triple equivalencia es extremadamente útil en la práctica: para decidir si $a \preceq b$ en una red dada algebraicamente (por tablas de $\lor,\land$, sin diagrama), alcanza con calcular $a \lor b$ o $a \land b$ y compararlo con $a$ o $b$.

### Teorema 3.3 — En una red distributiva, el complemento (si existe) es único

Este es **el teorema más importante de la unidad**: es el que garantiza que en un álgebra de Boole hablar de "el" complemento (con artículo determinado) tiene sentido, y es también el criterio negativo más usado para descartar que una red sea distributiva.

**Enunciado.** Sea $(A;\preceq)$ una red **distributiva** con mínimo $0_A$ y máximo $1_A$. Si $a \in A$ tiene complemento, este es único.

**Demostración.** Supongamos que $b$ y $c$ son **ambos** complementos de $a$. Por definición de complemento:

$$a \land b = 0_A, \qquad a \lor b = 1_A, \qquad a \land c = 0_A, \qquad a \lor c = 1_A$$

Queremos probar que $b = c$. Trabajamos a partir de $b$ y usamos las hipótesis anteriores y la distributividad:

$$b = b \land 1_A \quad \text{(}1_A\text{ es neutro/máximo: } b \land 1_A = b\text{)}$$

Sustituimos $1_A = a \lor c$ (complemento de $a$ es $c$):

$$b = b \land (a \lor c)$$

Aplicamos la ley distributiva de $\land$ sobre $\lor$:

$$b = (b \land a) \lor (b \land c)$$

Usamos que $b \land a = a \land b = 0_A$ (complemento de $a$ es $b$, y $\land$ es conmutativa):

$$b = 0_A \lor (b \land c)$$

Como $0_A$ es el mínimo, es neutro para $\lor$ ($0_A \lor x = x$ para todo $x$), así que:

$$b = b \land c$$

Por simetría del argumento (repitiendo exactamente los mismos pasos intercambiando los roles de $b$ y $c$), se obtiene también:

$$c = c \land 1_A = c \land (a \lor b) = (c\land a) \lor (c \land b) = 0_A \lor (c \land b) = c \land b$$

Como $\land$ es conmutativa, $b \land c = c \land b$. Juntando ambas cadenas de igualdades:

$$b = b \land c = c \land b = c$$

Por lo tanto $b = c$, es decir, el complemento es único. $\blacksquare$

> [!important] Consecuencia práctica (contrarrecíproco)
> Si en una red encontramos un elemento con **dos o más complementos distintos**, entonces la red **no puede ser distributiva** (y por lo tanto tampoco álgebra de Boole). Este es el método más rápido para descartar álgebras de Boole en un ejercicio: no hace falta revisar las leyes distributivas en general, alcanza con exhibir un elemento con complemento no único.

### Teorema 3.4 — Ley de De Morgan en álgebra de Boole: $(a\lor b)\overline{\phantom{a}} = \bar a \land \bar b$

**Enunciado.** Sea $B$ un álgebra de Boole y $a,b \in B$. Entonces $\bar a \land \bar b$ es el complemento de $a \lor b$, es decir:

$$\overline{(a \lor b)} = \bar a \land \bar b$$

**Demostración.** Por el Teorema 3.3 sabemos que el complemento en un álgebra de Boole (que es distributiva) es único. Entonces, para probar que $\overline{(a\lor b)} = \bar a \land \bar b$, alcanza con verificar que $\bar a \land \bar b$ **satisface la definición de complemento** de $a \lor b$, es decir, hay que probar las dos igualdades:

$$(a\lor b) \lor (\bar a \land \bar b) = 1_B \qquad \text{y} \qquad (a \lor b)\land (\bar a \land \bar b) = 0_B$$

**Primera igualdad — el "or":**

$$(a \lor b) \lor (\bar a \land \bar b) \overset{\text{distrib.}}{=} \big[(a\lor b) \lor \bar a\big] \land \big[(a \lor b) \lor \bar b\big]$$

(aplicamos $x \lor (y\land z) = (x\lor y)\land(x \lor z)$ con $x = a\lor b$, $y = \bar a$, $z = \bar b$).

Analicemos el primer factor: $(a \lor b)\lor \bar a = (a \lor \bar a) \lor b$ (asociando y conmutando) $= 1_B \lor b = 1_B$ (porque $a \lor \bar a = 1_B$ por definición de complemento, y $1_B$ es absorbente para $\lor$: $1_B \lor b = 1_B$, ya que $1_B$ es el máximo).

Análogamente, el segundo factor: $(a\lor b) \lor \bar b = a \lor (b \lor \bar b) = a \lor 1_B = 1_B$.

Entonces:
$$(a\lor b) \lor (\bar a \land \bar b) = 1_B \land 1_B = 1_B$$
(usando idempotencia de $\land$, o directamente que $1_B$ es neutro de $\land$).

**Segunda igualdad — el "and":**

$$(a\lor b) \land (\bar a \land \bar b) \overset{\text{distrib.}}{=} \big[a \land (\bar a \land \bar b)\big] \lor \big[b \land (\bar a \land \bar b)\big]$$

(aplicamos $(x \lor y) \land z = (x\land z)\lor(y\land z)$ con $x=a$, $y=b$, $z = \bar a \land \bar b$).

En el primer término: $a \land (\bar a \land \bar b) = (a \land \bar a) \land \bar b = 0_B \land \bar b = 0_B$ (porque $a\land \bar a = 0_B$, y $0_B$ es absorbente para $\land$: $0_B \land x = 0_B$, ya que $0_B$ es el mínimo).

En el segundo término: $b \land (\bar a \land \bar b) = (\bar a) \land (b \land \bar b) = \bar a \land 0_B = 0_B$.

Entonces:
$$(a\lor b)\land(\bar a \land \bar b) = 0_B \lor 0_B = 0_B$$

Como $\bar a \land \bar b$ cumple simultáneamente $(a\lor b)\lor(\bar a\land \bar b) = 1_B$ y $(a\lor b)\land(\bar a \land \bar b) = 0_B$, por definición es un complemento de $a \lor b$; y por unicidad del complemento (Teorema 3.3, aplicable porque toda álgebra de Boole es distributiva), es **el** complemento:

$$\overline{(a\lor b)} = \bar a \land \bar b \qquad \blacksquare$$

La segunda ley de De Morgan, $\overline{(a\land b)} = \bar a \lor \bar b$, se obtiene por el **principio de dualidad** (intercambiando $\lor \leftrightarrow \land$ y $0_B \leftrightarrow 1_B$ en toda la demostración anterior), o repitiendo el mismo argumento simétricamente.

### Teorema 3.5 — En $(D_n;|)$: $\sup\{a,b\} = \text{mcm}(a,b)$ e $\inf\{a,b\} = \text{mcd}(a,b)$

**Enunciado.** Sea $D_n$ el conjunto de divisores positivos de $n$, ordenado por divisibilidad ($a \preceq b \iff a \mid b$). Para $a,b \in D_n$:

$$\sup\{a,b\} = \text{mcm}(a,b) \qquad \inf\{a,b\} = \text{mcd}(a,b)$$

**Demostración (idea, argumentando por qué mcm/mcd cumplen exactamente la definición).**

*Para el supremo:* Sea $m = \text{mcm}(a,b)$. Por definición de mínimo común múltiplo, $a \mid m$ y $b \mid m$, así que $m$ es cota superior de $\{a,b\}$ en $(D_n;|)$ (siempre que $m \mid n$, lo cual está garantizado porque $a,b$ son divisores de $n$ y cualquier múltiplo común de $a$ y $b$ que además divida a $n$... en particular $n$ mismo es múltiplo común de $a$ y $b$, así que $m \mid n$). Ahora, si $c$ es **cualquier otra** cota superior común de $a$ y $b$ en $D_n$ (es decir $a\mid c$, $b \mid c$), entonces por la propiedad aritmética fundamental del mcm (el mcm divide a cualquier múltiplo común), se tiene $m \mid c$. Eso es exactamente decir que $m \preceq c$ para toda cota superior $c$, es decir, $m$ es la **menor** cota superior: $m = \sup\{a,b\}$.

*Para el ínfimo:* Sea $d = \text{mcd}(a,b)$. Por definición, $d \mid a$ y $d\mid b$, así que $d$ es cota inferior de $\{a,b\}$. Si $c$ es cualquier otra cota inferior común ($c \mid a$, $c\mid b$), por la propiedad fundamental del mcd (cualquier divisor común de $a$ y $b$ divide al mcd), se tiene $c \mid d$, es decir $c \preceq d$. Luego $d$ es la **mayor** cota inferior: $d = \inf\{a,b\}$. $\blacksquare$

Como el mcd y el mcm de dos divisores de $n$ **siempre existen** (son enteros positivos bien definidos) y además siempre dividen a $n$, se concluye que **$(D_n;|)$ es siempre una red**, para cualquier $n$. También se puede probar (no lo desarrollamos en detalle acá porque excede el nivel del final, pero es bueno saberlo) que $(D_n;|)$ es siempre **distributiva**, porque mcd y mcm satisfacen las leyes distributivas de la aritmética elemental.

### Teorema 3.6 — $(D_n;|)$ es álgebra de Boole $\iff$ $n$ es libre de cuadrados

**Enunciado.** $(D_n;|)$ es álgebra de Boole si y solo si $n = p_1 \cdot p_2 \cdots p_k$ con $p_i$ primos **distintos** (ningún factor primo repetido, "libre de cuadrados").

**Demostración (argumentativa).**

Como ya sabemos por el Teorema 3.5 que $(D_n;|)$ **siempre** es red y **siempre** es distributiva, lo único que falta para que sea álgebra de Boole es que sea **complementada**, es decir, que **todo divisor $d$ de $n$ tenga complemento**.

El candidato natural a complemento de $d$ es $\bar d = n/d$, porque intuitivamente "lo que le falta a $d$ para completar $n$". Verifiquemos si cumple la definición de complemento: necesitamos $\text{mcd}(d, n/d) = 1$ (el mínimo de $D_n$) y $\text{mcm}(d,n/d) = n$ (el máximo de $D_n$).

Escribamos la factorización prima de $n$: $n = p_1^{e_1} p_2^{e_2}\cdots p_k^{e_k}$, y la de un divisor genérico $d = p_1^{f_1}\cdots p_k^{f_k}$ con $0 \leq f_i \leq e_i$. Entonces $n/d = p_1^{e_1-f_1}\cdots p_k^{e_k-f_k}$.

- $\text{mcd}(d, n/d) = \prod_i p_i^{\min(f_i,\, e_i-f_i)}$.
- $\text{mcm}(d, n/d) = \prod_i p_i^{\max(f_i,\, e_i - f_i)}$.

**Caso $n$ libre de cuadrados** (todo $e_i = 1$): para cada primo, $f_i \in \{0,1\}$. Si $f_i = 0$, entonces $\min(0, 1-0)=\min(0,1)=0$ y $\max(0,1)=1$. Si $f_i=1$, $\min(1,0)=0$ y $\max(1,0)=1$. En **ambos casos**, $\min(f_i, e_i-f_i)=0$ y $\max(f_i,e_i-f_i)=1=e_i$. Por lo tanto $\text{mcd}(d,n/d)=\prod p_i^0 = 1$ y $\text{mcm}(d,n/d)=\prod p_i^{e_i}=n$. Es decir, **para todo divisor $d$**, $n/d$ es efectivamente su complemento. Como esto vale para todo $d \in D_n$, $(D_n;|)$ es complementada, y siendo también red y distributiva, **es álgebra de Boole**.

**Caso $n$ NO libre de cuadrados** (existe algún $e_i \geq 2$): tomemos ese primo $p_i$ con exponente $e_i \geq 2$ y elijamos $d$ tal que $0 < f_i < e_i$ (por ejemplo $f_i = 1$, posible porque $e_i\geq 2$). Entonces $e_i - f_i \geq 1$ también, así que $\min(f_i, e_i-f_i) \geq 1$, lo que hace que $p_i$ divida a $\text{mcd}(d,n/d)$, es decir $\text{mcd}(d,n/d) \neq 1$. Luego $d$ y $n/d$ **no** cumplen la condición de complemento (el mcd debería ser $1$ y no lo es). Esto muestra que el candidato natural $n/d$ falla; de hecho se puede probar que **ningún** otro elemento de $D_n$ funciona como complemento de ese $d$ (queda sin complemento), así que $(D_n;|)$ **no es complementada**, y por lo tanto **no es álgebra de Boole**.

**Ejemplo concreto de la falla:** en $D_{12}$, con $12 = 2^2\cdot 3$, tomemos $d=2$ (o $d=6$). Se ve directamente en el ejemplo resuelto de la sección 5(b) que $2$ no tiene complemento válido.

Esto cierra la equivalencia: $(D_n;|)$ es álgebra de Boole $\iff$ $n$ libre de cuadrados. $\blacksquare$

## 4. Fórmulas clave (tabla de repaso rápido)

| Concepto | Definición / criterio |
|---|---|
| Orden parcial | Reflexiva + antisimétrica + transitiva |
| Orden total | Orden parcial + todo par es comparable |
| Mínimo $0_A$ | $\forall x: 0_A \preceq x$ (único si existe; único minimal) |
| Máximo $1_A$ | $\forall x: x \preceq 1_A$ (único si existe; único maximal) |
| Minimal | Nadie es estrictamente menor que él (puede haber varios) |
| Maximal | Nadie es estrictamente mayor que él (puede haber varios) |
| Supremo de $S$ | Menor cota superior; si $\sup S \in S \Rightarrow$ es máximo de $S$ |
| Ínfimo de $S$ | Mayor cota inferior; si $\inf S \in S \Rightarrow$ es mínimo de $S$ |
| Red (orden) | $\forall a,b$ existen $\sup\{a,b\}$ e $\inf\{a,b\}$; alcanza revisar incomparables |
| $a \preceq b$ equivale a | $a \lor b = b \iff a \land b = a$ |
| Propiedades de $\lor,\land$ | Cerrada, asociativa, conmutativa, idempotente, absorción: $x\lor(x\land y)=x$, $x\land(x\lor y)=x$ |
| Red algebraica | $(A;\ast;\ast')$ con esas 5 propiedades $\iff$ red ordenada |
| Complemento de $a$ | $\bar a$ tal que $a\land \bar a = 0_A$ y $a \lor \bar a = 1_A$ (0, 1 o varios) |
| Red complementada | Existen $0_A,1_A$ y todo elemento tiene $\geq 1$ complemento |
| Red distributiva | $a\lor(b\land c)=(a\lor b)\land(a\lor c)$ y dual; sin subred $N_5$ ni $M_3$ |
| Complemento único | Garantizado si la red es **distributiva** (Teorema 3.3) |
| Álgebra de Boole | Red distributiva **y** complementada |
| $(D_n;\vert)$ | $\sup=\text{mcm}$, $\inf=\text{mcd}$; siempre red y distributiva; es Boole $\iff n$ libre de cuadrados |
| $(\mathcal{P}(A);\subseteq)$ | $\sup=\cup$, $\inf=\cap$, $\bar X = A-X$; **siempre** álgebra de Boole |
| $(\mathbb{N};\leq)$ | $\sup=\max$, $\inf=\min$ (es red, orden total, no acotada superiormente en general) |
| Cardinal de álgebra de Boole finita | Siempre potencia de $2$: $2^n$ |
| Isomorfismo | Toda álgebra de Boole finita de $2^n$ elementos $\cong (\mathcal{P}(\{a_1,\dots,a_n\});\subseteq)$ |
| De Morgan | $\overline{a\lor b}=\bar a\land\bar b$, $\ \overline{a\land b}=\bar a\lor\bar b$ |
| Dualidad | Se intercambia $\lor\leftrightarrow\land$ y $0\leftrightarrow 1$ en cualquier teorema válido |
| Involución | $\overline{\bar a}=a$ |
| Neutros complementados | $\overline{1_B}=0_B$, $\ \overline{0_B}=1_B$ |

## 5. Ejemplos resueltos paso a paso

### (a) Análisis completo de $(D_{30};\,|\,)$

**Paso 1 — Divisores de 30.** $30 = 2\cdot 3\cdot 5$. Sus divisores son: $D_{30}=\{1,2,3,5,6,10,15,30\}$ (8 elementos, porque $30$ tiene $3$ primos distintos, cada uno con exponente $1$: $2^3=8$ divisores).

**Paso 2 — Diagrama de Hasse.** Las relaciones de cobertura son las multiplicaciones por un primo:
- $1 \to 2, 1\to 3, 1\to 5$ (nivel de los primos)
- $2\to 6, 2\to 10, 3\to 6, 3\to 15, 5\to 10, 5\to 15$ (nivel de productos de dos primos)
- $6\to 30, 10\to 30, 15\to 30$ (nivel del producto de los tres)

El diagrama tiene forma de **cubo** (es literalmente el cubo booleano de 3 dimensiones): un mínimo $1$, tres átomos $\{2,3,5\}$, tres coátomos $\{6,10,15\}$ y un máximo $30$.

**Paso 3 — Elementos notables.** Mínimo: $0_{D_{30}}=1$. Máximo: $1_{D_{30}}=30$. Único minimal ($1$) y único maximal ($30$), coincidentes con mínimo y máximo.

**Paso 4 — ¿Es red?** Sí: en $D_n$ siempre lo es (Teorema 3.5), con $\sup=\text{mcm}$, $\inf=\text{mcd}$. Por ejemplo $\sup\{2,3\}=\text{mcm}(2,3)=6$, $\inf\{6,10\}=\text{mcd}(6,10)=2$.

**Paso 5 — ¿Es distributiva?** Sí, siempre en $D_n$ (mcd y mcm distribuyen entre sí aritméticamente).

**Paso 6 — ¿Es complementada?** Busquemos el complemento de cada divisor con la fórmula $\bar d = 30/d$:

| $d$ | $\bar d = 30/d$ | $\text{mcd}(d,\bar d)$ | $\text{mcm}(d,\bar d)$ | ¿Complemento válido? |
|---|---|---|---|---|
| 1 | 30 | 1 | 30 | Sí |
| 2 | 15 | 1 | 30 | Sí |
| 3 | 10 | 1 | 30 | Sí |
| 5 | 6 | 1 | 30 | Sí |
| 6 | 5 | 1 | 30 | Sí |
| 10 | 3 | 1 | 30 | Sí |
| 15 | 2 | 1 | 30 | Sí |
| 30 | 1 | 1 | 30 | Sí |

Todos los divisores tienen complemento (y es único en cada caso, como corresponde a una red distributiva). Es complementada.

**Paso 7 — ¿Es álgebra de Boole?** Sí: $30=2\cdot 3\cdot 5$ es libre de cuadrados. Al ser red distributiva y complementada, $(D_{30};|)$ **es álgebra de Boole**, con $2^3=8$ elementos, isomorfa a $(\mathcal{P}(\{2,3,5\});\subseteq)$ (identificando cada divisor con el subconjunto de sus factores primos: $6=2\cdot3 \leftrightarrow \{2,3\}$, etc.).

### (b) $(D_{12};\,|\,)$ — por qué NO es álgebra de Boole

**Paso 1.** $12=2^2\cdot 3$. Divisores: $D_{12}=\{1,2,3,4,6,12\}$ (6 elementos: $(2+1)(1+1)=6$).

**Paso 2 — Hasse.** Coberturas: $1\to2$, $1\to3$, $2\to4$, $2\to6$, $3\to6$, $4\to12$, $6\to12$.

**Pasos 3-5.** Mínimo $1$, máximo $12$, únicos minimal/maximal. Es red y es distributiva (como todo $D_n$, por Teorema 3.5).

**Paso 6 — ¿Es complementada? Acá aparece el problema.** Probemos con $d=2$. El candidato es $\bar d = 12/2 = 6$. Verifiquemos:

$$\text{mcd}(2,6)=2 \neq 1$$

¡Ya falla la primera condición! $\text{mcd}(2,6)$ debería ser $1_{D_{12}}=1$ para que $6$ sea complemento de $2$, pero da $2$. Repasando el porqué con el argumento del Teorema 3.6: $12=2^2\cdot 3$ tiene al primo $2$ con exponente $e=2\geq 2$; tomando $d=2=2^1$, tenemos $f=1$ con $0<f<e$, exactamente el caso "malo" de la demostración. Ni $6$ ni ningún otro elemento de $D_{12}$ sirve como complemento de $2$ (probando con cada uno: $\text{mcd}(2,1)=1$ pero $\text{mcm}(2,1)=2\neq12$; $\text{mcd}(2,3)=1$ pero $\text{mcm}(2,3)=6\neq 12$; $\text{mcd}(2,4)=2\neq1$; $\text{mcd}(2,6)=2\neq1$; $\text{mcd}(2,12)=2\neq1$). **Ningún divisor cumple simultáneamente las dos condiciones de complemento para $d=2$.**

**Conclusión.** Como el elemento $2$ **no tiene ningún complemento**, $(D_{12};|)$ **no es complementada**, y por lo tanto **no es álgebra de Boole**, aunque sí sea red y sea distributiva. Esto es consistente con el criterio: $12$ no es libre de cuadrados (tiene el factor $2^2$).

### (c) $(\mathcal{P}(\{a,b,c\});\subseteq)$ y su isomorfismo con un álgebra de Boole de 8 elementos

Sea $A=\{a,b,c\}$. Entonces $\mathcal{P}(A)$ tiene $2^3=8$ elementos:

$$\mathcal{P}(A) = \big\{\varnothing,\ \{a\},\{b\},\{c\},\ \{a,b\},\{a,c\},\{b,c\},\ \{a,b,c\}\big\}$$

**Orden:** $\subseteq$. **Mínimo:** $\varnothing$. **Máximo:** $\{a,b,c\}$. **Sup e ínfimo:** $\sup=\cup$, $\inf=\cap$ (por ejemplo $\{a,b\}\cup\{a,c\}=\{a,b,c\}$, $\{a,b\}\cap\{a,c\}=\{a\}$).

**Complementos:** para cada $X\subseteq A$, $\bar X = A - X$ (complemento respecto de $A$). Por ejemplo:

- $\overline{\varnothing} = \{a,b,c\}$
- $\overline{\{a\}} = \{b,c\}$
- $\overline{\{a,b\}} = \{c\}$

Verifiquemos la definición de complemento con $X=\{a,b\}$: $X \cap \bar X = \{a,b\}\cap\{c\}=\varnothing$ (el mínimo) y $X\cup \bar X = \{a,b\}\cup\{c\}=\{a,b,c\}$ (el máximo). Cumple. Y por el Teorema 3.3 (toda álgebra de Boole es distributiva, y $(\mathcal{P}(A);\subseteq)$ siempre lo es porque $\cup,\cap$ distribuyen entre sí), ese complemento es **único**.

**Isomorfismo con el cubo booleano de 3 bits.** Definimos $\varphi: \mathcal{P}(A) \to \{0,1\}^3$ asignando a cada subconjunto su vector característico según el orden $(a,b,c)$:

| Subconjunto | Vector $(a,b,c)$ |
|---|---|
| $\varnothing$ | $(0,0,0)$ |
| $\{a\}$ | $(1,0,0)$ |
| $\{b\}$ | $(0,1,0)$ |
| $\{c\}$ | $(0,0,1)$ |
| $\{a,b\}$ | $(1,1,0)$ |
| $\{a,c\}$ | $(1,0,1)$ |
| $\{b,c\}$ | $(0,1,1)$ |
| $\{a,b,c\}$ | $(1,1,1)$ |

Esta $\varphi$ es una biyección que respeta el orden ($\subseteq$ corresponde a comparar componente a componente) y las operaciones ($\cup \leftrightarrow$ "or" bit a bit, $\cap \leftrightarrow$ "and" bit a bit, complemento $\leftrightarrow$ invertir cada bit). Esto ilustra concretamente el teorema de isomorfismo: **toda álgebra de Boole finita con $2^n$ elementos es isomorfa a $(\mathcal{P}(\{a_1,\dots,a_n\});\subseteq)$**, que a su vez es isomorfa al cubo $\{0,1\}^n$ con las operaciones lógicas bit a bit. Fijate que $(D_{30};|)$ del ejemplo (a) es, de hecho, **otra copia isomorfa más** de esta misma álgebra de Boole abstracta de 8 elementos, con $2\leftrightarrow a$, $3\leftrightarrow b$, $5\leftrightarrow c$.

## 6. Conectores con otras unidades

**Con [[01-Razonamientos-Categoricos]]:** las operaciones $\lor,\land,\bar{\,\cdot\,}$ de un álgebra de Boole son la formalización algebraica exacta de los conectivos "o", "y", "no" de la lógica proposicional del Tema 1, y las leyes de De Morgan que demostramos acá con supremos e ínfimos son **la misma ley** que se usa ahí para negar disyunciones y conjunciones. Más aún, la estructura de las demostraciones es idéntica: en el Teorema 3.3 y el Teorema 3.4 encadenamos igualdades justificando cada paso con un axioma o ley previa (absorción, distributividad, neutros), exactamente como en una derivación de razonamiento categórico se encadenan pasos justificando cada uno con una regla de inferencia válida. Saber Boole "de memoria" ayuda a validar silogismos vía tablas de verdad, porque $(\{0,1\};+;\cdot)$ es, literalmente, el álgebra de Boole de la lógica clásica.

**Con [[02-Relaciones-de-Equivalencia]]:** conviene comparar explícitamente las dos definiciones. Una relación de equivalencia exige **reflexiva + simétrica + transitiva**; una relación de orden exige **reflexiva + antisimétrica + transitiva**. Comparten reflexividad y transitividad, pero difieren radicalmente en el tercer axioma: la **simetría** de la equivalencia dice "si $a$ se relaciona con $b$, da lo mismo el orden", lo cual borra toda noción de jerarquía y produce **clases que agrupan** elementos "iguales" entre sí. La **antisimetría** del orden, en cambio, dice "si $a\preceq b$ y $b\preceq a$ entonces son el mismo elemento", lo que impide ciclos y es precisamente lo que permite **jerarquizar** en vez de agrupar. Es un lindo ejercicio conceptual: cambiar un solo axioma (simetría por antisimetría) transforma una relación que particiona en una que ordena.

**Con [[04-Congruencias-Euler-Fermat]]:** esta es la conexión más fuerte y concreta de la unidad. El conjunto $D_n$ que usamos todo el tema como ejemplo estrella **es exactamente** el conjunto de divisores de $n$ que se estudia en profundidad en Congruencias. El $\text{mcd}$ y el $\text{mcm}$, que en esta unidad son el ínfimo y el supremo de la red $(D_n;|)$, son las **mismas** herramientas que en Congruencias se usan para el algoritmo de Euclides y para determinar cuándo una ecuación $ax\equiv b \pmod n$ tiene solución (se resuelve sii $\text{mcd}(a,n)\mid b$). Y el criterio "$n$ libre de cuadrados" que determina si $(D_n;|)$ es álgebra de Boole depende de la **misma factorización prima** $n=p_1^{e_1}\cdots p_k^{e_k}$ que se usa para calcular la función de Euler $\varphi(n)=n\prod_i(1-1/p_i)$ en el teorema de Euler-Fermat. En resumen: la teoría de números de la Unidad 4 y el álgebra de Boole de la Unidad 3 comparten el mismo objeto de estudio ($D_n$) mirado desde dos ángulos distintos (aritmético vs. algebraico-ordinal).

**Con [[05-Relaciones-de-Recurrencia]]:** acá el vínculo es más débil, y conviene decirlo honestamente: no hay un teorema compartido tan directo como con Congruencias. Pero sí hay un puente natural de pensamiento: la fórmula $|\mathcal{P}(A)| = 2^{|A|}$ (usada todo el tiempo en esta unidad para calcular el cardinal de un álgebra de Boole tipo $\mathcal{P}(A)$) se puede pensar recursivamente. Si $|A|=n$ y agregamos un elemento nuevo para llegar a $n+1$, cada subconjunto viejo genera dos subconjuntos nuevos (con y sin el elemento agregado), lo que da la recurrencia trivial $a_n = 2\cdot a_{n-1}$ con $a_0=1$. Es la recurrencia más simple posible, pero sirve como primer contacto informal con la lógica de "construir lo de tamaño $n$ a partir de lo de tamaño $n-1$" que se explota en serio en la Unidad 5.

## 7. Errores comunes y trampas del examen

1. **Confundir "minimal" con "mínimo".** El mínimo es único y comparable con todo el conjunto; puede haber varios minimales simultáneamente, y un minimal no necesariamente es menor que todos los demás elementos (solo que nadie es estrictamente menor que él). Si el poset tiene un único minimal, **no** se deduce automáticamente que sea mínimo salvo que se pruebe explícitamente la comparabilidad con todos los elementos.
2. **Creer que toda red es distributiva.** No es así: hay redes perfectamente válidas (con sup e inf bien definidos para todo par) que no distribuyen, típicamente porque contienen una subred isomorfa a $N_5$ o $M_3$. Red y red distributiva son cosas distintas; siempre hay que chequear las leyes distributivas o buscar el patrón prohibido.
3. **Olvidarse de revisar TODOS los pares incomparables al decidir si algo es red.** Basta con que **un solo par** incomparable carezca de sup o de inf (o tenga más de una cota mínima superior sin que ninguna domine a la otra) para que la estructura deje de ser red. Chequear solo "a ojo" unos pocos pares y generalizar es la fuente de error más común en los parciales.
4. **Calcular mal el mcd o el mcm al buscar complementos en $(D_n;|)$.** Un error típico es factorizar mal $n$ o el divisor $d$, o confundir mcd con mcm al armar la tabla de complementos. Conviene siempre factorizar primero $n$ en primos y trabajar con exponentes, en vez de tantear números al voleo.
5. **Confundir "tiene complemento" con "tiene complemento único".** Una red puede ser complementada (todo elemento tiene al menos un complemento) sin ser distributiva, en cuyo caso puede haber elementos con **más de un** complemento. La unicidad del complemento **no** es automática: es consecuencia exclusiva de la distributividad (Teorema 3.3).
6. **Aplicar el criterio "$n$ libre de cuadrados" sin verificar antes que se trata de $(D_n;|)$.** Ese criterio es específico de la divisibilidad; no tiene sentido aplicarlo a $(\mathcal{P}(A);\subseteq)$ (que siempre es álgebra de Boole) ni a otro poset cualquiera.
7. **Pensar que el diagrama de Hasse "pierde información" al omitir transitividad y lazos.** No la pierde: la reflexividad se repone siempre trivialmente y la transitividad se reconstruye siguiendo caminos ascendentes por las líneas dibujadas. Omitirlas es una simplificación válida, no una aproximación.
8. **Mezclar el orden de la unión/intersección al calcular sup/inf en $(\mathcal{P}(A);\subseteq)$.** Recordar siempre: $\sup = \cup$ (unión, "lo más grande que contiene a ambos") e $\inf = \cap$ (intersección, "lo más grande contenido en ambos"), nunca al revés.
9. **Suponer que un elemento con único complemento en una red no distributiva prueba que la red es distributiva.** La unicidad del complemento de *un* elemento particular no alcanza; hace falta que la propiedad valga para *todos* los elementos, y en rigor hay que verificar las leyes distributivas (o la ausencia de $N_5$/$M_3$) en general, no un caso aislado.

## 8. Preguntas de autoevaluación

1. Dado el poset $(\{1,2,3,4,6,12\};|)$, dibujá el diagrama de Hasse e identificá mínimo, máximo, minimales y maximales.
2. ¿Puede un poset tener dos elementos maximales distintos y seguir siendo una red? Justificá.
3. Demostrá que si un poset tiene supremo de $A$ (el conjunto completo) y ese supremo pertenece a $A$, entonces coincide con el máximo.
4. Probá, usando la definición de ínfimo y supremo (sin recurrir a las fórmulas de mcd/mcm), que en $(D_{18};|)$ el conjunto $\{2,3\}$ tiene supremo $6$.
5. ¿Es $(D_{18};|)$ un álgebra de Boole? Justificá con el criterio de libre de cuadrados y, además, exhibiendo un elemento problemático si corresponde.
6. Enunciá y demostrá la segunda ley de De Morgan ($\overline{a\land b} = \bar a \lor \bar b$) usando el principio de dualidad a partir de la demostración de la primera.
7. ¿Por qué la antisimetría es la propiedad que distingue un orden de una equivalencia? Dá un ejemplo de relación reflexiva y transitiva que no sea ni orden ni equivalencia (que falle tanto simetría como antisimetría).
8. En una red $(A;\preceq)$ con $0_A$ y $1_A$, ¿puede el mínimo $0_A$ ser su propio complemento? ¿Bajo qué condición sobre $A$?
9. Mostrá con un contraejemplo concreto (usando $N_5$ o $M_3$) que la distributividad no se deduce automáticamente de ser red complementada.
10. Si $|B|=16$ para un álgebra de Boole finita $B$, ¿con qué conjunto $(\mathcal{P}(A);\subseteq)$ es isomorfa? ¿Cuántos átomos (elementos que cubren al mínimo) tiene?

## 9. Referencias

- Teoría original: `../03_redes_algebras_boole/readme.md`
- Ejercicios resueltos: `../ejercicios-resueltos/tema3_boole.md`

---
**Ver también:** [[00-Indice-Matematica-Discreta]] · [[01-Razonamientos-Categoricos]] · [[02-Relaciones-de-Equivalencia]] · [[04-Congruencias-Euler-Fermat]] · [[05-Relaciones-de-Recurrencia]]
