# Finales Resueltos — Matemática Discreta (UNSAM)
## TIER 3: Ejercicios de Exámenes Finales Reales

Fuentes:
- F01 = Final 21/07/2023
- F02 = Final 04/08/2023
- F03 = Final 19/09/2023
- F04 = Final 07/12/2023
- F05 = Final 14/12/2023
- F06 = Final 22/02/2024

---

## Batch 22 — Finales Tema 2: Equivalencia

---

### F01-Ej6: xSy ⟺ x²-5x = y²-5y en ℝ

**Enunciado:** Hallar clases de equivalencia y conjunto cociente de S definida en ℝ tal que xSy ⟺ x²-5x = y²-5y.

**Tipo:** Equivalencia definida por función (f(x)=f(y))

**Verificar que es de equivalencia:**
- Reflexiva: x²-5x = x²-5x ✓
- Simétrica: si x²-5x = y²-5y, entonces y²-5y = x²-5x ✓
- Transitiva: si f(x)=f(y) y f(y)=f(z), entonces f(x)=f(z) ✓ → S es de equivalencia.

**Resolver x²-5x = y²-5y:**
```
x²-5x = y²-5y
x²-y² - 5x+5y = 0
(x-y)(x+y) - 5(x-y) = 0
(x-y)(x+y-5) = 0
```
→ x = y   O   x+y = 5, es decir y = 5-x

**Clases de equivalencia:**
- Si a ≠ 5/2: [a] = {a, 5-a}   (dos elementos simétricos respecto a 5/2)
- Si a = 5/2: [5/2] = {5/2}    (clase unipuntual, punto fijo de y=5-x)

**Conjunto cociente:**
```
ℝ/S = { {a, 5-a} : a ≤ 5/2 }
```
Cada clase queda representada por el elemento a ≤ 5/2 (el "lado izquierdo" de la parábola).

**Respuesta:** Las clases son pares de reales que suman 5, más la clase {5/2}.

**Tips:**
- Clave: x²-5x = y²-5y → factor común → (x-y)(x+y-5)=0
- La parábola f(x)=x²-5x tiene eje de simetría en x=5/2, por eso cada par {a, 5-a} tiene la misma imagen.

---

### F03-Ej7: (x,y) R (z,t) ⟺ |x|=|z| ∧ 2|(y+t) en ℝ²

**Enunciado:** Hallar clases de equivalencia de (1;4), (0;0) y (3;5).

**Tipo:** Equivalencia en producto cartesiano con dos condiciones

**Verificar que es de equivalencia:**
- Reflexiva: |x|=|x| ✓ y 2|(y+y)=2y ✓
- Simétrica: |x|=|z|→|z|=|x| ✓ y 2|(y+t)→2|(t+y) ✓
- Transitiva: |x|=|z| y |z|=|w| → |x|=|w| ✓; 2|(y+t) y 2|(t+s) → 2|(y+t+t+s)=2|(y+s+2t) → 2|(y+s) ✓ → ES de equivalencia.

**Forma de las clases:**
[(z,t)] = { (x,y) : |x|=|z|, 2|(y+t) }

Condición |x|=|z|: x=z ó x=-z
Condición 2|(y+t): y+t es par ⟺ y y t tienen la misma paridad

**Clase de (1;4):**
- |x|=1 → x=1 ó x=-1
- 2|(y+4) → y+4 par → y par
- [(1;4)] = { (±1, y) : y es par }

**Clase de (0;0):**
- |x|=0 → x=0
- 2|(y+0) → y par
- [(0;0)] = { (0, y) : y es par }

**Clase de (3;5):**
- |x|=3 → x=3 ó x=-3
- 2|(y+5) → y+5 par → y impar
- [(3;5)] = { (±3, y) : y es impar }

**Respuesta:** Clases determinadas por (|x|, paridad de y).

---

### F04-Ej2: Si P₁ y P₂ son particiones de A, entonces P₁∩P₂=∅ — V o F

**Enunciado:** Indicar V o F: Si P₁ y P₂ son dos particiones de un conjunto no vacío A, entonces P₁∩P₂=∅.

**Tipo:** V o F con justificación/contraejemplo

**Respuesta: FALSO**

**Contraejemplo:**
```
A = {1, 2, 3}
P₁ = {{1,2}, {3}}    (partición de A)
P₂ = {{1,2}, {3}}    (misma partición → P₁ = P₂)

P₁ ∩ P₂ = {{1,2}, {3}} ≠ ∅
```

O con particiones distintas que compartan algún bloque:
```
A = {1, 2, 3, 4}
P₁ = {{1,2}, {3,4}}
P₂ = {{1,2}, {3}, {4}}

P₁ ∩ P₂ = {{1,2}} ≠ ∅
```

**Nota:** P₁∩P₂ puede ser vacío (particiones incompatibles) o no vacío (cuando comparten algún bloque). No es necesariamente vacío.

---

### F04-Ej4: Identificar equivalencia por gráfica en ℝ

**Enunciado:** Dadas dos relaciones en ℝ por gráficas, identificar cuál es de equivalencia.

**Tipo:** Análisis geométrico de relaciones en ℝ²

**Análisis de las gráficas:**

**Gráfica izquierda** (círculo + líneas diagonales que se cruzan):
- El círculo representa pares (x,y) con x²+y²=r² → no es simétrica respecto a la diagonal
- Las líneas diagonales + el círculo violan la transitividad
- No es de equivalencia

**Gráfica derecha** (líneas diagonales paralelas, tipo y=x+k):
- Representa xRy ⟺ x-y = cte (clases de igual diferencia) o x-y ∈ ℤ
- Reflexiva: y=x pasa por todos los puntos → ✓ (diagonal está incluida)
- Simétrica: si (x,y) está, entonces (y,x) también → gráfica simétrica respecto y=x ✓
- Transitiva: si xRy y yRz → xRz ✓ (diferencias se conservan)
- ES de equivalencia

**Respuesta:** La gráfica derecha (líneas paralelas a la diagonal y=x) es de equivalencia.

---

### F05-Ej4: Analizar S (amigo), R (ingresó antes), T (mismo año)

**Enunciado:** Dadas relaciones en empleados de empresa, analizar si son de equivalencia.

**Tipo:** Análisis de propiedades R,S,T en contexto real

**Relación R: xRy ⟺ x ingresó a la empresa antes que y**
- Reflexiva: ¿x ingresó antes que sí mismo? NO (orden estricto)
- Simétrica: si x antes que y, ¿y antes que x? NO (son momentos distintos)
- Transitiva: si x antes que y, y antes que z → x antes que z. SÍ
- **NO es de equivalencia** (falla reflexiva y simétrica)

**Relación S: xSy ⟺ x es amigo de y**
- Reflexiva: ¿x es amigo de sí mismo? Depende de definición, generalmente NO o NO convencional
- Simétrica: ¿si x amigo de y, entonces y amigo de x? NO necesariamente (amistad puede ser unilateral)
- Transitiva: ¿si x amigo de y, y amigo de z, entonces x amigo de z? NO (no siempre)
- **NO es de equivalencia**

**Relación T: xTy ⟺ x nació el mismo año que y**
- Reflexiva: x nació el mismo año que x. SÍ ✓
- Simétrica: si x mismo año que y, entonces y mismo año que x. SÍ ✓
- Transitiva: si x mismo año que y, y mismo año que z, entonces x mismo año que z. SÍ ✓
- **SÍ es de equivalencia** — clases = {empleados nacidos en el año k} para cada año k

**Respuesta:** Solo T es de equivalencia.

---

## Batch 23 — Finales Tema 2 + Tema 3: Boole/Orden

---

### F06-Ej2: xRy ⟺ x+y=8 en A={1,2,...,8}, propiedades

**Enunciado:** Dada R en A={1,...,8} con xRy ⟺ x+y=8, indicar propiedades.

**Tipo:** Propiedades de relaciones

**Reflexiva:** xRx ⟺ 2x=8 ⟺ x=4. Solo 4R4, no todos. **NO reflexiva.**

**A-Reflexiva:** xRx es FALSO para todo x ⟺ 2x≠8 para todo x. Falla en x=4 (4R4). **NO a-reflexiva.**

**Simétrica:** x+y=8 → y+x=8. **SÍ simétrica.** ✓

**A-Simétrica:** xRy ∧ yRx ∧ x≠y implica contradicción. Si x+y=8 y y+x=8, siempre verdadero. Pero xRy ∧ yRx → x+y=8 y y+x=8 → siempre implica que ambos se cumplen para x=4,y=4 (único caso con x=y). Para x≠y: x+y=8 y y+x=8 → no implica x=y (ej. x=3,y=5). **NO antisimétrica.**

**Transitiva:** xRy ∧ yRz → xRz? x+y=8 y y+z=8 → x=z. ¿x+z=8? Solo si x+z=2x=8 → x=4. NO siempre. **NO transitiva.**

**Respuesta:**
- Reflexiva: NO | A-Reflexiva: NO
- Simétrica: SÍ | A-Simétrica: NO
- Antisimétrica: NO | Transitiva: NO

---

### F01-Ej8: (A={2,4,6,8,10,24,30,120}; |) — cotas, red, Boole

**Enunciado:** Para B={6,8,24}, hallar cotas sup/inf, supremo, ínfimo. ¿Es red? ¿Álgebra de Boole?

**Tipo:** Orden por divisibilidad, retículo

**Elementos de A:** 2, 4, 6, 8, 10, 24, 30, 120

**Relación de divisibilidad relevante:**
```
2 | 4, 6, 8, 10, 24, 30, 120
4 | 8, 24, 120
6 | 24, 30, 120
8 | 24, 120
10 | 30, 120
24 | 120
30 | 120
```

**Para B = {6, 8, 24}:**

Cotas superiores (x∈A: 6|x ∧ 8|x ∧ 24|x):
- 6|x ∧ 8|x → mcm(6,8)=24|x → 24|x
- x∈A con 24|x: x=24, x=120
- **CS(B) = {24, 120}**

Cotas inferiores (x∈A: x|6 ∧ x|8 ∧ x|24):
- x|6 ∧ x|8 → x|mcd(6,8)=2
- x∈A con x|2: x=2
- **CI(B) = {2}**

- **Supremo = 24** (mínimo de CS)
- **Ínfimo = 2** (máximo de CI)

**¿Es red?** Verificar si todo par tiene sup e ínf en A:
- {4, 6}: mcd(4,6)=2∈A ✓, mcm(4,6)=12 ∉ A ✗
- **NO es red** (4 y 6 no tienen supremo en A)

**¿Álgebra de Boole?** Si no es red, tampoco es AB. **NO.**

---

### F02-Ej6: Relación de orden en |A|=6 con Hasse de 5 aristas

**Enunciado:** Sea R de orden en A con |A|=6 y Hasse con 5 aristas. Indicar cuál afirmación es correcta.

**Tipo:** Propiedades de orden y diagrama de Hasse

**Análisis:**

Un Hasse con 6 nodos y 5 aristas es un árbol (árbol con n nodos tiene n-1 aristas).

**Opción a) A totalmente ordenado:**
Si fuera cadena a₁<a₂<a₃<a₄<a₅<a₆, el Hasse tiene 5 aristas. Sería posible, pero no necesario.

**Opción b) No hay primer elemento:**
Si hay un mínimo (estrella: 1 mínimo + 5 hojas), sí hay primer elemento. NO necesariamente.

**Opción c) Puede haber más de 3 maximales:**
Estructura estrella: {a→b, a→c, a→d, a→e, a→f} → 5 maximales: b,c,d,e,f. Sí puede.

**Opción d) R puede tener solo 11 pares ordenados:**
Estructura estrella: pares = {(a,a),(b,b),(c,c),(d,d),(e,e),(f,f)} + {(a,b),(a,c),(a,d),(a,e),(a,f)} = 6+5 = **11 pares**. ✓

**Respuesta: d)** R puede tener solo 11 pares ordenados. ✓ (También c es verdadero)

---

### F02-Ej8: ¿Cuál es isomorfo a (P({a,b,c}); ⊆)?

**Enunciado:** De (D₃₇₀₃;|), (D₂₁₀;|), (D₂₈₉;|), (D₂₇₁₇;|), indicar el isomorfo a P({a,b,c}).

**Tipo:** Álgebra de Boole — isomorfismo

**Clave:** P({a,b,c}) tiene 2³=8 elementos → necesitamos AB con 8 elementos.
(Dₙ;|) es AB ⟺ n es producto de primos distintos (libre de cuadrados).
AB isomorfo a P({1,...,k}) ⟺ n tiene exactamente k factores primos distintos.

Para P({a,b,c}): k=3 → necesitamos n con exactamente 3 primos distintos y libre de cuadrados.

**Factorizar cada opción:**
- D₃₇₀₃: 3703 = 7 × 529 = 7 × 23² → **NO libre de cuadrados** → NO AB
- D₂₁₀: 210 = 2×3×5×7 → 4 primos distintos → |D₂₁₀|=2⁴=16 ≠ 8 → NO isomorfo a P({a,b,c})
- D₂₈₉: 289 = 17² → **NO libre de cuadrados** → NO AB
- D₂₇₁₇: 2717 = 11×13×19 → 3 primos distintos, libre de cuadrados → |D₂₇₁₇|=2³=8 ✓

**Respuesta: d) (D₂₇₁₇; |)**

**Verificación:** 2717 = 11·13·19 (todos primos distintos) → AB con átomos {11,13,19} isomorfo a P({11,13,19}) ≅ P({a,b,c}).

---

### F03-Ej8: Red algebraica A={a,b,c,d,e,f,g,h}, tabla v, Hasse, ¿Boole?

**Enunciado:** Dado A={a,b,c,d,e,f,g,h} con 0_A=a, 1_A=h y tabla de v (join), hacer Hasse e indicar si es AB.

**Tipo:** Red algebraica — construcción de Hasse y análisis de Boole

**Tabla de join (∨) dada (datos del examen):**
```
∨  a  b  c  d  e  f  g  h
a  a  b  c  d  e  f  g  h
b  b  b  f  h  h  f  h  h
c  c  f  c  h  h  f  g  h     (c∨b=f; c∨d=h; c∨e=h; c∨f=f; c∨g=g)
d  d  h  h  d  h  h  h  h
e  e  h  h  h  e  h  h  h
f  f  f  f  h  h  f  h  h
g  g  h  g  h  h  h  g  h
h  h  h  h  h  h  h  h  h
```

**Relación de orden (x≤y ⟺ x∨y=y):**
- a es mínimo (a∨x=x para todo x)
- h es máximo (h∨x=h para todo x)
- b∨f=f → b≤f; c∨f=f → c≤f
- b∨h=h → b≤h; d∨h=h → d≤h
- f∨h=h → f≤h; g∨h=h → g≤h
- a∨b=b → a≤b; a∨c=c → a≤c; a∨d=d; a∨e=e; a∨g=g

**Hasse aproximado:**
```
        h
      / | \ \
     f  d  e  g
    / \
   b   c
    \ /
     a
```
(a < b,c,d,e,g; b,c < f; f,d,e,g < h)

**¿Es Álgebra de Boole?** Con |A|=8=2³, si la red es distributiva y cada elemento tiene complemento único → sí.

Verificar complementos (x∧x'=a, x∨x'=h):
- b∨g=h y b∧g=a? → si sí, b'=g
- c∨d=h y c∧d=a? → si sí, c'=d
- f∨e=h y f∧e=a? → si sí, f'=e

Si todas las condiciones se cumplen → **SÍ es Álgebra de Boole**, isomorfa a P({1,2,3}).

**Respuesta:** La red algebraica alcanza estructura de AB si todos los complementos son únicos (verificar con la tabla completa).

---

## Batch 24 — Finales Tema 3: Boole + Tema 5: Recurrencia

---

### F04-Ej5: Hasse dado, cotas sup/inf de B={c,g}

**Enunciado:** Sea A={a,b,c,d,e,f,g,h,i,k,n} ordenado según diagrama de Hasse. Para B={c,g}, hallar cotas superiores, inferiores, supremo e ínfimo.

**Tipo:** Orden parcial — cotas en Hasse

**Lectura del diagrama (Final 07/12/2023):**
```
         k --- h
        /
   e - f
  /       \
 b    c    i
  \  / \  /
   \/   g
   a     \
    \     n
     d
```
Aproximadamente: a es mínimo, h,k son máximos.
Relaciones: a<b, a<d, b<c, b<e, d<g, c<f, e<f, g<i, g<n, f<k, f<h, i<h

**Para B = {c, g}:**

Cotas superiores (x: c≤x ∧ g≤x):
- Elementos mayores que c: f, k, h
- Elementos mayores que g: i, n, h
- CS(B) = {f,k,h} ∩ {i,n,h} = {h}
- **CS(B) = {h}**

Cotas inferiores (x: x≤c ∧ x≤g):
- Elementos menores que c: b, a
- Elementos menores que g: d, a
- CI(B) = {b,a} ∩ {d,a} = {a}
- **CI(B) = {a}**

- **Supremo = h** (único elemento de CS)
- **Ínfimo = a** (único elemento de CI)

---

### F05-Ej5: (D₄₀; |) — propiedades

**Enunciado:** Sea (D₄₀; |). Marcar opciones correctas.

**Tipo:** Álgebra de Boole — análisis de D_n

**Factorizar:** 40 = 2³ × 5

**Divisores de 40:** 1, 2, 4, 5, 8, 10, 20, 40 → |D₄₀| = 8

**¿Red?** Los divisores de n siempre forman red con mcd(inf) y mcm(sup). **SÍ es red.**

**¿Distributiva?** Los retículos de divisores siempre son distributivos. **SÍ distributiva.**

**¿Complementada?** Para ser complementada (como AB) necesita n libre de cuadrados.
40 = 2³×5 → 2³ → NO libre de cuadrados → **NO complementada.**

**Análisis de opciones:**
- a) Red distributiva pero NO complementada → **SÍ ✓**
- b) Red distributiva Y complementada → NO
- c) Red complementada y NO distributiva → NO
- d) Álgebra de Boole → NO (no complementada)
- e) No es red → NO

**Respuesta: a) Es red distributiva pero NO complementada.**

---

### F06-Ej4: (D₄₀; |) — totalmente ordenado, Boole, isomorfo D₃₀

**Enunciado:** (D₄₀; |) es: a) Totalmente ordenado, b) AB, c) Red isomorfa a (D₃₀;|), d) Red distributiva pero no complementada.

**Tipo:** Clasificación de estructura algebraica

**40 = 2³×5, 30 = 2×3×5**

- a) Totalmente ordenado: 4 y 5 son divisores de 40 pero 4∤5 y 5∤4 → NO comparables → **NO totalmente ordenado**
- b) Álgebra de Boole: 40 no es libre de cuadrados (tiene 2³) → **NO AB**
- c) Isomorfa a D₃₀: D₃₀=2×3×5 (3 primos, libre de cuadrados) → D₃₀ es AB con 8 elementos; D₄₀ no es AB → **NO isomorfas como AB**. Como retículos tampoco son isomorfas (D₃₀ tiene 8 átomos distintos, D₄₀ no).
- d) Red distributiva pero no complementada → **SÍ ✓**

**Respuesta: d)**

---

### F01-Ej9: aₙ = 3aₙ₋₁ - 2aₙ₋₂, a₀=1, a₁=0

**Enunciado:** Resolver la relación de recurrencia.

**Tipo:** Orden 2 homogénea, raíces reales distintas

**Paso 1 — Ecuación característica:**
```
r² - 3r + 2 = 0
(r-1)(r-2) = 0
r₁ = 1,  r₂ = 2
```

**Paso 2 — Solución general:**
```
aₙ = A·1ⁿ + B·2ⁿ = A + B·2ⁿ
```

**Paso 3 — Condiciones iniciales:**
```
n=0: A + B = 1
n=1: A + 2B = 0
```

Restando: B = -1 → A = 2

**Paso 4 — Solución:**
```
aₙ = 2 + (-1)·2ⁿ = 2 - 2ⁿ
```

**Verificación:**
- a₀ = 2-1 = 1 ✓
- a₁ = 2-2 = 0 ✓
- a₂ = 3·0 - 2·1 = -2; fórmula: 2-4 = -2 ✓

**Respuesta: aₙ = 2 - 2ⁿ**

---

### F02-Ej9: aₙ₊₂ - 4aₙ₊₁ - 5aₙ = 10·4ⁿ, a₀=1, a₁=7

**Enunciado:** Resolver la recurrencia no homogénea.

**Tipo:** Orden 2 no homogénea, término 4ⁿ (no es raíz)

**Paso 1 — Homogénea asociada:**
```
r² - 4r - 5 = 0
(r-5)(r+1) = 0
r₁ = 5,  r₂ = -1
```
```
aₙ^(h) = A·5ⁿ + B·(-1)ⁿ
```

**Paso 2 — Solución particular (4ⁿ, no es raíz → forma C·4ⁿ):**

Sustituir aₙ^(p) = C·4ⁿ:
```
C·4^(n+2) - 4C·4^(n+1) - 5C·4ⁿ = 10·4ⁿ
C·16·4ⁿ - 4C·4·4ⁿ - 5C·4ⁿ = 10·4ⁿ
4ⁿ · C(16 - 16 - 5) = 10·4ⁿ
-5C = 10
C = -2
```
```
aₙ^(p) = -2·4ⁿ
```

**Paso 3 — Solución general:**
```
aₙ = A·5ⁿ + B·(-1)ⁿ - 2·4ⁿ
```

**Paso 4 — Condiciones iniciales:**
```
n=0: A + B - 2 = 1     → A + B = 3
n=1: 5A - B - 8 = 7    → 5A - B = 15
```

Sumando: 6A = 18 → A = 3, B = 0

**Respuesta: aₙ = 3·5ⁿ - 2·4ⁿ**

**Verificación:**
- a₀ = 3-2 = 1 ✓
- a₁ = 15-8 = 7 ✓

---

## Batch 25 — Finales Tema 5: Recurrencia + Tema 4: Congruencias

---

### F03-Ej9: Recurrencia orden 1 con solución particular aₙ = 3·5ⁿ

**Enunciado:** Escribir una recurrencia de orden 1 que tenga como solución particular aₙ = 3·5ⁿ.

**Tipo:** Problema inverso — construir recurrencia

**Razonamiento:**
Para orden 1 no homogénea: aₙ = r·aₙ₋₁ + f(n)
La particular tiene forma aₙ^(p) = K·5ⁿ si r≠5 (sin resonancia).

Si r≠5, particular = K·5ⁿ:
```
K·5ⁿ = r·K·5^(n-1) + f(n)
K·5 = r·K + f     (dividiendo por 5^(n-1), si f es constante respecto a n)
```

**Estrategia:** Elegir r=1 (raíz de homogénea), buscar f(n):
```
aₙ - aₙ₋₁ = f(n)
Si aₙ^(p) = 3·5ⁿ: f(n) = 3·5ⁿ - 3·5^(n-1) = 3·5^(n-1)(5-1) = 12·5^(n-1)
```

**Recurrencia:** aₙ - aₙ₋₁ = 12·5^(n-1)  (orden 1, no homogénea)

**Verificación:** aₙ^(p) = 3·5ⁿ
- 3·5ⁿ - 3·5^(n-1) = 3·5^(n-1)(5-1) = 12·5^(n-1) ✓

**Alternativa más simple:**
Recurrencia: aₙ = r·aₙ₋₁ + c·5ⁿ con r≠5.
Tomando r=2: K·5ⁿ = 2K·5^(n-1) + c·5ⁿ → 5K = 2K + 5c → 3K=5c → con K=5: c=3.
```
aₙ = 2aₙ₋₁ + 3·5ⁿ
```
Verificación: aₙ^(p) = 5·5ⁿ (K=5, no 3). No da exactamente 3·5ⁿ.

**Respuesta preferida:** aₙ = aₙ₋₁ + 12·5^(n-1) tiene a 3·5ⁿ como solución particular.

---

### F04-Ej6: Recurrencia orden 1 no homogénea con solución particular aₙ = 4·2ⁿ

**Enunciado:** Escribir recurrencia de orden 1 no homogénea que tenga aₙ = 4·2ⁿ como solución particular.

**Tipo:** Problema inverso

**Construcción:**

Si la recurrencia es aₙ - r·aₙ₋₁ = f(n) con r≠2:
Particular K·2ⁿ: K·2ⁿ - r·K·2^(n-1) = f(n) → K·2^(n-1)(2-r) = f(n)

Para K=4 y f constante → necesitamos 2-r racional y f ∝ 2^(n-1) (no constante).

**Enfoque directo:** aₙ = aₙ₋₁ + f(n), con particular 4·2ⁿ:
```
4·2ⁿ = 4·2^(n-1) + f(n)
f(n) = 4·2ⁿ - 4·2^(n-1) = 4·2^(n-1)(2-1) = 4·2^(n-1) = 2^(n+1)
```

**Recurrencia:** aₙ = aₙ₋₁ + 2^(n+1)   (equivalente: aₙ - aₙ₋₁ = 2^(n+1))

**Verificación:** 4·2ⁿ - 4·2^(n-1) = 4·2^(n-1) = 2·2ⁿ = 2^(n+1) ✓

---

### F05-Ej6: aₙ = k·5ⁿ + 4, ¿de qué tipo es esta recurrencia?

**Enunciado:** La sucesión aₙ = k·5ⁿ + 4 puede ser solución general de una recurrencia de qué tipo.

**Tipo:** Clasificación de recurrencias por su solución general

**Análisis de la forma:**
- k·5ⁿ → parte homogénea con raíz r=5
- +4 = 4·1ⁿ → parte particular constante (proviene de no-homogeneidad con raíz r=1)

**Estructura:** Dos raíces (r=5 de homogénea, r=1 implícita en particular) → **orden 1 no homogénea** o **orden 2 homogénea** (con raíces 5 y 1).

Pero: en solución GENERAL de orden 1, solo hay UNA constante arbitraria (k). Aquí k es libre y 4 es la particular → **Orden 1 no homogénea** con:
- Homogénea: aₙ = k·5ⁿ (raíz r=5)
- Particular: aₙ^(p) = 4 (constante)
- Recurrencia: aₙ - 5aₙ₋₁ = c (con c tal que particular = 4)

Verificar: K = 4, aₙ^(p) = 4: 4 - 5·4 = -16 → c = -16
Recurrencia: aₙ - 5aₙ₋₁ = -16

**Respuesta: b) Orden 1 no homogénea.**

---

### F06-Ej10: aₙ₊₁ - 4aₙ = -6·2ⁿ, ¿aₙ = 3·2ⁿ es solución particular o general?

**Enunciado:** Dada la recurrencia aₙ₊₁ - 4aₙ = -6·2ⁿ, ¿aₙ = 3·2ⁿ es: a) solución particular, b) solución general, c) no es solución?

**Paso 1 — Verificar si es solución:**
Sustituir aₙ = 3·2ⁿ en la recurrencia:
```
3·2^(n+1) - 4·3·2ⁿ = 6·2ⁿ - 12·2ⁿ = -6·2ⁿ ✓
```
Sí es solución.

**Paso 2 — ¿Particular o general?**
- Homogénea: aₙ₊₁ - 4aₙ = 0 → r = 4 → aₙ^(h) = C·4ⁿ
- Solución general = C·4ⁿ + aₙ^(p)
- aₙ = 3·2ⁿ no tiene constante arbitraria C → **es solución particular** (no general)

**Respuesta: a) Es solución particular.**

**Nota:** La solución general sería aₙ = C·4ⁿ + 3·2ⁿ (con C arbitraria).

---

### F01-Ej7: 4731x ≡ 589 (76513) — cantidad de soluciones principales

**Enunciado:** Indicar cantidad de soluciones principales de 4731x ≡ 589 (mod 76513).

**Tipo:** Ecuación de congruencia — existencia y cantidad de soluciones

**Paso 1 — Calcular d = mcd(4731, 76513) con Euclides:**
```
76513 = 16·4731 + 817    (16×4731=75696; 76513-75696=817)
4731  =  5·817  + 646    (5×817=4085; 4731-4085=646)
817   =  1·646  + 171
646   =  3·171  + 133
171   =  1·133  + 38
133   =  3·38   + 19
38    =  2·19   + 0
```
→ **d = mcd(4731, 76513) = 19**

**Paso 2 — Verificar si d | 589:**
589 ÷ 19 = 31 → 19·31 = 589 ✓ → **d | 589, tiene soluciones**

**Paso 3 — Cantidad de soluciones principales:**
Número de soluciones principales = d = **19**

**Respuesta: 19 soluciones principales.**

---

## Batch 26 — Finales Tema 4: Congruencias + Tema 1: Categoricos

---

### F02-Ej7: Resto m/15 = 8, deducir propiedades

**Enunciado:** Sabiendo que el resto de dividir m por 15 es 8, indicar qué se desprende necesariamente.

**Tipo:** Aritmética modular — consecuencias de una congruencia

**Dato:** m ≡ 8 (mod 15), es decir m = 15k + 8 para algún k∈ℤ.

**Opción a) 6|(2m-4):**
```
2m - 4 = 2(15k+8) - 4 = 30k + 16 - 4 = 30k + 12 = 6(5k + 2)
```
→ **SÍ, 6|(2m-4)** para todo k. ✓

**Opción b) 10|5m:**
```
5m = 5(15k+8) = 75k + 40
10|5m ⟺ 2|m
m = 15k+8: si k=0 → m=8 (par, 2|m ✓); si k=1 → m=23 (impar, 2∤m ✗)
```
→ **NO necesariamente.**

**Opción c) mcd(m+7, 15)=1:**
```
m+7 = 15k+8+7 = 15k+15 = 15(k+1)
→ 15|(m+7) → mcd(m+7, 15) = 15 ≠ 1
```
→ **Falso.**

**Respuesta: a) 6|(2m-4)** ✓

---

### F03-Ej4: Resto de (b-2c-18) por 10

**Enunciado:** División entera de b por q: cociente 10, resto 7. División entera de c por 5: resto 3. Hallar resto de (b-2c-18) por 10.

**Tipo:** Aritmética modular — operaciones con restos

**Datos:**
- b = q·10 + 7  (b÷q: cociente 10, resto 7) → b ≡ 7 (mod 10)... Espera.

Nota: "b ÷ q con cociente 10 y resto 7" → b = 10·q + 7, donde q es el divisor.
Esto nos dice b mod 10:
```
b = 10q + 7  →  b ≡ 7 (mod 10)   ✓ (pues 10q ≡ 0 mod 10)
```

- c ≡ 3 (mod 5) → c = 5s + 3 → 2c = 10s + 6 → **2c ≡ 6 (mod 10)**

**Calcular (b - 2c - 18) mod 10:**
```
b - 2c - 18 ≡ 7 - 6 - 18  (mod 10)
           ≡ 7 - 6 - 18
           ≡ -17           (mod 10)
           ≡ -17 + 20      (mod 10)
           ≡ 3             (mod 10)
```

**Respuesta: el resto es 3.**

*(En Final 05, la opción correcta es e) "otro valor" = 3, ya que ninguna de las opciones a,b,c menciona 3)*

---

### F04-Ej3: ¿Existe n∈ℕ tal que mcd(5n+3, 2n+1) = 3?

**Enunciado:** Si es posible, hallar n∈ℕ tal que mcd(5n+3, 2n+1)=3; si no, justificar.

**Tipo:** Propiedades del mcd — combinación lineal

**Aplicar propiedad:** mcd(a,b) | (αa + βb) para cualquier α,β∈ℤ.

```
5·(2n+1) - 2·(5n+3) = 10n+5 - 10n-6 = -1
```

Entonces mcd(5n+3, 2n+1) | (-1)

→ mcd(5n+3, 2n+1) = 1 para todo n.

**Conclusión:** Es imposible que mcd(5n+3, 2n+1) = 3.
No existe tal n∈ℕ porque el mcd siempre es 1 (se pueden combinar linealmente para obtener -1).

---

### F06-Ej7: 72x ≡ 54 (126) — soluciones principales

**Enunciado:** La ecuación 72x ≡ 54 (mod 126) tiene cuántas soluciones principales?

**Tipo:** Ecuación de congruencia — cantidad de soluciones

**Paso 1 — d = mcd(72, 126):**
```
126 = 1·72 + 54
72  = 1·54 + 18
54  = 3·18 + 0
```
→ **d = 18**

**Paso 2 — ¿d | 54?**
54 ÷ 18 = 3 ✓ → tiene soluciones.

**Paso 3 — Número de soluciones principales = d = 18**

**Respuesta: c) 18 soluciones.**

---

### F06-Ej8: ∃s,t∈ℤ: 3 = as+bt → ¿qué se asegura de mcd(a,b)?

**Enunciado:** Si dados a,b∈ℤ existen s,t∈ℤ tales que 3=as+bt, ¿qué se puede asegurar de mcd(a,b)?

**Tipo:** Teorema de Bezout inverso

**Análisis:**
Por teorema de Bezout: d = mcd(a,b) es el menor entero positivo de la forma as+bt.
Si 3 = as+bt, entonces d | 3 (el mcd divide a toda combinación lineal).

Por tanto: mcd(a,b) | 3 → mcd(a,b) ∈ {1, 3}

**Opciones:**
- a) mcd(a,b)=3: NO siempre (si a=1, b=2: mcd=1, s=3, t=0 → 3=1·3+2·0 ✓ pero mcd=1≠3)
- b) mcd(a,b)≠1: NO (contraejemplo anterior: mcd=1)
- c) mcd(a,b)≠3: NO (si a=3, b=6: mcd=3, s=1, t=0 → 3=3·1+6·0 ✓ y mcd=3)
- d) n.a. (ninguna de las anteriores)

Lo único que se puede asegurar es que **mcd(a,b) | 3**, es decir mcd(a,b) ∈ {1,3}.

**Respuesta: d) n.a.** (no se puede asegurar ninguna de las opciones anteriores específicamente)

---

## Batch 27 — Finales Tema 1: Categóricos y Razonamientos

---

### F02-Ej1: "Si estudio, apruebo. Si apruebo, me pongo feliz. Estoy feliz. ∴ estudio y apruebo"

**Enunciado:** El razonamiento es: a) categórico y válido, b) categórico e inválido, c) no categórico y válido, d) no categórico e inválido.

**Tipo:** Clasificación y validez de razonamiento

**¿Es categórico?**
Un razonamiento categórico usa proposiciones del tipo "Todos/Algunos A son B" (cuantificadores de clase).
Este razonamiento usa:
- p → q (condicional proposicional)
- q → r
- r
- ∴ p ∧ q

No usa cuantificadores de clase (todo, algún, ningún) sobre categorías → **NO es categórico.**

**¿Es válido?**
Simbolizar:
- p = "estudio", q = "apruebo", r = "me pongo feliz"
- Premisas: p→q, q→r, r
- Conclusión: p∧q

Contraejemplo (que hace premisas verdaderas y conclusión falsa):
- p = F (no estudio), q = F (no apruebo), r = V (estoy feliz por otro motivo)
- p→q: F→F = V ✓
- q→r: F→V = V ✓
- r: V ✓
- p∧q: F∧F = F ✗ (conclusión falsa)

→ El razonamiento es **INVÁLIDO** (falacia de afirmación del consecuente).

**Respuesta: d) No categórico e inválido.**

---

### F04-Ej1: ∃x[r(x)∨t(x)]; ∃x:~t(x) ∴ ∃x:r(x) — ¿válido?

**Enunciado:** Analizar y justificar si es válido o no: ∃x[r(x)∨t(x)]; ∃x:~t(x) ∴ ∃x:r(x).

**Tipo:** Razonamiento de predicados — validez

**Intuición:** "Existe algo que es r o t. Existe algo que no es t. ¿Existe algo que es r?"

**Contraejemplo (invalida el razonamiento):**

Sea el universo U = {a, b}:
- r(a) = F, r(b) = F (nada es r)
- t(a) = V, t(b) = F

Verificar premisas:
- P1: ∃x[r(x)∨t(x)] → r(a)∨t(a) = F∨V = V ✓ (a lo satisface)
- P2: ∃x:~t(x) → ~t(b) = ~F = V ✓ (b lo satisface)

Verificar conclusión:
- C: ∃x:r(x) → r(a)=F, r(b)=F → **FALSA** ✗

**Conclusión: El razonamiento es INVÁLIDO.**

El problema es que el x que satisface P1 podría satisfacerlo solo por t(x)=V (no por r(x)), y el x que satisface P2 (no es t) puede no ser r.

---

### F06-Ej1: Simbolizar p y q con opciones 1-4

**Enunciado:**
- p: "Los sillones de mi casa son cómodos"
- q: "Algunos sillones de mi casa son cómodos"

Las expresiones simbólicas:
1. ∀x:[p(x)→q(x)]
2. ∀x:[p(x)∧q(x)]
3. ∃x:[p(x)→q(x)]
4. ∃x:[p(x)∧q(x)]

Donde p(x)="x es sillón de mi casa", q(x)="x es cómodo".

**Simbolizar p:** "LOS sillones de mi casa son cómodos" → TODOS → cuantificador universal.
- "Para todo x, si x es sillón de mi casa, entonces es cómodo"
- **∀x:[p(x)→q(x)] → Opción 1** ✓

**Simbolizar q:** "ALGUNOS sillones de mi casa son cómodos" → existencial.
- "Existe x tal que x es sillón de mi casa Y es cómodo"
- **∃x:[p(x)∧q(x)] → Opción 4** ✓

**Respuesta:**
- p se simboliza con la **opción 1**: ∀x:[p(x)→q(x)]
- q se simboliza con la **opción 4**: ∃x:[p(x)∧q(x)]

**Tips clave:**
- "Todos/Los" → ∀ con →
- "Algunos/Existe" → ∃ con ∧
- Error común: usar ∃ con → (siempre verdadero si hay algo que no cumple el antecedente)

---

## Resumen de Respuestas — TIER 3 FINALES

| Batch | Ejercicio | Respuesta Clave |
|-------|-----------|-----------------|
| 22 | F01-Ej6 | Clases: {a, 5-a} — parábola simétrica |
| 22 | F03-Ej7 | [(x,y)] = {(±z, t) : paridad fija} |
| 22 | F04-Ej2 | FALSO — contraejemplo P₁=P₂ |
| 22 | F04-Ej4 | Gráfica derecha (líneas paralelas) es equivalencia |
| 22 | F05-Ej4 | Solo T (mismo año) es de equivalencia |
| 23 | F06-Ej2 | Simétrica SÍ; Reflexiva, Transitiva NO |
| 23 | F01-Ej8 | No es red ({4,6} no tiene supremo en A) |
| 23 | F02-Ej6 | d) 11 pares (estrella: 1 mínimo + 5 máximos) |
| 23 | F02-Ej8 | d) D₂₇₁₇ = 11·13·19 → 3 primos → |D|=8 |
| 23 | F03-Ej8 | Red algebraica → analizar complementos |
| 24 | F04-Ej5 | Sup={h}, Inf={a} para B={c,g} |
| 24 | F05-Ej5 | a) Red distributiva pero NO complementada |
| 24 | F06-Ej4 | d) Red distributiva pero no complementada |
| 24 | F01-Ej9 | aₙ = 2 - 2ⁿ |
| 24 | F02-Ej9 | aₙ = 3·5ⁿ - 2·4ⁿ |
| 25 | F03-Ej9 | aₙ - aₙ₋₁ = 12·5^(n-1) |
| 25 | F04-Ej6 | aₙ - aₙ₋₁ = 2^(n+1) |
| 25 | F05-Ej6 | b) Orden 1 no homogénea |
| 25 | F06-Ej10 | a) Solución particular |
| 25 | F01-Ej7 | 19 soluciones (mcd(4731,76513)=19) |
| 26 | F02-Ej7 | a) 6|(2m-4) ✓ |
| 26 | F03-Ej4 | Resto = 3 |
| 26 | F04-Ej3 | Imposible — mcd siempre es 1 |
| 26 | F06-Ej7 | c) 18 soluciones (mcd=18) |
| 26 | F06-Ej8 | d) n.a. (solo se sabe mcd|3) |
| 27 | F02-Ej1 | d) No categórico e inválido |
| 27 | F04-Ej1 | Inválido — contraejemplo con r(x) siempre falso |
| 27 | F06-Ej1 | p→opción 1 (∀→), q→opción 4 (∃∧) |
