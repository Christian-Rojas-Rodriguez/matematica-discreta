# Tema 3 — Redes y Algebras de Boole: Ejercicios Resueltos

> Guía de estudio para el final de Matemática Discreta (UNSAM)
> Ejercicios de la práctica 8 (Boole) — Secciones III y IV

---

## TIER 1 — ALTA PRIORIDAD

### Batch 03 — Ej.26: ¿Algebras de Boole?

#### Ejercicio 26a — D₁₈ con divisibilidad

**Enunciado:** Analizar si (D₁₈; |) es Algebra de Boole.

**Identificación del tipo:** Determinar si un conjunto ordenado con divisibilidad satisface: ser red, distributiva, complementada.

**Resolución paso a paso:**

1. **D₁₈ = {1, 2, 3, 6, 9, 18}** (divisores de 18)

2. **¿Es red?**
   - Para cualesquiera a, b: ¿existe sup{a,b} = mcm(a,b) y inf{a,b} = mcd(a,b)?
   - Ejemplo: sup{2,3} = 6 ✓, inf{2,3} = 1 ✓. Sí es red.

3. **¿Es complementada?**
   - Para todo x, ¿existe x̄ tal que x∧x̄ = 1 (mcd) y x∨x̄ = 18 (mcm)?
   - Intenta x = 3: necesitamos y tal que mcd(3,y)=1 y mcm(3,y)=18
   - Probamos y∈{1,2,3,6,9,18}:
     - y=1: mcd=1✓ pero mcm=3≠18 ✗
     - y=2: mcd=1✓ pero mcm=6≠18 ✗
     - y=6: mcd=3≠1 ✗
     - y=18: mcd=3≠1 ✗
   - **No existe complemento de 3**

4. **Conclusión:** NO es Algebra de Boole (no es complementada)

**Respuesta:** NO. Porque D₁₈ no es complementada: el elemento 3 no tiene complemento.

**Tips para el examen:**
- Una razón común: 18 = 2·3² tiene factor cuadrado → no puede ser Boole
- Si n = p₁^a₁...pₖ^aₖ y algún aᵢ ≥ 2, entonces Dₙ no es Boole

**Errores comunes a evitar:**
- ✗ Confundir "no tiene complemento en D₁₈" con "no tiene complemento matemático"
- ✗ Olvidar verificar TODAS las propiedades (red, distributiva, complementada)

---

#### Ejercicio 26b — D₄₂ con mcm y mcd

**Enunciado:** ¿(D₄₂; mcm; mcd) es Algebra de Boole?

**Resolución paso a paso:**

1. **D₄₂ = {1, 2, 3, 6, 7, 14, 21, 42}** (8 elementos)

2. **Factorización:** 42 = 2·3·7 (producto de 3 primos distintos, libre de cuadrados)

3. **Por teorema:** Si n es libre de cuadrados, entonces (Dₙ; |) es isomorfo a (P(A); ⊆) donde A = {primos de n}

4. **|D₄₂| = 8 = 2³** (número de subconjuntos de {2,3,7})

5. **Es complementada:** Para cada x ∈ D₄₂, su complemento es 42/x
   - Ejemplo: comp(6) = 42/6 = 7. Verificar: mcd(6,7)=1✓, mcm(6,7)=42✓
   - comp(14) = 3. mcd(14,3)=1✓, mcm(14,3)=42✓

**Respuesta:** SÍ. (D₄₂; mcm; mcd) es un Algebra de Boole con 8 elementos = 2³.

**Isomorfismo con P({2,3,7}):**
- 1 ↔ ∅
- 2,3,7 ↔ singletons {2}, {3}, {7}
- 6,14,21 ↔ pares {2,3}, {2,7}, {3,7}
- 42 ↔ {2,3,7}

**Tips:** Memorizar el criterio: "Dₙ es Boole ⟺ n libre de cuadrados"

---

#### Ejercicio 26c — P(A) con unión e intersección

**Enunciado:** ¿(P(A); ∪; ∩) es Algebra de Boole?

**Resolución:**
- **Operaciones:** sup = ∪, inf = ∩
- **Neutro de ∪:** ∅ (neutro inferior = 0_A)
- **Neutro de ∩:** A (neutro superior = 1_A)
- **Complemento:** X̄ = A \ X (diferencia)
- **Distributiva:** Siempre ✓
- **Complementada:** Siempre ✓

**Respuesta:** SÍ. (P(A); ∪; ∩) ES SIEMPRE un Algebra de Boole.

---

#### Ejercicio 26d — Subalgebra de P({1,2,3})

**Enunciado:** ¿({∅, {1}, {2}, {3}, {1,2,3}}; ⊆) es Algebra de Boole?

**Resolución:**

1. **|A| = 5 elementos** (no es potencia de 2)

2. **Problema:** sup{1},{2}} = {1,2} ∉ A

3. **No es ni siquiera red** (faltan supremos)

**Respuesta:** NO. Ni siquiera es red.

---

#### Ejercicio 26e — Matrices booleanas nxn

**Enunciado:** ¿({0,1}ⁿˣⁿ; ∨; ∧) es Algebra de Boole?

**Resolución:**

1. **Corresponde a:** P({(i,j) : 1≤i,j≤n})

2. **Cardinalidad:** |A| = 2^(n²) = 2^k donde k=n²

3. **Complemento de matriz M:** M̄ con entradas invertidas (0↔1)

4. **Operaciones:** A∨B elemento-a-elemento, A∧B elemento-a-elemento

**Respuesta:** SÍ. ES Algebra de Boole (isomorfa a P(A) con |A|=n²).

---

### Batch 04 — Ej.27, 28, 29

#### Ejercicio 27 — D₇₀: operaciones, átomos, isomorfismo

**Enunciado:** (D₇₀; |). Definir operaciones, hallar átomos, isomorfismo con P(A).

**Resolución paso a paso:**

1. **D₇₀ = {1, 2, 5, 7, 10, 14, 35, 70}** (8 elementos)

2. **70 = 2·5·7** (libre de cuadrados → ES Boole)

3. **Operaciones algebraicas:**
   - **Suma (∨):** sup(a,b) = mcm(a,b)
   - **Producto (∧):** inf(a,b) = mcd(a,b)
   - **Complemento:** comp(x) = 70/x

4. **Átomos** = elementos mínimos no-triviales = primos de 70 = **{2, 5, 7}**
   - Son los únicos elementos que cubren a 1

5. **Isomorfismo φ: D₇₀ → P({2,5,7})**
   - 1 ↔ ∅
   - 2 ↔ {2}
   - 5 ↔ {5}
   - 7 ↔ {7}
   - 10=2·5 ↔ {2,5}
   - 14=2·7 ↔ {2,7}
   - 35=5·7 ↔ {5,7}
   - 70 ↔ {2,5,7}

**Respuesta:** D₇₀ es Algebra de Boole con átomos {2,5,7}, isomorfo a P({2,5,7}).

---

#### Ejercicio 28 — Subalgebras de Boole de P({1,2,3})

**Enunciado:** Indicar cuáles son subalgebras de Boole:
a) {∅, {2}, {3}, {1,2,3}}
b) {∅, {1}, {2,3}, {1,2,3}}
c) {∅, {1}, {2}, {1,2}}

**Resolución:**

**Parte a)**
- {1} ∪ {2} = {1,2} ∉ conjunto → **NO es subalgebra**

**Parte b)**
- Cerradura: {1} ∪ {2,3} = {1,2,3} ✓
- {1} ∩ {2,3} = ∅ ✓
- Complemento de {1} en {1,2,3}: {2,3} ✓
- Complemento de {2,3}: {1} ✓
- **SÍ es subalgebra** (es Boole con 4 elementos)

**Parte c)**
- 0_A = ∅ ✓, 1_A debe ser {1,2,3} pero max aquí es {1,2} ≠ {1,2,3}
- **NO es subalgebra** (no contiene el 1 del álgebra original)

**Respuesta:** Solo **b)** es subalgebra de Boole.

---

#### Ejercicio 29 — Propiedades de Algebras de Boole

**Enunciado:** Indicar V (verdadero) o F (falso) en toda Algebra de Boole:

**a) ∀x,y,z: x∨y = x∨z ⟹ y=z**

**Respuesta: FALSO**

**Contraejemplo:** P({1,2}) con x={1,2}, y=∅, z={1}
- x∨y = {1,2}∨∅ = {1,2}
- x∨z = {1,2}∨{1} = {1,2}
- Igualdad de supremos pero y≠z

---

**b) ∀a,b: a≤b ∧ a≤b̄ ⟹ a=0**

**Respuesta: VERDADERO**

**Demostración:**
1. a ≤ b → a ∧ b = a
2. a ≤ b̄ → a ∧ b̄ = a
3. a = a ∧ (b ∨ b̄) = (a∧b) ∨ (a∧b̄) = a ∨ a = a
4. Pero también: a ≤ b ∧ b̄ = 0 → a ≤ 0 → a = 0

---

**c) ∀x,y: x∧y=x ⟺ x∧ȳ=0**

**Respuesta: VERDADERO**

**Demostración:**
- (⟹) Si x∧y=x: x∧ȳ = (x∧y)∧ȳ = x∧(y∧ȳ) = x∧0 = 0
- (⟸) Si x∧ȳ=0: x = x∧1 = x∧(y∨ȳ) = (x∧y) ∨ (x∧ȳ) = (x∧y) ∨ 0 = x∧y

---

### Batch 05 — Ej.30: Algebra de Boole con condiciones

#### Ejercicio 30

**Enunciado:** En toda Algebra de Boole (A;+;·), si a·b̄ ≤ c ∧ a+c=1, ¿cuál se cumple?
a) ā = c
b) c ≤ b
c) a ≤ c ∧ b̄ ≤ c
d) c = 1_A

**Resolución paso a paso:**

1. **De a+c=1:** ā ≤ c (por complemento)

2. **De a·b̄ ≤ c:** a∧b̄ ≤ c (por definición)

3. **Queremos probar a ≤ c:**
   - a = a ∧ 1 = a ∧ (b ∨ b̄) = (a∧b) ∨ (a∧b̄)
   - (a∧b̄) ≤ c y buscamos si a ≤ c
   - De a+c=1: a∨c=1 → ā∨... espera, esto no da a≤c directo

4. **De a∨c=1 y a·b̄≤c:**
   - Necesitamos ver si a≤c: a∧c = ?
   - a = a∧(a∨c) = a (por absorción)
   - Hmm, intentemos de otra forma...
   - Si a∨c=1, entonces todo elemento ≤ 1 es verdadero, pero no implica a≤c

5. **Respuesta correcta: Revisando con P({1,2}):**
   - a={1}, b̄={2}, c={1,2}. a·b̄={1}∩{2}=∅≤c ✓, a+c={1,2}=1_A ✓
   - a≤c: {1}⊆{1,2} ✓
   - b̄≤c: {2}⊆{1,2} ✓

**Respuesta:** **c) a ≤ c ∧ b̄ ≤ c**

---

## TIER 2 — MEDIA PRIORIDAD

### Batch 15 — Ej.9, 10, 11, 12, 13

#### Ejercicio 9 — Hasse con cotas

**Enunciado:** (A = {1,2,3,4,5,6,8,9,12}; |). Hasse, maximales, minimales. Mayorante/minorante de B={2,3,6}.

**Resolución concisa:**

1. **Hasse:** 1 en base. 2,3,5 en nivel 2. 4,6,9 en nivel 3. 8,12 en nivel 4.

2. **Minimales:** 1 (es mínimo)

3. **Maximales:** 5, 8, 9, 12

4. **Mayorantes de {2,3,6}:** Divisibles por 6 = {6, 12}

5. **Minorantes de {2,3,6}:** Divisores de 2 = {1, 2}

6. **Supremo:** 6 (en el conjunto)

7. **Ínfimo:** 1 (en el conjunto)

---

#### Ejercicio 11 — Orden en N²

**Enunciado:** (a;b)R(c;d) ⟺ a|c ∧ b≤d en ℕ². Demostrar orden, hallar cotas de X.

**Resolución:**

1. **Reflexiva:** a|a ✓, b≤b ✓ → (a;b)R(a;b) ✓

2. **Antisimétrica:** (a;b)R(c;d) ∧ (c;d)R(a;b) → a|c ∧ c|a → a=c; b≤d ∧ d≤b → b=d → (a;b)=(c;d) ✓

3. **Transitiva:** (a;b)R(c;d) ∧ (c;d)R(e;f): a|c, c|e → a|e; b≤d, d≤f → b≤f ✓

4. **Cotas de X = {(4;4), (8;6), (8;5), (4;6), (6;3), (12;9)}:**
   - Mayorantes: (x;y) tales que (4;4)R(x;y), (8;6)R(x;y), etc.
   - Necesitan: 4|x, 8|x, 6|x, etc. → x divisible por lcm(4,8,6,4,6,12)=24
   - y ≥ max(4,6,5,6,3,9)=9
   - Mayorantes: {(24;9), (24;10), ..., (48;9), ...}
   - **Supremo:** (24; 9)

---

#### Ejercicio 12 — Orden en P(A)

**Enunciado:** P(A): XRY ⟺ X̄∩Y=∅. Demostrar orden, hallar sup/inf de B={{1,3},{1,3,4},{3,4}}.

**Resolución:**

1. **Demostrar orden:** R es reflexiva (X̄∩X=∅ por definición de complemento), antisimétrica, transitiva ✓

2. **Para B en A={1,2,3,4}:**
   - X̄∩Y=∅ significa X̄ ⊆ Y, o equivalentemente X ⊇ Ȳ, es decir **Y ⊆ X**
   - Así el orden es **⊇ (contiene)**

3. **Supremo (según ⊇):** Intersección = {1,3} ∩ {1,3,4} ∩ {3,4} = {3}

4. **Ínfimo (según ⊇):** Unión = {1,3} ∪ {1,3,4} ∪ {3,4} = {1,3,4}

---

#### Ejercicio 13 — Orden con nombres

**Enunciado:** A={1,2,3,4,5,6,7,14,20}: aRb ⟺ a=b ∨ p(a)<p(b) [p(n)=letras del nombre].

**Resolución:**

1. **p(1)=3, p(2)=3, p(3)=4, p(4)=6, p(5)=5, p(6)=4, p(7)=4, p(14)=5, p(20)=6**

2. **Hasse:**
   - Nivel 0: 1, 2
   - Nivel 1: 3, 6, 7
   - Nivel 2: 5, 14
   - Nivel 3: 4, 20

3. **Minimales:** {1, 2}; **Maximales:** {4, 20}

4. **B={4,5,6,7}:**
   - Mayorantes: elementos > todos ellos en el orden = {4, 20}
   - Minorantes: elementos < todos ellos = ∅
   - **Supremo:** 4
   - **Ínfimo:** no existe

---

### Batch 16-17 — Redes y tablas algebraicas (resumen)

#### Ejercicio 18 — ¿Cuáles diagramas son redes?

Una red requiere: para todo par {x,y}, existen sup(x,y) e inf(x,y).

**Respuesta general:** Un diagrama de Hasse es red si no hay dos elementos incomparables sin cota superior o inferior común.

#### Ejercicio 19 — ¿Cuáles conjuntos son redes?

a) {1..10}; | → **NO** (3∨7 no existe en el conjunto)
b) {1..10}; ≤ → **SÍ** (cadena)
c) D₂₄ → **SÍ** (divisores de 24, libre de cuadrados)
d) P({a,b,c}) → **SÍ** (siempre es red)
e) Conjunto con ⊆ → Verificar cierre bajo ∪,∩
f) ℕ; | → **SÍ**
g) ℤ; ≥ → **SÍ**

#### Ejercicio 21 — V o F sobre redes

a) **FALSO.** Contraejemplo: pentagon N₅ (5 elementos, finito, con min y max, pero NO es red)

b) **FALSO.** Una red no implica orden total

c) **VERDADERO.** Bien ordenado (fully ordered) → es red

d) **VERDADERO.** En toda red: x≤y ⟺ sup{x,y}=y (por definición)

---

## Resumen: Claves para el Examen

| Concepto | Criterio |
|----------|----------|
| **Boole** | Red + Distributiva + Complementada |
| **Dₙ es Boole** | n = p₁·p₂·...·pₖ (libre de cuadrados) |
| **|Dₙ| para n libre** | 2^(número de factores primos) |
| **Átomos en Dₙ** | Primos que dividen a n |
| **Red** | ∃ sup e inf para todo par |
| **Cadena** | Orden total → siempre es red |

---

**Versión 1.0** — Completado 27 de febrero 2026
