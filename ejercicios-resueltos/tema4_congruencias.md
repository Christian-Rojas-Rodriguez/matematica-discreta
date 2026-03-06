# Tema 4 — Congruencias y Teoria de Numeros: Ejercicios Resueltos

> Guia de estudio para el final de Matematica Discreta (UNSAM)
> Ejercicios de la practica 6 (Teoria de Numeros) — Secciones III y IV

---

## TIER 1 — ALTA PROBABILIDAD DE APARECER EN EL EXAMEN

---

### Ejercicio 14 — Calculo de la funcion phi de Euler

**Enunciado:** Calcular φ(n) para los siguientes valores de n.

**Identificacion del tipo:** Calculo directo de la funcion indicatriz de Euler. Se usa la formula:
Si n = p1^{a1} · p2^{a2} · ... · pk^{ak}, entonces φ(n) = n · (1 - 1/p1) · (1 - 1/p2) · ... · (1 - 1/pk).

---

#### Ejercicio 14a — φ(450)

**Enunciado:** Calcular φ(450).

**Resolucion paso a paso:**

1. **Factorizar 450:**
   - 450 / 2 = 225
   - 225 / 3 = 75
   - 75 / 3 = 25
   - 25 / 5 = 5
   - 5 / 5 = 1
   - Entonces: 450 = 2 · 3^2 · 5^2

2. **Aplicar la formula de Euler:**
   - φ(450) = 450 · (1 - 1/2) · (1 - 1/3) · (1 - 1/5)
   - φ(450) = 450 · (1/2) · (2/3) · (4/5)

3. **Calcular paso a paso:**
   - 450 · (1/2) = 225
   - 225 · (2/3) = 450/3 = 150
   - 150 · (4/5) = 600/5 = 120

**Respuesta:** φ(450) = 120

---

#### Ejercicio 14b — φ(211)

**Enunciado:** Calcular φ(211).

**Resolucion paso a paso:**

1. **Verificar si 211 es primo:**
   - Necesitamos probar divisores primos hasta √211 ≈ 14.5, es decir: 2, 3, 5, 7, 11, 13.
   - 211 / 2 = 105.5 (no es entero)
   - 211 / 3 = 70.33... (no es entero; ademas 2+1+1 = 4, que no es multiplo de 3)
   - 211 / 5 = 42.2 (no es entero)
   - 211 / 7 = 30.14... (no es entero)
   - 211 / 11 = 19.18... (no es entero)
   - 211 / 13 = 16.23... (no es entero)
   - Ningun primo hasta √211 divide a 211, asi que **211 es primo**.

2. **Aplicar la propiedad para primos:**
   - Si p es primo, entonces φ(p) = p - 1.
   - φ(211) = 211 - 1 = 210

**Respuesta:** φ(211) = 210

---

#### Ejercicio 14c — φ(840)

**Enunciado:** Calcular φ(840).

**Resolucion paso a paso:**

1. **Factorizar 840:**
   - 840 / 2 = 420
   - 420 / 2 = 210
   - 210 / 2 = 105
   - 105 / 3 = 35
   - 35 / 5 = 7
   - 7 / 7 = 1
   - Entonces: 840 = 2^3 · 3 · 5 · 7

2. **Aplicar la formula de Euler:**
   - φ(840) = 840 · (1 - 1/2) · (1 - 1/3) · (1 - 1/5) · (1 - 1/7)
   - φ(840) = 840 · (1/2) · (2/3) · (4/5) · (6/7)

3. **Calcular paso a paso:**
   - 840 · (1/2) = 420
   - 420 · (2/3) = 840/3 = 280
   - 280 · (4/5) = 1120/5 = 224
   - 224 · (6/7) = 1344/7 = 192

**Respuesta:** φ(840) = 192

---

#### Ejercicio 14d — φ(500)

**Enunciado:** Calcular φ(500).

**Resolucion paso a paso:**

1. **Factorizar 500:**
   - 500 / 2 = 250
   - 250 / 2 = 125
   - 125 / 5 = 25
   - 25 / 5 = 5
   - 5 / 5 = 1
   - Entonces: 500 = 2^2 · 5^3

2. **Aplicar la formula de Euler:**
   - φ(500) = 500 · (1 - 1/2) · (1 - 1/5)
   - φ(500) = 500 · (1/2) · (4/5)

3. **Calcular paso a paso:**
   - 500 · (1/2) = 250
   - 250 · (4/5) = 1000/5 = 200

**Respuesta:** φ(500) = 200

---

#### Ejercicio 14e — φ(2019)

**Enunciado:** Calcular φ(2019).

**Resolucion paso a paso:**

1. **Factorizar 2019:**
   - 2019 / 3 = 673 (verificacion: 2+0+1+9 = 12, que es multiplo de 3)
   - Ahora verificar si 673 es primo. Probamos divisores primos hasta √673 ≈ 25.9: 2, 3, 5, 7, 11, 13, 17, 19, 23.
     - 673 / 2 = 336.5 (no)
     - 673 / 3 = 224.33... (no; 6+7+3 = 16, no multiplo de 3)
     - 673 / 5 = 134.6 (no)
     - 673 / 7 = 96.14... (no)
     - 673 / 11 = 61.18... (no)
     - 673 / 13 = 51.77... (no)
     - 673 / 17 = 39.59... (no)
     - 673 / 19 = 35.42... (no)
     - 673 / 23 = 29.26... (no)
   - **673 es primo.**
   - Entonces: 2019 = 3 · 673

2. **Aplicar la formula de Euler:**
   - φ(2019) = 2019 · (1 - 1/3) · (1 - 1/673)
   - φ(2019) = 2019 · (2/3) · (672/673)

3. **Calcular paso a paso:**
   - 2019 · (2/3) = 4038/3 = 1346
   - 1346 · (672/673) = ?
   - Observemos: 1346 = 2 · 673, entonces:
   - (2 · 673) · (672/673) = 2 · 672 = 1344

**Respuesta:** φ(2019) = 1344

---

#### Ejercicio 14f — φ(2401)

**Enunciado:** Calcular φ(2401).

**Resolucion paso a paso:**

1. **Factorizar 2401:**
   - 2401 / 7 = 343
   - 343 / 7 = 49
   - 49 / 7 = 7
   - 7 / 7 = 1
   - Entonces: 2401 = 7^4

2. **Aplicar la formula de Euler:**
   - φ(2401) = 2401 · (1 - 1/7)
   - φ(2401) = 2401 · (6/7)

3. **Calcular:**
   - 2401 · 6 / 7 = 2401/7 · 6 = 343 · 6 = 2058

   **Nota alternativa:** Para potencias de primos, φ(p^k) = p^k - p^{k-1} = p^{k-1}(p-1).
   - φ(7^4) = 7^3 · (7-1) = 343 · 6 = 2058

**Respuesta:** φ(2401) = 2058

**Tips para el examen (Ejercicio 14 completo):**
- Siempre comenzar factorizando n en primos. Si no se factoriza bien, todo el calculo sera incorrecto.
- Para primos: φ(p) = p - 1. Para potencias de primos: φ(p^k) = p^{k-1}(p-1).
- La formula multiplicativa φ(m·n) = φ(m)·φ(n) solo vale cuando mcd(m,n) = 1.
- Verificar con: la suma de φ(d) para todos los divisores d de n es igual a n.

**Errores comunes a evitar:**
- Confundir los factores primos (por ejemplo, olvidar que 2019 = 3·673 y no intentar dividir por 2 o 5).
- En la formula (1 - 1/p), usar TODOS los primos que aparecen en la factorizacion, incluso si su exponente es 1.
- Olvidar verificar si un numero es primo antes de aplicar la formula.
- Error aritmetico al multiplicar fracciones: siempre simplificar antes de multiplicar.

---

### Ejercicio 15 — Problemas inversos y propiedades de φ

**Enunciado:**

a) Hallar todos los n tales que φ(n) = 8.

b) Calcular φ(2^k) para todo k ≥ 1.

**Identificacion del tipo:** Problema inverso de la funcion φ (inciso a) y formula para potencias de primos (inciso b).

---

#### Ejercicio 15a — Hallar todos los n tales que φ(n) = 8

**Resolucion paso a paso:**

1. **Estrategia:** Necesitamos encontrar todos los enteros positivos n tales que φ(n) = 8. Analizamos por casos segun la forma de n.

2. **Caso n = potencia de primo (p^k):**
   - φ(p^k) = p^{k-1}(p-1) = 8
   - Si k = 1: p - 1 = 8, entonces p = 9. Pero 9 = 3^2 no es primo. Descartado.
   - Si k = 2: p(p-1) = 8. Probamos p = 2: 2·1 = 2 ≠ 8. p = 3: 3·2 = 6 ≠ 8. No hay solucion.
   - Si k = 3: p^2(p-1) = 8. p = 2: 4·1 = 4 ≠ 8. No hay solucion.
   - Si k = 4: p^3(p-1) = 8. p = 2: 8·1 = 8. SI! Entonces n = 2^4 = **16**.
   - Si k ≥ 5 con p = 2: 2^{k-1} ≥ 16 > 8. No hay mas soluciones.

3. **Caso n = 2·p^k con p primo impar:**
   - φ(2·p^k) = φ(2)·φ(p^k) = 1 · p^{k-1}(p-1) = 8 (ya que mcd(2, p^k) = 1 para p impar)
   - Es lo mismo que el caso anterior pero p debe ser impar.
   - Si k = 1: p - 1 = 8, p = 9 (no primo). Descartado.
   - No hay soluciones nuevas por esta via directa. Pero veamos otros enfoques.

4. **Busqueda sistematica:** Como φ(n) = 8 y φ es creciente en general, n no puede ser demasiado grande. Verificamos valores candidatos:

   - **n = 15:** 15 = 3 · 5. φ(15) = 15 · (1-1/3) · (1-1/5) = 15 · 2/3 · 4/5 = 8. SI.
   - **n = 16:** 16 = 2^4. φ(16) = 2^3 · 1 = 8. SI.
   - **n = 20:** 20 = 2^2 · 5. φ(20) = 20 · 1/2 · 4/5 = 8. SI.
   - **n = 24:** 24 = 2^3 · 3. φ(24) = 24 · 1/2 · 2/3 = 8. SI.
   - **n = 30:** 30 = 2 · 3 · 5. φ(30) = 30 · 1/2 · 2/3 · 4/5 = 8. SI.

   Verificamos que no hay mas: para n > 30, si n tiene al menos 3 primos distintos todos ≥ 2, 3, 5, necesitariamos φ(n) ≥ n · 1/2 · 2/3 · 4/5 · ... que crece con n. Para n = 32: φ(32) = 16. Para n = 25: φ(25) = 20. Para n = 40: φ(40) = 16. Ningun otro valor entre 1 y 30 (que no hayamos listado) cumple φ(n) = 8.

**Respuesta:** Los valores de n tales que φ(n) = 8 son: **n = 15, 16, 20, 24, 30**.

---

#### Ejercicio 15b — Calcular φ(2^k)

**Resolucion paso a paso:**

1. **Aplicar la formula para potencias de primos:**
   - Para p primo y k ≥ 1: φ(p^k) = p^{k-1} · (p - 1)

2. **Sustituir p = 2:**
   - φ(2^k) = 2^{k-1} · (2 - 1) = 2^{k-1} · 1 = 2^{k-1}

3. **Verificacion con ejemplos:**
   - φ(2^1) = φ(2) = 1 = 2^0. Correcto.
   - φ(2^2) = φ(4) = 2 = 2^1. Correcto (los coprimos con 4 en {1,2,3,4} son 1 y 3).
   - φ(2^3) = φ(8) = 4 = 2^2. Correcto (los coprimos con 8 en {1,...,8} son 1, 3, 5, 7).

**Respuesta:** φ(2^k) = 2^{k-1} para todo k ≥ 1.

**Tips para el examen (Ejercicio 15):**
- Para el problema inverso φ(n) = valor, conviene hacer una busqueda sistematica.
- Recordar que si n es impar y φ(n) = valor, entonces φ(2n) = valor tambien (porque φ(2) = 1 y mcd(2,n) = 1).
- Esto explica por que las soluciones vienen en pares: 15 y 30, o 16 y no 32 (porque 32 da φ = 16).

**Errores comunes a evitar:**
- Olvidar que φ(2n) = φ(n) cuando n es impar, lo cual genera soluciones adicionales.
- No verificar exhaustivamente todos los candidatos.

---

### Ejercicio 16 — Propiedades teoricas de φ

**Enunciado:**

a) Demostrar que si n es impar, entonces φ(2n) = φ(n).

b) Demostrar que si n > 2, entonces φ(n) es par.

**Identificacion del tipo:** Demostraciones teoricas sobre propiedades de la funcion φ de Euler. Se usan la multiplicatividad de φ y analisis por casos.

---

#### Ejercicio 16a — Si n es impar, entonces φ(2n) = φ(n)

**Resolucion paso a paso:**

1. **Hipotesis:** n es un entero positivo impar (es decir, 2 no divide a n).

2. **Como n es impar, mcd(2, n) = 1.** Esto es clave.

3. **Aplicar la propiedad multiplicativa de φ:**
   - Cuando mcd(a, b) = 1, se cumple que φ(a · b) = φ(a) · φ(b).
   - Como mcd(2, n) = 1, tenemos:
   - φ(2n) = φ(2) · φ(n)

4. **Calcular φ(2):**
   - φ(2) = 1 (el unico entero en {1, 2} que es coprimo con 2 es el 1).

5. **Concluir:**
   - φ(2n) = φ(2) · φ(n) = 1 · φ(n) = φ(n). QED.

---

#### Ejercicio 16b — Si n > 2, entonces φ(n) es par

**Resolucion paso a paso:**

1. **Analisis por casos segun la paridad de n:**

2. **Caso 1: n es par (n > 2).**
   - Escribimos n = 2^k · m donde k ≥ 1 y m es impar.
   - Si k ≥ 2: φ(n) contiene al factor φ(2^k) = 2^{k-1} que es ≥ 2, asi que φ(n) es par.
   - Si k = 1: n = 2m con m impar y m > 1 (porque n > 2).
     - φ(n) = φ(2m) = φ(2) · φ(m) = φ(m) (por el inciso a).
     - Como m > 1 y m es impar, caemos en el Caso 2.

3. **Caso 2: n es impar y n > 2.**
   - Entonces n tiene al menos un factor primo impar p.
   - Sea n = p^a · q donde mcd(p, q) = 1 (posiblemente q = 1, pero a ≥ 1).
   - φ(n) = φ(p^a) · φ(q) = p^{a-1} · (p - 1) · φ(q).
   - Como p es primo impar, p ≥ 3, entonces p - 1 ≥ 2 y p - 1 es **par**.
   - Por lo tanto, φ(n) tiene al factor (p - 1) que es par, asi que φ(n) es par.

4. **Conclusion:** En todos los casos, si n > 2, φ(n) es par. QED.

**Tips para el examen (Ejercicio 16):**
- La clave del inciso (a) es que la funcion φ es multiplicativa para coprimos.
- La clave del inciso (b) es que todo primo impar p tiene p - 1 par, y 2^k con k ≥ 2 contribuye factor par.
- Estas propiedades son utiles como lemas auxiliares en otros problemas.

**Errores comunes a evitar:**
- En (a), olvidar justificar por que mcd(2, n) = 1 (es porque n es impar).
- En (b), no cubrir todos los casos (par e impar).
- Confundir "φ es multiplicativa" con "φ es multiplicativa para CUALQUIER par de numeros". Solo vale cuando mcd(a,b) = 1.

---

### Ejercicio 18 — Restos usando el Teorema Pequeno de Fermat

**Enunciado:** Hallar los siguientes restos usando el Teorema Pequeno de Fermat.

**Identificacion del tipo:** Aplicacion directa del Teorema Pequeno de Fermat: si p es primo y mcd(a, p) = 1, entonces a^{p-1} ≡ 1 (mod p). El metodo consiste en reducir el exponente modulo (p-1).

---

#### Ejercicio 18a — 8^{44138} mod 11

**Enunciado:** Hallar el resto de dividir 8^{44138} por 11.

**Resolucion paso a paso:**

1. **Verificar hipotesis de Fermat:**
   - p = 11 es primo.
   - mcd(8, 11) = 1 (8 no es multiplo de 11).
   - Por Fermat: 8^{10} ≡ 1 (mod 11).

2. **Reducir el exponente modulo 10:**
   - Dividimos 44138 entre 10:
   - 44138 = 10 · 4413 + 8
   - Verificacion: 10 · 4413 = 44130. 44130 + 8 = 44138. Correcto.
   - Entonces: 8^{44138} = 8^{10·4413 + 8} = (8^{10})^{4413} · 8^8 ≡ 1^{4413} · 8^8 ≡ 8^8 (mod 11).

3. **Calcular 8^8 mod 11 por cuadrados sucesivos:**
   - 8^1 ≡ 8 (mod 11)
   - 8^2 = 64. 64 = 5 · 11 + 9. Entonces 8^2 ≡ 9 (mod 11).
   - 8^4 = (8^2)^2 ≡ 9^2 = 81 (mod 11). 81 = 7 · 11 + 4. Entonces 8^4 ≡ 4 (mod 11).
   - 8^8 = (8^4)^2 ≡ 4^2 = 16 (mod 11). 16 = 1 · 11 + 5. Entonces 8^8 ≡ 5 (mod 11).

**Respuesta:** 8^{44138} ≡ 5 (mod 11). El resto es **5**.

---

#### Ejercicio 18b — 5^{48963} mod 13

**Enunciado:** Hallar el resto de dividir 5^{48963} por 13.

**Resolucion paso a paso:**

1. **Verificar hipotesis de Fermat:**
   - p = 13 es primo.
   - mcd(5, 13) = 1.
   - Por Fermat: 5^{12} ≡ 1 (mod 13).

2. **Reducir el exponente modulo 12:**
   - 48963 / 12 = 4080 con resto r.
   - 12 · 4080 = 48960.
   - 48963 - 48960 = 3.
   - Entonces: 48963 = 12 · 4080 + 3.
   - 5^{48963} ≡ (5^{12})^{4080} · 5^3 ≡ 1 · 5^3 ≡ 5^3 (mod 13).

3. **Calcular 5^3 mod 13:**
   - 5^3 = 125.
   - 125 / 13 = 9 con resto: 13 · 9 = 117. 125 - 117 = 8.
   - 5^3 ≡ 8 (mod 13).

**Respuesta:** 5^{48963} ≡ 8 (mod 13). El resto es **8**.

---

#### Ejercicio 18c — 2^{94990} mod 47

**Enunciado:** Hallar el resto de dividir 2^{94990} por 47.

**Resolucion paso a paso:**

1. **Verificar hipotesis de Fermat:**
   - p = 47 es primo (verificar: no es divisible por 2, 3, 5; y √47 ≈ 6.86, asi que basta probar 2, 3, 5. Ninguno divide a 47).
   - mcd(2, 47) = 1.
   - Por Fermat: 2^{46} ≡ 1 (mod 47).

2. **Reducir el exponente modulo 46:**
   - 94990 / 46 = ?
   - 46 · 2000 = 92000.
   - 94990 - 92000 = 2990.
   - 46 · 65 = 2990. Verificacion: 46 · 60 = 2760, 46 · 5 = 230, 2760 + 230 = 2990. Correcto.
   - Entonces: 94990 = 46 · 2065 + 0.
   - Verificacion: 46 · 2065 = 46 · 2000 + 46 · 65 = 92000 + 2990 = 94990. Correcto.
   - El resto es 0.

3. **Concluir:**
   - 2^{94990} = (2^{46})^{2065} ≡ 1^{2065} ≡ 1 (mod 47).

**Respuesta:** 2^{94990} ≡ 1 (mod 47). El resto es **1**.

---

#### Ejercicio 18d — 3^{123159} mod 61

**Enunciado:** Hallar el resto de dividir 3^{123159} por 61.

**Resolucion paso a paso:**

1. **Verificar hipotesis de Fermat:**
   - p = 61 es primo (√61 ≈ 7.8; probamos 2, 3, 5, 7: ninguno divide a 61).
   - mcd(3, 61) = 1.
   - Por Fermat: 3^{60} ≡ 1 (mod 61).

2. **Reducir el exponente modulo 60:**
   - 123159 / 60 = ?
   - 60 · 2000 = 120000.
   - 123159 - 120000 = 3159.
   - 60 · 52 = 3120.
   - 3159 - 3120 = 39.
   - Entonces: 123159 = 60 · 2052 + 39.
   - Verificacion: 60 · 2052 = 123120. 123120 + 39 = 123159. Correcto.
   - 3^{123159} ≡ 3^{39} (mod 61).

3. **Calcular 3^{39} mod 61 por cuadrados sucesivos:**
   - Escribimos 39 en binario: 39 = 32 + 4 + 2 + 1 = 2^5 + 2^2 + 2^1 + 2^0.
   - Calculamos potencias de 3 modulo 61:
     - 3^1 ≡ 3 (mod 61)
     - 3^2 = 9 (mod 61)
     - 3^4 = (3^2)^2 = 9^2 = 81. 81 - 61 = 20. Entonces 3^4 ≡ 20 (mod 61).
     - 3^8 = (3^4)^2 = 20^2 = 400. 400 / 61 = 6 con resto: 61 · 6 = 366, 400 - 366 = 34. Entonces 3^8 ≡ 34 (mod 61).
     - 3^{16} = (3^8)^2 = 34^2 = 1156. 1156 / 61 = 18 con resto: 61 · 18 = 1098, 1156 - 1098 = 58. Entonces 3^{16} ≡ 58 (mod 61).
       - Nota: 58 ≡ -3 (mod 61). Esto puede simplificar calculos posteriores.
     - 3^{32} = (3^{16})^2 = 58^2 = 3364. 3364 / 61 = 55 con resto: 61 · 55 = 3355, 3364 - 3355 = 9. Entonces 3^{32} ≡ 9 (mod 61).
       - Alternativa: (-3)^2 = 9 (mod 61). Confirma.

   - Ahora: 3^{39} = 3^{32} · 3^{4} · 3^{2} · 3^{1}.
     - 3^{39} ≡ 9 · 20 · 9 · 3 (mod 61)
   - Calculamos paso a paso:
     - 9 · 20 = 180. 180 / 61 = 2 con resto: 61 · 2 = 122, 180 - 122 = 58. Entonces 9 · 20 ≡ 58 (mod 61).
     - 58 · 9 = 522. 522 / 61 = 8 con resto: 61 · 8 = 488, 522 - 488 = 34. Entonces 58 · 9 ≡ 34 (mod 61).
     - 34 · 3 = 102. 102 / 61 = 1 con resto: 102 - 61 = 41. Entonces 34 · 3 ≡ 41 (mod 61).

**Respuesta:** 3^{123159} ≡ 41 (mod 61). El resto es **41**.

---

#### Ejercicio 18e — 5^{28574} mod 17

**Enunciado:** Hallar el resto de dividir 5^{28574} por 17.

**Resolucion paso a paso:**

1. **Verificar hipotesis de Fermat:**
   - p = 17 es primo.
   - mcd(5, 17) = 1.
   - Por Fermat: 5^{16} ≡ 1 (mod 17).

2. **Reducir el exponente modulo 16:**
   - 28574 / 16 = ?
   - 16 · 1785 = 28560.
   - 28574 - 28560 = 14.
   - Entonces: 28574 = 16 · 1785 + 14.
   - 5^{28574} ≡ 5^{14} (mod 17).

3. **Calcular 5^{14} mod 17 por cuadrados sucesivos:**
   - 14 = 8 + 4 + 2 = 2^3 + 2^2 + 2^1.
   - Potencias de 5 modulo 17:
     - 5^1 ≡ 5 (mod 17)
     - 5^2 = 25. 25 - 17 = 8. Entonces 5^2 ≡ 8 (mod 17).
     - 5^4 = (5^2)^2 = 8^2 = 64. 64 / 17 = 3 con resto: 17 · 3 = 51, 64 - 51 = 13. Entonces 5^4 ≡ 13 (mod 17).
       - Nota: 13 ≡ -4 (mod 17).
     - 5^8 = (5^4)^2 = 13^2 = 169. 169 / 17 = 9 con resto: 17 · 9 = 153, 169 - 153 = 16. Entonces 5^8 ≡ 16 (mod 17).
       - Nota: 16 ≡ -1 (mod 17).

   - Ahora: 5^{14} = 5^8 · 5^4 · 5^2.
     - 5^{14} ≡ 16 · 13 · 8 (mod 17)
   - Calculamos paso a paso:
     - 16 · 13 = 208. 208 / 17 = 12 con resto: 17 · 12 = 204, 208 - 204 = 4. Entonces 16 · 13 ≡ 4 (mod 17).
       - Alternativa: (-1) · (-4) = 4 (mod 17). Confirma.
     - 4 · 8 = 32. 32 - 17 = 15. Entonces 4 · 8 ≡ 15 (mod 17).

**Respuesta:** 5^{28574} ≡ 15 (mod 17). El resto es **15**.

**Tips para el examen (Ejercicio 18 completo):**
- Siempre verificar: (1) que el modulo es primo, (2) que mcd(base, modulo) = 1.
- El algoritmo es siempre el mismo: reducir exponente modulo (p-1), luego calcular la potencia reducida.
- Para calcular potencias grandes modulo n, usar **exponenciacion por cuadrados sucesivos**: escribir el exponente en binario y multiplicar las potencias correspondientes.
- Usar equivalencias negativas (por ejemplo 58 ≡ -3 mod 61) para simplificar los cuadrados.

**Errores comunes a evitar:**
- Reducir el exponente modulo p en vez de modulo p-1. El Teorema dice a^{p-1} ≡ 1, no a^p ≡ 1.
- Olvidar que Fermat solo aplica cuando el modulo es PRIMO. Si no es primo, usar Euler-Fermat.
- Error al dividir el exponente: siempre verificar que cociente · divisor + resto = exponente original.
- No reducir los productos intermedios modulo p durante la exponenciacion (los numeros se hacen muy grandes).

---

### Ejercicio 19 — Restos usando el Teorema de Euler-Fermat

**Enunciado:** Hallar los siguientes restos usando el Teorema de Euler-Fermat.

**Identificacion del tipo:** Aplicacion del Teorema de Euler-Fermat: si mcd(a, n) = 1, entonces a^{φ(n)} ≡ 1 (mod n). Se usa cuando el modulo NO es primo.

---

#### Ejercicio 19a — 2^{340} mod 341

**Enunciado:** Hallar el resto de dividir 2^{340} por 341.

**Resolucion paso a paso:**

1. **Analizar el modulo:**
   - 341 NO es primo. Verifiquemos: 341 / 11 = 31. Entonces 341 = 11 · 31.
   - Verificacion: 11 · 31 = 11 · 30 + 11 = 330 + 11 = 341. Correcto.

2. **Calcular φ(341):**
   - 341 = 11 · 31 (ambos primos).
   - φ(341) = φ(11) · φ(31) = (11-1) · (31-1) = 10 · 30 = 300.

3. **Verificar hipotesis:**
   - mcd(2, 341) = 1 (2 no divide a 341, que es 11·31).
   - Por Euler-Fermat: 2^{300} ≡ 1 (mod 341).

4. **Reducir el exponente modulo 300:**
   - 340 = 300 · 1 + 40.
   - 2^{340} = 2^{300} · 2^{40} ≡ 1 · 2^{40} ≡ 2^{40} (mod 341).

5. **Calcular 2^{40} mod 341 por cuadrados sucesivos:**
   - 2^1 = 2
   - 2^2 = 4
   - 2^4 = 16
   - 2^8 = 256
   - 2^{16} = (2^8)^2 = 256^2 = 65536.
     - 65536 / 341 = 192 con resto: 341 · 192 = 65472. 65536 - 65472 = 64.
     - 2^{16} ≡ 64 (mod 341).
   - 2^{32} = (2^{16})^2 = 64^2 = 4096.
     - 4096 / 341 = 12 con resto: 341 · 12 = 4092. 4096 - 4092 = 4.
     - 2^{32} ≡ 4 (mod 341).
   - 2^{40} = 2^{32} · 2^8 = 4 · 256 = 1024.
     - 1024 / 341 = 3 con resto: 341 · 3 = 1023. 1024 - 1023 = 1.
     - 2^{40} ≡ 1 (mod 341).

**Respuesta:** 2^{340} ≡ 1 (mod 341). El resto es **1**.

**Nota interesante:** Este resultado muestra que 341 es un **pseudoprimo de Fermat** en base 2: cumple 2^{340} ≡ 1 (mod 341) como si fuera primo, pero 341 = 11 · 31 no es primo.

---

#### Ejercicio 19b — 4444^{4444} mod 9

**Enunciado:** Hallar el resto de dividir 4444^{4444} por 9.

**Resolucion paso a paso:**

1. **Reducir la base modulo 9:**
   - 4444 / 9 = 493 con resto: 9 · 493 = 4437. 4444 - 4437 = 7.
   - Entonces 4444 ≡ 7 (mod 9).
   - El problema se reduce a calcular 7^{4444} mod 9.

2. **Calcular φ(9):**
   - 9 = 3^2.
   - φ(9) = 9 · (1 - 1/3) = 9 · 2/3 = 6.
   - Alternativa: φ(3^2) = 3^1 · (3-1) = 3 · 2 = 6.

3. **Verificar hipotesis:**
   - mcd(7, 9) = 1. Correcto.
   - Por Euler-Fermat: 7^6 ≡ 1 (mod 9).

4. **Reducir el exponente modulo 6:**
   - 4444 / 6 = 740 con resto: 6 · 740 = 4440. 4444 - 4440 = 4.
   - Entonces: 4444 = 6 · 740 + 4.
   - 7^{4444} ≡ 7^4 (mod 9).

5. **Calcular 7^4 mod 9:**
   - 7^1 ≡ 7 (mod 9)
   - 7^2 = 49. 49 / 9 = 5 con resto 4. Entonces 7^2 ≡ 4 (mod 9).
   - 7^4 = (7^2)^2 ≡ 4^2 = 16 (mod 9). 16 - 9 = 7. Entonces 7^4 ≡ 7 (mod 9).

**Respuesta:** 4444^{4444} ≡ 7 (mod 9). El resto es **7**.

---

#### Ejercicio 19c — 7^{2019} mod 100

**Enunciado:** Hallar el resto de dividir 7^{2019} por 100.

**Resolucion paso a paso:**

1. **Calcular φ(100):**
   - 100 = 2^2 · 5^2.
   - φ(100) = 100 · (1 - 1/2) · (1 - 1/5) = 100 · 1/2 · 4/5 = 40.

2. **Verificar hipotesis:**
   - mcd(7, 100) = 1 (7 no divide a 100, y 100 = 4·25, ambos coprimos con 7).
   - Por Euler-Fermat: 7^{40} ≡ 1 (mod 100).

3. **Reducir el exponente modulo 40:**
   - 2019 / 40 = 50 con resto: 40 · 50 = 2000. 2019 - 2000 = 19.
   - Entonces: 2019 = 40 · 50 + 19.
   - 7^{2019} ≡ 7^{19} (mod 100).

4. **Calcular 7^{19} mod 100 por cuadrados sucesivos:**
   - 19 = 16 + 2 + 1 = 2^4 + 2^1 + 2^0.
   - Potencias de 7 modulo 100:
     - 7^1 = 7
     - 7^2 = 49
     - 7^4 = (7^2)^2 = 49^2 = 2401. 2401 mod 100 = 1 (ultimo dos digitos). Entonces 7^4 ≡ 1 (mod 100).
       - Verificacion: 2401 / 100 = 24 con resto 1. Correcto.

   - Esto simplifica mucho el calculo!
     - 7^8 = (7^4)^2 ≡ 1^2 = 1 (mod 100).
     - 7^{16} = (7^8)^2 ≡ 1^2 = 1 (mod 100).

   - Ahora: 7^{19} = 7^{16} · 7^{2} · 7^{1} ≡ 1 · 49 · 7 = 343 (mod 100).
     - 343 mod 100 = 43.

**Respuesta:** 7^{2019} ≡ 43 (mod 100). El resto es **43**.

**Nota:** Esto significa que los dos ultimos digitos de 7^{2019} son 43.

**Tips para el examen (Ejercicio 19 completo):**
- Cuando el modulo NO es primo, usar Euler-Fermat en vez de Fermat.
- SIEMPRE reducir la base modulo n primero (como hicimos con 4444 mod 9 = 7). Esto simplifica enormemente.
- Despues reducir el exponente modulo φ(n).
- Si durante la exponenciacion aparece una potencia ≡ 1, todas las potencias mayores seran tambien ≡ 1, lo cual simplifica mucho (como 7^4 ≡ 1 mod 100).

**Errores comunes a evitar:**
- Confundir Fermat (modulo primo, exponente p-1) con Euler-Fermat (modulo cualquiera, exponente φ(n)).
- Olvidar reducir la base antes de empezar la exponenciacion.
- Calcular mal φ(n) — siempre factorizar primero.
- En 19b, intentar calcular 4444^{4444} directamente sin reducir a 7^{4444}.

---

### Ejercicio 21 — Ecuaciones de congruencia lineal ax ≡ b (mod n)

**Enunciado:** Resolver las siguientes ecuaciones de congruencia.

**Identificacion del tipo:** Ecuaciones de congruencia lineal. El metodo general es:
- Calcular d = mcd(a, n).
- Si d no divide a b: **no tiene solucion**.
- Si d divide a b: tiene exactamente **d soluciones principales** (incongruentes modulo n). Se simplifica dividiendo toda la ecuacion por d, y se resuelve la ecuacion simplificada usando el inverso multiplicativo (via Euclides extendido).

---

#### Ejercicio 21a — 99x ≡ 25 (mod 140)

**Enunciado:** Resolver 99x ≡ 25 (mod 140).

**Resolucion paso a paso:**

1. **Calcular d = mcd(99, 140) usando Euclides:**
   - 140 = 1 · 99 + 41
   - 99 = 2 · 41 + 17
   - 41 = 2 · 17 + 7
   - 17 = 2 · 7 + 3
   - 7 = 2 · 3 + 1
   - 3 = 3 · 1 + 0
   - d = mcd(99, 140) = 1.

2. **Verificar existencia de solucion:**
   - d = 1 divide a 25. Tiene solucion. Ademas, como d = 1, la solucion es **unica** modulo 140.

3. **Encontrar el inverso de 99 modulo 140 usando Euclides extendido:**
   - Necesitamos expresar 1 = mcd(99, 140) como combinacion lineal de 99 y 140.
   - Retrocedemos en el algoritmo de Euclides:
     - 1 = 7 - 2 · 3
     - 3 = 17 - 2 · 7, entonces: 1 = 7 - 2 · (17 - 2 · 7) = 5 · 7 - 2 · 17
     - 7 = 41 - 2 · 17, entonces: 1 = 5 · (41 - 2 · 17) - 2 · 17 = 5 · 41 - 12 · 17
     - 17 = 99 - 2 · 41, entonces: 1 = 5 · 41 - 12 · (99 - 2 · 41) = 29 · 41 - 12 · 99
     - 41 = 140 - 1 · 99, entonces: 1 = 29 · (140 - 99) - 12 · 99 = 29 · 140 - 41 · 99

   - Entonces: -41 · 99 + 29 · 140 = 1.
   - Es decir: -41 · 99 ≡ 1 (mod 140).
   - El inverso de 99 modulo 140 es -41 ≡ 140 - 41 = 99 (mod 140).
   - Verificacion: 99 · 99 = 9801. 9801 / 140 = 70 con resto: 140 · 70 = 9800. 9801 - 9800 = 1. Correcto: 99 · 99 ≡ 1 (mod 140).

4. **Resolver la ecuacion:**
   - 99x ≡ 25 (mod 140)
   - Multiplicamos ambos lados por 99 (el inverso de 99):
   - x ≡ 99 · 25 (mod 140)
   - 99 · 25 = 2475.
   - 2475 / 140 = 17 con resto: 140 · 17 = 2380. 2475 - 2380 = 95.
   - x ≡ 95 (mod 140).

5. **Verificacion:**
   - 99 · 95 = 9405.
   - 9405 / 140 = 67 con resto: 140 · 67 = 9380. 9405 - 9380 = 25.
   - 99 · 95 ≡ 25 (mod 140). Correcto.

**Respuesta:** x ≡ 95 (mod 140). La unica solucion principal es **x = 95**.

---

#### Ejercicio 21b — 33x ≡ 24 (mod 15)

**Enunciado:** Resolver 33x ≡ 24 (mod 15).

**Resolucion paso a paso:**

1. **Calcular d = mcd(33, 15):**
   - 33 = 2 · 15 + 3
   - 15 = 5 · 3 + 0
   - d = mcd(33, 15) = 3.

2. **Verificar existencia de solucion:**
   - d = 3. ¿3 divide a 24? 24 / 3 = 8. SI. Tiene solucion.
   - Hay **3 soluciones principales** (modulo 15).

3. **Simplificar la ecuacion dividiendo por d = 3:**
   - (33/3)x ≡ (24/3) (mod 15/3)
   - 11x ≡ 8 (mod 5)

4. **Reducir 11 modulo 5:**
   - 11 = 2 · 5 + 1, entonces 11 ≡ 1 (mod 5).
   - La ecuacion se convierte en: 1 · x ≡ 8 (mod 5), es decir: x ≡ 8 (mod 5).
   - 8 = 1 · 5 + 3, entonces x ≡ 3 (mod 5).

5. **Obtener todas las soluciones modulo 15:**
   - La solucion base es x_0 = 3.
   - Las 3 soluciones principales modulo 15 son:
     - x_0 = 3
     - x_0 + 15/3 = 3 + 5 = 8
     - x_0 + 2 · (15/3) = 3 + 10 = 13

6. **Verificacion de cada solucion:**
   - 33 · 3 = 99. 99 / 15 = 6 con resto 9. Pero 24 mod 15 = 9. Entonces 33 · 3 ≡ 9 ≡ 24 (mod 15). Correcto.
   - 33 · 8 = 264. 264 / 15 = 17 con resto 9. 264 - 255 = 9 ≡ 24 (mod 15). Correcto.
   - 33 · 13 = 429. 429 / 15 = 28 con resto 9. 429 - 420 = 9 ≡ 24 (mod 15). Correcto.

**Respuesta:** Las 3 soluciones principales son **x ≡ 3, 8, 13 (mod 15)**.

---

#### Ejercicio 21c — 35x ≡ 14 (mod 182)

**Enunciado:** Resolver 35x ≡ 14 (mod 182).

**Resolucion paso a paso:**

1. **Calcular d = mcd(35, 182):**
   - 182 = 5 · 35 + 7
   - 35 = 5 · 7 + 0
   - d = mcd(35, 182) = 7.

2. **Verificar existencia de solucion:**
   - d = 7. ¿7 divide a 14? 14 / 7 = 2. SI. Tiene solucion.
   - Hay **7 soluciones principales** (modulo 182).

3. **Simplificar dividiendo por d = 7:**
   - (35/7)x ≡ (14/7) (mod 182/7)
   - 5x ≡ 2 (mod 26)

4. **Encontrar el inverso de 5 modulo 26:**
   - Usamos Euclides extendido para mcd(5, 26):
     - 26 = 5 · 5 + 1
     - 5 = 5 · 1 + 0
   - Retrocediendo: 1 = 26 - 5 · 5.
   - Entonces: -5 · 5 ≡ 1 (mod 26), es decir: (-5) · 5 ≡ 1 (mod 26).
   - El inverso de 5 modulo 26 es -5 ≡ 26 - 5 = 21 (mod 26).
   - Verificacion: 5 · 21 = 105. 105 / 26 = 4 con resto 1. Correcto.

5. **Resolver:**
   - x ≡ 21 · 2 (mod 26) = 42 (mod 26).
   - 42 - 26 = 16.
   - x ≡ 16 (mod 26).

6. **Obtener todas las soluciones modulo 182:**
   - La solucion base es x_0 = 16.
   - El paso es 182/7 = 26.
   - Las 7 soluciones principales modulo 182 son:
     - x_0 = 16
     - x_0 + 26 = 42
     - x_0 + 52 = 68
     - x_0 + 78 = 94
     - x_0 + 104 = 120
     - x_0 + 130 = 146
     - x_0 + 156 = 172

7. **Verificacion (una muestra):**
   - 35 · 16 = 560. 560 / 182 = 3 con resto: 182 · 3 = 546. 560 - 546 = 14. Correcto: 35 · 16 ≡ 14 (mod 182).
   - 35 · 42 = 1470. 1470 / 182 = 8 con resto: 182 · 8 = 1456. 1470 - 1456 = 14. Correcto.

**Respuesta:** Las 7 soluciones principales son **x ≡ 16, 42, 68, 94, 120, 146, 172 (mod 182)**.

---

#### Ejercicio 21d — 48x ≡ 50 (mod 98)

**Enunciado:** Resolver 48x ≡ 50 (mod 98).

**Resolucion paso a paso:**

1. **Calcular d = mcd(48, 98):**
   - 98 = 2 · 48 + 2
   - 48 = 24 · 2 + 0
   - d = mcd(48, 98) = 2.

2. **Verificar existencia de solucion:**
   - d = 2. ¿2 divide a 50? 50 / 2 = 25. SI. Tiene solucion.
   - Hay **2 soluciones principales** (modulo 98).

3. **Simplificar dividiendo por d = 2:**
   - (48/2)x ≡ (50/2) (mod 98/2)
   - 24x ≡ 25 (mod 49)

4. **Encontrar el inverso de 24 modulo 49:**
   - Euclides para mcd(24, 49):
     - 49 = 2 · 24 + 1
     - 24 = 24 · 1 + 0
   - Retrocediendo: 1 = 49 - 2 · 24.
   - Entonces: -2 · 24 ≡ 1 (mod 49).
   - El inverso de 24 modulo 49 es -2 ≡ 49 - 2 = 47 (mod 49).
   - Verificacion: 24 · 47 = 1128. 1128 / 49 = 23 con resto: 49 · 23 = 1127. 1128 - 1127 = 1. Correcto.

5. **Resolver:**
   - x ≡ 47 · 25 (mod 49).
   - 47 · 25 = 1175.
   - 1175 / 49 = 23 con resto: 49 · 23 = 1127. 1175 - 1127 = 48.
   - Alternativa: 47 ≡ -2 (mod 49), entonces (-2) · 25 = -50 ≡ 49 - 50 + 49 = 48 (mod 49). Mas precisamente: -50 + 2·49 = -50 + 98 = 48.
   - x ≡ 48 (mod 49).

6. **Obtener todas las soluciones modulo 98:**
   - La solucion base es x_0 = 48.
   - El paso es 98/2 = 49.
   - Las 2 soluciones principales:
     - x_0 = 48
     - x_0 + 49 = 97

7. **Verificacion:**
   - 48 · 48 = 2304. 2304 / 98 = 23 con resto: 98 · 23 = 2254. 2304 - 2254 = 50. Correcto.
   - 48 · 97 = 4656. 4656 / 98 = 47 con resto: 98 · 47 = 4606. 4656 - 4606 = 50. Correcto.

**Respuesta:** Las 2 soluciones principales son **x ≡ 48, 97 (mod 98)**.

---

#### Ejercicio 21e — 64x ≡ 18 (mod 96)

**Enunciado:** Resolver 64x ≡ 18 (mod 96).

**Resolucion paso a paso:**

1. **Calcular d = mcd(64, 96):**
   - 96 = 1 · 64 + 32
   - 64 = 2 · 32 + 0
   - d = mcd(64, 96) = 32.

2. **Verificar existencia de solucion:**
   - d = 32. ¿32 divide a 18?
   - 18 / 32 = 0.5625. NO es entero.
   - 32 **no divide** a 18.

3. **Conclusion:**
   - La ecuacion **NO TIENE SOLUCION**.

**Respuesta:** La ecuacion 64x ≡ 18 (mod 96) **no tiene solucion**.

**Justificacion detallada:** Para que ax ≡ b (mod n) tenga solucion, es condicion necesaria y suficiente que mcd(a,n) | b. Aqui mcd(64, 96) = 32, y 32 no divide a 18 (ya que 18 = 0 · 32 + 18, y 0 < 18 < 32), por lo que no existe ningun entero x que satisfaga la congruencia.

---

#### Ejercicio 21f — 15x ≡ 125 (mod 140)

**Enunciado:** Resolver 15x ≡ 125 (mod 140).

**Resolucion paso a paso:**

1. **Calcular d = mcd(15, 140):**
   - 140 = 9 · 15 + 5
   - 15 = 3 · 5 + 0
   - d = mcd(15, 140) = 5.

2. **Verificar existencia de solucion:**
   - d = 5. ¿5 divide a 125? 125 / 5 = 25. SI. Tiene solucion.
   - Hay **5 soluciones principales** (modulo 140).

3. **Simplificar dividiendo por d = 5:**
   - (15/5)x ≡ (125/5) (mod 140/5)
   - 3x ≡ 25 (mod 28)

4. **Encontrar el inverso de 3 modulo 28:**
   - Euclides para mcd(3, 28):
     - 28 = 9 · 3 + 1
     - 3 = 3 · 1 + 0
   - Retrocediendo: 1 = 28 - 9 · 3.
   - Entonces: -9 · 3 ≡ 1 (mod 28).
   - El inverso de 3 modulo 28 es -9 ≡ 28 - 9 = 19 (mod 28).
   - Verificacion: 3 · 19 = 57. 57 / 28 = 2 con resto 1. Correcto.

5. **Resolver:**
   - x ≡ 19 · 25 (mod 28).
   - 19 · 25 = 475.
   - 475 / 28 = 16 con resto: 28 · 16 = 448. 475 - 448 = 27.
   - x ≡ 27 (mod 28).

6. **Obtener todas las soluciones modulo 140:**
   - La solucion base es x_0 = 27.
   - El paso es 140/5 = 28.
   - Las 5 soluciones principales:
     - x_0 = 27
     - x_0 + 28 = 55
     - x_0 + 56 = 83
     - x_0 + 84 = 111
     - x_0 + 112 = 139

7. **Verificacion (una muestra):**
   - 15 · 27 = 405. 405 / 140 = 2 con resto: 140 · 2 = 280. 405 - 280 = 125. Correcto.
   - 15 · 55 = 825. 825 / 140 = 5 con resto: 140 · 5 = 700. 825 - 700 = 125. Correcto.

**Respuesta:** Las 5 soluciones principales son **x ≡ 27, 55, 83, 111, 139 (mod 140)**.

**Tips para el examen (Ejercicio 21 completo):**
- Siempre empezar con mcd(a, n). Si d no divide a b, la respuesta es directa: no tiene solucion.
- Despues de simplificar, el nuevo modulo es n/d y la ecuacion tiene coeficiente coprimo con el nuevo modulo, asi que se puede encontrar el inverso.
- Las soluciones se obtienen sumando n/d a la solucion base, hasta completar d soluciones.
- SIEMPRE verificar al menos una solucion sustituyendo en la ecuacion original.

**Errores comunes a evitar:**
- Olvidar dividir TAMBIEN el modulo por d (dividir solo a y b, pero no n).
- Confundir el numero de soluciones: son d = mcd(a,n) soluciones modulo n.
- Dar la solucion modulo n/d en vez de modulo n. La pregunta pide soluciones modulo n original.
- No verificar la respuesta. Un error aritmetico en Euclides extendido se propaga a todo el resultado.

---

### Ejercicio 22 — Verdadero o Falso sobre congruencias lineales

**Enunciado:** Determinar si las siguientes afirmaciones son verdaderas o falsas. Justificar.

**Identificacion del tipo:** Ejercicio de analisis y verificacion sobre ecuaciones de congruencia lineal. Se usan los criterios de existencia y unicidad de soluciones, y verificacion directa.

---

#### Ejercicio 22a — 102x ≡ 35 (mod 342) no tiene solucion

**Enunciado:** V o F: "La ecuacion 102x ≡ 35 (mod 342) no tiene solucion."

**Resolucion paso a paso:**

1. **Calcular d = mcd(102, 342):**
   - 342 = 3 · 102 + 36
   - 102 = 2 · 36 + 30
   - 36 = 1 · 30 + 6
   - 30 = 5 · 6 + 0
   - d = mcd(102, 342) = 6.

2. **Verificar si d divide a b:**
   - ¿6 divide a 35?
   - 35 / 6 = 5.833... NO es entero.
   - 6 **no divide** a 35.

3. **Conclusion:** Como mcd(102, 342) = 6 y 6 no divide a 35, la ecuacion no tiene solucion.

**Respuesta:** **VERDADERO.**

---

#### Ejercicio 22b — 112x ≡ 392 (mod 91) tiene 7 soluciones principales

**Enunciado:** V o F: "La ecuacion 112x ≡ 392 (mod 91) tiene 7 soluciones principales."

**Resolucion paso a paso:**

1. **Calcular d = mcd(112, 91):**
   - 112 = 1 · 91 + 21
   - 91 = 4 · 21 + 7
   - 21 = 3 · 7 + 0
   - d = mcd(112, 91) = 7.

2. **Verificar si d divide a b:**
   - ¿7 divide a 392?
   - 392 / 7 = 56. SI, es entero.

3. **Numero de soluciones principales:**
   - Cuando mcd(a,n) | b, hay exactamente d = mcd(a,n) soluciones principales modulo n.
   - Aqui d = 7, asi que hay 7 soluciones principales modulo 91.

**Respuesta:** **VERDADERO.**

---

#### Ejercicio 22c — x = 62 es solucion de 72x ≡ 54 (mod 126)

**Enunciado:** V o F: "x = 62 es solucion de 72x ≡ 54 (mod 126)."

**Resolucion paso a paso:**

1. **Sustituir x = 62 en la ecuacion:**
   - 72 · 62 = ?
   - 72 · 60 = 4320
   - 72 · 2 = 144
   - 72 · 62 = 4320 + 144 = 4464.

2. **Calcular 4464 mod 126:**
   - 4464 / 126 = ?
   - 126 · 35 = 4410.
   - 4464 - 4410 = 54.
   - Entonces 4464 ≡ 54 (mod 126).

3. **Verificar:**
   - ¿72 · 62 ≡ 54 (mod 126)? SI, 4464 ≡ 54 (mod 126).

**Respuesta:** **VERDADERO.**

---

#### Ejercicio 22d — x = 56 es solucion de 78x ≡ 84 (mod 102)

**Enunciado:** V o F: "x = 56 es solucion de 78x ≡ 84 (mod 102)."

**Resolucion paso a paso:**

1. **Sustituir x = 56 en la ecuacion:**
   - 78 · 56 = ?
   - 78 · 50 = 3900
   - 78 · 6 = 468
   - 78 · 56 = 3900 + 468 = 4368.

2. **Calcular 4368 mod 102:**
   - 4368 / 102 = ?
   - 102 · 42 = 4284.
   - 4368 - 4284 = 84.
   - Entonces 4368 ≡ 84 (mod 102).

3. **Verificar:**
   - ¿78 · 56 ≡ 84 (mod 102)? SI, 4368 ≡ 84 (mod 102).

**Respuesta:** **VERDADERO.**

---

#### Ejercicio 22e — 102x ≡ 24 (mod 42) tiene 6 soluciones principales

**Enunciado:** V o F: "La ecuacion 102x ≡ 24 (mod 42) tiene 6 soluciones principales."

**Resolucion paso a paso:**

1. **Calcular d = mcd(102, 42):**
   - 102 = 2 · 42 + 18
   - 42 = 2 · 18 + 6
   - 18 = 3 · 6 + 0
   - d = mcd(102, 42) = 6.

2. **Verificar si d divide a b:**
   - ¿6 divide a 24?
   - 24 / 6 = 4. SI.

3. **Numero de soluciones principales:**
   - d = 6 y 6 | 24, asi que hay 6 soluciones principales modulo 42.

**Respuesta:** **VERDADERO.**

**Tips para el examen (Ejercicio 22 completo):**
- Para V/F sobre existencia de solucion: calcular mcd y verificar divisibilidad. Es rapido.
- Para V/F sobre numero de soluciones: el numero es exactamente mcd(a,n) (siempre que haya solucion).
- Para V/F sobre si un valor particular es solucion: simplemente sustituir y verificar la congruencia.
- En un examen, estos ejercicios son rapidos si se dominan los criterios.

**Errores comunes a evitar:**
- Confundir "numero de soluciones" con "numero de soluciones modulo n/d". Las soluciones principales siempre se cuentan modulo n.
- Error aritmetico en la verificacion directa. Hacer la multiplicacion con cuidado.
- Olvidar que hay que verificar d | b para que haya solucion, no solo calcular d.

---

## RESUMEN DE FORMULAS Y TEOREMAS CLAVE

### Funcion phi de Euler
- **Definicion:** φ(n) = cantidad de enteros en {1, 2, ..., n} que son coprimos con n.
- **Formula:** Si n = p1^{a1} · p2^{a2} · ... · pk^{ak}, entonces:
  φ(n) = n · (1 - 1/p1) · (1 - 1/p2) · ... · (1 - 1/pk)
- **Casos especiales:**
  - φ(1) = 1
  - φ(p) = p - 1 (p primo)
  - φ(p^k) = p^{k-1}(p - 1) (p primo, k ≥ 1)
- **Multiplicatividad:** Si mcd(m, n) = 1, entonces φ(m·n) = φ(m)·φ(n).
- **Propiedad:** Si n es impar, φ(2n) = φ(n).
- **Propiedad:** Si n > 2, φ(n) es par.

### Teorema Pequeno de Fermat
- **Hipotesis:** p primo, mcd(a, p) = 1.
- **Tesis:** a^{p-1} ≡ 1 (mod p).
- **Uso:** Reducir a^k mod p calculando k mod (p-1).

### Teorema de Euler-Fermat
- **Hipotesis:** mcd(a, n) = 1.
- **Tesis:** a^{φ(n)} ≡ 1 (mod n).
- **Uso:** Reducir a^k mod n calculando k mod φ(n).
- **Nota:** Generaliza a Fermat (cuando n = p primo, φ(p) = p-1).

### Ecuacion de congruencia lineal ax ≡ b (mod n)
- **Condicion de existencia:** Tiene solucion si y solo si d | b, donde d = mcd(a, n).
- **Numero de soluciones:** Si tiene solucion, hay exactamente d soluciones principales (modulo n).
- **Metodo de resolucion:**
  1. Calcular d = mcd(a, n).
  2. Verificar d | b.
  3. Simplificar: (a/d)x ≡ (b/d) (mod n/d).
  4. Encontrar el inverso de (a/d) modulo (n/d) usando Euclides extendido.
  5. Obtener x_0 = inverso · (b/d) mod (n/d).
  6. Las d soluciones son: x_0, x_0 + n/d, x_0 + 2·(n/d), ..., x_0 + (d-1)·(n/d) (todas mod n).

### Exponenciacion modular por cuadrados sucesivos
1. Escribir el exponente en binario: k = suma de potencias de 2.
2. Calcular a^1, a^2, a^4, a^8, ... mod n (cada uno es el cuadrado del anterior, reducido mod n).
3. Multiplicar las potencias correspondientes a los bits encendidos, reduciendo mod n en cada paso.
