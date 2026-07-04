---
tags: [matematica-discreta, tema-1, logica, unsam]
aliases: ["Razonamientos Categóricos", "Cuantificadores", "Tema 1"]
---

# Razonamientos Categóricos

> [!info] Ubicación en la materia
> Esta unidad es la base lógica de toda la materia: acá aprendemos a leer, simbolizar y **demostrar** enunciados con cuantificadores, que es exactamente el lenguaje que se usa después para probar propiedades de relaciones ([[02-Relaciones-de-Equivalencia]]), leyes de álgebras de Boole ([[03-Redes-y-Algebras-de-Boole]]), teoremas de congruencias ([[04-Congruencias-Euler-Fermat]]) e inducción en recurrencias ([[05-Relaciones-de-Recurrencia]]).

## 1. Introducción y motivación

En matemática discreta (y en matemática en general) casi ninguna afirmación interesante es "chata". Cuando decimos "todo número par es divisible por 2" o "existe un número primo mayor que 100" no estamos hablando de una proposición aislada, sino de una afirmación sobre **todos** o **algunos** elementos de un conjunto. Para poder manipular este tipo de enunciados con precisión —y sobre todo para poder **demostrar** que una conclusión se sigue necesariamente de ciertas premisas— necesitamos un lenguaje formal más rico que el de la lógica proposicional pura (la de $p$, $q$, $\land$, $\lor$, etc.). Ese lenguaje es la **lógica de predicados** (también llamada lógica de primer orden), y las herramientas centrales son los **cuantificadores** $\forall$ (para todo) y $\exists$ (existe).

Un **razonamiento categórico** es, en esta materia, un razonamiento formado por premisas y una conclusión que involucran predicados cuantificados sobre un conjunto universal fijo. La tarea central de esta unidad es doble:

1. **Simbolizar** correctamente un razonamiento dado en lenguaje natural: definir el universo, elegir letras predicado, y traducir cada premisa y la conclusión a fórmulas con cuantificadores.
2. **Determinar si el razonamiento es válido.** Si lo es, hay que **demostrarlo** con una derivación formal (una cadena de pasos justificados por reglas de inferencia). Si no lo es, hay que **refutarlo** exhibiendo un **contraejemplo**: una interpretación concreta del universo y los predicados donde todas las premisas resultan verdaderas pero la conclusión resulta falsa.

Esta doble tarea (demostrar o refutar) es el esqueleto metodológico que se repite en casi toda la materia: cada vez que después tengamos que probar que una relación es transitiva, que una operación booleana cumple una ley, o que una fórmula de recurrencia vale "para todo $n$", vamos a estar haciendo, en esencia, un razonamiento categórico. Por eso vale la pena entenderlo con total rigor acá, al principio.

Es importante también distinguir esta unidad de la lógica proposicional "pura": ahí trabajamos con letras proposicionales $p, q, r, \dots$ que representan proposiciones completas y fijas (verdaderas o falsas, sin variables libres). Acá, en cambio, trabajamos con **funciones proposicionales** (predicados) que dependen de una variable que recorre un universo, y necesitamos los cuantificadores para "cerrar" esa variable y obtener afirmaciones que sí tengan un valor de verdad definido.

## 2. Definiciones formales

### 2.1 Proposición

Una **proposición** es un enunciado declarativo al que se le puede asignar exactamente un valor de verdad: **verdadero (V)** o **falso (F)**, sin ambigüedad ni dependencia de una variable no cuantificada. Ejemplos: "$5$ es un número primo" (V), "$2+2=5$" (F). No son proposiciones las preguntas, las órdenes, ni los enunciados con variables libres como "$x$ es mayor que $3$" (todavía no sabemos qué es $x$).

### 2.2 Función proposicional (predicado)

Una **función proposicional** o **predicado** es una expresión $P(x)$ que contiene una o más variables libres, tal que al reemplazar cada variable por un elemento específico del conjunto universal, la expresión se convierte en una proposición (con un valor de verdad definido). Formalmente, si $U$ es el conjunto universal, un predicado de una variable es una función

$$P : U \to \{V, F\}$$

Notación: $P(x)$: "$x$ es programador", $R(x,y)$: "$x$ es amigo de $y$" (predicado binario, con dos variables). Un predicado **no** es una proposición hasta que sus variables se fijan (con una constante) o se cuantifican.

### 2.3 Conjunto universal (dominio del discurso)

El **conjunto universal** $U$ (también llamado dominio del discurso) es el conjunto de todos los objetos que las variables de nuestro razonamiento pueden representar. Es un dato **imprescindible** del problema: la misma fórmula puede ser verdadera en un universo y falsa en otro (esto se explota justamente en los contraejemplos, sección 5.3). Fijar $U$ es siempre el primer paso de cualquier simbolización.

### 2.4 Cuantificador universal

El **cuantificador universal**, simbolizado $\forall x$ ("para todo $x$"), convierte el predicado $P(x)$ en la proposición

$$\forall x \, P(x)$$

cuyo significado es: "para cada elemento $x$ del universo $U$, $P(x)$ es verdadero". Su valor de verdad se define así:

| Situación semántica | Valor de $\forall x\, P(x)$ |
|---|---|
| $P(x)$ es V para **todos** los elementos $x \in U$ | **V** |
| Existe **al menos un** elemento $x \in U$ tal que $P(x)$ es F | **F** |

Es decir, $\forall x\, P(x)$ equivale (si $U = \{a_1, a_2, \dots, a_n\}$ es finito) a la conjunción extendida

$$P(a_1) \land P(a_2) \land \cdots \land P(a_n)$$

y una conjunción es falsa apenas **uno** de sus términos es falso. Por eso alcanza un solo elemento "malo" (un **contraejemplo puntual**) para tumbar un universal.

### 2.5 Cuantificador existencial

El **cuantificador existencial**, simbolizado $\exists x$ ("existe un $x$ tal que"), convierte $P(x)$ en

$$\exists x \, P(x)$$

cuyo significado es: "hay al menos un elemento $x \in U$ para el cual $P(x)$ es verdadero". Su tabla de verdad:

| Situación semántica | Valor de $\exists x\, P(x)$ |
|---|---|
| Existe **al menos un** elemento $x \in U$ tal que $P(x)$ es V | **V** |
| $P(x)$ es F para **todos** los elementos $x \in U$ | **F** |

Análogamente, en un universo finito $\exists x\, P(x)$ equivale a la disyunción extendida

$$P(a_1) \lor P(a_2) \lor \cdots \lor P(a_n)$$

y una disyunción es verdadera apenas **uno** de sus términos es verdadero.

> [!warning] $U$ no puede ser vacío
> Se asume siempre $U \neq \emptyset$. Si $U = \emptyset$, por convención $\forall x\,P(x)$ sería vacuamente verdadero y $\exists x\,P(x)$ sería falso para cualquier $P$, lo cual rompe la intuición de los ejemplos de la materia. En los ejercicios de la cursada siempre trabajamos con universos no vacíos (y casi siempre no triviales).

### 2.6 Negación de cuantificadores

Las dos leyes de negación de cuantificadores son:

$$\neg(\forall x\, P(x)) \equiv \exists x\, \neg P(x)$$

$$\neg(\exists x\, P(x)) \equiv \forall x\, \neg P(x)$$

La justificación semántica rigurosa de estas equivalencias se desarrolla con demostración completa en la Sección 3.2. Intuitivamente: negar "todos cumplen $P$" es afirmar "hay alguno que no cumple $P$"; y negar "alguno cumple $P$" es afirmar "ninguno cumple $P$", es decir, "todos no cumplen $P$".

### 2.7 Razonamiento categórico

Un **razonamiento categórico** es un par $(\{H_1, H_2, \dots, H_n\}, C)$ donde $H_1, \dots, H_n$ son fórmulas (premisas, "hipótesis") y $C$ es una fórmula (la conclusión), todas construidas a partir de predicados sobre un mismo universo $U$ mediante conectivos lógicos y cuantificadores. Se escribe habitualmente

$$H_1, H_2, \dots, H_n \; \therefore \; C$$

o en columna, con el símbolo $\vdash$ (se lee "se deriva" o "por lo tanto") separando premisas de conclusión:

$$H_1, H_2, \dots, H_n \vdash C$$

### 2.8 Validez semántica de un razonamiento

Un razonamiento $H_1, \dots, H_n \vdash C$ es **válido** (o **lógicamente correcto**) si y solo si **en toda interpretación posible** del universo $U$ y de los predicados que aparecen, cada vez que todas las premisas $H_1, \dots, H_n$ resultan verdaderas, la conclusión $C$ también resulta verdadera. Formalmente:

$$\text{El razonamiento es válido} \iff \text{para toda interpretación } I: \; \big(I \models H_1 \land \cdots \land I \models H_n\big) \implies I \models C$$

donde $I \models F$ se lee "$F$ es verdadera bajo la interpretación $I$" (es decir, con ese universo y esas extensiones de los predicados).

Notar la asimetría metodológica que esto genera:

- Para **probar que es válido** hace falta un argumento que funcione para **cualquier** interpretación posible: no alcanza con probarlo en un caso particular. Por eso se usa una **derivación formal** (Sección 3.4), que es un argumento puramente sintáctico (basado en reglas de inferencia) válido independientemente de qué signifiquen los predicados.
- Para **probar que es inválido** alcanza con encontrar **una sola** interpretación (un contraejemplo) donde las premisas sean todas verdaderas y la conclusión falsa. No hace falta ningún argumento general: un contraejemplo concreto y verificado basta, porque contradice la definición de validez (que exige que la implicación valga *siempre*).

Esta asimetría (validez = argumento universal; invalidez = un contraejemplo) es exactamente la misma lógica de $\forall$ vs. $\exists$ que estamos estudiando, aplicada un nivel más arriba, al metarrazonamiento sobre razonamientos.

## 3. Teoremas y demostraciones

### 3.1 Justificación semántica de Modus Ponens y Modus Tollens

**Modus Ponens (M.P.):** $p \to q, \; p \; \vdash \; q$.

*Demostración (por tabla de verdad).* Hay que ver que en toda fila donde $p \to q$ es V **y** $p$ es V, necesariamente $q$ es V. Repasemos la tabla de verdad del condicional:

| $p$ | $q$ | $p \to q$ |
|---|---|---|
| V | V | V |
| V | F | F |
| F | V | V |
| F | F | V |

Buscamos las filas donde **ambas** premisas ($p \to q$ y $p$) son verdaderas. Eso ocurre únicamente en la primera fila ($p=V, q=V, p\to q = V$). En esa fila, $q = V$. No hay ninguna otra fila donde $p=V$ y $p\to q = V$ simultáneamente (la fila 2 tiene $p=V$ pero $p\to q=F$). Por lo tanto, siempre que las dos premisas son verdaderas, $q$ también lo es. $\blacksquare$

**Modus Tollens (M.T.):** $p \to q, \; \neg q \; \vdash \; \neg p$.

*Demostración.* Buscamos en la tabla las filas donde $p\to q = V$ **y** $\neg q = V$ (es decir, $q = F$). Mirando la tabla: $q=F$ ocurre en las filas 2 y 4. De esas, la fila 2 ($p=V, q=F$) tiene $p\to q = F$, así que **no** cumple la premisa $p \to q = V$. La única fila que cumple ambas premisas es la fila 4: $p=F, q=F, p\to q=V, \neg q = V$. En esa fila, $p = F$, es decir $\neg p = V$. Por lo tanto, siempre que las dos premisas son verdaderas, $\neg p$ es verdadera. $\blacksquare$

Este es el patrón general de justificación semántica de cualquier regla proposicional: se arma la tabla de verdad conjunta de las premisas y la conclusión, y se verifica que en **toda** fila donde las premisas dan V, la conclusión también da V (equivalentemente, que la fórmula $(\text{premisa}_1 \land \cdots \land \text{premisa}_n) \to \text{conclusión}$ es una **tautología**).

### 3.2 Demostración de la ley de De Morgan generalizada para cuantificadores

**Teorema.** Para todo predicado $P$ sobre un universo $U$:

$$\neg(\forall x\, P(x)) \equiv \exists x\, \neg P(x) \qquad \text{y} \qquad \neg(\exists x\, P(x)) \equiv \forall x\, \neg P(x)$$

*Demostración semántica (primera equivalencia).* Hay que probar que ambos lados tienen siempre el mismo valor de verdad, para cualquier interpretación de $U$ y $P$. Lo hacemos por doble implicación sobre los valores de verdad.

($\Rightarrow$) Supongamos $\neg(\forall x\, P(x))$ es verdadera. Entonces $\forall x\, P(x)$ es falsa. Por la definición semántica del cuantificador universal (Sección 2.4), $\forall x\, P(x)$ es falsa exactamente cuando **existe al menos un** elemento $a \in U$ tal que $P(a)$ es falso. Que $P(a)$ sea falso significa, por definición de negación, que $\neg P(a)$ es verdadero. Entonces existe (al menos) ese elemento $a \in U$ para el cual $\neg P(a)$ es verdadero, que es precisamente la condición de verdad de $\exists x\, \neg P(x)$ (Sección 2.5). Luego $\exists x\, \neg P(x)$ es verdadera.

($\Leftarrow$) Supongamos $\exists x\, \neg P(x)$ es verdadera. Entonces existe un elemento $a \in U$ tal que $\neg P(a)$ es verdadero, es decir, $P(a)$ es falso. Como hay (al menos) un elemento del universo donde $P$ falla, por definición $\forall x\, P(x)$ es falsa. Luego $\neg(\forall x\, P(x))$ es verdadera.

Como ambas implicaciones valen, las dos fórmulas son equivalentes: tienen siempre el mismo valor de verdad. $\blacksquare$

*Demostración de la segunda equivalencia* ($\neg(\exists x\,P(x)) \equiv \forall x\,\neg P(x)$). Se puede derivar directamente de la primera aplicándola al predicado $\neg P$: por la primera ley, $\neg(\forall x\, \neg P(x)) \equiv \exists x\, \neg(\neg P(x)) \equiv \exists x\, P(x)$ (usando la doble negación $\neg\neg P(x) \equiv P(x)$). Negando ambos miembros de esta equivalencia: $\forall x\, \neg P(x) \equiv \neg(\exists x\, P(x))$, que es justo lo que queríamos. Alternativamente, se prueba por el mismo método directo de doble implicación que en el caso anterior, intercambiando los roles de $\forall$ y $\exists$. $\blacksquare$

**Intuición para recordarlo sin errores:** pensar $\forall$ como una "gran conjunción" ($P(a_1) \land P(a_2) \land \cdots$) y $\exists$ como una "gran disyunción" ($P(a_1) \lor P(a_2) \lor \cdots$). Entonces estas leyes son exactamente las leyes de De Morgan proposicionales ($\neg(p\land q) \equiv \neg p \lor \neg q$ y $\neg(p \lor q) \equiv \neg p \land \neg q$) "estiradas" a un universo posiblemente infinito. El cuantificador cambia de tipo ($\forall \leftrightarrow \exists$) y la negación "entra" al predicado.

### 3.3 Por qué P.U. no tiene restricciones pero G.U. sí, y por qué P.E. exige un nombre nuevo

**Particularización Universal (P.U.): sin restricciones.**

Si $\forall x\, P(x)$ es verdadera, entonces $P(x)$ vale para *todos* los elementos del universo sin excepción. Por lo tanto, para **cualquier** elemento $a$ que yo elija de $U$ —ya haya aparecido antes en la demostración o no, sea una constante nombrada en las premisas o no— puedo concluir $P(a)$. No hay ningún riesgo lógico en esto: estoy simplemente "instanciando" una afirmación que ya sabemos que vale universalmente. Por eso P.U. no tiene restricciones.

**Generalización Universal (G.U.): "$a$" debe ser arbitrario.**

La regla dice: de $P(a)$ se puede concluir $\forall x\, P(x)$, **siempre y cuando $a$ represente un elemento arbitrario y genérico del universo**, es decir, que no haya recibido ninguna propiedad especial ni haya sido fijado por una premisa, una hipótesis auxiliar, o una particularización existencial previa en la demostración.

La razón es que la validez de la inferencia "si vale para uno arbitrario, vale para todos" depende exactamente de que ese "uno" no tenga nada de especial: si $a$ fue elegido sin restricciones, entonces el argumento que prueba $P(a)$ sirve palabra por palabra para cualquier otro elemento del universo, y por lo tanto vale para todos. Si en cambio $a$ tiene una propiedad particular (por ejemplo, proviene de una premisa del tipo $\exists x\, Q(x)$, particularizada a un cierto $c$), entonces lo que probamos es válido solo para *ese* elemento con esa propiedad, no para todo el universo.

**Contraejemplo de qué pasa si no se respeta la restricción.** Sea $U = \mathbb{Z}$ (los enteros) y consideremos la premisa

$$\exists x \, (x^2 = 4)$$

que es verdadera (con $x=2$, o $x=-2$). Por P.E. (Sección 3.3, más abajo) puedo particularizar: sea $c$ tal que $c^2 = 4$ (nombre nuevo). Ahora, si **incorrectamente** aplicara G.U. sobre $c$ diciendo "$c$ es un elemento del universo, luego para todo $x$, $x^2=4$", llegaría a la conclusión falsa $\forall x\,(x^2=4)$, que evidentemente es falsa (por ejemplo con $x=3$). El error está clarísimo: $c$ **no** era arbitrario, tenía la propiedad especial $c^2=4$ impuesta por la premisa existencial. Por eso G.U. exige explícitamente que la constante generalizada no haya aparecido antes en premisas ni en particularizaciones existenciales usadas para llegar hasta ahí: si se permitiera generalizar sobre una constante "contaminada", cualquier razonamiento con una premisa existencial podría "demostrar" que esa propiedad vale para todo el universo, lo cual es absurdo.

**Particularización Existencial (P.E.): "$c$" debe ser un nombre nuevo.**

Si $\exists x\, P(x)$ es verdadera, sabemos que *algún* elemento del universo cumple $P$, pero no sabemos **cuál**. La regla P.E. nos permite darle un nombre temporal $c$ a ese elemento (hasta ahora desconocido) y razonar con $P(c)$, **con la condición de que $c$ sea un símbolo que no se haya usado antes** en la demostración (ni como constante de una premisa, ni como resultado de otra particularización).

**Contraejemplo de qué pasa si no se respeta la restricción.** Sea $U = \mathbb{Z}$ y las premisas:

$$\exists x\, (x > 5) \qquad \text{y} \qquad \exists x\, (x < 0)$$

Ambas son verdaderas por separado. Si **incorrectamente** reutilizara el mismo nombre $c$ para las dos particularizaciones existenciales (violando la restricción de "nombre nuevo"), obtendría:

$$c > 5 \qquad \text{y} \qquad c < 0$$

lo cual es una contradicción absurda ($c$ no puede ser a la vez mayor que $5$ y menor que $0$). El error es evidente: la primera premisa dice que *algún* entero (llamémoslo $c_1$) es mayor que 5, y la segunda dice que *algún* entero, posiblemente **distinto** (llamémoslo $c_2$), es menor que 0. No hay ninguna garantía de que sea el mismo elemento el que cumple ambas cosas. Al forzar el mismo nombre $c$ para ambos, estaría asumiendo indebidamente que son el mismo elemento, lo que puede introducir contradicciones falsas o conclusiones inválidas. Por eso P.E. exige que cada particularización existencial use un nombre genuinamente nuevo, no usado en ninguna línea anterior de la derivación.

### 3.4 Derivación formal completa de un razonamiento válido con cuantificadores

**Razonamiento a demostrar:**

Universo $U$: personas. Predicados: $E(x)$: "$x$ estudia"; $A(x)$: "$x$ aprueba"; $F(x)$: "$x$ es feliz".

Premisas:
1. $\forall x\, (E(x) \to A(x))$ — "Todo el que estudia, aprueba."
2. $\forall x\, (A(x) \to F(x))$ — "Todo el que aprueba, es feliz."
3. $\exists x\, E(x)$ — "Alguien estudia."

Conclusión: $\exists x\, F(x)$ — "Alguien es feliz."

**Derivación numerada:**

| # | Fórmula | Justificación |
|---|---|---|
| 1 | $\forall x\, (E(x) \to A(x))$ | Premisa |
| 2 | $\forall x\, (A(x) \to F(x))$ | Premisa |
| 3 | $\exists x\, E(x)$ | Premisa |
| 4 | $E(c)$ | P.E. en (3), $c$ nombre **nuevo** (no usado antes) |
| 5 | $E(c) \to A(c)$ | P.U. en (1), instanciando en $c$ (sin restricción) |
| 6 | $A(c) \to F(c)$ | P.U. en (2), instanciando en $c$ (sin restricción) |
| 7 | $A(c)$ | M.P. en (4) y (5) |
| 8 | $F(c)$ | M.P. en (7) y (6) |
| 9 | $\exists x\, F(x)$ | G.E. en (8), sin restricciones |

**Justificación línea por línea:** Las líneas 1–3 son las premisas dadas. En la línea 4 usamos P.E. sobre la premisa (3): como sabemos que *algún* elemento cumple $E$, le damos el nombre temporal $c$ —crucial que $c$ no haya sido usado antes en la derivación, porque es la primera vez que introducimos un nombre—. En las líneas 5 y 6 usamos P.U. sobre las premisas universales (1) y (2), instanciándolas en ese mismo $c$: como valen *para todo* $x$, valen en particular para $c$ (sin ninguna restricción, tal como se justificó en la Sección 3.3). Ahora tenemos tres fórmulas proposicionales "puras" en la variable fija $c$: $E(c)$, $E(c)\to A(c)$, $A(c)\to F(c)$. En la línea 7 aplicamos Modus Ponens entre (4) y (5) para obtener $A(c)$. En la línea 8 aplicamos Modus Ponens de nuevo, entre (7) y (6), para obtener $F(c)$. Finalmente, en la línea 9, como probamos $F(c)$ para un elemento específico (no arbitrario, sino el mismo $c$ particular que salió de la premisa existencial), lo correcto es generalizar **existencialmente** (G.E., que no tiene restricciones): concluimos $\exists x\, F(x)$, que es la conclusión buscada. Notar que **no** podríamos haber aplicado G.U. sobre $F(c)$ para concluir $\forall x\, F(x)$, porque $c$ no es arbitrario (viene de una particularización existencial): esto es exactamente la restricción de la Sección 3.3, y aquí se ve por qué la conclusión de este razonamiento es (correctamente) existencial y no universal.

## 4. Fórmulas clave (tabla de repaso rápido)

| Símbolo / Nombre | Se lee | Esquema / Regla |
|---|---|---|
| $\neg$ | "no" | Negación |
| $\land$ | "y" | Conjunción |
| $\lor$ | "o" | Disyunción (inclusiva) |
| $\to$ | "si... entonces" | Condicional |
| $\leftrightarrow$ | "si y solo si" | Bicondicional |
| $\forall x\, P(x)$ | "para todo $x$, $P(x)$" | Cuantificador universal |
| $\exists x\, P(x)$ | "existe un $x$ tal que $P(x)$" | Cuantificador existencial |
| $\neg(\forall x\,P(x)) \equiv \exists x\,\neg P(x)$ | — | Negación de $\forall$ (De Morgan generalizada) |
| $\neg(\exists x\,P(x)) \equiv \forall x\,\neg P(x)$ | — | Negación de $\exists$ (De Morgan generalizada) |
| M.P. — Modus Ponens | — | $p\to q,\; p \;\vdash\; q$ |
| M.T. — Modus Tollens | — | $p\to q,\; \neg q \;\vdash\; \neg p$ |
| S.D. — Silogismo Disyuntivo | — | $p\lor q,\; \neg p \;\vdash\; q$ |
| S.H. — Silogismo Hipotético | — | $p\to q,\; q\to r \;\vdash\; p\to r$ |
| D.C. — Dilema Constructivo | — | $p\to q,\; r\to s,\; p\lor r \;\vdash\; q\lor s$ |
| Absorción | — | $p\to q \;\vdash\; p\to(p\land q)$ |
| Simplificación | — | $p\land q \;\vdash\; p$ |
| Adición | — | $p \;\vdash\; p\lor q$ |
| Conjunción | — | $p,\; q \;\vdash\; p\land q$ |
| P.U. — Particularización Universal | sin restricciones | $\forall x\, P(x) \;\vdash\; P(a)$, para **cualquier** $a\in U$ |
| G.U. — Generalización Universal | $a$ debe ser **arbitrario** | $P(a) \;\vdash\; \forall x\, P(x)$ |
| P.E. — Particularización Existencial | $c$ debe ser **nombre nuevo** | $\exists x\, P(x) \;\vdash\; P(c)$ |
| G.E. — Generalización Existencial | sin restricciones | $P(a) \;\vdash\; \exists x\, P(x)$ |

> [!tip] Orden típico de una derivación
> Premisas $\to$ **P.U./P.E.** (bajar de cuantificadores a proposicional) $\to$ reglas proposicionales básicas (M.P., M.T., S.D., S.H., etc.) $\to$ **G.U./G.E.** (subir de nuevo a cuantificadores, si la conclusión los tiene).

## 5. Ejemplos resueltos paso a paso

### 5.1 Ejemplo resuelto: análisis de un razonamiento en lenguaje natural

**Enunciado:** "Si estudio, apruebo. Si apruebo, me pongo feliz. Estudio. Por lo tanto, me pongo feliz."

**Paso 1 — ¿Es un razonamiento categórico?** No tiene cuantificadores explícitos ni predicados sobre un universo de individuos: habla de un único sujeto implícito (yo). Es, en rigor, un razonamiento puramente **proposicional** (no hace falta un diccionario de predicados con universo, porque no hay variable que recorra un conjunto). Se puede simbolizar directamente con letras proposicionales:

- $p$: "estudio"
- $q$: "apruebo"
- $r$: "me pongo feliz"

Premisas: $p \to q$, $q \to r$, $p$. Conclusión: $r$.

**Paso 2 — ¿Es válido?** Aplicamos Silogismo Hipotético (S.H.) a las dos primeras premisas:

| # | Fórmula | Justificación |
|---|---|---|
| 1 | $p \to q$ | Premisa |
| 2 | $q \to r$ | Premisa |
| 3 | $p$ | Premisa |
| 4 | $p \to r$ | S.H. en (1) y (2) |
| 5 | $r$ | M.P. en (3) y (4) |

El razonamiento es **válido**. (Alternativamente, se podía ir directo: M.P. en (3) y (1) da $q$; M.P. en ese resultado y (2) da $r$. Ambos caminos son correctos.)

**Nota conceptual:** aunque el enunciado tiene "forma" de razonamiento categórico (premisas encadenadas, conclusión), técnicamente **no lo es** en el sentido estricto de esta unidad porque no involucra predicados cuantificados sobre un universo de varios individuos, sino proposiciones fijas sobre un único sujeto implícito. Es útil como ejercicio de calentamiento porque muestra que las reglas básicas (S.H., M.P.) son el "motor interno" que después se usa dentro de cualquier derivación categórica, una vez que particularizamos los cuantificadores.

### 5.2 Ejemplo resuelto: refutación con contraejemplo explícito

**Enunciado:**

$$\exists x\,[r(x) \lor t(x)]; \qquad \exists x\, \neg t(x) \qquad \therefore \qquad \exists x\, r(x)$$

**Paso 1 — ¿Por qué "parece" válido a primera vista?** La tentación es razonar así: "hay algo que cumple $r$ o $t$; hay algo que no cumple $t$; entonces por silogismo disyuntivo, ese algo debe cumplir $r$". El error está en que las dos premisas existenciales **no garantizan que hablen del mismo elemento**. Esto es exactamente el peligro señalado en la Sección 3.3 sobre P.E.: no puedo particularizar ambas existenciales con el mismo nombre.

**Paso 2 — construcción del contraejemplo.** Elegimos un universo chico y concreto:

$$U = \{1, 2\}$$

Definimos las extensiones (los conjuntos de elementos que cumplen cada predicado):

- $r$ se cumple en: $\{\,\}$ (ningún elemento cumple $r$; es decir, $r(1) = F$, $r(2) = F$).
- $t$ se cumple en: $\{1\}$ (es decir, $t(1) = V$, $t(2) = F$).

**Paso 3 — verificar que las premisas son verdaderas.**

- Premisa 1: $\exists x\, [r(x) \lor t(x)]$. Probamos $x=1$: $r(1) \lor t(1) = F \lor V = V$. Como hay al menos un elemento (el $1$) que cumple $r(x) \lor t(x)$, la premisa es **verdadera**. ✓
- Premisa 2: $\exists x\, \neg t(x)$. Probamos $x=2$: $\neg t(2) = \neg F = V$. Como hay al menos un elemento (el $2$) que cumple $\neg t(x)$, la premisa es **verdadera**. ✓

**Paso 4 — verificar que la conclusión es falsa.**

- Conclusión: $\exists x\, r(x)$. Revisamos todo el universo: $r(1) = F$ y $r(2) = F$. No hay **ningún** elemento que cumpla $r$. Por lo tanto $\exists x\, r(x)$ es **falsa**. ✓

**Conclusión del ejercicio.** Encontramos una interpretación ($U=\{1,2\}$, con $r$ vacío y $t=\{1\}$) donde ambas premisas son verdaderas y la conclusión es falsa. Por lo tanto, el razonamiento es **inválido**. El "elemento que cumple $r(x)\lor t(x)$" (el $1$, porque cumple $t$) es un elemento distinto del que hace falsa a $t$ (el $2$); no hay ningún elemento en común que fuerce $r$. Esto confirma con un ejemplo concreto por qué no se pueden combinar dos particularizaciones existenciales bajo el mismo nombre: acá literalmente son elementos distintos.

### 5.3 Ejemplo resuelto: verdad/falsedad de una proposición cuantificada variando el universo

**Predicado:** $P(n): \; n^2 \le n! + 2$, sobre distintos universos numéricos.

**Caso $U = \{0, 1, 2\}$, proposición $\forall n\, P(n)$.**

Verificamos cada elemento (recordando $0! = 1$, $1! = 1$, $2! = 2$):

- $n=0$: $0^2 = 0$, $0! + 2 = 1+2 = 3$. ¿$0 \le 3$? Sí. $P(0) = V$.
- $n=1$: $1^2 = 1$, $1!+2 = 1+2=3$. ¿$1 \le 3$? Sí. $P(1) = V$.
- $n=2$: $2^2 = 4$, $2!+2 = 2+2 = 4$. ¿$4 \le 4$? Sí (igualdad). $P(2) = V$.

Como $P(n)$ es verdadera para **todos** los elementos de este universo chico, $\forall n\, P(n)$ es **verdadera** en $U=\{0,1,2\}$.

**Caso $U = \mathbb{N}$ (naturales, incluyendo todos), proposición $\forall n\, P(n)$.**

Probamos valores más grandes, donde el factorial empieza a crecer mucho más rápido que el cuadrado:

- $n=3$: $3^2=9$, $3!+2 = 6+2=8$. ¿$9 \le 8$? **No.** $P(3) = F$.

Encontramos un elemento del universo ($n=3$) donde el predicado falla. Por lo tanto, en $U = \mathbb{N}$:

$$\forall n\, P(n) \text{ es } \mathbf{FALSA} \qquad \text{(contraejemplo puntual: } n=3\text{)}$$

Pero al mismo tiempo, como sí hay elementos que cumplen $P$ (por ejemplo $n=0,1,2$, y de hecho para $n\ge 3$ el factorial supera ampliamente al cuadrado, así que $P(n)$ vuelve a ser V para $n\ge4$ también, salvo el caso puntual $n=3$):

$$\exists n\, P(n) \text{ es } \mathbf{VERDADERA} \qquad \text{(testigo: } n=0\text{, entre varios otros)}$$

**Conclusión pedagógica del ejemplo.** Este caso muestra con total claridad por qué el universo **no es un detalle accesorio sino parte constitutiva del enunciado**: la misma fórmula $P(n)$ da lugar a un $\forall n\, P(n)$ verdadero en $U=\{0,1,2\}$ y falso en $U=\mathbb{N}$, simplemente porque el segundo universo incluye un testigo ($n=3$) que el primero no tenía. Nunca se puede evaluar $\forall$ o $\exists$ sin tener perfectamente fijado el conjunto universal.

## 6. Conectores con otras unidades

**Con [[02-Relaciones-de-Equivalencia]].** Cuando definimos una relación $R$ sobre un conjunto $A$ y queremos probar que es **reflexiva**, en realidad estamos probando la proposición categórica universal $\forall x \in A: \, xRx$. Por ejemplo, si $A = \mathbb{Z}$ y $R$ se define como $xRy \iff x-y$ es múltiplo de $3$, probar reflexividad consiste en el razonamiento: "sea $x \in \mathbb{Z}$ arbitrario; $x - x = 0 = 3\cdot 0$, luego $x-x$ es múltiplo de $3$; luego $xRx$. Como $x$ era arbitrario, por G.U., $\forall x\in\mathbb{Z}: xRx$." Esa frase "sea $x$ arbitrario... luego, como $x$ era arbitrario..." **es literalmente Generalización Universal aplicada**, con toda la restricción de arbitrariedad discutida en la Sección 3.3: si en la demostración de reflexividad usáramos un $x$ particular (por ejemplo $x=5$ nada más), NO podríamos generalizar a todo $A$. Lo mismo pasa con simetría ($\forall x,y \in A: xRy \to yRx$) y transitividad ($\forall x,y,z\in A: (xRy \land yRz) \to xRz$): son proposiciones universales sobre triplas o pares arbitrarios, y la demostración estándar ("sean $x,y,z$ arbitrarios tales que...") es exactamente una derivación categórica con G.U. al final.

**Con [[03-Redes-y-Algebras-de-Boole]].** Las leyes de un álgebra de Boole (conmutatividad, asociatividad, distributividad, leyes de De Morgan $\overline{a+b} = \bar a \cdot \bar b$, etc.) son la contraparte algebraica exacta de los conectivos $\land, \lor, \neg$ de esta unidad: de hecho, el álgebra de Boole de dos elementos $\{0,1\}$ con $+$ interpretado como $\lor$, $\cdot$ como $\land$ y complemento como $\neg$ **es** el álgebra de la lógica proposicional. Más aún, las demostraciones de igualdades booleanas (por ejemplo, probar que $a + a\cdot b = a$, la ley de absorción booleana) tienen exactamente la misma estructura deductiva que una derivación categórica: cada paso se justifica citando una ley (axioma o teorema previo), igual que cada línea de una derivación categórica se justifica citando una regla de inferencia. Comparación en paralelo:

| Derivación categórica | Demostración algebraica booleana |
|---|---|
| $1.\; p\to q$ (premisa) | $1.\; a+a\cdot b$ (expresión a simplificar) |
| $2.\; p$ (premisa) | $2.\; = a\cdot 1 + a\cdot b$ (neutro de $\cdot$) |
| $3.\; q$ (M.P. en 1,2) | $3.\; = a\cdot(1+b)$ (distributividad) |
| — | $4.\; = a\cdot 1$ (dominación: $1+b=1$) |
| — | $5.\; = a$ (neutro de $\cdot$) |

En ambos casos, la validez de la cadena completa depende de que **cada paso individual** esté justificado por una regla ya establecida, y la conclusión final se sostiene porque toda la cadena es una sucesión de pasos válidos, no porque "se vea" intuitivamente correcta.

**Con [[04-Congruencias-Euler-Fermat]].** El Pequeño Teorema de Fermat ("si $p$ es primo y $a$ no es múltiplo de $p$, entonces $a^{p-1} \equiv 1 \pmod p$") y su generalización, el Teorema de Euler-Fermat ("para todo $a$ coprimo con $n$, $a^{\varphi(n)} \equiv 1 \pmod n$"), son, en su formulación exacta, proposiciones categóricas universales del tipo $\forall a\, (\gcd(a,n)=1 \to a^{\varphi(n)} \equiv 1 \pmod n)$, cuantificando sobre todos los enteros $a$ coprimos con $n$. Su demostración estándar (usando el grupo multiplicativo $(\mathbb{Z}/n\mathbb{Z})^*$ y el teorema de Lagrange, o el argumento combinatorio de permutar los restos) es un razonamiento deductivo formal exactamente del mismo tipo estudiado en esta unidad: se parte de hipótesis generales (que $a$ es arbitrario coprimo con $n$), se encadenan pasos justificados (propiedades de congruencias, cancelación, etc.), y se generaliza al final a "para todo $a$ coprimo con $n$" mediante el mismo mecanismo de G.U. sobre un elemento arbitrario que no tuvo ninguna propiedad especial más allá de la hipótesis de coprimalidad.

**Con [[05-Relaciones-de-Recurrencia]].** La demostración por **inducción matemática**, que se usa constantemente para verificar que una fórmula cerrada realmente resuelve una relación de recurrencia, es estructuralmente una aplicación repetida de Generalización Universal. El principio de inducción dice:

$$\big[P(0) \; \land \; \forall k\,(P(k) \to P(k+1))\big] \;\vdash\; \forall n\, P(n)$$

Comparemos el paralelismo paso a paso con lo visto en esta unidad:

1. **Caso base** $P(0)$: es una P.U./verificación puntual, análoga a probar una proposición concreta.
2. **Paso inductivo** $\forall k\,(P(k)\to P(k+1))$: acá se dice "sea $k$ arbitrario tal que $P(k)$ (hipótesis inductiva); demostramos $P(k+1)$". El "sea $k$ arbitrario" es exactamente la misma jugada de G.U. que vimos en la Sección 3.3 y en la conexión con relaciones de equivalencia: como $k$ no tiene ninguna propiedad especial (es un natural cualquiera, no uno fijado de antemano), lo que se prueba para él vale para todos.
3. **Conclusión** $\forall n\, P(n)$: se obtiene combinando el caso base con el paso inductivo aplicado repetidamente (formalmente, es un axioma/regla adicional del sistema de los naturales, pero su *uso* dentro de una demostración concreta es indistinguible en espíritu de una G.U.: fijamos un $k$ arbitrario, demostramos algo sobre él, y "subimos" a una afirmación universal).

Por eso, cuando en la unidad de recurrencias haya que demostrar "la fórmula cerrada $a_n = 2^n$ satisface la recurrencia $a_n = 2a_{n-1}$ para todo $n\ge 1$", el argumento va a tener la misma anatomía que una derivación categórica: hipótesis (la definición recursiva), un paso donde se toma un índice arbitrario, encadenamiento de igualdades justificadas, y una generalización final.

## 7. Errores comunes y trampas del examen

1. **Confundir P.E. con reutilización de nombres.** Particularizar dos premisas existenciales distintas con el mismo nombre (como en el ejemplo 5.2) asumiendo indebidamente que se trata del mismo elemento. Cada $\exists$ necesita su propio nombre nuevo.
2. **Aplicar G.U. sobre una constante "contaminada".** Generalizar universalmente sobre un elemento que salió de una P.E., de una premisa con constante nombrada, o de una hipótesis auxiliar. Solo se puede hacer G.U. sobre variables genuinamente arbitrarias (ver Sección 3.3).
3. **Negar mal los cuantificadores.** Errores típicos: escribir $\neg(\forall x\,P(x)) \equiv \forall x\,\neg P(x)$ (dejando el mismo cuantificador en vez de cambiarlo) en lugar de la forma correcta $\exists x\,\neg P(x)$; o negar solamente el cuantificador sin negar el predicado interno (dejar $\exists x\, P(x)$ en vez de $\exists x\, \neg P(x)$).
4. **Construir un contraejemplo donde alguna premisa queda falsa sin darse cuenta.** Al elegir extensiones "a ojo" para refutar, es fácil que una de las premisas termine siendo falsa en la interpretación elegida; siempre hay que **verificar explícitamente, una por una, todas las premisas**, no solo la conclusión.
5. **Olvidar fijar o declarar el conjunto universal $U$.** Sin $U$ explícito, ni la simbolización ni el contraejemplo tienen sentido preciso: la misma fórmula puede ser verdadera o falsa según el universo (ver ejemplo 5.3).
6. **Aplicar reglas proposicionales (M.P., S.D., etc.) directamente sobre fórmulas cuantificadas sin particularizar antes.** Las reglas básicas (M.P., M.T., S.D., S.H., etc.) son reglas de la lógica proposicional: solo se pueden aplicar sobre fórmulas ya "libres de cuantificadores" (después de P.U. o P.E.), nunca directamente sobre $\forall x\,(\dots)$ o $\exists x\,(\dots)$ enteras.
7. **Mezclar el orden: generalizar antes de tiempo o particularizar de más.** Generalizar (G.U./G.E.) en medio de la derivación cuando todavía faltan pasos proposicionales, en vez de dejar la generalización para el final, puede llevar a aplicar reglas proposicionales sobre fórmulas que ya volvieron a tener cuantificador, lo cual no es válido.
8. **Creer que un ejemplo (uno que funciona) prueba la validez de un razonamiento.** Para validez hace falta un argumento general (derivación) que funcione en cualquier interpretación; un solo caso donde "funciona" no prueba nada, así como un solo contraejemplo sí alcanza para tumbar la validez.

## 8. Preguntas de autoevaluación

1. Definí con tus palabras la diferencia entre una proposición y una función proposicional (predicado). Dar un ejemplo de cada una.
2. ¿Por qué la definición de validez de un razonamiento exige que la implicación (premisas verdaderas $\Rightarrow$ conclusión verdadera) valga *en toda interpretación*, y no alcanza con verificarla en un solo caso?
3. Demostrá semánticamente (con tabla de verdad o argumento de valores de verdad) que el Silogismo Disyuntivo ($p\lor q, \neg p \vdash q$) es una regla válida.
4. Explicá con tus palabras por qué $\neg(\exists x\, P(x)) \equiv \forall x\, \neg P(x)$, dando el argumento semántico completo (no solo citando la fórmula).
5. Dado el razonamiento $\forall x\,(P(x)\to Q(x)),\; \exists x\, P(x) \;\vdash\; \exists x\, Q(x)$, escribí la derivación formal numerada completa, indicando la regla usada en cada línea.
6. ¿Por qué en la derivación anterior no se podría concluir $\forall x\, Q(x)$ en lugar de $\exists x\, Q(x)$? Justificá citando la restricción correspondiente.
7. Construí un contraejemplo completo (universo, extensiones de los predicados, verificación de premisas y conclusión) para mostrar que el razonamiento $\forall x\,(P(x)\lor Q(x)),\; \exists x\, Q(x) \;\vdash\; \forall x\, P(x)$ es inválido.
8. Simbolizá el siguiente enunciado con diccionario completo (universo, predicados, premisas, conclusión) y determiná si es válido: "Todos los estudiantes de la materia que aprueban el parcial, aprueban la cursada. Juan es estudiante de la materia y aprobó el parcial. Por lo tanto, Juan aprueba la cursada."
9. Explicá con un ejemplo propio (no el del apunte) el paralelismo entre la demostración de transitividad de una relación y la Generalización Universal.
10. ¿Qué diferencia concreta hay entre P.U. y G.U. en cuanto a las restricciones que exige cada regla? ¿Y entre P.E. y G.E.?

## 9. Referencias

- Teoría original: [../01_razonamientos_categoricos/readme.md](../01_razonamientos_categoricos/readme.md)
- Ejercicios resueltos: [../ejercicios-resueltos/tema1_categoricos.md](../ejercicios-resueltos/tema1_categoricos.md)

---
Volver al índice: [[00-Indice-Matematica-Discreta]]
