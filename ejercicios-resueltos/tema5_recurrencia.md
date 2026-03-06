# Tema 5 — Relaciones de Recurrencia: Ejercicios Resueltos

> Guia de estudio para el final de Matematica Discreta (UNSAM)
> Ejercicios de la practica 9 (Recurrencia)

---

## TIER 1 — ALTA PRIORIDAD

---

### Ejercicio 8a — Recurrencia lineal homogenea de orden 2 con raices reales distintas

**Enunciado:** Resolver a_n = 2·a_{n-1} + 8·a_{n-2}, con a_0 = 1 y a_1 = 10. Probar por induccion.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 2, con coeficientes constantes. Se resuelve hallando la ecuacion caracteristica, encontrando sus raices, armando la solucion general y usando las condiciones iniciales para determinar las constantes.

**Resolucion paso a paso:**

**Paso 1 — Reescribir en forma estandar:**

Pasamos todo al mismo lado:

a_n - 2·a_{n-1} - 8·a_{n-2} = 0

**Paso 2 — Plantear la ecuacion caracteristica:**

Reemplazamos a_n por r^n, a_{n-1} por r^{n-1}, a_{n-2} por r^{n-2}:

r^n - 2·r^{n-1} - 8·r^{n-2} = 0

Dividimos todo por r^{n-2} (que es distinto de cero porque r = 0 no es solucion):

r^2 - 2r - 8 = 0

**Paso 3 — Resolver la ecuacion caracteristica:**

Usamos la formula cuadratica:

r = (2 +/- sqrt(4 + 32)) / 2 = (2 +/- sqrt(36)) / 2 = (2 +/- 6) / 2

- r_1 = (2 + 6) / 2 = 8 / 2 = **4**
- r_2 = (2 - 6) / 2 = -4 / 2 = **-2**

Las raices son r_1 = 4 y r_2 = -2 (reales y distintas).

**Paso 4 — Escribir la solucion general:**

Como las raices son reales y distintas, la solucion general es:

a_n = C_1 · 4^n + C_2 · (-2)^n

**Paso 5 — Usar las condiciones iniciales para hallar C_1 y C_2:**

Con a_0 = 1:

a_0 = C_1 · 4^0 + C_2 · (-2)^0 = C_1 · 1 + C_2 · 1 = C_1 + C_2 = 1  ... (I)

Con a_1 = 10:

a_1 = C_1 · 4^1 + C_2 · (-2)^1 = 4·C_1 + (-2)·C_2 = 4·C_1 - 2·C_2 = 10  ... (II)

**Paso 6 — Resolver el sistema de ecuaciones:**

De (I): C_1 = 1 - C_2

Sustituimos en (II):

4·(1 - C_2) - 2·C_2 = 10
4 - 4·C_2 - 2·C_2 = 10
4 - 6·C_2 = 10
-6·C_2 = 6
C_2 = -1

Entonces: C_1 = 1 - (-1) = 2

**Paso 7 — Escribir la solucion particular:**

**a_n = 2 · 4^n + (-1) · (-2)^n = 2 · 4^n - (-2)^n**

**Paso 8 — Verificacion con los primeros terminos:**

- a_0 = 2 · 4^0 - (-2)^0 = 2 · 1 - 1 = 2 - 1 = 1 ✓
- a_1 = 2 · 4^1 - (-2)^1 = 2 · 4 - (-2) = 8 + 2 = 10 ✓
- a_2 = 2 · a_1 + 8 · a_0 = 2 · 10 + 8 · 1 = 20 + 8 = 28
- Verificacion: a_2 = 2 · 4^2 - (-2)^2 = 2 · 16 - 4 = 32 - 4 = 28 ✓

**Paso 9 — Demostracion por induccion:**

Queremos probar que a_n = 2 · 4^n - (-2)^n satisface a_n = 2·a_{n-1} + 8·a_{n-2} para todo n >= 2.

**Caso base (n = 2):**

- Lado izquierdo: a_2 = 2 · 4^2 - (-2)^2 = 32 - 4 = 28
- Lado derecho: 2 · a_1 + 8 · a_0 = 2 · 10 + 8 · 1 = 28
- 28 = 28 ✓

**Caso base (n = 3):**

- a_3 por formula: 2 · 4^3 - (-2)^3 = 2 · 64 - (-8) = 128 + 8 = 136
- a_3 por recurrencia: 2 · a_2 + 8 · a_1 = 2 · 28 + 8 · 10 = 56 + 80 = 136 ✓

**Hipotesis inductiva:** Supongamos que para todo k <= n (con n >= 3) se cumple a_k = 2 · 4^k - (-2)^k.

**Paso inductivo (probar para n+1):**

a_{n+1} = 2 · a_n + 8 · a_{n-1}

Por hipotesis inductiva:

a_{n+1} = 2 · [2 · 4^n - (-2)^n] + 8 · [2 · 4^{n-1} - (-2)^{n-1}]

Expandimos:

= 4 · 4^n - 2 · (-2)^n + 16 · 4^{n-1} - 8 · (-2)^{n-1}

Simplificamos cada termino:

- 4 · 4^n = 4^{n+1}
- 16 · 4^{n-1} = 4^2 · 4^{n-1} = 4^{n+1}
- -2 · (-2)^n = (-1) · 2 · (-2)^n = (-1) · (-1) · (-2) · (-2)^n ... Mejor asi: -2 · (-2)^n = (-2)^1 · (-2)^n · (-1)...

Vamos con mas cuidado:

- -2 · (-2)^n = -(2 · (-2)^n)

Notemos que 2 = -(-2), entonces: 2 · (-2)^n = -(-2) · (-2)^n = -(-2)^{n+1}

Por lo tanto: -2 · (-2)^n = -(-(-2)^{n+1}) = (-2)^{n+1}

Hmm, hagamoslo directamente:

-2 · (-2)^n = (-1) · 2 · (-2)^n

Y: -8 · (-2)^{n-1} = (-1) · 8 · (-2)^{n-1} = (-1) · (-2)^3 · (-1)^3 · (-2)^{n-1}...

Mejor enfoque directo. Notemos que:

- (-2)^1 · (-2)^n = (-2)^{n+1}
- (-2)^3 · (-2)^{n-1}... No, vamos con numeros:

-2 · (-2)^n: escribamos (-2) = (-2)^1, pero tenemos -2 que es (-1)·2 y no es lo mismo que (-2). Sin embargo, -2 = (-2)^1. Si: -2 = (-2). Entonces:

-2 · (-2)^n = (-2)^1 · (-2)^n = (-2)^{n+1}

Y: -8 · (-2)^{n-1} = (-8) · (-2)^{n-1} = (-2)^3 · (-2)^{n-1} = (-2)^{n+2}

Volvemos a la expresion:

a_{n+1} = 4^{n+1} + (-2)^{n+1} + 4^{n+1} + (-2)^{n+2}

Hmm, esto no cierra bien. Replanteemos con mas cuidado:

a_{n+1} = 2·[2·4^n - (-2)^n] + 8·[2·4^{n-1} - (-2)^{n-1}]

= 4·4^n - 2·(-2)^n + 16·4^{n-1} - 8·(-2)^{n-1}

Terminos con base 4:
- 4·4^n + 16·4^{n-1} = 4^{n+1} + 4^2·4^{n-1} = 4^{n+1} + 4^{n+1} = 2·4^{n+1}

Terminos con base (-2):
- -2·(-2)^n - 8·(-2)^{n-1}
- = (-2)^{n+1} - 8·(-2)^{n-1}

Ahora, -8·(-2)^{n-1}: notemos que 8 = 2^3 y (-2)^{n-1} = (-1)^{n-1} · 2^{n-1}, entonces:
-8·(-2)^{n-1} = -2^3 · (-1)^{n-1} · 2^{n-1} = -(-1)^{n-1} · 2^{n+2}

Y (-2)^{n+1} = (-1)^{n+1} · 2^{n+1}

Sumamos: (-1)^{n+1}·2^{n+1} - (-1)^{n-1}·2^{n+2}

Factor comun (-1)^{n-1}·2^{n+1}:
= (-1)^{n-1}·2^{n+1}·[(-1)^2 - 2]
= (-1)^{n-1}·2^{n+1}·[1 - 2]
= (-1)^{n-1}·2^{n+1}·(-1)
= (-1)^n · 2^{n+1}
= -(-2)^{n+1}

(Porque (-1)^n · 2^{n+1} = (-1)^n · 2 · 2^n = -[(-1)^{n+1} · 2^{n+1}] = ... veamos:
(-1)^n · 2^{n+1} = (-1)^n · 2 · 2^n = 2 · [(-1)^n · 2^n] = 2 · (-2)^n
Pero (-2)^{n+1} = (-2)·(-2)^n = -2·(-2)^n

Entonces: 2·(-2)^n = -(-2)^{n+1}? Verifiquemos con n=0: 2·(-2)^0 = 2 y -(-2)^1 = -(-2) = 2. Si ✓)

Entonces los terminos con base (-2) suman: -(-2)^{n+1}

**Total:**

a_{n+1} = 2·4^{n+1} - (-2)^{n+1}

Que es exactamente la formula evaluada en n+1. **Queda demostrado.** ∎

**Respuesta:** a_n = 2 · 4^n - (-2)^n

**Tips para el examen:**
- Siempre reescribir la recurrencia en forma estandar (todo a un lado, igualado a cero) antes de plantear la ecuacion caracteristica.
- Verificar la solucion calculando al menos 3 terminos.
- En la induccion para recurrencias de orden 2, se necesitan DOS casos base (n=2 y n=3, o n=0 y n=1).

**Errores comunes a evitar:**
- Confundir los signos al armar la ecuacion caracteristica. Si la recurrencia es a_n = 2·a_{n-1} + 8·a_{n-2}, la caracteristica es r^2 - 2r - 8 = 0 (se cambian los signos al pasar al otro lado).
- Olvidar que (-2)^n alterna signo segun la paridad de n.
- No verificar con las condiciones iniciales despues de hallar C_1 y C_2.

---

### Ejercicio 8b — Recurrencia lineal homogenea de orden 2 (segunda variante)

**Enunciado:** Resolver a_{n+2} - 3·a_{n+1} + 2·a_n = 0, con a_0 = 7 y a_1 = 8.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 2, con coeficientes constantes. Ya esta en forma estandar.

**Resolucion paso a paso:**

**Paso 1 — Ecuacion caracteristica:**

De a_{n+2} - 3·a_{n+1} + 2·a_n = 0, reemplazamos:

r^2 - 3r + 2 = 0

**Paso 2 — Resolver la ecuacion caracteristica:**

Factorizamos: (r - 1)(r - 2) = 0

Verificacion: r^2 - 2r - r + 2 = r^2 - 3r + 2 ✓

Raices: r_1 = 1, r_2 = 2 (reales y distintas).

**Paso 3 — Solucion general:**

a_n = C_1 · 1^n + C_2 · 2^n = C_1 + C_2 · 2^n

(Nota: 1^n = 1 para todo n, asi que se simplifica.)

**Paso 4 — Aplicar condiciones iniciales:**

Con a_0 = 7:

a_0 = C_1 + C_2 · 2^0 = C_1 + C_2 = 7  ... (I)

Con a_1 = 8:

a_1 = C_1 + C_2 · 2^1 = C_1 + 2·C_2 = 8  ... (II)

**Paso 5 — Resolver el sistema:**

Restamos (I) de (II):

(C_1 + 2·C_2) - (C_1 + C_2) = 8 - 7
C_2 = 1

De (I): C_1 = 7 - C_2 = 7 - 1 = 6

**Paso 6 — Solucion particular:**

a_n = 6 + 1 · 2^n = 6 + 2^n

**Paso 7 — Verificacion:**

- a_0 = 6 + 2^0 = 6 + 1 = 7 ✓
- a_1 = 6 + 2^1 = 6 + 2 = 8 ✓
- a_2 por recurrencia: a_2 = 3·a_1 - 2·a_0 = 3·8 - 2·7 = 24 - 14 = 10
- a_2 por formula: 6 + 2^2 = 6 + 4 = 10 ✓
- a_3 por recurrencia: a_3 = 3·a_2 - 2·a_1 = 3·10 - 2·8 = 30 - 16 = 14
- a_3 por formula: 6 + 2^3 = 6 + 8 = 14 ✓

**Respuesta:** a_n = 6 + 2^n

**Tips para el examen:**
- Cuando una raiz es r = 1, el termino correspondiente es C·1^n = C (una constante). Esto simplifica mucho la expresion final.
- Siempre verificar con al menos un termino mas alla de las condiciones iniciales.

**Errores comunes a evitar:**
- Olvidar que la ecuacion caracteristica se saca directamente de los coeficientes de la recurrencia.
- Escribir 1^n como n (error grave: 1^n = 1, no n).

---

### Ejercicio 8c — Recurrencia lineal homogenea de orden 2 (tercera variante)

**Enunciado:** Resolver a_{n+2} - 4·a_{n+1} - 5·a_n = 0, con a_0 = 4 y a_1 = 2.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 2, con coeficientes constantes.

**Resolucion paso a paso:**

**Paso 1 — Ecuacion caracteristica:**

r^2 - 4r - 5 = 0

**Paso 2 — Resolver la ecuacion caracteristica:**

Factorizamos: (r - 5)(r + 1) = 0

Verificacion: r^2 + r - 5r - 5 = r^2 - 4r - 5 ✓

Raices: r_1 = 5, r_2 = -1 (reales y distintas).

**Paso 3 — Solucion general:**

a_n = C_1 · 5^n + C_2 · (-1)^n

**Paso 4 — Aplicar condiciones iniciales:**

Con a_0 = 4:

a_0 = C_1 · 5^0 + C_2 · (-1)^0 = C_1 + C_2 = 4  ... (I)

Con a_1 = 2:

a_1 = C_1 · 5^1 + C_2 · (-1)^1 = 5·C_1 - C_2 = 2  ... (II)

**Paso 5 — Resolver el sistema:**

Sumamos (I) y (II):

(C_1 + C_2) + (5·C_1 - C_2) = 4 + 2
6·C_1 = 6
C_1 = 1

De (I): C_2 = 4 - C_1 = 4 - 1 = 3

**Paso 6 — Solucion particular:**

a_n = 1 · 5^n + 3 · (-1)^n = 5^n + 3·(-1)^n

**Paso 7 — Verificacion:**

- a_0 = 5^0 + 3·(-1)^0 = 1 + 3 = 4 ✓
- a_1 = 5^1 + 3·(-1)^1 = 5 - 3 = 2 ✓
- a_2 por recurrencia: a_2 = 4·a_1 + 5·a_0 = 4·2 + 5·4 = 8 + 20 = 28
- a_2 por formula: 5^2 + 3·(-1)^2 = 25 + 3 = 28 ✓
- a_3 por recurrencia: a_3 = 4·a_2 + 5·a_1 = 4·28 + 5·2 = 112 + 10 = 122
- a_3 por formula: 5^3 + 3·(-1)^3 = 125 - 3 = 122 ✓

**Respuesta:** a_n = 5^n + 3·(-1)^n

**Tips para el examen:**
- Cuando las raices son de signo opuesto (como 5 y -1), sumar las ecuaciones del sistema elimina una incognita limpiamente.
- El termino (-1)^n alterna: vale 1 si n es par, -1 si n es impar.

**Errores comunes a evitar:**
- Confundir el signo en la ecuacion caracteristica: el coeficiente de a_n es -5, no +5.
- Al plantear la condicion a_1, olvidar que (-1)^1 = -1.

---

## TIER 2 — MEDIA PRIORIDAD

---

### Ejercicio 4 — Recurrencia lineal homogenea de orden 1 (formula cerrada + induccion)

**Enunciado:** Dada a_n = 3·a_{n-1} con a_0 = 4:
a) Calcular los siguientes 4 elementos.
b) Hallar expresion no recursiva (formula cerrada).
c) Probar por induccion.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 1, con coeficientes constantes. Es la mas simple: una progresion geometrica.

**Resolucion paso a paso:**

**Parte a) — Calcular a_1, a_2, a_3, a_4:**

- a_0 = 4 (dato)
- a_1 = 3 · a_0 = 3 · 4 = **12**
- a_2 = 3 · a_1 = 3 · 12 = **36**
- a_3 = 3 · a_2 = 3 · 36 = **108**
- a_4 = 3 · a_3 = 3 · 108 = **324**

La sucesion es: 4, 12, 36, 108, 324, ...

**Parte b) — Hallar formula cerrada:**

Observemos el patron:
- a_0 = 4 = 4 · 3^0
- a_1 = 12 = 4 · 3^1
- a_2 = 36 = 4 · 3^2
- a_3 = 108 = 4 · 3^3
- a_4 = 324 = 4 · 3^4

La formula cerrada es:

**a_n = 4 · 3^n**

Alternativamente, podemos obtenerla resolviendo la ecuacion caracteristica:

La recurrencia es a_n - 3·a_{n-1} = 0. Ecuacion caracteristica: r - 3 = 0, raiz r = 3.

Solucion general: a_n = C · 3^n.

Con a_0 = 4: C · 3^0 = C = 4.

Por lo tanto: a_n = 4 · 3^n.

**Parte c) — Demostracion por induccion:**

Queremos probar que a_n = 4 · 3^n para todo n >= 0.

**Caso base (n = 0):**

a_0 = 4 · 3^0 = 4 · 1 = 4 ✓ (coincide con el dato)

**Hipotesis inductiva:** Supongamos que a_k = 4 · 3^k para algun k >= 0.

**Paso inductivo (probar para k+1):**

Por la recurrencia: a_{k+1} = 3 · a_k

Aplicamos la hipotesis inductiva:

a_{k+1} = 3 · (4 · 3^k) = 4 · 3 · 3^k = 4 · 3^{k+1}

Que es exactamente la formula evaluada en k+1. **Queda demostrado.** ∎

**Respuesta:** a_n = 4 · 3^n

**Tips para el examen:**
- Las recurrencias de orden 1 de la forma a_n = c · a_{n-1} siempre tienen solucion a_n = a_0 · c^n.
- La induccion para recurrencias de orden 1 solo necesita UN caso base.

**Errores comunes a evitar:**
- No confundir a_n = 3^n (sin el factor 4) como solucion.
- En la induccion, el paso inductivo debe USAR la recurrencia, no solo la formula.

---

### Ejercicio 5 — Clasificacion de recurrencias

**Enunciado:** Clasificar segun orden, grado, homogeneidad y tipo de coeficientes.

**Identificacion del tipo:** Ejercicio teorico de clasificacion. Se analizan las propiedades de cada recurrencia sin resolverla.

**Conceptos clave para clasificar:**

- **Orden:** La diferencia entre el mayor y menor subindice de a que aparece.
- **Grado:** El mayor exponente al que esta elevado algun termino a_k. Si todos los a_k aparecen a la primera potencia, el grado es 1 (lineal).
- **Homogeneidad:** Si NO hay terminos independientes de a (terminos que son solo funciones de n o constantes), es homogenea. Si hay terminos "sueltos", es no homogenea.
- **Coeficientes constantes:** Si los coeficientes que multiplican a los a_k son numeros fijos (no dependen de n), son constantes. Si dependen de n, son variables.

**Resolucion paso a paso:**

**a) a_n = 2·a_{n-1} + 3**

Reescribimos: a_n - 2·a_{n-1} = 3

- **Orden:** Los subindices son n y n-1. Orden = n - (n-1) = **1**
- **Grado:** Todos los terminos a_k aparecen a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** Hay un termino independiente "+3". Es **no homogenea**
- **Coeficientes:** El coeficiente de a_n es 1 y el de a_{n-1} es -2, ambos constantes. **Coeficientes constantes**

**Clasificacion: Lineal, de orden 1, no homogenea, con coeficientes constantes.**

---

**b) a_{n+1} = 3·a_n - a_{n-1} + 1**

Reescribimos: a_{n+1} - 3·a_n + a_{n-1} = 1

- **Orden:** Los subindices son n+1, n, n-1. Orden = (n+1) - (n-1) = **2**
- **Grado:** Todos a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** Hay un termino "+1". Es **no homogenea**
- **Coeficientes:** 1, -3, 1, todos constantes. **Coeficientes constantes**

**Clasificacion: Lineal, de orden 2, no homogenea, con coeficientes constantes.**

---

**c) a_{n+1} = a_n + n^2**

Reescribimos: a_{n+1} - a_n = n^2

- **Orden:** Los subindices son n+1 y n. Orden = (n+1) - n = **1**
- **Grado:** Todos a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** Hay un termino n^2 (que depende de n pero no de a). Es **no homogenea**
- **Coeficientes:** El coeficiente de a_{n+1} es 1 y el de a_n es -1, ambos constantes. **Coeficientes constantes**

**Clasificacion: Lineal, de orden 1, no homogenea, con coeficientes constantes.**

(Nota: n^2 es el termino no homogeneo, no un coeficiente. Los coeficientes son los que multiplican a los a_k.)

---

**d) a_{n+2} = a_n - 3·a_{n-1} + 4·a_{n-2}**

Reescribimos: a_{n+2} - a_n + 3·a_{n-1} - 4·a_{n-2} = 0

- **Orden:** Los subindices son n+2, n, n-1, n-2. Orden = (n+2) - (n-2) = **4**
- **Grado:** Todos a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** No hay terminos independientes de a. Es **homogenea**
- **Coeficientes:** 1, -1, 3, -4, todos constantes. **Coeficientes constantes**

**Clasificacion: Lineal, de orden 4, homogenea, con coeficientes constantes.**

**ATENCION:** El orden es 4, no 2. Aunque "falta" a_{n+1}, el orden se mide por la distancia entre el mayor y el menor subindice: (n+2) - (n-2) = 4.

---

**e) a_{n+1} - 3·a_n = 0**

- **Orden:** Los subindices son n+1 y n. Orden = **1**
- **Grado:** Todos a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** No hay terminos independientes. Es **homogenea**
- **Coeficientes:** 1 y -3, ambos constantes. **Coeficientes constantes**

**Clasificacion: Lineal, de orden 1, homogenea, con coeficientes constantes.**

---

**f) a_{n+2} = n·a_{n+1} + 2**

Reescribimos: a_{n+2} - n·a_{n+1} = 2

- **Orden:** Los subindices son n+2 y n+1. Orden = (n+2) - (n+1) = **1**
- **Grado:** Todos a la primera potencia. Grado = **1** (lineal)
- **Homogeneidad:** Hay un termino "+2". Es **no homogenea**
- **Coeficientes:** El coeficiente de a_{n+2} es 1 (constante), pero el de a_{n+1} es **n** (depende de n). **Coeficientes variables**

**Clasificacion: Lineal, de orden 1, no homogenea, con coeficientes variables.**

---

**g) a_{n+2} = n·a_{n+1} + 2 ... Correccion: a_{n+2} - 4·a_{n+1} = 4·(a_n)^2**

Reescribimos: a_{n+2} - 4·a_{n+1} - 4·a_n^2 = 0

- **Orden:** Los subindices son n+2, n+1, n. Orden = (n+2) - n = **2**
- **Grado:** El termino a_n^2 esta elevado al cuadrado. Grado = **2** (NO lineal)
- **Homogeneidad:** No hay terminos independientes de a. Es **homogenea** (nota: la homogeneidad se refiere a la ausencia de terminos independientes de la sucesion)
- **Coeficientes:** 1, -4, -4, todos constantes. **Coeficientes constantes**

**Clasificacion: NO lineal (grado 2), de orden 2, homogenea, con coeficientes constantes.**

**Respuesta:** Ver clasificacion de cada inciso arriba.

**Tips para el examen:**
- El orden NO se cuenta por la cantidad de terminos a_k que aparecen, sino por la diferencia entre el mayor y el menor subindice.
- Un termino como n^2 o 3^n que no involucra a la sucesion a es un "termino no homogeneo" (forzante), NO un coeficiente variable.
- Si algun a_k aparece con exponente mayor que 1 (como a_n^2), la recurrencia NO es lineal.

**Errores comunes a evitar:**
- En el inciso (d), decir que el orden es 2 porque los terminos "saltan". El orden es 4.
- En el inciso (f), confundir n·a_{n+1} (coeficiente variable) con a_n · a_{n+1} (no lineal).
- En el inciso (c), decir que n^2 hace que los coeficientes sean variables. n^2 no es coeficiente de ningun a_k.

---

### Ejercicio 7a — Recurrencia homogenea de orden 1 (primera variante)

**Enunciado:** Resolver a_{n+1} = 3·a_n, con a_0 = 5. Probar por induccion.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 1, con coeficientes constantes.

**Resolucion paso a paso:**

**Paso 1 — Ecuacion caracteristica:**

a_{n+1} - 3·a_n = 0 → r - 3 = 0 → r = 3

**Paso 2 — Solucion general:**

a_n = C · 3^n

**Paso 3 — Condicion inicial:**

a_0 = C · 3^0 = C = 5

**Paso 4 — Solucion particular:**

a_n = 5 · 3^n

**Paso 5 — Verificacion:**

- a_0 = 5 · 3^0 = 5 ✓
- a_1 = 5 · 3^1 = 15; por recurrencia: 3 · 5 = 15 ✓
- a_2 = 5 · 3^2 = 45; por recurrencia: 3 · 15 = 45 ✓

**Paso 6 — Demostracion por induccion:**

**Caso base (n = 0):** a_0 = 5 · 3^0 = 5 ✓

**Hipotesis inductiva:** Supongamos a_k = 5 · 3^k para algun k >= 0.

**Paso inductivo:**

a_{k+1} = 3 · a_k = 3 · (5 · 3^k) = 5 · 3^{k+1} ✓ ∎

**Respuesta:** a_n = 5 · 3^n

**Tips para el examen:**
- Este tipo de ejercicio es rapido. No perder tiempo: la formula siempre es a_n = a_0 · r^n donde r es la raiz.

**Errores comunes a evitar:**
- Ninguno grave, pero verificar siempre con a_0.

---

### Ejercicio 7b — Recurrencia homogenea de orden 1 (segunda variante)

**Enunciado:** Resolver 2·a_n - 5·a_{n+1} = 0, con a_0 = 3. Probar por induccion.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 1, con coeficientes constantes. Notar que esta escrita en orden "invertido".

**Resolucion paso a paso:**

**Paso 1 — Reescribir en forma estandar:**

2·a_n - 5·a_{n+1} = 0

Despejamos a_{n+1}:

5·a_{n+1} = 2·a_n
a_{n+1} = (2/5)·a_n

O equivalentemente: -5·a_{n+1} + 2·a_n = 0, dividimos por -5:

a_{n+1} - (2/5)·a_n = 0

**Paso 2 — Ecuacion caracteristica:**

r - 2/5 = 0 → r = 2/5

**Paso 3 — Solucion general:**

a_n = C · (2/5)^n

**Paso 4 — Condicion inicial:**

a_0 = C · (2/5)^0 = C = 3

**Paso 5 — Solucion particular:**

a_n = 3 · (2/5)^n

**Paso 6 — Verificacion:**

- a_0 = 3 · (2/5)^0 = 3 ✓
- a_1 = 3 · (2/5)^1 = 6/5; por recurrencia: (2/5) · 3 = 6/5 ✓
- Verificacion con la ecuacion original: 2·a_0 - 5·a_1 = 2·3 - 5·(6/5) = 6 - 6 = 0 ✓

**Paso 7 — Demostracion por induccion:**

**Caso base (n = 0):** a_0 = 3 · (2/5)^0 = 3 ✓

**Hipotesis inductiva:** Supongamos a_k = 3 · (2/5)^k para algun k >= 0.

**Paso inductivo:**

a_{k+1} = (2/5) · a_k = (2/5) · 3 · (2/5)^k = 3 · (2/5)^{k+1} ✓ ∎

**Respuesta:** a_n = 3 · (2/5)^n

**Tips para el examen:**
- Cuando la recurrencia esta escrita "al reves" (con a_{n+1} no como primer termino), reordenar antes de resolver.
- Las raices pueden ser fracciones; no asumir que siempre son enteros.

**Errores comunes a evitar:**
- Olvidar dividir por el coeficiente de a_{n+1} al despejar. Si 2·a_n - 5·a_{n+1} = 0, la razon es 2/5, NO 5/2.
- Confundir cual termino es el "siguiente" y cual el "anterior".

---

### Ejercicio 7c — Recurrencia homogenea de orden 1 (tercera variante)

**Enunciado:** Resolver a_n - a_{n-1} = 0, con a_0 = 4. Probar por induccion.

**Identificacion del tipo:** Recurrencia lineal, homogenea, de orden 1, con coeficientes constantes.

**Resolucion paso a paso:**

**Paso 1 — Analisis:**

a_n - a_{n-1} = 0 significa a_n = a_{n-1}

Esto quiere decir que cada termino es igual al anterior: la sucesion es constante.

**Paso 2 — Ecuacion caracteristica:**

r - 1 = 0 → r = 1

**Paso 3 — Solucion general:**

a_n = C · 1^n = C

**Paso 4 — Condicion inicial:**

a_0 = C = 4

**Paso 5 — Solucion particular:**

a_n = 4 (para todo n)

**Paso 6 — Verificacion:**

- a_0 = 4 ✓
- a_1 = 4, y a_1 = a_0 = 4 ✓
- Todos los terminos son 4. ✓

**Paso 7 — Demostracion por induccion:**

**Caso base (n = 0):** a_0 = 4 ✓

**Hipotesis inductiva:** Supongamos a_k = 4 para algun k >= 0.

**Paso inductivo:**

a_{k+1} = a_k = 4 (por hipotesis inductiva) ✓ ∎

**Respuesta:** a_n = 4

**Tips para el examen:**
- Si la raiz caracteristica es 1, la sucesion es constante.
- Es el caso mas simple posible; no complicarlo innecesariamente.

**Errores comunes a evitar:**
- Escribir a_n = 4n o a_n = 4^n. La solucion es simplemente la constante 4.

---

### Ejercicio 9 — Problema inverso: armar la ecuacion de recurrencia

**Enunciado:** Armar una ecuacion de recurrencia lineal homogenea de orden 2 que tenga por solucion a_n = 2·4^n + 3^n. Indicar condiciones iniciales.

**Identificacion del tipo:** Problema inverso. Se nos da la solucion y debemos encontrar la recurrencia. Se trabaja "al reves": de las raices a la ecuacion caracteristica, y de ahi a la recurrencia.

**Resolucion paso a paso:**

**Paso 1 — Identificar las raices de la ecuacion caracteristica:**

La solucion general de una recurrencia homogenea de orden 2 con raices distintas es:

a_n = C_1 · r_1^n + C_2 · r_2^n

Comparando con a_n = 2·4^n + 1·3^n:

- r_1 = 4 (con C_1 = 2)
- r_2 = 3 (con C_2 = 1)

**Paso 2 — Armar la ecuacion caracteristica:**

Si las raices son r = 4 y r = 3, la ecuacion caracteristica es:

(r - 4)(r - 3) = 0

Expandimos:

r^2 - 3r - 4r + 12 = 0
r^2 - 7r + 12 = 0

**Paso 3 — Traducir a recurrencia:**

La ecuacion caracteristica r^2 - 7r + 12 = 0 corresponde a la recurrencia:

a_{n+2} - 7·a_{n+1} + 12·a_n = 0

O equivalentemente:

**a_{n+2} = 7·a_{n+1} - 12·a_n**

(O con indices desplazados: a_n = 7·a_{n-1} - 12·a_{n-2})

**Paso 4 — Hallar las condiciones iniciales:**

Usamos la formula a_n = 2·4^n + 3^n:

- a_0 = 2·4^0 + 3^0 = 2·1 + 1 = **3**
- a_1 = 2·4^1 + 3^1 = 2·4 + 3 = **11**

**Paso 5 — Verificacion:**

Comprobemos que a_2 = 7·a_1 - 12·a_0:

- a_2 por formula: 2·4^2 + 3^2 = 2·16 + 9 = 32 + 9 = 41
- a_2 por recurrencia: 7·11 - 12·3 = 77 - 36 = 41 ✓

Comprobemos a_3:

- a_3 por formula: 2·4^3 + 3^3 = 2·64 + 27 = 128 + 27 = 155
- a_3 por recurrencia: 7·41 - 12·11 = 287 - 132 = 155 ✓

**Respuesta:**

La recurrencia es: **a_{n+2} = 7·a_{n+1} - 12·a_n** (o equivalentemente a_n = 7·a_{n-1} - 12·a_{n-2})

Condiciones iniciales: **a_0 = 3, a_1 = 11**

**Tips para el examen:**
- El procedimiento inverso es: bases de las exponenciales → raices → ecuacion caracteristica → recurrencia.
- Los coeficientes de la recurrencia salen de expandir (r - r_1)(r - r_2) y cambiar signo al pasar de la ecuacion caracteristica a la recurrencia.

**Errores comunes a evitar:**
- Confundir los signos al pasar de la ecuacion caracteristica a la recurrencia. Si la ecuacion es r^2 - 7r + 12 = 0, la recurrencia es a_{n+2} - 7·a_{n+1} + 12·a_n = 0 (MISMOS coeficientes).
- Olvidar calcular las condiciones iniciales usando la formula dada.
- Confundir C_1 y C_2 con las raices. C_1 = 2 y C_2 = 1 son las constantes; las raices son 4 y 3.

---

### Ejercicio 10 — Clasificacion + solucion general y particular de orden 1 no homogenea

**Enunciado:** Clasificar a_{n+1} = 3·a_n + 2 segun orden, grado, homogeneidad, coeficientes. Hallar solucion general y particular para a_0 = 1.

**Identificacion del tipo:** Recurrencia lineal, no homogenea, de orden 1, con coeficientes constantes.

**Resolucion paso a paso:**

**Parte 1 — Clasificacion:**

a_{n+1} - 3·a_n = 2

- **Orden:** (n+1) - n = **1**
- **Grado:** Todos los a_k a la primera potencia → Grado **1** (lineal)
- **Homogeneidad:** Hay un termino "+2" independiente de a → **No homogenea**
- **Coeficientes:** 1 y -3, ambos constantes → **Coeficientes constantes**

**Parte 2 — Solucion homogenea asociada:**

La homogenea asociada es: a_{n+1} - 3·a_n = 0

Ecuacion caracteristica: r - 3 = 0 → r = 3

Solucion homogenea: a_n^(h) = C · 3^n

**Parte 3 — Solucion particular:**

El termino no homogeneo es f(n) = 2 (una constante, es decir un polinomio de grado 0).

Proponemos una solucion particular de la forma: a_n^(p) = A (constante).

Sustituimos en la recurrencia:

A = 3·A + 2
A - 3A = 2
-2A = 2
A = -1

Solucion particular: a_n^(p) = -1

**NOTA IMPORTANTE:** Debemos verificar que la constante propuesta no sea solucion de la homogenea. La solucion homogenea es C·3^n. Una constante equivale a C·1^n. Como 1 ≠ 3 (la raiz caracteristica), no hay conflicto. Si la raiz fuera 1, tendriamos que proponer a_n^(p) = A·n en lugar de A.

**Parte 4 — Solucion general:**

a_n = a_n^(h) + a_n^(p) = C · 3^n + (-1) = C · 3^n - 1

**Parte 5 — Solucion particular con a_0 = 1:**

a_0 = C · 3^0 - 1 = C - 1 = 1

C = 2

**Solucion particular:**

a_n = 2 · 3^n - 1

**Parte 6 — Verificacion:**

- a_0 = 2·3^0 - 1 = 2 - 1 = 1 ✓
- a_1 por recurrencia: 3·a_0 + 2 = 3·1 + 2 = 5
- a_1 por formula: 2·3^1 - 1 = 6 - 1 = 5 ✓
- a_2 por recurrencia: 3·a_1 + 2 = 3·5 + 2 = 17
- a_2 por formula: 2·3^2 - 1 = 18 - 1 = 17 ✓
- a_3 por recurrencia: 3·a_2 + 2 = 3·17 + 2 = 53
- a_3 por formula: 2·3^3 - 1 = 54 - 1 = 53 ✓

**Respuesta:**

- Clasificacion: Lineal, orden 1, no homogenea, coeficientes constantes.
- Solucion general: a_n = C · 3^n - 1
- Solucion particular (a_0 = 1): a_n = 2 · 3^n - 1

**Tips para el examen:**
- El metodo para no homogeneas es siempre: resolver la homogenea + proponer particular + sumar.
- Cuando f(n) es constante y la raiz de la caracteristica no es 1, la particular es simplemente una constante.

**Errores comunes a evitar:**
- Olvidar el termino particular al dar la solucion general. La solucion NO es solo C·3^n.
- Sustituir la condicion inicial en la solucion homogenea en vez de en la solucion GENERAL (homogenea + particular).

---

### Ejercicio 11a — Recurrencia lineal no homogenea de orden 1 con f(n) polinomio

**Enunciado:** Resolver a_n + 2·a_{n-1} = 3n^2, con a_0 = 4.

**Identificacion del tipo:** Recurrencia lineal, no homogenea, de orden 1, con coeficientes constantes. El termino no homogeneo es f(n) = 3n^2 (polinomio de grado 2).

**Resolucion paso a paso:**

**Paso 1 — Reescribir en forma estandar:**

a_n = -2·a_{n-1} + 3n^2

O equivalentemente: a_n + 2·a_{n-1} = 3n^2 (ya esta)

**Paso 2 — Resolver la homogenea asociada:**

a_n + 2·a_{n-1} = 0

Reescribimos: a_n = -2·a_{n-1}

Ecuacion caracteristica: r - (-2) = 0, es decir r + 2 = 0 → r = -2

Solucion homogenea: a_n^(h) = C · (-2)^n

**Paso 3 — Proponer solucion particular:**

f(n) = 3n^2 es un polinomio de grado 2.

Verificamos: ¿Es la raiz r = -2 igual a alguna base de f(n)? f(n) es polinomio, equivale a polinomio · 1^n. Como -2 ≠ 1, no hay resonancia.

Proponemos: a_n^(p) = An^2 + Bn + D (polinomio de grado 2)

**Paso 4 — Sustituir en la recurrencia:**

a_n^(p) + 2·a_{n-1}^(p) = 3n^2

Calculamos a_{n-1}^(p):

a_{n-1}^(p) = A(n-1)^2 + B(n-1) + D = A(n^2 - 2n + 1) + B(n - 1) + D
= An^2 - 2An + A + Bn - B + D

Sustituimos:

(An^2 + Bn + D) + 2·(An^2 - 2An + A + Bn - B + D) = 3n^2

Expandimos el lado izquierdo:

An^2 + Bn + D + 2An^2 - 4An + 2A + 2Bn - 2B + 2D = 3n^2

Agrupamos por potencias de n:

- **Terminos con n^2:** An^2 + 2An^2 = 3An^2
- **Terminos con n:** Bn - 4An + 2Bn = (3B - 4A)n
- **Terminos independientes:** D + 2A - 2B + 2D = 3D + 2A - 2B

Igualamos con el lado derecho (3n^2 + 0·n + 0):

- n^2: 3A = 3 → **A = 1**
- n^1: 3B - 4A = 0 → 3B - 4 = 0 → 3B = 4 → **B = 4/3**
- n^0: 3D + 2A - 2B = 0 → 3D + 2 - 8/3 = 0 → 3D = 8/3 - 2 = 8/3 - 6/3 = 2/3 → **D = 2/9**

**Paso 5 — Solucion particular:**

a_n^(p) = n^2 + (4/3)n + 2/9

**Paso 6 — Solucion general:**

a_n = a_n^(h) + a_n^(p) = C·(-2)^n + n^2 + (4/3)n + 2/9

**Paso 7 — Aplicar condicion inicial a_0 = 4:**

a_0 = C·(-2)^0 + 0 + 0 + 2/9 = C + 2/9 = 4

C = 4 - 2/9 = 36/9 - 2/9 = 34/9

**Paso 8 — Solucion final:**

a_n = (34/9)·(-2)^n + n^2 + (4/3)n + 2/9

**Paso 9 — Verificacion:**

Para n = 0:
a_0 = (34/9)·1 + 0 + 0 + 2/9 = 34/9 + 2/9 = 36/9 = 4 ✓

Para n = 1:
- Por recurrencia: a_1 + 2·a_0 = 3·1^2 → a_1 + 8 = 3 → a_1 = -5
- Por formula: (34/9)·(-2)^1 + 1 + 4/3 + 2/9 = -68/9 + 1 + 4/3 + 2/9
  = -68/9 + 9/9 + 12/9 + 2/9 = (-68 + 9 + 12 + 2)/9 = -45/9 = -5 ✓

Para n = 2:
- Por recurrencia: a_2 + 2·a_1 = 3·4 → a_2 + 2·(-5) = 12 → a_2 - 10 = 12 → a_2 = 22
- Por formula: (34/9)·(-2)^2 + 4 + 8/3 + 2/9 = (34/9)·4 + 4 + 8/3 + 2/9
  = 136/9 + 36/9 + 24/9 + 2/9 = 198/9 = 22 ✓

**Respuesta:** a_n = (34/9)·(-2)^n + n^2 + (4/3)·n + 2/9

**Tips para el examen:**
- Cuando f(n) es un polinomio de grado k, la particular propuesta es un polinomio GENERICO de grado k (con k+1 coeficientes indeterminados).
- Hay que expandir a_{n-1}^(p) con cuidado, desarrollando (n-1)^2, etc.
- Agrupar por potencias de n y armar un sistema de ecuaciones.

**Errores comunes a evitar:**
- Olvidar algun termino al expandir (n-1)^2 = n^2 - 2n + 1.
- Proponer un polinomio de grado incorrecto (ej: grado 1 cuando f(n) es de grado 2).
- Usar el coeficiente D como constante e inadvertidamente llamarlo C (confundiendolo con la constante de la homogenea).

---

### Ejercicio 11b — Recurrencia lineal no homogenea de orden 1 con f(n) exponencial

**Enunciado:** Resolver a_n - 2·a_{n-1} = 3^n, con a_0 = 5.

**Identificacion del tipo:** Recurrencia lineal, no homogenea, de orden 1, con coeficientes constantes. El termino no homogeneo es f(n) = 3^n (exponencial).

**Resolucion paso a paso:**

**Paso 1 — Resolver la homogenea asociada:**

a_n - 2·a_{n-1} = 0 → a_n = 2·a_{n-1}

Ecuacion caracteristica: r - 2 = 0 → r = 2

Solucion homogenea: a_n^(h) = C · 2^n

**Paso 2 — Proponer solucion particular:**

f(n) = 3^n es una exponencial de base 3.

Verificamos resonancia: ¿Es 3 raiz de la ecuacion caracteristica? La raiz es r = 2, y 3 ≠ 2. No hay resonancia.

Proponemos: a_n^(p) = A · 3^n

**Paso 3 — Sustituir en la recurrencia:**

a_n^(p) - 2·a_{n-1}^(p) = 3^n

A·3^n - 2·A·3^{n-1} = 3^n

Factorizamos A·3^{n-1}:

A·3^{n-1}·(3 - 2) = 3^n

A·3^{n-1}·1 = 3^n

A·3^{n-1} = 3^n

A = 3^n / 3^{n-1} = 3

**Paso 4 — Solucion particular:**

a_n^(p) = 3 · 3^n = 3^{n+1}

**Paso 5 — Solucion general:**

a_n = C · 2^n + 3^{n+1}

**Paso 6 — Aplicar condicion inicial a_0 = 5:**

a_0 = C · 2^0 + 3^1 = C + 3 = 5

C = 2

**Paso 7 — Solucion final:**

a_n = 2 · 2^n + 3^{n+1} = 2^{n+1} + 3^{n+1}

**Paso 8 — Verificacion:**

Para n = 0: a_0 = 2^1 + 3^1 = 2 + 3 = 5 ✓

Para n = 1:
- Por recurrencia: a_1 = 2·a_0 + 3^1 = 2·5 + 3 = 13
- Por formula: 2^2 + 3^2 = 4 + 9 = 13 ✓

Para n = 2:
- Por recurrencia: a_2 = 2·a_1 + 3^2 = 2·13 + 9 = 35
- Por formula: 2^3 + 3^3 = 8 + 27 = 35 ✓

Para n = 3:
- Por recurrencia: a_3 = 2·a_2 + 3^3 = 2·35 + 27 = 97
- Por formula: 2^4 + 3^4 = 16 + 81 = 97 ✓

**Respuesta:** a_n = 2^{n+1} + 3^{n+1}

**Tips para el examen:**
- Cuando f(n) = c^n y c NO es raiz de la caracteristica, la particular es simplemente A·c^n.
- Factorizar c^{n-1} ayuda a simplificar rapidamente.
- Observar que la solucion final tiene una forma muy elegante: 2^{n+1} + 3^{n+1}.

**Errores comunes a evitar:**
- Proponer a_n^(p) = A·n·3^n cuando no hay resonancia (eso solo se hace cuando 3 ES raiz de la caracteristica).
- Olvidar que a_{n-1}^(p) = A·3^{n-1}, no A·3^n.

---

### Ejercicio 11c — Recurrencia lineal no homogenea de orden 1 con f(n) lineal

**Enunciado:** Resolver a_n = a_{n-1} + 2n - 1, con a_1 = 2.

**Identificacion del tipo:** Recurrencia lineal, no homogenea, de orden 1, con coeficientes constantes. El termino no homogeneo es f(n) = 2n - 1 (polinomio de grado 1). Notar que la condicion inicial es a_1 = 2 (no a_0).

**Resolucion paso a paso:**

**Paso 1 — Reescribir en forma estandar:**

a_n - a_{n-1} = 2n - 1

**Paso 2 — Resolver la homogenea asociada:**

a_n - a_{n-1} = 0 → a_n = a_{n-1}

Ecuacion caracteristica: r - 1 = 0 → r = 1

Solucion homogenea: a_n^(h) = C · 1^n = C

**Paso 3 — Proponer solucion particular:**

f(n) = 2n - 1 es un polinomio de grado 1 (equivale a un polinomio de grado 1 multiplicado por 1^n).

**ATENCION - HAY RESONANCIA:** La raiz de la ecuacion caracteristica es r = 1, y f(n) es un polinomio multiplicado por 1^n. Como 1 es raiz de la caracteristica, debemos multiplicar la propuesta por n.

Sin resonancia propondriamos: An + B
Con resonancia (multiplicamos por n): a_n^(p) = n·(An + B) = An^2 + Bn

**Paso 4 — Sustituir en la recurrencia:**

a_n^(p) - a_{n-1}^(p) = 2n - 1

Calculamos:
- a_n^(p) = An^2 + Bn
- a_{n-1}^(p) = A(n-1)^2 + B(n-1) = A(n^2 - 2n + 1) + Bn - B = An^2 - 2An + A + Bn - B

Restamos:

a_n^(p) - a_{n-1}^(p) = (An^2 + Bn) - (An^2 - 2An + A + Bn - B)
= An^2 + Bn - An^2 + 2An - A - Bn + B
= 2An + (B - A)

Igualamos con 2n - 1:

- Coeficiente de n: 2A = 2 → **A = 1**
- Termino independiente: B - A = -1 → B - 1 = -1 → **B = 0**

**Paso 5 — Solucion particular:**

a_n^(p) = 1·n^2 + 0·n = n^2

**Paso 6 — Solucion general:**

a_n = C + n^2

**Paso 7 — Aplicar condicion inicial a_1 = 2:**

a_1 = C + 1^2 = C + 1 = 2

C = 1

**Paso 8 — Solucion final:**

a_n = 1 + n^2 = n^2 + 1

**Paso 9 — Verificacion:**

- a_1 = 1 + 1 = 2 ✓
- a_2 por recurrencia: a_1 + 2·2 - 1 = 2 + 4 - 1 = 5
- a_2 por formula: 4 + 1 = 5 ✓
- a_3 por recurrencia: a_2 + 2·3 - 1 = 5 + 6 - 1 = 10
- a_3 por formula: 9 + 1 = 10 ✓
- a_4 por recurrencia: a_3 + 2·4 - 1 = 10 + 8 - 1 = 17
- a_4 por formula: 16 + 1 = 17 ✓

**Observacion interesante:** La recurrencia a_n = a_{n-1} + 2n - 1 con a_1 = 1 daria a_n = n^2 (la suma de los primeros n impares). Aqui, con a_1 = 2, obtenemos n^2 + 1.

**Respuesta:** a_n = n^2 + 1

**Tips para el examen:**
- SIEMPRE verificar si hay resonancia antes de proponer la particular. Resonancia ocurre cuando la base de la exponencial en f(n) coincide con una raiz de la caracteristica.
- Cuando hay resonancia, se multiplica la propuesta por n (o n^2 si la raiz es doble, etc.).
- En este caso f(n) = (2n-1)·1^n y la raiz es r = 1, asi que hay resonancia.

**Errores comunes a evitar:**
- No detectar la resonancia. Si proponemos a_n^(p) = An + B sin el factor n extra, al sustituir se obtendria un sistema incompatible (sin solucion).
- Confundir la condicion a_1 = 2 con a_0 = 2. Aca la condicion es para n = 1.

---

### Ejercicio 11d — Recurrencia lineal no homogenea de orden 1 con f(n) exponencial (segunda variante)

**Enunciado:** Resolver a_n + 2·a_{n-1} = 5·3^n, con a_0 = -1.

**Identificacion del tipo:** Recurrencia lineal, no homogenea, de orden 1, con coeficientes constantes. El termino no homogeneo es f(n) = 5·3^n (exponencial).

**Resolucion paso a paso:**

**Paso 1 — Reescribir:**

a_n = -2·a_{n-1} + 5·3^n

**Paso 2 — Resolver la homogenea asociada:**

a_n + 2·a_{n-1} = 0 → a_n = -2·a_{n-1}

Ecuacion caracteristica: r + 2 = 0 → r = -2

Solucion homogenea: a_n^(h) = C · (-2)^n

**Paso 3 — Proponer solucion particular:**

f(n) = 5·3^n, base exponencial = 3.

Verificamos resonancia: ¿Es 3 raiz de la caracteristica? La raiz es -2, y 3 ≠ -2. No hay resonancia.

Proponemos: a_n^(p) = A · 3^n

**Paso 4 — Sustituir en la recurrencia:**

a_n^(p) + 2·a_{n-1}^(p) = 5·3^n

A·3^n + 2·A·3^{n-1} = 5·3^n

Factorizamos A·3^{n-1}:

A·3^{n-1}·(3 + 2) = 5·3^n

A·3^{n-1}·5 = 5·3^n

5A·3^{n-1} = 5·3^n

A·3^{n-1} = 3^n

A = 3^n / 3^{n-1} = 3

**Paso 5 — Solucion particular:**

a_n^(p) = 3 · 3^n = 3^{n+1}

**Paso 6 — Solucion general:**

a_n = C · (-2)^n + 3^{n+1}

**Paso 7 — Aplicar condicion inicial a_0 = -1:**

a_0 = C · (-2)^0 + 3^1 = C + 3 = -1

C = -4

**Paso 8 — Solucion final:**

a_n = -4 · (-2)^n + 3^{n+1}

Podemos reescribir: a_n = -4·(-2)^n + 3^{n+1} = (-1)·4·(-2)^n + 3^{n+1} = (-1)·(-2)^2·(-2)^n + 3^{n+1} = -(-2)^{n+2} + 3^{n+1}

O dejarlo como esta: a_n = 3^{n+1} - 4·(-2)^n

**Paso 9 — Verificacion:**

Para n = 0:
a_0 = 3^1 - 4·(-2)^0 = 3 - 4 = -1 ✓

Para n = 1:
- Por recurrencia: a_1 + 2·a_0 = 5·3^1 → a_1 + 2·(-1) = 15 → a_1 - 2 = 15 → a_1 = 17
- Por formula: 3^2 - 4·(-2)^1 = 9 - 4·(-2) = 9 + 8 = 17 ✓

Para n = 2:
- Por recurrencia: a_2 + 2·a_1 = 5·3^2 → a_2 + 34 = 45 → a_2 = 11
- Por formula: 3^3 - 4·(-2)^2 = 27 - 4·4 = 27 - 16 = 11 ✓

Para n = 3:
- Por recurrencia: a_3 + 2·a_2 = 5·3^3 → a_3 + 22 = 135 → a_3 = 113
- Por formula: 3^4 - 4·(-2)^3 = 81 - 4·(-8) = 81 + 32 = 113 ✓

**Respuesta:** a_n = 3^{n+1} - 4·(-2)^n

**Tips para el examen:**
- El procedimiento es identico al Ej. 11b: proponer A·c^n, sustituir, resolver para A.
- Factorizar c^{n-1} siempre simplifica el calculo.
- Es buena practica reescribir la solucion de la forma mas simple posible.

**Errores comunes a evitar:**
- Confundir el signo en la ecuacion: a_n + 2·a_{n-1} = 5·3^n tiene un +2, lo que da la ecuacion caracteristica r + 2 = 0 (raiz r = -2), NO r - 2 = 0.
- Al sustituir la particular, olvidar que a_{n-1}^(p) = A·3^{n-1} (con n-1 en el exponente).

---

## Resumen de Metodos

### Recurrencias lineales homogeneas con coeficientes constantes

| Orden | Metodo |
|-------|--------|
| 1: a_n = r·a_{n-1} | Solucion: a_n = a_0·r^n |
| 2: raices reales distintas r_1, r_2 | a_n = C_1·r_1^n + C_2·r_2^n |
| 2: raiz doble r | a_n = (C_1 + C_2·n)·r^n |

### Recurrencias lineales NO homogeneas: a_n + b·a_{n-1} = f(n)

| Tipo de f(n) | Particular propuesta (sin resonancia) | Con resonancia |
|-------------|---------------------------------------|----------------|
| Constante k | a_n^(p) = A | a_n^(p) = A·n |
| Polinomio grado 1 | a_n^(p) = An + B | a_n^(p) = n(An + B) |
| Polinomio grado 2 | a_n^(p) = An^2 + Bn + D | a_n^(p) = n(An^2 + Bn + D) |
| Exponencial c^n | a_n^(p) = A·c^n | a_n^(p) = A·n·c^n |

### Resonancia
Hay resonancia cuando la base de la exponencial en f(n) coincide con una raiz de la ecuacion caracteristica. En ese caso, se multiplica la propuesta por n.

### Procedimiento general para no homogeneas:
1. Resolver la homogenea asociada → a_n^(h)
2. Proponer particular segun f(n), verificando resonancia → a_n^(p)
3. Sustituir en la recurrencia y hallar coeficientes
4. Solucion general = a_n^(h) + a_n^(p)
5. Aplicar condiciones iniciales sobre la solucion GENERAL (no sobre la homogenea sola)

---

## Problema inverso (reconstruir la recurrencia)

### Procedimiento:
1. Identificar las bases de las exponenciales en la solucion → son las raices r_1, r_2
2. Armar la ecuacion caracteristica: (r - r_1)(r - r_2) = 0
3. Expandir y traducir a recurrencia
4. Calcular a_0 y a_1 usando la formula dada
