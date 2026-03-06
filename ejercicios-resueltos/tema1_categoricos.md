# Tema 1 — Razonamientos Categoricos: Ejercicios Resueltos

> Guia de estudio para el final de Matematica Discreta (UNSAM)
> Ejercicios de la practica 1 (Logica) — Seccion III y IV: Razonamientos con cuantificadores

---

## Reglas de inferencia utilizadas (referencia rapida)

| Abreviatura | Nombre completo | Forma |
|---|---|---|
| P.U. | Particularizacion Universal | De `∀x: P(x)` se obtiene `P(a)` para cualquier `a` del universo |
| P.E. | Particularizacion Existencial | De `∃x: P(x)` se obtiene `P(a)` para algun `a` particular (nuevo) |
| G.E. | Generalizacion Existencial | De `P(a)` se obtiene `∃x: P(x)` |
| G.U. | Generalizacion Universal | De `P(a)` (con `a` generico) se obtiene `∀x: P(x)` |
| M.P. | Modus Ponens | De `p→q` y `p` se obtiene `q` |
| M.T. | Modus Tollens | De `p→q` y `¬q` se obtiene `¬p` |
| S.D. | Silogismo Disyuntivo | De `p∨q` y `¬p` se obtiene `q` |
| S.H. | Silogismo Hipotetico | De `p→q` y `q→r` se obtiene `p→r` |
| Simplif. | Simplificacion | De `p∧q` se obtiene `p` (o `q`) |
| Conj. | Conjuncion | De `p` y `q` se obtiene `p∧q` |
| Adic. | Adicion | De `p` se obtiene `p∨q` |
| D.C. | Dilema Constructivo | De `p→q`, `r→s` y `p∨r` se obtiene `q∨s` |
| DeM. | De Morgan | `¬(p∨q) ≡ ¬p∧¬q` y `¬(p∧q) ≡ ¬p∨¬q` |
| Contrarr. | Contrarreciproca | `p→q ≡ ¬q→¬p` |

---

## TIER 1 — PRIORIDAD ALTA

---

### Ejercicio 13a — Grafos completos, conexos y simples

**Enunciado:** "Todos los grafos completos son conexos. Existen grafos simples que no son conexos. Por lo tanto, existen grafos simples que no son completos."

**Identificacion del tipo:** Razonamiento categorico con cuantificadores universales y existenciales. Se resuelve mediante reglas de inferencia para predicados (P.U., P.E., G.E.) combinadas con reglas proposicionales (M.T., Simplificacion, Conjuncion).

**Simbolizacion:**

- **Universo:** U = {x / x es grafo}
- **Diccionario de predicados:**
  - c(x): "x es completo"
  - n(x): "x es conexo"
  - s(x): "x es simple"
- **Forma simbolica:**
  - Premisa 1: ∀x:[c(x) → n(x)]
  - Premisa 2: ∃x:[s(x) ∧ ¬n(x)]
  - Conclusion: ∃x:[s(x) ∧ ¬c(x)]

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[c(x) → n(x)] | Premisa |
| 2 | ∃x:[s(x) ∧ ¬n(x)] | Premisa |
| 3 | s(a) ∧ ¬n(a) | P.E. sobre (2): existe algun grafo `a` que es simple y no conexo. Se elige `a` como testigo del existencial. **Importante:** `a` es un elemento nuevo, no usado antes. |
| 4 | c(a) → n(a) | P.U. sobre (1): la propiedad universal vale para todo grafo, en particular para `a`. |
| 5 | ¬n(a) | Simplificacion sobre (3): de la conjuncion `s(a) ∧ ¬n(a)` se extrae el segundo componente. |
| 6 | ¬c(a) | M.T. sobre (4) y (5): si `c(a) → n(a)` y `¬n(a)`, entonces `¬c(a)`. Es decir, como `a` no es conexo y todo completo es conexo, entonces `a` no es completo. |
| 7 | s(a) | Simplificacion sobre (3): de la conjuncion `s(a) ∧ ¬n(a)` se extrae el primer componente. |
| 8 | s(a) ∧ ¬c(a) | Conjuncion de (7) y (6): combinamos que `a` es simple y que `a` no es completo. |
| 9 | ∃x:[s(x) ∧ ¬c(x)] | G.E. sobre (8): como encontramos un elemento `a` que cumple `s(a) ∧ ¬c(a)`, podemos generalizar existencialmente. |

**Respuesta:** El razonamiento es **VALIDO**. La demostracion formal por reglas de inferencia llega a la conclusion deseada.

**Tips para el examen:**
- Siempre que tengas una premisa existencial y una universal, **primero particulariza el existencial (P.E.)** y luego usa ese mismo elemento para particularizar el universal (P.U.).
- El orden P.E. antes de P.U. es obligatorio: P.E. requiere un nombre nuevo, mientras que P.U. se puede aplicar a cualquier elemento ya existente.
- Modus Tollens es la herramienta clave cuando tenes un universal tipo `∀x:[A(x) → B(x)]` y sabes que `¬B` para algun elemento.

**Errores comunes a evitar:**
- Aplicar P.U. antes que P.E. y luego intentar usar el mismo nombre para P.E. (esto viola la restriccion de nombre nuevo en P.E.).
- Olvidar el paso de G.E. al final: sin este paso, la demostracion no concluye formalmente con la expresion existencial pedida.
- Confundir la direccion del condicional: de `c(a) → n(a)` y `¬c(a)` **no se puede** concluir `¬n(a)` (eso seria falacia de negacion del antecedente).

---

### Ejercicio 13b — Invitados, ingenieros y clases en la facultad

**Enunciado:** "Algunos invitados son ingenieros. Algunos ingenieros dan clases en la facultad. Por lo tanto, algunos invitados dan clases en la facultad."

**Identificacion del tipo:** Razonamiento categorico con dos cuantificadores existenciales. Se analiza validez y, al sospechar invalidez, se construye un contraejemplo con un universo finito.

**Simbolizacion:**

- **Universo:** U = {x / x es persona}
- **Diccionario de predicados:**
  - i(x): "x es invitado"
  - g(x): "x es ingeniero"
  - c(x): "x da clases en la facultad"
- **Forma simbolica:**
  - Premisa 1: ∃x:[i(x) ∧ g(x)]
  - Premisa 2: ∃x:[g(x) ∧ c(x)]
  - Conclusion: ∃x:[i(x) ∧ c(x)]

**Resolucion paso a paso:**

**Paso 1 — Intentar demostracion formal:**

Si particularizamos la Premisa 1: existe un `a` tal que `i(a) ∧ g(a)`.
Si particularizamos la Premisa 2: existe un `b` tal que `g(b) ∧ c(b)`.

**Problema critico:** Los elementos `a` y `b` son testigos de existenciales **distintos**, por lo tanto no podemos asumir que `a = b`. El elemento que es invitado e ingeniero (persona `a`) no necesariamente es el mismo que el ingeniero que da clases (persona `b`). No hay forma de conectar `i(a)` con `c(b)`.

**Paso 2 — Construir contraejemplo:**

- U = {1, 2, 3}
- Asignaciones:
  - Persona 1: i(1) = V, g(1) = V, c(1) = F (es invitado e ingeniero, pero NO da clases)
  - Persona 2: i(2) = F, g(2) = V, c(2) = V (es ingeniero y da clases, pero NO es invitado)
  - Persona 3: i(3) = F, g(3) = F, c(3) = F (no es nada relevante)

- **Verificacion de Premisa 1:** ∃x:[i(x) ∧ g(x)]. La persona 1 cumple: i(1) ∧ g(1) = V ∧ V = V. **Premisa 1 VERDADERA.**
- **Verificacion de Premisa 2:** ∃x:[g(x) ∧ c(x)]. La persona 2 cumple: g(2) ∧ c(2) = V ∧ V = V. **Premisa 2 VERDADERA.**
- **Verificacion de Conclusion:** ∃x:[i(x) ∧ c(x)].
  - i(1) ∧ c(1) = V ∧ F = F
  - i(2) ∧ c(2) = F ∧ V = F
  - i(3) ∧ c(3) = F ∧ F = F
  - **Conclusion FALSA.**

**Respuesta:** El razonamiento es **INVALIDO**. Premisas verdaderas y conclusion falsa en el contraejemplo dado.

**Tips para el examen:**
- **Regla de oro:** Dos cuantificadores existenciales **nunca** se pueden particularizar en el mismo elemento. Cada ∃ introduce un testigo independiente.
- Cuando veas un razonamiento con dos premisas existenciales y ninguna universal que las conecte, sospecha inmediatamente de invalidez.
- Para el contraejemplo, basta un universo pequeno (2 o 3 elementos). La clave es que el "ingeniero invitado" y el "ingeniero que da clases" sean personas distintas.

**Errores comunes a evitar:**
- Particularizar ambos existenciales con la misma variable `a`, asumiendo que se refieren al mismo elemento. Esto es un error logico gravísimo.
- Creer que porque ambas premisas mencionan "ingenieros", las dos hablan del mismo ingeniero.
- Olvidar que en un contraejemplo **todas** las premisas deben ser verdaderas y **la conclusion** debe ser falsa.

---

### Ejercicio 13c — Bebes de Terapia, incubadora y respirador

**Enunciado:** "Todos los bebes de Terapia estaban en incubadora o con respirador. Los que estaban en incubadora eran prematuros y de bajo peso. Lucio, uno de los bebes de Terapia, tenia buen peso. Por lo tanto, al menos un bebe de Terapia estaba con respirador."

**Identificacion del tipo:** Razonamiento categorico con dos universales, un dato particular (constante individual Lucio), y conclusion existencial. Se resuelve con P.U., M.P., M.T., S.D. y G.E.

**Simbolizacion:**

- **Universo:** U = {x / x es bebe}
- **Diccionario de predicados:**
  - t(x): "x esta en Terapia"
  - i(x): "x esta en incubadora"
  - r(x): "x tiene respirador"
  - p(x): "x es prematuro"
  - b(x): "x es de bajo peso"
- **Constante individual:** L = Lucio
- **Forma simbolica:**
  - Premisa 1: ∀x:[t(x) → (i(x) ∨ r(x))]
  - Premisa 2: ∀x:[i(x) → (p(x) ∧ b(x))]
  - Premisa 3: t(L) ∧ ¬b(L)
  - Conclusion: ∃x:[t(x) ∧ r(x)]

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[t(x) → (i(x) ∨ r(x))] | Premisa |
| 2 | ∀x:[i(x) → (p(x) ∧ b(x))] | Premisa |
| 3 | t(L) ∧ ¬b(L) | Premisa (Lucio esta en Terapia y tiene buen peso, es decir, NO es de bajo peso) |
| 4 | t(L) → (i(L) ∨ r(L)) | P.U. sobre (1): la propiedad universal vale para todo bebe, en particular para Lucio. |
| 5 | t(L) | Simplificacion sobre (3): de `t(L) ∧ ¬b(L)` extraemos el primer componente. |
| 6 | i(L) ∨ r(L) | M.P. sobre (4) y (5): como `t(L) → (i(L) ∨ r(L))` y `t(L)` es verdadero, entonces `i(L) ∨ r(L)`. Es decir, Lucio esta en incubadora o con respirador. |
| 7 | i(L) → (p(L) ∧ b(L)) | P.U. sobre (2): la propiedad universal vale para Lucio. |
| 8 | ¬b(L) | Simplificacion sobre (3): de `t(L) ∧ ¬b(L)` extraemos el segundo componente. |
| 9 | ¬(p(L) ∧ b(L)) | De (8) por logica proposicional: si `¬b(L)` es verdadero, entonces la conjuncion `p(L) ∧ b(L)` es falsa. Formalmente: `¬b(L) → ¬b(L) ∨ ¬p(L)` (Adicion), y `¬b(L) ∨ ¬p(L) ≡ ¬(p(L) ∧ b(L))` (De Morgan). |
| 10 | ¬i(L) | M.T. sobre (7) y (9): si `i(L) → (p(L) ∧ b(L))` y `¬(p(L) ∧ b(L))`, entonces `¬i(L)`. Es decir, Lucio NO estaba en incubadora. |
| 11 | r(L) | S.D. sobre (6) y (10): de `i(L) ∨ r(L)` y `¬i(L)`, se deduce `r(L)`. Lucio tenia respirador. |
| 12 | t(L) ∧ r(L) | Conjuncion de (5) y (11): Lucio esta en Terapia y tiene respirador. |
| 13 | ∃x:[t(x) ∧ r(x)] | G.E. sobre (12): como Lucio cumple la propiedad, al menos un bebe de Terapia estaba con respirador. |

**Respuesta:** El razonamiento es **VALIDO**. La cadena logica es: Lucio esta en Terapia y tiene buen peso → como esta en Terapia, esta en incubadora o con respirador → como la incubadora implica bajo peso y Lucio tiene buen peso, no esta en incubadora → por lo tanto esta con respirador.

**Tips para el examen:**
- Cuando tenes una constante individual (nombre propio como "Lucio"), podes aplicar P.U. directamente a ese nombre sin necesidad de P.E.
- El paso 9 es el mas delicado: para negar una conjuncion basta negar uno de sus componentes. Si `¬b(L)`, entonces automaticamente `¬(p(L) ∧ b(L))`.
- La combinacion M.T. + S.D. es un patron muy frecuente: primero eliminas una opcion de la disyuncion (via M.T.) y luego usas S.D. para quedarte con la otra.

**Errores comunes a evitar:**
- Olvidar que "buen peso" se traduce como `¬b(L)` (negacion de "bajo peso"). Prestar atencion a las negaciones implicitas en el lenguaje natural.
- En el paso 9, algunos intentan aplicar De Morgan directamente sobre `¬b(L)`, lo cual no tiene sentido. Lo correcto es razonar que si un componente de una conjuncion es falso, toda la conjuncion es falsa.
- Olvidar el paso final de G.E.: la conclusion pide "al menos un bebe" (∃x), asi que hay que generalizar existencialmente.

---

### Ejercicio 13d — Matrices, filas iguales, inversibilidad y determinante

**Enunciado:** "Todas las matrices que tienen dos filas iguales no son inversibles. Las matrices inversibles tienen determinante distinto de cero. El determinante de la matriz A es cero. Por lo tanto, la matriz A tiene dos filas iguales."

**Identificacion del tipo:** Razonamiento categorico con universales y un dato particular. Se sospecha invalidez por la estructura logica (intento de afirmar el antecedente a partir del consecuente).

**Simbolizacion:**

- **Universo:** U = {x / x es matriz}
- **Diccionario de predicados:**
  - f(x): "x tiene dos filas iguales"
  - i(x): "x es inversible"
  - d(x): "el determinante de x es distinto de cero"
- **Constante individual:** A (la matriz A)
- **Forma simbolica:**
  - Premisa 1: ∀x:[f(x) → ¬i(x)]
  - Premisa 2: ∀x:[i(x) → d(x)]
  - Premisa 3: ¬d(A)
  - Conclusion: f(A)

**Resolucion paso a paso:**

**Paso 1 — Intentar demostracion y detectar el problema:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[f(x) → ¬i(x)] | Premisa |
| 2 | ∀x:[i(x) → d(x)] | Premisa |
| 3 | ¬d(A) | Premisa |
| 4 | i(A) → d(A) | P.U. sobre (2) |
| 5 | ¬i(A) | M.T. sobre (4) y (3): como `i(A) → d(A)` y `¬d(A)`, entonces `¬i(A)`. La matriz A no es inversible. |
| 6 | f(A) → ¬i(A) | P.U. sobre (1) |

**ALTO:** Ahora tenemos `f(A) → ¬i(A)` y `¬i(A)`. Queremos concluir `f(A)`, pero esto seria **afirmar el consecuente** (falacia). De `p → q` y `q` **NO** se puede deducir `p`.

La cadena logica va en una sola direccion: `f(A) → ¬i(A)`, pero no al reves. Que A no sea inversible no implica que tenga filas iguales; hay muchas razones por las que una matriz puede no ser inversible.

**Paso 2 — Contraejemplo:**

Consideremos la matriz A = [[1, 0], [0, 0]].

- **Premisa 1:** ∀x:[f(x) → ¬i(x)]. Toda matriz con dos filas iguales no es inversible. Esto es un teorema verdadero del algebra lineal. **VERDADERA.**
- **Premisa 2:** ∀x:[i(x) → d(x)]. Toda matriz inversible tiene determinante distinto de cero. Esto es un teorema del algebra lineal. **VERDADERA.**
- **Premisa 3:** ¬d(A). El determinante de A = 1·0 - 0·0 = 0. Por lo tanto, d(A) es falso y ¬d(A) es verdadero. **VERDADERA.**
- **Conclusion:** f(A). La matriz A = [[1, 0], [0, 0]] tiene la fila 1 = (1, 0) y la fila 2 = (0, 0). Las filas son **distintas**. **CONCLUSION FALSA.**

**Respuesta:** El razonamiento es **INVALIDO**. Las tres premisas son verdaderas pero la conclusion es falsa. La estructura logica comete la **falacia de afirmacion del consecuente**: de `f → ¬i` y `¬i` no se puede deducir `f`.

**Tips para el examen:**
- Antes de intentar una demostracion formal, analiza la estructura logica. Si las premisas te dan `A → B` y `B`, y la conclusion pide `A`, es inmediatamente sospechoso de falacia.
- La cadena deductiva maxima que se logra es: `¬d(A) → ¬i(A)` (por contrarreciproca de P2). Pero de la Premisa 1 solo obtenemos `f(A) → ¬i(A)`, cuya contrarreciproca es `i(A) → ¬f(A)`, que no sirve porque ya sabemos que `¬i(A)`.
- Para contraejemplos con matrices, basta pensar en matrices singulares (determinante 0) que no tengan filas repetidas.

**Errores comunes a evitar:**
- Confundir `f(A) → ¬i(A)` con `¬i(A) → f(A)`. El condicional NO es simetrico.
- Creer que como obtuvimos `¬i(A)` y la Premisa 1 dice `f → ¬i`, entonces podemos "ir para atras". Esto es exactamente la falacia de afirmacion del consecuente.
- Dar un contraejemplo abstracto sin verificar todas las premisas. Siempre verifica las tres premisas y la conclusion con valores concretos.

---

### Ejercicio 14 — Contraejemplo con multiplos

**Enunciado:** Mostrar con un contraejemplo que el siguiente razonamiento es invalido:
∀x:[d(x) → c(x)]; ∃x:[¬c(x) ∧ p(x)] ∴ ∀x:[c(x) ∨ p(x)]

**Identificacion del tipo:** Analisis de validez mediante contraejemplo numerico. Se necesita un universo finito donde ambas premisas sean verdaderas y la conclusion sea falsa.

**Resolucion paso a paso:**

**Paso 1 — Elegir el universo y la interpretacion:**

- U = {3, 4, 5}
- d(x): "x es multiplo de 4"
- c(x): "x es par"
- p(x): "x es multiplo de 5"

**Paso 2 — Evaluar los predicados para cada elemento:**

| Elemento | d(x): multiplo de 4 | c(x): es par | p(x): multiplo de 5 |
|----------|---------------------|--------------|----------------------|
| 3 | F | F | F |
| 4 | V | V | F |
| 5 | F | F | V |

**Paso 3 — Verificar Premisa 1: ∀x:[d(x) → c(x)]**

- x = 3: d(3) → c(3) = F → F = **V** (condicional con antecedente falso es verdadero)
- x = 4: d(4) → c(4) = V → V = **V**
- x = 5: d(5) → c(5) = F → F = **V**
- **Premisa 1: VERDADERA** (se cumple para todos los elementos)

**Paso 4 — Verificar Premisa 2: ∃x:[¬c(x) ∧ p(x)]**

- x = 3: ¬c(3) ∧ p(3) = V ∧ F = F
- x = 4: ¬c(4) ∧ p(4) = F ∧ F = F
- x = 5: ¬c(5) ∧ p(5) = V ∧ V = **V**
- **Premisa 2: VERDADERA** (se cumple al menos para x = 5: 5 no es par y es multiplo de 5)

**Paso 5 — Verificar Conclusion: ∀x:[c(x) ∨ p(x)]**

- x = 3: c(3) ∨ p(3) = F ∨ F = **F**
- Como x = 3 ya da falso, la universal es **FALSA**.
- (El 3 no es par ni multiplo de 5.)
- **Conclusion: FALSA**

**Respuesta:** El razonamiento es **INVALIDO**. Con U = {3, 4, 5} y la interpretacion dada (d = multiplo de 4, c = par, p = multiplo de 5), las dos premisas son verdaderas pero la conclusion es falsa. El elemento x = 3 es el que hace falsa la conclusion, ya que no es par ni multiplo de 5.

**Tips para el examen:**
- Para construir contraejemplos con cuantificadores, la estrategia es: (1) hacer falsa la conclusion primero (buscar un elemento que viole el universal de la conclusion), y (2) luego verificar que las premisas siguen siendo verdaderas.
- Los numeros pequenos (3, 4, 5 o 1, 2, 3) suelen ser suficientes para contraejemplos.
- Cuando la conclusion es un universal `∀x:[...]`, basta encontrar **un solo** elemento que la haga falsa.

**Errores comunes a evitar:**
- Olvidar verificar TODAS las premisas para TODOS los elementos del universo.
- Dar un contraejemplo donde alguna premisa sea falsa (eso no prueba invalidez).
- Usar un universo demasiado grande que complica la verificacion innecesariamente.

---

### Ejercicio 15 — Completar conclusion valida y demostrar

**Enunciado:** Dadas las premisas: ∀x:[p(x) ∨ q(x)]; ∀x:[p(x) → r(x)]; ¬r(a), completar la conclusion valida y demostrar: "por lo tanto ∃x: ........"

**Identificacion del tipo:** Ejercicio de completar la conclusion a partir de las premisas y luego demostrar formalmente. Involucra P.U., M.T., S.D. y G.E.

**Resolucion paso a paso:**

**Paso 1 — Analizar que se puede deducir:**

Tenemos `¬r(a)` como dato. La Premisa 2 dice `p(x) → r(x)`, asi que por contrarreciproca, `¬r(a) → ¬p(a)`. Es decir, `¬p(a)`. Luego, la Premisa 1 dice `p(a) ∨ q(a)`, y como `¬p(a)`, por S.D. obtenemos `q(a)`. Entonces la conclusion es **∃x: q(x)**.

**Paso 2 — Demostracion formal:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[p(x) ∨ q(x)] | Premisa |
| 2 | ∀x:[p(x) → r(x)] | Premisa |
| 3 | ¬r(a) | Premisa |
| 4 | p(a) → r(a) | P.U. sobre (2): la propiedad universal vale para el elemento `a` mencionado en la Premisa 3. |
| 5 | ¬p(a) | M.T. sobre (4) y (3): como `p(a) → r(a)` y `¬r(a)`, se deduce `¬p(a)`. Si `r` no se cumple para `a`, entonces `p` tampoco puede cumplirse (porque `p` implicaria `r`). |
| 6 | p(a) ∨ q(a) | P.U. sobre (1): la propiedad universal vale para `a`. |
| 7 | q(a) | S.D. sobre (6) y (5): de `p(a) ∨ q(a)` y `¬p(a)`, se deduce `q(a)`. Al descartar `p(a)`, la unica opcion es `q(a)`. |
| 8 | ∃x: q(x) | G.E. sobre (7): como `q(a)` es verdadero para `a`, existe al menos un elemento que cumple `q`. |

**Respuesta:** La conclusion valida es **∃x: q(x)**. La demostracion es valida por las reglas de inferencia indicadas.

**Tips para el examen:**
- Para "completar la conclusion", trabaja las premisas de atras hacia adelante: empieza por lo que sabes (¬r(a)) y ve encadenando reglas.
- El patron M.T. + S.D. es el patron tipico cuando tenes un condicional, la negacion del consecuente, y una disyuncion.
- Notar que `a` aparece como constante individual en la Premisa 3, lo cual permite aplicar P.U. a ese mismo `a` sin problemas.

**Errores comunes a evitar:**
- Intentar completar con `∃x: ¬r(x)` u otra expresion que no se sigue logicamente. Solo `q(a)` se puede derivar, no cualquier cosa.
- Olvidar el paso final de G.E. La pregunta pide una conclusion existencial, asi que hay que generalizar.

---

### Ejercicio 16a — Dos existenciales y una conjuncion

**Enunciado:** Analizar la validez de: ∃x:[p(x) ∨ q(x)]; ∃x:[¬q(x) ∧ r(x)] ∴ ∃x:[p(x) ∧ r(x)]

**Identificacion del tipo:** Razonamiento categorico con dos premisas existenciales. Al no haber universales que conecten los testigos, se sospecha invalidez.

**Resolucion paso a paso:**

**Paso 1 — Analisis de la estructura:**

Ambas premisas son existenciales. Si particularizamos:
- P.E. sobre Premisa 1: existe `a` tal que `p(a) ∨ q(a)`.
- P.E. sobre Premisa 2: existe `b` tal que `¬q(b) ∧ r(b)`.

Los testigos `a` y `b` son elementos distintos (no podemos asumir `a = b`). Sin una premisa universal que conecte las propiedades, no podemos deducir que exista un unico elemento que cumpla `p(x) ∧ r(x)`.

**Paso 2 — Contraejemplo:**

- U = {1, 2}
- Asignaciones:

| Elemento | p(x) | q(x) | r(x) |
|----------|-------|-------|-------|
| 1 | V | V | F |
| 2 | F | F | V |

- **Premisa 1:** ∃x:[p(x) ∨ q(x)].
  - x = 1: p(1) ∨ q(1) = V ∨ V = V. **VERDADERA.**
- **Premisa 2:** ∃x:[¬q(x) ∧ r(x)].
  - x = 2: ¬q(2) ∧ r(2) = V ∧ V = V. **VERDADERA.**
- **Conclusion:** ∃x:[p(x) ∧ r(x)].
  - x = 1: p(1) ∧ r(1) = V ∧ F = F
  - x = 2: p(2) ∧ r(2) = F ∧ V = F
  - **CONCLUSION FALSA.**

**Respuesta:** El razonamiento es **INVALIDO**. El contraejemplo muestra que las premisas pueden ser verdaderas mientras la conclusion es falsa. La razon fundamental es que los dos existenciales se refieren a elementos distintos.

**Tips para el examen:**
- Patron recurrente: dos premisas existenciales sin universal que las vincule = casi seguro invalido.
- Para el contraejemplo, distribuye las propiedades entre dos elementos de manera que cada uno satisfaga una premisa diferente, pero ninguno satisfaga la conclusion.

**Errores comunes a evitar:**
- Particularizar los dos existenciales con el mismo nombre de variable. Es el error mas grave y mas frecuente en este tipo de ejercicios.
- Olvidar verificar ambas premisas al construir el contraejemplo.

---

### Ejercicio 16b — Universal negada y conclusion existencial

**Enunciado:** Analizar la validez de: ∀x:¬[p(x) ∨ q(x)] ∴ ∃x:¬q(x)

**Identificacion del tipo:** Razonamiento categorico con una premisa universal y conclusion existencial. Se resuelve con P.U., De Morgan, Simplificacion y G.E.

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:¬[p(x) ∨ q(x)] | Premisa |
| 2 | ¬[p(a) ∨ q(a)] | P.U. sobre (1): elegimos cualquier elemento `a` del universo. La propiedad vale para todos, asi que vale para `a`. **Nota importante:** Esto es valido siempre que el universo sea no vacio, lo cual se asume por convencion en logica de predicados. |
| 3 | ¬p(a) ∧ ¬q(a) | De Morgan sobre (2): la negacion de una disyuncion es la conjuncion de las negaciones. `¬(A ∨ B) ≡ ¬A ∧ ¬B`. |
| 4 | ¬q(a) | Simplificacion sobre (3): de la conjuncion `¬p(a) ∧ ¬q(a)` extraemos el segundo componente. |
| 5 | ∃x:¬q(x) | G.E. sobre (4): como `¬q(a)` es verdadero para el elemento `a`, existe al menos un `x` tal que `¬q(x)`. |

**Respuesta:** El razonamiento es **VALIDO**. Si para todo `x` es falso que `p(x) ∨ q(x)`, entonces en particular `q(x)` es falso para todo `x`, y por lo tanto existe al menos un `x` con `¬q(x)`.

**Tips para el examen:**
- La ley de De Morgan para predicados es esencial: `¬(p ∨ q) ≡ ¬p ∧ ¬q`.
- Un universal siempre implica un existencial (asumiendo universo no vacio): si algo vale para todos, entonces vale para al menos uno.
- Este es un ejercicio "facil" pero sirve para confirmar que dominas la cadena P.U. → De Morgan → Simplif. → G.E.

**Errores comunes a evitar:**
- Olvidar aplicar De Morgan y dejar `¬[p(a) ∨ q(a)]` sin descomponer.
- Intentar aplicar G.E. directamente sobre la premisa universal sin antes particularizar. La secuencia correcta es P.U. primero, luego G.E. al final.

---

### Ejercicio 17 — Frutas, heladera, lavado y deliciosas

**Enunciado:** Premisas: "Todas las frutas que estan en la heladera estan lavadas. Algunas frutas no estan lavadas y son deliciosas." Determinar cual de las siguientes conclusiones es valida:
- c1: Algunas frutas estan en la heladera y son deliciosas
- c2: Todas las frutas que estan en la heladera son deliciosas
- c3: Algunas frutas no estan en la heladera y son deliciosas

**Identificacion del tipo:** Razonamiento categorico con un universal y un existencial. Se debe derivar la unica conclusion valida entre tres opciones y demostrarla formalmente.

**Simbolizacion:**

- **Universo:** U = {x / x es fruta}
- **Diccionario de predicados:**
  - h(x): "x esta en la heladera"
  - l(x): "x esta lavada"
  - d(x): "x es deliciosa"
- **Forma simbolica:**
  - Premisa 1: ∀x:[h(x) → l(x)]
  - Premisa 2: ∃x:[¬l(x) ∧ d(x)]
- **Conclusiones candidatas:**
  - c1: ∃x:[h(x) ∧ d(x)]
  - c2: ∀x:[h(x) → d(x)]
  - c3: ∃x:[¬h(x) ∧ d(x)]

**Resolucion paso a paso:**

**Paso 1 — Demostracion de c3 (la conclusion valida):**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[h(x) → l(x)] | Premisa |
| 2 | ∃x:[¬l(x) ∧ d(x)] | Premisa |
| 3 | ¬l(a) ∧ d(a) | P.E. sobre (2): existe una fruta `a` que no esta lavada y es deliciosa. Se introduce `a` como testigo nuevo. |
| 4 | h(a) → l(a) | P.U. sobre (1): la propiedad universal vale para la fruta `a` en particular. |
| 5 | ¬l(a) | Simplificacion sobre (3): extraemos que la fruta `a` no esta lavada. |
| 6 | ¬h(a) | M.T. sobre (4) y (5): como `h(a) → l(a)` y `¬l(a)`, entonces `¬h(a)`. Si la fruta `a` no esta lavada, no puede estar en la heladera (porque todas las de la heladera estan lavadas). |
| 7 | d(a) | Simplificacion sobre (3): extraemos que la fruta `a` es deliciosa. |
| 8 | ¬h(a) ∧ d(a) | Conjuncion de (6) y (7): la fruta `a` no esta en la heladera y es deliciosa. |
| 9 | ∃x:[¬h(x) ∧ d(x)] | G.E. sobre (8): existe al menos una fruta que no esta en la heladera y es deliciosa. |

**Paso 2 — Explicacion de por que c1 y c2 no son validas:**

- **c1 (∃x:[h(x) ∧ d(x)]) es invalida:** Las premisas nos dicen que alguna fruta no lavada es deliciosa, y que la fruta no lavada no puede estar en la heladera. Pero no dicen nada sobre si alguna fruta de la heladera es deliciosa. Contraejemplo: solo hay dos frutas; una esta en la heladera, lavada pero no deliciosa; la otra no esta en la heladera, no lavada y deliciosa.

- **c2 (∀x:[h(x) → d(x)]) es invalida:** Nada en las premisas conecta "estar en la heladera" con "ser deliciosa". Que esten lavadas no implica que sean deliciosas. Mismo contraejemplo que c1.

**Respuesta:** La unica conclusion valida es **c3: ∃x:[¬h(x) ∧ d(x)]**, es decir, "Algunas frutas no estan en la heladera y son deliciosas."

**Tips para el examen:**
- Este tipo de ejercicio (elegir entre varias conclusiones) aparece con frecuencia. La estrategia es: intenta demostrar cada conclusion; la que se derive formalmente de las premisas es la respuesta.
- El patron es el mismo que el Ejercicio 13a: P.E. → P.U. → M.T. → Simplif. → Conj. → G.E.
- La estructura `∀x:[A → B]` con `∃x:[¬B ∧ C]` siempre permite concluir `∃x:[¬A ∧ C]` via M.T.

**Errores comunes a evitar:**
- Elegir c1 porque "suena razonable" sin verificar formalmente.
- Confundir la direccion del condicional en la Premisa 1: dice h(x) → l(x), no l(x) → h(x).

---

### Ejercicio 18a — Venn: Modus Tollens con conjuntos

**Enunciado:** Analizar validez con diagramas de Venn: ∀x:[p(x) → q(x)]; ¬q(a) ∴ ¬p(a)

**Identificacion del tipo:** Razonamiento categorico que puede analizarse tanto por reglas de inferencia como por diagramas de Venn. El universal `∀x:[p(x) → q(x)]` se traduce como inclusion de conjuntos.

**Resolucion paso a paso:**

**Paso 1 — Traduccion a conjuntos:**

- `∀x:[p(x) → q(x)]` equivale a `P ⊆ Q` (el conjunto de elementos que cumplen `p` esta contenido en el conjunto de elementos que cumplen `q`).
- `¬q(a)` significa que `a ∉ Q` (el elemento `a` no pertenece al conjunto Q).

**Paso 2 — Analisis con diagrama de Venn:**

Dibujamos dos circulos: P dentro de Q (porque P ⊆ Q).

```
  ┌─────────────────────┐
  │         Q            │
  │   ┌─────────┐       │
  │   │    P    │       │
  │   │         │       │
  │   └─────────┘       │
  │                      │
  └─────────────────────┘
              a (fuera de Q)
```

Si `a` esta fuera de Q, como P esta contenido dentro de Q, `a` necesariamente esta fuera de P.

**Paso 3 — Verificacion por reglas de inferencia:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[p(x) → q(x)] | Premisa |
| 2 | ¬q(a) | Premisa |
| 3 | p(a) → q(a) | P.U. sobre (1) |
| 4 | ¬p(a) | M.T. sobre (3) y (2) |

**Respuesta:** El razonamiento es **VALIDO**. Es una instancia directa de Modus Tollens. En terminos de conjuntos: si P ⊆ Q y a ∉ Q, entonces a ∉ P.

**Tips para el examen:**
- La traduccion `∀x:[p(x) → q(x)]` ↔ `P ⊆ Q` es fundamental para los diagramas de Venn.
- Este es el caso mas basico de Modus Tollens. Aparece como componente en ejercicios mas complejos.

**Errores comunes a evitar:**
- Dibujar P y Q como conjuntos que se intersectan en vez de P ⊆ Q. La inclusion es estricta segun el universal.
- Confundir la direccion: de `P ⊆ Q` y `a ∈ Q` **no** se puede concluir `a ∈ P` (eso seria afirmacion del consecuente).

---

### Ejercicio 18b — Venn: Universal con existencial y disyuncion

**Enunciado:** Analizar validez con diagramas de Venn: ∀x:[a(x) ∨ b(x)]; ∃x:[c(x) ∧ ¬a(x)] ∴ ∃x:[c(x) ∧ b(x)]

**Identificacion del tipo:** Razonamiento categorico con un universal que establece cobertura total (union = universo) y un existencial. Se analiza con diagramas de Venn y se confirma con reglas de inferencia.

**Resolucion paso a paso:**

**Paso 1 — Traduccion a conjuntos:**

- `∀x:[a(x) ∨ b(x)]` equivale a `A ∪ B = U` (todo elemento del universo pertenece a A o a B o a ambos).
- `∃x:[c(x) ∧ ¬a(x)]` equivale a `C ∩ Ā ≠ ∅` (existe al menos un elemento que esta en C pero no en A).
- La conclusion `∃x:[c(x) ∧ b(x)]` equivale a `C ∩ B ≠ ∅`.

**Paso 2 — Analisis con diagrama de Venn:**

```
  ┌─────────────────────────────┐  U
  │     A          B            │
  │  ┌──────┬──────────┐       │
  │  │      │          │       │
  │  │      │   ●(en C │       │
  │  │      │  y en B) │       │
  │  └──────┴──────────┘       │
  │  (A∪B cubre todo U)        │
  └─────────────────────────────┘
```

Como A ∪ B = U, todo elemento pertenece a A o a B. Si existe un elemento en C ∩ Ā (esta en C pero no en A), ese elemento **debe** estar en B (porque A ∪ B = U y no esta en A, entonces esta en B). Por lo tanto, ese elemento esta en C ∩ B, lo que prueba que C ∩ B ≠ ∅.

**Paso 3 — Verificacion por reglas de inferencia:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ∀x:[a(x) ∨ b(x)] | Premisa |
| 2 | ∃x:[c(x) ∧ ¬a(x)] | Premisa |
| 3 | c(e) ∧ ¬a(e) | P.E. sobre (2): existe un elemento `e` en C que no esta en A. |
| 4 | a(e) ∨ b(e) | P.U. sobre (1): la cobertura universal vale para `e`. |
| 5 | ¬a(e) | Simplificacion sobre (3): `e` no esta en A. |
| 6 | b(e) | S.D. sobre (4) y (5): de `a(e) ∨ b(e)` y `¬a(e)`, se deduce `b(e)`. Como `e` no esta en A y todo elemento esta en A o B, entonces `e` esta en B. |
| 7 | c(e) | Simplificacion sobre (3): `e` esta en C. |
| 8 | c(e) ∧ b(e) | Conjuncion de (7) y (6): `e` esta en C y en B. |
| 9 | ∃x:[c(x) ∧ b(x)] | G.E. sobre (8): existe al menos un elemento en C ∩ B. |

**Respuesta:** El razonamiento es **VALIDO**. Tanto el diagrama de Venn como la demostracion formal confirman que si A ∪ B cubre todo el universo y existe un elemento en C fuera de A, ese elemento necesariamente esta en B (y sigue estando en C).

**Tips para el examen:**
- `∀x:[a(x) ∨ b(x)]` se lee como "A y B cubren todo el universo". Esto es diferente de `∀x:[a(x) → b(x)]` (que seria A ⊆ B).
- El silogismo disyuntivo (S.D.) es la herramienta natural cuando tenes una disyuncion y la negacion de uno de los disyuntos.
- En el diagrama de Venn, como A ∪ B = U, no hay region fuera de A y B. Todo punto del universo esta dentro de al menos uno de los dos.

**Errores comunes a evitar:**
- Confundir `∀x:[a(x) ∨ b(x)]` (cobertura total) con `∀x:[a(x) ∧ b(x)]` (interseccion total, que es mucho mas fuerte).
- En el diagrama de Venn, dibujar regiones fuera de A ∪ B, lo cual contradice la Premisa 1.

---

## TIER 2 — PRIORIDAD MEDIA

---

### Ejercicio 10a — Aguinaldo, sueldo, deuda y pasajes (Dilema Constructivo)

**Enunciado:** "Si me pagan el aguinaldo hoy, pagare la deuda. Si me pagan el sueldo hoy, comprare los pasajes. Me pagan el sueldo o el aguinaldo hoy. Por lo tanto pagare la deuda o comprare los pasajes."

**Identificacion del tipo:** Razonamiento proposicional (sin cuantificadores). Se resuelve reconociendo la estructura de Dilema Constructivo, o bien por demostracion paso a paso.

**Simbolizacion:**

- a: "me pagan el aguinaldo hoy"
- s: "me pagan el sueldo hoy"
- d: "pago la deuda"
- p: "compro los pasajes"
- **Forma simbolica:** a → d; s → p; s ∨ a ∴ d ∨ p

**Resolucion paso a paso:**

**Metodo 1 — Reconocimiento directo (Dilema Constructivo):**

La regla del Dilema Constructivo establece que:
- Si `p → q` y `r → s` y `p ∨ r`, entonces `q ∨ s`.

Nuestras premisas tienen exactamente esta estructura:
- `a → d` (si aguinaldo, entonces deuda)
- `s → p` (si sueldo, entonces pasajes)
- `s ∨ a` (equivalente a `a ∨ s` por conmutatividad de la disyuncion)

Por lo tanto: `d ∨ p`.

**Metodo 2 — Demostracion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | a → d | Premisa |
| 2 | s → p | Premisa |
| 3 | s ∨ a | Premisa |
| 4 | a ∨ s | Conmutatividad de la disyuncion sobre (3) |

Analisis por casos sobre (4):

**Caso 1:** Supongamos `a` verdadero.
- De (1) y `a`, por M.P.: `d`.
- De `d`, por Adicion: `d ∨ p`.

**Caso 2:** Supongamos `s` verdadero.
- De (2) y `s`, por M.P.: `p`.
- De `p`, por Adicion: `d ∨ p`.

En ambos casos se obtiene `d ∨ p`. Por lo tanto, la conclusion es valida.

| 5 | d ∨ p | D.C. sobre (1), (2) y (4): Dilema Constructivo |

**Respuesta:** El razonamiento es **VALIDO** por Dilema Constructivo.

**Tips para el examen:**
- El Dilema Constructivo es una regla poderosa que ahorra muchos pasos. Aprendela de memoria: `(p→q) ∧ (r→s) ∧ (p∨r) ⊢ q∨s`.
- La disyuncion es conmutativa: `s ∨ a ≡ a ∨ s`. No te confundas si el orden no coincide exactamente con la regla.
- Este ejercicio es proposicional (no tiene cuantificadores), pero aparece en la seccion de razonamientos como repaso.

**Errores comunes a evitar:**
- No reconocer la estructura del Dilema Constructivo y hacer la demostracion de forma innecesariamente larga.
- Confundir Dilema Constructivo con Dilema Destructivo (que usa las negaciones de los consecuentes).

---

### Ejercicio 10b — Lluvia, viento, avion y malestar

**Enunciado:** "Si no llueve y no hay viento entonces vuelo en el avion. Siempre que llueve me siento mal. Ayer no vole en el avion y me senti bien. Por lo tanto, ayer estuvo ventoso."

**Identificacion del tipo:** Razonamiento proposicional. Requiere contrarreciproca, Modus Tollens, De Morgan y Silogismo Disyuntivo.

**Simbolizacion:**

- l: "llueve"
- v: "hay viento"
- a: "vuelo en el avion"
- m: "me siento mal"
- **Forma simbolica:**
  - Premisa 1: (¬l ∧ ¬v) → a
  - Premisa 2: l → m
  - Premisa 3: ¬a ∧ ¬m
  - Conclusion: v

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | (¬l ∧ ¬v) → a | Premisa |
| 2 | l → m | Premisa |
| 3 | ¬a ∧ ¬m | Premisa |
| 4 | ¬m | Simplificacion sobre (3): me senti bien, es decir, no me senti mal. |
| 5 | ¬l | M.T. sobre (2) y (4): como `l → m` y `¬m`, entonces `¬l`. Si me senti bien (no me senti mal), entonces no llovio (porque si hubiera llovido, me habria sentido mal). |
| 6 | ¬a | Simplificacion sobre (3): no vole en el avion. |
| 7 | ¬(¬l ∧ ¬v) | M.T. sobre (1) y (6): como `(¬l ∧ ¬v) → a` y `¬a`, entonces `¬(¬l ∧ ¬v)`. Si no vole, entonces no se dio la condicion de "no llueve y no hay viento". |
| 8 | l ∨ v | De Morgan sobre (7): `¬(¬l ∧ ¬v) ≡ ¬(¬l) ∨ ¬(¬v) ≡ l ∨ v`. Es decir, llovio o hubo viento. |
| 9 | v | S.D. sobre (8) y (5): de `l ∨ v` y `¬l`, se deduce `v`. Como no llovio (paso 5) y "llovio o hubo viento" (paso 8), la unica opcion es que hubo viento. |

**Respuesta:** El razonamiento es **VALIDO**. La cadena logica completa es: no me senti mal → no llovio (por contrarreciproca de P2). No vole → no se cumplio "no llueve y no viento" (por contrarreciproca de P1). Esto da "llovio o hubo viento". Como no llovio, hubo viento.

**Tips para el examen:**
- La contrarreciproca (implicita en M.T.) es la herramienta principal para "ir hacia atras" en una cadena de implicaciones.
- De Morgan transforma `¬(¬l ∧ ¬v)` en `l ∨ v`. Recordar la regla: negar una conjuncion da disyuncion de negaciones, y la doble negacion se cancela.
- El S.D. final es el "cierre" tipico: tenes una disyuncion y podes eliminar una opcion.

**Errores comunes a evitar:**
- Olvidar aplicar De Morgan en el paso 7→8. Dejar `¬(¬l ∧ ¬v)` sin simplificar no permite avanzar.
- Aplicar mal De Morgan: `¬(¬l ∧ ¬v)` NO es `¬l ∨ ¬v` sino `l ∨ v` (hay doble negacion).
- Intentar resolver "directamente" sin descomponer la Premisa 3 primero.

---

### Ejercicio 10c — Lluvia, cine, pochoclo y helado (Falacia)

**Enunciado:** "Si llueve, Pablo va al cine. Siempre que Pablo va al cine, compra pochoclo o helado. Pablo compra pochoclo. Por lo tanto, llueve."

**Identificacion del tipo:** Razonamiento proposicional. Se sospecha invalidez porque la conclusion intenta deducir el antecedente de una cadena de condicionales a partir de informacion sobre el consecuente.

**Simbolizacion:**

- l: "llueve"
- c: "Pablo va al cine"
- p: "Pablo compra pochoclo"
- h: "Pablo compra helado"
- **Forma simbolica:**
  - Premisa 1: l → c
  - Premisa 2: c → (p ∨ h)
  - Premisa 3: p
  - Conclusion: l

**Resolucion paso a paso:**

**Paso 1 — Analisis de la estructura logica:**

Por Silogismo Hipotetico, de las Premisas 1 y 2: `l → (p ∨ h)`.
Es decir, la cadena es: `l → c → (p ∨ h)`.

La Premisa 3 dice `p`, de donde por Adicion: `p ∨ h`.
Pero tener `p ∨ h` y `l → (p ∨ h)` **no** permite concluir `l`.
Esto es la **falacia de afirmacion del consecuente**: de `A → B` y `B`, no se puede deducir `A`.

**Paso 2 — Contraejemplo:**

- l = F (no llueve)
- c = V (Pablo va al cine de todos modos, por otra razon)
- p = V (Pablo compra pochoclo)
- h = F (no compra helado)

Verificacion:
- Premisa 1: l → c = F → V = **V** (el condicional con antecedente falso es verdadero).
- Premisa 2: c → (p ∨ h) = V → (V ∨ F) = V → V = **V**.
- Premisa 3: p = **V**.
- Conclusion: l = **F**.

**Alternativa aun mas clara:** Pablo puede ir al cine sin que llueva (va porque quiere, no solo cuando llueve), y compra pochoclo igualmente.

**Respuesta:** El razonamiento es **INVALIDO**. Es una instancia de la **falacia de afirmacion del consecuente**. Que Pablo compre pochoclo no implica que haya llovido; puede haber ido al cine y comprado pochoclo por cualquier otra razon.

**Tips para el examen:**
- Siempre que la conclusion sea el antecedente de un condicional y lo que sabes es el consecuente (o algo derivado de el), sospecha de falacia de afirmacion del consecuente.
- El contraejemplo mas simple para romper `l → c` es hacer `l = F, c = V`: Pablo va al cine sin que llueva.
- Pablo compra pochoclo (p = V) por su cuenta; esto satisface trivialmente `p ∨ h` sin necesidad de que llueva.

**Errores comunes a evitar:**
- Razonar "al reves": "como p es verdadero, p ∨ h es verdadero, y como c → (p ∨ h), entonces c es verdadero, y como l → c, entonces l es verdadero." Esto es una cadena de falacias.
- Confundir el condicional con el bicondicional: `l → c` no significa `l ↔ c`.

---

### Ejercicio 10d — Planeta Kamino, Archivos y borrado

**Enunciado:** "El planeta Kamino no figura en los Archivos. Si un planeta no figura en los Archivos, es porque no existe o alguien lo borro. El planeta Kamino existe. Por lo tanto, alguien lo debe haber borrado del Archivo."

**Identificacion del tipo:** Razonamiento proposicional. Se resuelve con Modus Ponens y Silogismo Disyuntivo.

**Simbolizacion:**

- a: "Kamino figura en los Archivos"
- e: "Kamino existe"
- b: "alguien borro a Kamino del Archivo"
- **Forma simbolica:**
  - Premisa 1: ¬a
  - Premisa 2: ¬a → (¬e ∨ b)
  - Premisa 3: e
  - Conclusion: b

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ¬a | Premisa: Kamino no figura en los Archivos. |
| 2 | ¬a → (¬e ∨ b) | Premisa: si no figura, es porque no existe o alguien lo borro. |
| 3 | e | Premisa: Kamino existe. |
| 4 | ¬e ∨ b | M.P. sobre (2) y (1): como `¬a → (¬e ∨ b)` y `¬a`, entonces `¬e ∨ b`. Es decir, Kamino no existe o alguien lo borro. |
| 5 | ¬¬e | Doble negacion sobre (3): de `e` obtenemos `¬¬e`. Esto es necesario para aplicar S.D. con `¬e ∨ b`. |
| 6 | b | S.D. sobre (4) y (5): de `¬e ∨ b` y `¬¬e` (es decir, descartamos `¬e`), se deduce `b`. Como Kamino SI existe, la opcion "no existe" se elimina, y queda "alguien lo borro". |

**Respuesta:** El razonamiento es **VALIDO**. La logica es impecable: Kamino no esta en los Archivos, pero existe; como la unica explicacion de la ausencia es que no exista o que lo borraron, y si existe, entonces alguien lo borro.

**Tips para el examen:**
- El paso de doble negacion (`e → ¬¬e`) es necesario formalmente para aplicar S.D. sobre `¬e ∨ b`. En la practica, muchos profesores aceptan "de `e` descartamos `¬e`" directamente.
- Este ejercicio es un M.P. seguido de un S.D., un patron muy limpio y directo.
- Es un buen ejemplo de como la logica formal modela razonamientos de la vida real (o ficticia, en este caso de Star Wars).

**Errores comunes a evitar:**
- Olvidar el paso de doble negacion. Si tenes `¬e ∨ b` y `e`, necesitas formalmente pasar a `¬¬e` para poder eliminar `¬e` del disyunto.
- Simbolizar mal la Premisa 2: "no figura en los Archivos" ya esta negado, asi que la premisa es `¬a → (¬e ∨ b)`, no `a → (¬e ∨ b)`.

---

### Ejercicio 11 — Validez por condicional asociado

**Enunciado:** Determinar la validez de los siguientes razonamientos por el metodo del condicional asociado:

#### Ejercicio 11a — ¬p; q→t∨r; t→p ∴ q→r

**Identificacion del tipo:** Razonamiento proposicional. Se verifica validez por demostracion directa (asumiendo premisas y la hipotesis del condicional de la conclusion).

**Resolucion paso a paso:**

Para demostrar `q → r`, asumimos `q` como hipotesis adicional y derivamos `r`.

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | ¬p | Premisa |
| 2 | q → (t ∨ r) | Premisa |
| 3 | t → p | Premisa |
| 4 | q | Hipotesis (asumimos `q` para demostrar `q → r`) |
| 5 | t ∨ r | M.P. sobre (2) y (4): como `q → (t ∨ r)` y `q`, entonces `t ∨ r`. |
| 6 | ¬t | M.T. sobre (3) y (1): como `t → p` y `¬p`, entonces `¬t`. |
| 7 | r | S.D. sobre (5) y (6): de `t ∨ r` y `¬t`, se deduce `r`. |

Como pudimos derivar `r` asumiendo `q`, la conclusion `q → r` es valida.

**Respuesta:** **VALIDO.**

**Tips para el examen:**
- Para demostrar que la conclusion es un condicional `q → r`, se asume `q` como hipotesis y se intenta derivar `r`.
- El patron M.T. + S.D. aparece de nuevo: `t → p` y `¬p` dan `¬t`, y luego `t ∨ r` con `¬t` da `r`.

---

#### Ejercicio 11b — (p∧q)→r; ¬r∨t; ¬t ∴ ¬p

**Identificacion del tipo:** Razonamiento proposicional. Se sospecha invalidez.

**Resolucion paso a paso:**

**Paso 1 — Intentar demostracion:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | (p ∧ q) → r | Premisa |
| 2 | ¬r ∨ t | Premisa |
| 3 | ¬t | Premisa |
| 4 | ¬r | S.D. sobre (2) y (3): de `¬r ∨ t` y `¬t`, se deduce `¬r`. |
| 5 | ¬(p ∧ q) | M.T. sobre (1) y (4): como `(p ∧ q) → r` y `¬r`, entonces `¬(p ∧ q)`. |
| 6 | ¬p ∨ ¬q | De Morgan sobre (5): `¬(p ∧ q) ≡ ¬p ∨ ¬q`. |

**ALTO:** De `¬p ∨ ¬q` no podemos concluir `¬p` (podria ser `¬q` el verdadero).

**Paso 2 — Contraejemplo:**

- p = V, q = F, r = F, t = F

Verificacion:
- Premisa 1: (p ∧ q) → r = (V ∧ F) → F = F → F = **V**.
- Premisa 2: ¬r ∨ t = V ∨ F = **V**.
- Premisa 3: ¬t = ¬F = **V**.
- Conclusion: ¬p = ¬V = **F**.

**Respuesta:** **INVALIDO.** Contraejemplo: p = V, q = F, r = F, t = F. Las tres premisas son verdaderas, pero la conclusion ¬p es falsa. El problema es que de `¬(p ∧ q)` solo se deduce `¬p ∨ ¬q`, y podria ser `q` el falso, no `p`.

**Errores comunes a evitar:**
- Creer que de `¬(p ∧ q)` se puede deducir `¬p`. La negacion de una conjuncion es una disyuncion de negaciones (De Morgan), no la negacion de un solo componente.

---

#### Ejercicio 11c — a→b; ¬b∨¬c; d→a∨c ∴ ¬d

**Identificacion del tipo:** Razonamiento proposicional. Se sospecha invalidez.

**Resolucion paso a paso:**

**Paso 1 — Intentar demostracion:**

De las premisas:
- a → b (Premisa 1)
- ¬b ∨ ¬c (Premisa 2)
- d → (a ∨ c) (Premisa 3)

Para probar ¬d, necesitariamos ¬(a ∨ c), es decir, ¬a ∧ ¬c (por M.T. sobre P3). Pero de P1 y P2 no se obtiene eso necesariamente.

**Paso 2 — Contraejemplo:**

- a = V, b = V, c = F, d = V

Verificacion:
- Premisa 1: a → b = V → V = **V**.
- Premisa 2: ¬b ∨ ¬c = F ∨ V = **V**.
- Premisa 3: d → (a ∨ c) = V → (V ∨ F) = V → V = **V**.
- Conclusion: ¬d = ¬V = **F**.

**Respuesta:** **INVALIDO.** Contraejemplo: a = V, b = V, c = F, d = V. Todas las premisas verdaderas, conclusion falsa. El problema es que si a = V y b = V, las primeras dos premisas se satisfacen, y d puede ser verdadero si a ∨ c es verdadero (lo cual ocurre por a = V).

---

#### Ejercicio 11d — p→q∨r; p∨(¬t∨s); ¬q∧¬s; s→¬t ∴ ¬t

**Identificacion del tipo:** Razonamiento proposicional. Se sospecha invalidez.

**Resolucion paso a paso:**

**Paso 1 — Intentar demostracion:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | p → (q ∨ r) | Premisa |
| 2 | p ∨ (¬t ∨ s) | Premisa |
| 3 | ¬q ∧ ¬s | Premisa |
| 4 | s → ¬t | Premisa |
| 5 | ¬q | Simplificacion sobre (3) |
| 6 | ¬s | Simplificacion sobre (3) |

De P4 y ¬s: no podemos aplicar M.P. (necesitariamos s, no ¬s). La contrarreciproca de P4 es `t → ¬s`, pero ya sabemos ¬s, lo cual no nos da informacion sobre t.

De P2: `p ∨ (¬t ∨ s)`. Con ¬s, no podemos simplificar directamente porque ¬s no es la negacion de todo el segundo disyunto.

**Paso 2 — Contraejemplo:**

- p = V, q = F, r = V, s = F, t = V

Verificacion:
- Premisa 1: p → (q ∨ r) = V → (F ∨ V) = V → V = **V**.
- Premisa 2: p ∨ (¬t ∨ s) = V ∨ (F ∨ F) = V ∨ F = **V**.
- Premisa 3: ¬q ∧ ¬s = V ∧ V = **V**.
- Premisa 4: s → ¬t = F → F = **V** (antecedente falso, condicional verdadero).
- Conclusion: ¬t = ¬V = **F**.

**Respuesta:** **INVALIDO.** Contraejemplo: p = V, q = F, r = V, s = F, t = V. Las cuatro premisas son verdaderas pero la conclusion ¬t es falsa.

**Tips para el examen (Ejercicios 11a-d en general):**
- Para verificar validez por condicional asociado, el razonamiento `P1; P2; ...; Pn ∴ C` es valido si y solo si `(P1 ∧ P2 ∧ ... ∧ Pn) → C` es una tautologia.
- Si sospechas invalidez, busca un contraejemplo asignando V/F a las variables de modo que todas las premisas sean verdaderas y la conclusion falsa.
- Tip practico: empieza asignando valores que hagan la conclusion **falsa** y luego verifica si podes hacer todas las premisas verdaderas con esa asignacion.

**Errores comunes a evitar:**
- Buscar contraejemplos "al azar" sin estrategia. Siempre empieza fijando la conclusion como falsa.
- Olvidar verificar TODAS las premisas en el contraejemplo. Si alguna premisa es falsa, el contraejemplo no sirve.

---

### Ejercicio 12 — El jefe, el suplicio y el asesinato

**Enunciado:** "Si el iba solo y desarmado, su jefe no lo mataria. Para suplicarle perdon era necesario ir desarmado. Le suplico pero igualmente su jefe lo mato." ¿Por que lo mato?

**Identificacion del tipo:** Razonamiento proposicional. Se trata de deducir informacion a partir de las premisas para explicar por que ocurrio el hecho.

**Simbolizacion:**

- s: "va solo"
- d: "va desarmado"
- m: "su jefe lo mata"
- p: "le suplica perdon"
- **Forma simbolica:**
  - Premisa 1: (s ∧ d) → ¬m
  - Premisa 2: p → d (suplicar perdon requiere ir desarmado; es condicion necesaria)
  - Premisa 3: p ∧ m (le suplico y lo mato)

**Resolucion paso a paso:**

| Paso | Expresion | Justificacion |
|------|-----------|---------------|
| 1 | (s ∧ d) → ¬m | Premisa |
| 2 | p → d | Premisa |
| 3 | p ∧ m | Premisa |
| 4 | p | Simplificacion sobre (3): le suplico perdon. |
| 5 | m | Simplificacion sobre (3): su jefe lo mato. |
| 6 | d | M.P. sobre (2) y (4): como `p → d` y `p`, entonces `d`. Si le suplico perdon, fue desarmado (era condicion necesaria). |
| 7 | ¬¬m | Doble negacion sobre (5): equivalente a `m`, necesario formalmente para M.T. |
| 8 | ¬(s ∧ d) | M.T. sobre (1) y (7): como `(s ∧ d) → ¬m` y `¬(¬m)` (es decir, `m`), entonces `¬(s ∧ d)`. No se cumplio la condicion de ir solo y desarmado. |
| 9 | ¬s ∨ ¬d | De Morgan sobre (8): `¬(s ∧ d) ≡ ¬s ∨ ¬d`. O no fue solo, o no fue desarmado. |
| 10 | ¬¬d | Doble negacion sobre (6): `d` equivale a `¬¬d`. |
| 11 | ¬s | S.D. sobre (9) y (10): de `¬s ∨ ¬d` y `¬¬d` (descartamos `¬d`), se deduce `¬s`. |

**Respuesta:** **Lo mato porque no fue solo.** La deduccion muestra que `s` es falso: el no iba solo. Aunque fue desarmado (porque le suplico perdon, lo cual requeria ir desarmado), no fue **solo**. La Premisa 1 decia que si iba solo **Y** desarmado, no lo matarian. Como no iba solo (probablemente lo acompanaba alguien amenazante), el jefe lo mato de todos modos.

**Tips para el examen:**
- Este tipo de ejercicio pide "explicar por que" algo ocurrio. La respuesta es el valor de verdad de una variable proposicional que se deduce de las premisas.
- La cadena es: suplico → fue desarmado; lo mataron → no se cumplio (solo ∧ desarmado); como fue desarmado → no fue solo.
- Presta atencion a la frase "era necesario": `p → d` significa que ir desarmado es **necesario** para suplicar (no suficiente).

**Errores comunes a evitar:**
- Simbolizar "para suplicar era necesario ir desarmado" como `d → p` (eso seria "ir desarmado es suficiente para suplicar"). Lo correcto es `p → d` ("si suplica, entonces fue desarmado").
- Olvidar la doble negacion en los pasos 7 y 10. Formalmente es necesaria para que M.T. y S.D. funcionen.
- Responder vagamente "porque el jefe quiso". La pregunta pide una deduccion logica, no una opinion.

---

## Resumen de patrones y estrategias

### Patron 1: Universal + Existencial → Conclusion existencial
**Estructura:** ∀x:[A(x) → B(x)]; ∃x:[¬B(x) ∧ C(x)] ∴ ∃x:[¬A(x) ∧ C(x)]
**Estrategia:** P.E. primero → P.U. al mismo elemento → M.T. → Simplif. → Conj. → G.E.
**Ejercicios:** 13a, 13c, 15, 16b, 17

### Patron 2: Dos existenciales sin universal conector → INVALIDO
**Estructura:** ∃x:[...]; ∃x:[...] ∴ ∃x:[...]
**Estrategia:** Contraejemplo con elementos distintos para cada existencial.
**Ejercicios:** 13b, 16a

### Patron 3: Falacia de afirmacion del consecuente
**Estructura:** A → B; B ∴ A (INVALIDO)
**Estrategia:** Contraejemplo donde A es falso y B es verdadero.
**Ejercicios:** 13d, 10c

### Patron 4: M.P. + S.D.
**Estructura:** Premisas tipo condicional y disyuncion combinadas.
**Estrategia:** Encadenar M.P. y M.T. para descartar opciones, luego S.D.
**Ejercicios:** 10b, 10d (Kamino), 12

### Patron 5: Dilema Constructivo
**Estructura:** (p→q) ∧ (r→s) ∧ (p∨r) ∴ q∨s
**Ejercicios:** 10a

---

## Checklist pre-examen

- [ ] Se aplicar P.E. antes que P.U. cuando hay existenciales.
- [ ] Nunca particularizo dos existenciales en el mismo elemento.
- [ ] Reconozco la falacia de afirmacion del consecuente.
- [ ] Se construir contraejemplos con universos pequenos (2-3 elementos).
- [ ] Domino las reglas: M.P., M.T., S.D., S.H., De Morgan, Simplificacion, Conjuncion, Adicion.
- [ ] Para diagramas de Venn: `∀x:[p→q]` es P ⊆ Q, y `∀x:[p∨q]` es P ∪ Q = U.
- [ ] Siempre cierro demostraciones con G.E. cuando la conclusion es existencial.
- [ ] Verifico TODAS las premisas y la conclusion en un contraejemplo.
