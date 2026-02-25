# Relaciones de Recurrencia

## Que es y que NO es este subtema

**QUE ES:** Clasificar, resolver y construir relaciones de recurrencia lineales de orden 1 y 2 (homogeneas y no homogeneas), con coeficientes constantes. Verificar soluciones por induccion.

**QUE NO ES:** Combinatoria, principio de conteo, permutaciones/combinaciones (salvo que aparezcan como aplicacion de recurrencia).

## Contexto del Examen
- Formato tipico: resolver 1 relacion de recurrencia de orden 2 (homogenea o no homogenea)
- Pueden pedir: clasificar la relacion, hallar la solucion general, hallar la solucion particular con condiciones iniciales
- Pueden pedir: verificar la solucion por induccion
- Pueden pedir: problema inverso (dada una formula cerrada, construir la recurrencia)

---

## HOJA DE TEORIA (Teoria Condensada)

### 1. Clasificacion de Relaciones de Recurrencia
| Criterio | Opciones |
|----------|----------|
| **Orden** | Cantidad de terminos anteriores que usa (orden 1: usa a_{n-1}, orden 2: usa a_{n-1} y a_{n-2}) |
| **Grado** | Mayor potencia de los terminos a_i |
| **Lineal** | Los a_i aparecen con exponente 1, sin multiplicarse entre si |
| **Homogenea** | NO tiene termino independiente (f(n) = 0) |
| **No homogenea** | Tiene termino independiente f(n) ≠ 0 |
| **Coef. constantes** | Los coeficientes de los a_i no dependen de n |

### 2. Orden 1 - Lineal Homogenea con Coef. Constantes
Forma: `a_n = c · a_{n-1}` con a₁ dado

**Solucion:** a_n = c^(n-1) · a₁  (o equivalente: a_n = K · c^n)

### 3. Orden 2 - Lineal Homogenea con Coef. Constantes
Forma: `a_{n+2} + p·a_{n+1} + q·a_n = 0`  (o equivalente con subindices n, n-1, n-2)

**Paso 1:** Plantear ecuacion caracteristica: **x² + p·x + q = 0**

**Paso 2:** Resolver la ecuacion cuadratica:

| Caso | Raices | Solucion General |
|------|--------|-----------------|
| **Raices distintas** r₁ ≠ r₂ | x² + px + q = 0 tiene 2 raices | **a_n = k₁·r₁^n + k₂·r₂^n** |
| **Raiz doble** r₁ = r₂ = r | Discriminante = 0 | **a_n = k₁·r^n + k₂·n·r^n** |

**Paso 3:** Usar condiciones iniciales (a₀, a₁) para hallar k₁ y k₂ (sistema 2x2).

**Ejemplo (Fibonacci):** a_{n+2} = a_{n+1} + a_n → x² - x - 1 = 0 → r = (1±√5)/2

### 4. No Homogeneas - Metodo General
Forma: `c_n·a_n + c_{n-1}·a_{n-1} + ... = f(n)`

**Solucion general = Solucion homogenea + Solucion particular**
```
a_n = a_{nH} + a_{nP}
```

**Paso 1:** Resolver la homogenea asociada (f(n) = 0) → obtener a_{nH}

**Paso 2:** Proponer a_{nP} segun la forma de f(n):

| f(n) tiene forma | Proponer a_{nP} como |
|-------------------|---------------------|
| Constante (ej: 5) | a_{nP} = A |
| Lineal (ej: 3n+2) | a_{nP} = An + B |
| Cuadratica (ej: n²) | a_{nP} = An² + Bn + C |
| Exponencial (ej: 5^n) | a_{nP} = A·5^n |
| k^n (k es raiz de la caract.) | a_{nP} = A·n·k^n |

**IMPORTANTE:** Si la forma propuesta NO funciona (da absurdo o es linealmente dependiente de a_{nH}), **multiplicar por n** y reintentar:
- Si A no funciona → probar A·n
- Si A·n no funciona → probar A·n²

**Paso 3:** Reemplazar a_{nP} en la ecuacion original, igualar coeficientes, hallar las constantes.

**Paso 4:** a_n = a_{nH} + a_{nP}, usar condiciones iniciales para k₁, k₂.

### 5. Tabla resumen - Solucion particular para Orden 1
| f(n) | a_{nP} propuesta |
|------|-----------------|
| b (constante, raiz caract. ≠ 1) | A |
| b (constante, raiz caract. = 1) | A·n |
| b·n | A·n + B |
| b·n (raiz caract. = 1) | A·n² + B·n |
| b·s^n (s no es raiz caract.) | A·s^n |
| b·s^n (s es raiz caract.) | A·n·s^n |

### 6. Verificacion por Induccion
Dado que a_n = f(n) es solucion de una recurrencia:

**Paso base:** n = valor inicial. Verificar que f(n₀) = a_{n₀} (dato).

**Hipotesis inductiva:** Suponer a_h = f(h) para n = h.

**Tesis inductiva:** Demostrar a_{h+1} = f(h+1).

**Demostracion:** Partir de a_{h+1} (expresado con la recurrencia), reemplazar a_h por la hipotesis, operar hasta llegar a f(h+1).

### 7. Problema Inverso
Dada una formula cerrada a_n = f(n), construir la relacion de recurrencia:
1. Escribir a_n = f(n) y a_{n-1} = f(n-1)
2. Operar para eliminar constantes y obtener a_n en terminos de a_{n-1} (y posiblemente a_{n-2})
3. Verificar con los primeros terminos

---

## Metodo de Resolucion Paso a Paso

### Para RESOLVER una recurrencia de orden 2:
1. **Clasificar:** orden, lineal, homogenea/no, coef constantes
2. **Si es homogenea:**
   - Ecuacion caracteristica x² + px + q = 0
   - Hallar raices r₁, r₂
   - Escribir solucion general segun caso (distintas o doble)
   - Usar condiciones iniciales → sistema 2x2 → k₁, k₂
3. **Si es NO homogenea:**
   - Resolver la homogenea asociada → a_{nH}
   - Proponer a_{nP} segun tabla
   - Reemplazar en la ecuacion, hallar constantes
   - a_n = a_{nH} + a_{nP}
   - Condiciones iniciales → k₁, k₂

### Ejemplo resuelto completo:
`a_{n+2} - 4a_{n+1} + 3a_n = -2` con a₀ = 7, a₁ = 12

1. Homogenea: x² - 4x + 3 = 0 → x = 1 o x = 3 → a_{nH} = k₁ + k₂·3^n
2. Particular: f(n) = -2 (constante). Como 1 es raiz, probar a_{nP} = B·n
   - Reemplazar: B(n+2) - 4B(n+1) + 3Bn = -2 → -2B = -2 → B = 1
   - a_{nP} = n
3. General: a_n = k₁ + k₂·3^n + n
4. Condiciones: a₀ = k₁ + k₂ = 7, a₁ = k₁ + 3k₂ + 1 = 12 → k₁ = 5, k₂ = 2
5. **Solucion: a_n = 5 + 2·3^n + n**

---

## Referencias Cruzadas

### Ejercicios RELEVANTES
- `9_ejercicio_recurrencia.pdf` → **Ej.1-13** (todos relevantes)
- **Respuestas:** `9_respuesta_recurrencia_a.pdf` + `9_respuesta_recurrencia_b.pdf`

### Teoria de referencia
- `9_teoria_recurrencia.pdf` (completo, 27 slides)

---

## Prioridad de Practica
1. **ALTA**: Orden 2 homogenea con raices distintas (caso mas frecuente en finales)
2. **ALTA**: Orden 2 no homogenea (con f(n) constante o exponencial)
3. **MEDIA**: Orden 1 no homogenea (para entender el metodo)
4. **MEDIA**: Verificacion por induccion
5. **BAJA**: Problema inverso (menos frecuente en finales)
